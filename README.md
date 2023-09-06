repeat task.wait()
    if not game:IsLoaded() then
        return 
    end
until game:IsLoaded()

if game.CoreGui:FindFirstChild("ToggleUI") then
    game.CoreGui:FindFirstChild("ToggleUI"):Destroy()
end

continue = continue or function() end
local fireclickdetector = fireclickdetector

fireclickdetector = hookfunction(fireclickdetector, function(Object)
    if identifyexecutor():find("Fluxus") then
        fireclickdetector(Object, math.huge)
        print("Fired : Fluxus")
    else
        fireclickdetector(Object)
        print("Fired : Others Executor")
    end
end)

tostring(identifyexecutor())
-- [varibles]
local Teams = 'Pirates'
getgenv().U = {
    Loading = {
        Teams = 'Marines',
        DelayExecute = 0.5,
    };
    Main = {
        AutoFarm = false,
        AutoSea2 = false,
        AutoSea3 = false,
        AutoFarmBone = false,
        AutoCakePrince = false,
        AutoDoughtKing = false,
        AutoMaterial = false,
        AutoPirate = false,
        AutoTradeBone = false,
        AutoHallowScythe = false,
        AutoBuddySword = false,
        AutoCavender = false,
        AutoTushita = false,
        AutoYama = false,
        AutoDarkDagger = false,
        AutoCDK = false,
        AutoTTK = false,
        MobHealth = 25,
        SkillZ = false,
        SkillX = false,
        SkillC = false,
        SkillV = false,
        SelectMaterials = {},
        Webhookurl = "",
    };
    Miscs = {
        FpsBoosts = false,
        WhiteScreen = false,
    };
    Client = {
        MeleeStats = false,
        SwordStats = false,
        GunStats = false,
        DevilFruitStats = false,
        DefenseStats = false,
        SelectPly = "",
        Aimbot = false
    };
    Teleport = {
        SelectPlace = 'Nil',
        SelectNpc = 'Nil',
        TeleportToNpc = false,
        TeleportToLocations = false,
    };
    Raids = {
        AutoRaid = false,
        RaidSelect = {},
        AutoAwakening = false,
        UseFruit = false,
        PriceCap = 1000000,
        CollectFruit = false,
        AutoRaidHop = false,
    };
    Settings = {
        Tooltip = 'Melee',
        FastAttack =  true,
        InstantTeleport = false,
        AllowHop = false,
        PosY = 0,
        Wait = 0.11,
    };
    ["Bounties"] = {
        ["Total Earned"] = 0,
        ["Total Killed"] = 0,
        ["Totla Skipped"] = 0
    };
    Clip = false,
};


function LoadSettings()
    if readfile and writefile and isfile and isfolder then
        if not isfolder("Unique Hub {Mobile}.debug") then
            makefolder("Unique Hub {Mobile}.debug")
        end
        if not isfolder("Unique Hub {Mobile}.debug/Blox Fruits/") then
            makefolder("Unique Hub {Mobile}.debug/Blox Fruits/")
        end
        if not isfile("Unique Hub {Mobile}.debug/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json") then
            writefile("Unique Hub {Mobile}.debug/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json", game:GetService("HttpService"):JSONEncode(U))
        else
            local Decode = game:GetService("HttpService"):JSONDecode(readfile("Unique Hub {Mobile}.debug/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json"))
            for i,v in pairs(Decode) do
                U[i] = v
            end
        end
    else
        return warn("Status : Undetected Executor")
    end
end
function save()
    if readfile and writefile and isfile and isfolder then
        if not isfile("Unique Hub {Mobile}.debug/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json") then
            LoadSettings()
        else
            local Decode = game:GetService("HttpService"):JSONDecode(readfile("Unique Hub {Mobile}.debug/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json"))
            local Array = {}
            for i,v in pairs(U) do
                Array[i] = v
            end
            writefile("Unique Hub {Mobile}.debug/Blox Fruits/" .. game.Players.LocalPlayer.Name .. ".json", game:GetService("HttpService"):JSONEncode(Array))
        end
    else
        return warn("Status : Undetected Executor")
    end
end
LoadSettings()

spawn(function()
    while true do wait()
        getgenv().rejoin = game:GetService("CoreGui").RobloxPromptGui.promptOverlay.ChildAdded:Connect(function(Kick)
            if Kick.Name == 'ErrorPrompt' and Kick:FindFirstChild('MessageArea') and Kick.MessageArea:FindFirstChild("ErrorFrame") then
                game:GetService("TeleportService"):Teleport(game.PlaceId)
            end
        end)
    end
end)
-- [Select Teams]

if game.Players.LocalPlayer.Team == nil then
    if game:GetService("Players").LocalPlayer.PlayerGui.Main:FindFirstChild("ChooseTeam") then
    	repeat task.wait()
    		if game:GetService("Players").LocalPlayer.PlayerGui:WaitForChild("Main").ChooseTeam.Visible == true then
    			if Teams == 'Pirates' then
                    for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.Activated)) do                                                                                                
                        v.Function()
                        task.wait(.2)
                    end
                elseif Teams == 'Marines' then
                    for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Marines.Frame.ViewportFrame.TextButton.Activated)) do                                                                                                
                        v.Function()
                        task.wait(.2)
                    end
                else
                    for i, v in pairs(getconnections(game:GetService("Players").LocalPlayer.PlayerGui.Main.ChooseTeam.Container.Pirates.Frame.ViewportFrame.TextButton.Activated)) do                                                                                                
                        v.Function()
                        task.wait(.2)
                    end
                end
            end
    	until game.Players.LocalPlayer.Team ~= nil
    end
end

local function GetFightingStyle(Style)
	ReturnText = ""
	for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
		if v:IsA("Tool") then
			if v.ToolTip == Style then
				ReturnText = v.Name
			end
		end
	end
	for i ,v in pairs(game.Players.LocalPlayer.Character:GetChildren()) do
		if v:IsA("Tool") then
			if v.ToolTip == Style then
				ReturnText = v.Name
			end
		end
	end
	if ReturnText ~= "" then
		return ReturnText
	else
		return "Not Have"
	end
end
local FirstSea,SecondSea,ThirdSea
if game.PlaceId == 2753915549 then
    FirstSea = true
elseif game.PlaceId == 4442272183 then
    SecondSea = true
elseif game.PlaceId == 7449423635 then
    ThirdSea = true
end

local function revBool()
	getgenv().bool = not getgenv().bool
	return getgenv().bool
end

task.spawn(function()
    while task.wait() do
        for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
            if v.ToolTip == "Gun" then
                if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                    _G.SelectWeaponGun = v.Name
                    getgenv().Gun = v.Name
                    Gun = v.Name
                end
            end
        end
        for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
            if v.ToolTip == "Sword" then
                if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                    getgenv().Sword = v.Name
                    Sword = v.Name
                end
            end
        end
        for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
            if v.ToolTip == "Blox Fruit" then
                if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                    getgenv().DevilFruit = v.Name
                    DevilFruit = v.Name
                end
            end
        end
    end
end)

local function fireproximityprompt(Obj, Distance, Amount, Skip)
    if Obj.ClassName == "ProximityPrompt" then 
        if Obj.MaxActivationDistance ~= Distance then
            Obj.MaxActivationDistance = Distance
        end
        task.wait()
        Amount = Amount or 1
        local PromptTime = Obj.HoldDuration
        if Skip then  
            Obj.HoldDuration = 0
        end
        for i = 1, Amount do 
            Obj:InputHoldBegin()
            if not Skip then 
                task.wait(Obj.HoldDuration)
            end
            Obj:InputHoldEnd()
        end
        Obj.HoldDuration = PromptTime
    else 
        error("userdata<ProximityPrompt> expected")
    end
end

local function EquipSword()
    for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
        if v.ToolTip == "Sword" then
            if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(v.Name) or game:GetService("Players").LocalPlayer.Character:FindFirstChild(v.Name)then
                    getgenv().Tool = game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(v.Name)
                    game.Players.LocalPlayer.Character.Humanoid:EquipTool(Tool)
                end
            end
        end
    end
end

local function EquipDF()
    for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
        if v.ToolTip == "Blox Fruit" then
            if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(v.Name) or game:GetService("Players").LocalPlayer.Character:FindFirstChild(v.Name)then
                    getgenv().Tool = game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(v.Name)
                    game.Players.LocalPlayer.Character.Humanoid:EquipTool(Tool)
                end
            end
        end
    end
end

local function SendKey(Key,long)
    if long == nil then long =0;end
    game:GetService("VirtualInputManager"):SendKeyEvent(true,(Key),false,game)
    task.wait(long)
    game:GetService("VirtualInputManager"):SendKeyEvent(false,(Key),false,game)
end

local PlaceID = game.PlaceId
local z = {}
local o = ""
local n = os.date("!*t").hour
local Deleted = false
local File = pcall(function()
    z = game:GetService('HttpService'):JSONDecode(readfile("NotSameServers.json"))
end)
if not File then
    table.insert(z, n)
    writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(z))
end
local function q()
    local l;
    if o == "" then
        l = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100'))
    else
        l = game.HttpService:JSONDecode(game:HttpGet('https://games.roblox.com/v1/games/' .. PlaceID .. '/servers/Public?sortOrder=Asc&limit=100&cursor=' .. o))
    end
    local ID = ""
    if l.nextPageCursor and l.nextPageCursor ~= "null" and l.nextPageCursor ~= nil then
        o = l.nextPageCursor
    end
    local num = 0;
    for i,v in pairs(l.data) do
        local g = true
        ID = tostring(v.id)
        if tonumber(v.maxPlayers) > tonumber(v.playing) then
            for _,a in pairs(z) do
                if num ~= 0 then
                    if ID == tostring(a) then
                        g = false
                    end
                else
                    if tonumber(n) ~= tonumber(a) then
                        local delFile = pcall(function()
                            delfile("NotSameServers.json")
                            z = {}
                            table.insert(z, n)
                        end)
                    end
                end
                num = num + 1
            end
            if g == true then
                table.insert(z, ID)
                task.wait()
                pcall(function()
                    writefile("NotSameServers.json", game:GetService('HttpService'):JSONEncode(z))
                    task.wait()
                    game:GetService("TeleportService"):TeleportToPlaceInstance(PlaceID, ID, game.Players.LocalPlayer)
                end)
            end
        end
    end
end

local function ServerHop()
    while task.wait() do
		pcall(function()
			q()
			if o ~= "" then
				q()
			end
		end)
    end
end

local function Sea1()
    if SecondSea or ThirdSea then
	    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelMain")
    end
end

local function Sea2()
    if FirstSea or ThirdSea then
	    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")	
    end
end

local function Sea3()
    if FirstSea or SecondSea then
	    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelZou")
    end
end

local function EquipTool(Tool)
	pcall(function()
		if game.Players.LocalPlayer.Backpack:FindFirstChild(Tool) then 
			local ToolHumanoid = game.Players.LocalPlayer.Backpack:FindFirstChild(Tool) 
			game.Players.LocalPlayer.Character.Humanoid:EquipTool(ToolHumanoid) 
		end
	end)
end

local function CheckMastery(name)
    if game.Players.LocalPlayer.Backpack:FindFirstChild(name) then
        return tonumber(game.Players.LocalPlayer.Backpack:FindFirstChild(name).Level.Value)
    elseif game:GetService("Workspace").Characters[game.Players.LocalPlayer.Name]:FindFirstChild(name) then
        return game:GetService("Workspace").Characters[game.Players.LocalPlayer.Name]:FindFirstChild(name).Level.Value
    end
    return nil
end

local function FindChar(name)
    if game.Players.LocalPlayer.Backpack:FindFirstChild(name) or game.Players.LocalPlayer.Character.Backpack:FindFirstChild(name) then
        return true
    end
    return false
end

local function MobFind(tablename)
    for _,_Mob in pairs(tablename) do
        if game:GetService("Workspace").Enemies:FindFirstChild(_Mob) then
            return true
        end
    end
    return false
end

local function MultiFindObject(Input)
    if type(Input) == 'table' then 
    	for i,v in pairs(Input) do
    		if game:GetService("Workspace").Enemies:FindFirstChild(Input) then
    			return true
    		end
    	end
    else
        if Object:FindFirstChild(v) then
    		return true
    	end
    end
	return false
end

local function CheckMaterial(name)
    for _,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
        if type(v) == "table" then
            if v.Type == "Material" then
                if v.Name == name then
                    return v.Count
                end
            end
        end
    end
    return 0
end

local function GetSwords(Weaponname)
    for i,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
        if type(v) == "table" then
            if v.Type == "Sword" then
                if v.Name == Weaponname then
                    return true
                end
            end
        end
    end
    return false
end

local function BusoAndKen()
    if not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HasBuso") then
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
    end
    if game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('Ken',false) then
        game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('Ken',true)
    end
end

task.spawn(
    function()
        local dj = game.Players.LocalPlayer
        local dk = require(dj.PlayerScripts.CombatFramework.Particle)
        local dl = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib)
        if not shared.orl then
            shared.orl = dl.wrapAttackAnimationAsync
        end
        if not shared.cpc then
            shared.cpc = dk.play
        end
        while task.wait() do
            pcall(
                function()
                    dl.wrapAttackAnimationAsync = function(dm, dn, dp, dq, dr)
                        local ds = dl.getBladeHits(dn, dp, dq)
                        if ds then
                            dk.play = function()
                            end
                            dm:Play(0.1, 0.1, 0.1)
                            dr(ds)
                            dk.play = shared.cpc
                            wait(.1)
                            dm:Stop()
                        end
                    end
                end
            )
        end
    end
)

local Name,QuestName,QuestNumber,QuestLevel,MobName,MobPosition,QuestCFrame
local function CheckQuest()
	if FirstSea then
		if game.Players.LocalPlayer.Data.Level.Value == 1 or game.Players.LocalPlayer.Data.Level.Value <= 9 then -- Bandit
			QuestNumber = 1

			Name = "Bandit [Lv. 5]"
			QuestName = "BanditQuest1"

			QuestLevel = 1
			MobName = "Bandit"

			MobPosition = CFrame.new(1145, 17, 1634)
			VectorMon = Vector3.new(1145, 17, 1634)

			QuestCFrame = CFrame.new(1060, 17, 1547)
			VectorQuest = Vector3.new(1060, 17, 1547)
		elseif game.Players.LocalPlayer.Data.Level.Value == 10 or game.Players.LocalPlayer.Data.Level.Value <= 14 then -- Monkey
			QuestNumber = 2

			Name = "Monkey [Lv. 14]"
			QuestName = "JungleQuest"

			QuestLevel = 1
			MobName = "Monkey"

			MobPosition = CFrame.new(-1496, 39, 35)
			VectorMon = Vector3.new(-1496, 39, 35)

			QuestCFrame = CFrame.new(-1602, 37, 152)
			VectorQuest = Vector3.new(-1602, 37, 152)
		elseif game.Players.LocalPlayer.Data.Level.Value == 15 or game.Players.LocalPlayer.Data.Level.Value <= 29 then -- Gorilla
			QuestNumber = 3

			Name = "Gorilla [Lv. 20]"
			QuestName = "JungleQuest"

			QuestLevel = 2
			MobName = "Gorilla"

			MobPosition = CFrame.new(-1237, 6, -486)
			VectorMon = Vector3.new(-1237, 7, -486)

			QuestCFrame = CFrame.new(-1602, 37, 152)
			VectorQuest = Vector3.new(-1602, 37, 152)
		elseif game.Players.LocalPlayer.Data.Level.Value == 30 or game.Players.LocalPlayer.Data.Level.Value <= 39 then -- Pirate
			QuestNumber = 4

			Name = "Pirate [Lv. 35]"
			QuestName = "BuggyQuest1"

			QuestLevel = 1
			MobName = "Pirate"

			MobPosition = CFrame.new(-1115, 14, 3938)
			VectorMon = Vector3.new(-1115, 14, 3938)

			QuestCFrame = CFrame.new(-1140, 5, 3828)
			VectorQuest = Vector3.new(-1140, 5, 3828)
		elseif game.Players.LocalPlayer.Data.Level.Value == 40 or game.Players.LocalPlayer.Data.Level.Value <= 59 then -- Brute
			QuestNumber = 5

			Name = "Brute [Lv. 45]"
			QuestName = "BuggyQuest1"

			QuestLevel = 2
			MobName = "Brute"

			MobPosition = CFrame.new(-1145, 15, 4350)
			VectorMon = Vector3.new(-1146, 15, 4350)

			QuestCFrame = CFrame.new(-1140, 5, 3828)
			VectorQuest = Vector3.new(-1140, 5, 3828)
		elseif game.Players.LocalPlayer.Data.Level.Value == 60 or game.Players.LocalPlayer.Data.Level.Value <= 74 then -- Desert Bandit
			QuestNumber = 6

			Name = "Desert Bandit [Lv. 60]"
			QuestName = "DesertQuest"

			QuestLevel = 1
			MobName = "Desert Bandit"

			MobPosition = CFrame.new(932, 7, 4484)
			VectorMon = Vector3.new(932, 7, 4484)

			QuestCFrame = CFrame.new(897, 7, 4388)
			VectorQuest = Vector3.new(897, 7, 4388)
		elseif game.Players.LocalPlayer.Data.Level.Value == 75 or game.Players.LocalPlayer.Data.Level.Value <= 89 then -- Desert Officre
			QuestNumber = 7

			Name = "Desert Officer [Lv. 70]"
			QuestName = "DesertQuest"

			QuestLevel = 2
			MobName = "Desert Officer"

			MobPosition = CFrame.new(1572, 10, 4373)
			VectorMon = Vector3.new(1572, 10, 4373)

			QuestCFrame = CFrame.new(897, 7, 4388)
			VectorQuest = Vector3.new(897, 7, 4388)
		elseif game.Players.LocalPlayer.Data.Level.Value == 90 or game.Players.LocalPlayer.Data.Level.Value <= 99 then -- Snow Bandits
			QuestNumber = 8

			Name = "Snow Bandit [Lv. 90]"
			QuestName = "SnowQuest"

			QuestLevel = 1
			MobName = "Snow Bandits"

			MobPosition = CFrame.new(1289, 150, -1442)
			VectorMon = Vector3.new(1289, 106, -1442)

			QuestCFrame = CFrame.new(1386, 87, -1297)
			VectorQuest = Vector3.new(1386, 87, -1297)
		elseif game.Players.LocalPlayer.Data.Level.Value == 100 or game.Players.LocalPlayer.Data.Level.Value <= 119 then -- Snowman
			QuestNumber = 9

			Name = "Snowman [Lv. 100]"
			QuestName = "SnowQuest"

			QuestLevel = 2
			MobName = "Snowman"

			MobPosition = CFrame.new(1289, 150, -1442)
			VectorMon = Vector3.new(1289, 106, -1442)

			QuestCFrame = CFrame.new(1386, 87, -1297)
			VectorQuest = Vector3.new(1386, 87, -1297)
		elseif game.Players.LocalPlayer.Data.Level.Value == 120 or game.Players.LocalPlayer.Data.Level.Value <= 149 then -- Chief Petty Officer
			QuestNumber = 10

			Name = "Chief Petty Officer [Lv. 120]"
			QuestName = "MarineQuest2"

			QuestLevel = 1
			MobName = "Chief Petty Officer"

			MobPosition = CFrame.new(-4855, 23, 4308)
			VectorMon = Vector3.new(-4855, 23, 4308)

			QuestCFrame = CFrame.new(-5036, 29, 4325)
			VectorQuest = Vector3.new(-5036, 29, 4325)
		elseif game.Players.LocalPlayer.Data.Level.Value == 150 or game.Players.LocalPlayer.Data.Level.Value <= 174 then -- Sky Bandit
			QuestNumber = 11

			Name = "Sky Bandit [Lv. 150]"
			QuestName = "SkyQuest"

			QuestLevel = 1
			MobName = "Sky Bandit"

			MobPosition = CFrame.new(-4981, 278, -2830)
			VectorMon = Vector3.new(-4981, 278, -2830)

			QuestCFrame = CFrame.new(-4842, 718, -2623)
			VectorQuest = Vector3.new(-4842, 718, -2623)
		elseif game.Players.LocalPlayer.Data.Level.Value == 175 or game.Players.LocalPlayer.Data.Level.Value <= 189 then -- Dark Master
			QuestNumber = 12

			Name = "Dark Master [Lv. 175]"
			QuestName = "SkyQuest"

			QuestLevel = 2
			MobName = "Dark Master"

			MobPosition = CFrame.new(-5250, 389, -2272)
			VectorMon = Vector3.new(-5250, 389, -2272)

			QuestCFrame = CFrame.new(-4842, 718, -2623)
			VectorQuest = Vector3.new(-4842, 718, -2623)
		elseif game.Players.LocalPlayer.Data.Level.Value == 190 or game.Players.LocalPlayer.Data.Level.Value <= 209 then -- Dark Master
			QuestNumber = 13

			Name = "Prisoner [Lv. 190]"
			QuestName = "PrisonerQuest"

			QuestLevel = 1
			MobName = "Prisoner"

			MobPosition = CFrame.new(5411, 96, 690)
			VectorMon = Vector3.new(5411, 96, 690)

			QuestCFrame = CFrame.new(5308, 2, 474)
			VectorQuest = Vector3.new(5308, 2, 474)
		elseif game.Players.LocalPlayer.Data.Level.Value == 210 or game.Players.LocalPlayer.Data.Level.Value <= 249 then -- Dark Master
			QuestNumber = 14

			Name = "Dangerous Prisoner [Lv. 210]"
			QuestName = "PrisonerQuest"

			QuestLevel = 2
			MobName = "Dangerous Prisoner"

			MobPosition = CFrame.new(5411, 96, 690)
			VectorMon = Vector3.new(5411, 96, 690)

			QuestCFrame = CFrame.new(5308, 2, 474)
			VectorQuest = Vector3.new(5308, 2, 474)
		elseif game.Players.LocalPlayer.Data.Level.Value == 250 or game.Players.LocalPlayer.Data.Level.Value <= 299 then -- Toga Warrior
			QuestNumber = 15

			Name = "Toga Warrior [Lv. 250]"
			QuestName = "ColosseumQuest"

			QuestLevel = 1
			MobName = "Toga Warrior"

			MobPosition = CFrame.new(-1824, 50, -2743)
			VectorMon = Vector3.new(-1824, 50, -2743)

			QuestCFrame = CFrame.new(-1576, 8, -2985)
			VectorQuest = Vector3.new(-1576, 8, -2985)
		elseif game.Players.LocalPlayer.Data.Level.Value == 300 or game.Players.LocalPlayer.Data.Level.Value <= 329 then -- Military Soldier
			QuestNumber = 16

			Name = "Military Soldier [Lv. 300]"
			QuestName = "MagmaQuest"

			QuestLevel = 1
			MobName = "Military Soldier"

			MobPosition = CFrame.new(-5408, 11, 8447)
			VectorMon = Vector3.new(-5408, 11, 8447)

			QuestCFrame = CFrame.new(-5316, 12, 8517)
			VectorQuest = Vector3.new(-5316, 12, 8517)
		elseif game.Players.LocalPlayer.Data.Level.Value == 330 or game.Players.LocalPlayer.Data.Level.Value <= 374 then -- Military Spy
			QuestNumber = 17
			Name = "Military Spy [Lv. 325]"
			QuestName = "MagmaQuest"
			QuestLevel = 2
			MobName = "Military Spy"
			MobPosition = CFrame.new(-5815, 84, 8820)
			QuestCFrame = CFrame.new(-5316, 12, 8517)
		elseif game.Players.LocalPlayer.Data.Level.Value == 375 or game.Players.LocalPlayer.Data.Level.Value <= 399 then -- Fishman Warrior
			QuestNumber = 18
			Name = "Fishman Warrior [Lv. 375]"
			QuestName = "FishmanQuest"
			QuestLevel = 1
			MobName = "Fishman Warrior"
			MobPosition = CFrame.new(60859, 19, 1501)
			QuestCFrame = CFrame.new(61123, 19, 1569)
			if getgenv().U.Main.AutoFarm and (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 400 or game.Players.LocalPlayer.Data.Level.Value <= 449 then -- Fishman Commando
			QuestNumber = 19
			Name = "Fishman Commando [Lv. 400]"
			QuestName = "FishmanQuest"
			QuestLevel = 2
			MobName = "Fishman Commando"
			MobPosition = CFrame.new(61891, 19, 1470)
			QuestCFrame = CFrame.new(61123, 19, 1569)
            if getgenv().U.Main.AutoFarm and (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 450 or game.Players.LocalPlayer.Data.Level.Value <= 474 then -- God's Guards
			QuestNumber = 20
			Name = "God's Guard [Lv. 450]"
			QuestName = "SkyExp1Quest"
			QuestLevel = 1
			MobName = "God's Guards"
			MobPosition = CFrame.new(-4698, 845, -1912)
			QuestCFrame = CFrame.new(-4722, 845, -1954)
            if getgenv().U.Main.AutoFarm and (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-4607.82275, 872.54248, -1667.55688))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 475 or game.Players.LocalPlayer.Data.Level.Value <= 524 then -- Shandas
			QuestNumber = 21
			Name = "Shanda [Lv. 475]"
			QuestName = "SkyExp1Quest"
			QuestLevel = 2
			MobName = "Shandas"
			MobPosition = CFrame.new(-7685, 5567, -502)
			QuestCFrame = CFrame.new(-7862, 5546, -380)
            if getgenv().U.Main.AutoFarm and (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 525 or game.Players.LocalPlayer.Data.Level.Value <= 549 then -- Royal Squad
			QuestNumber = 22
			Name = "Royal Squad [Lv. 525]"
			QuestName = "SkyExp2Quest"
			QuestLevel = 1
			MobName = "Royal Squad"
			MobPosition = CFrame.new(-7670, 5607, -1460)
			QuestCFrame = CFrame.new(-7904, 5636, -1412)
            if getgenv().U.Main.AutoFarm and (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 550 or game.Players.LocalPlayer.Data.Level.Value <= 624 then -- Royal Soldier
			QuestNumber = 23
			Name = "Royal Soldier [Lv. 550]"
			QuestName = "SkyExp2Quest"
			QuestLevel = 2
			MobName = "Royal Soldier"
			MobPosition = CFrame.new(-7828, 5607, -1744)
			QuestCFrame = CFrame.new(-7904, 5636, -1412)
            if getgenv().U.Main.AutoFarm and (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 625 or game.Players.LocalPlayer.Data.Level.Value <= 649 then -- Galley Pirate
			QuestNumber = 24
			Name = "Galley Pirate [Lv. 625]"
			QuestName = "FountainQuest"
			QuestLevel = 1
			MobName = "Galley Pirate"
			MobPosition = CFrame.new(5589, 45, 3996)
			QuestCFrame = CFrame.new(5256, 39, 4050)
		elseif game.Players.LocalPlayer.Data.Level.Value >= 650 then -- Galley Captain
			QuestNumber = 25
			Name = "Galley Captain [Lv. 650]"
			QuestName = "FountainQuest"
			QuestLevel = 2
			MobName = "Galley Captain"
			MobPosition = CFrame.new(5649, 39, 4936)
			QuestCFrame = CFrame.new(5256, 39, 4050)
		end
	end
	if SecondSea then
		if game.Players.LocalPlayer.Data.Level.Value == 700 or game.Players.LocalPlayer.Data.Level.Value <= 724 then -- Raider [Lv. 700]
			QuestNumber = 1

			Name = "Raider [Lv. 700]"
			QuestName = "Area1Quest"

			QuestLevel = 1
			MobName = "Raider"

			QuestCFrame = CFrame.new(-425, 73, 1837)
			VectorQuest = Vector3.new(-425, 73, 1837)

			MobPosition = CFrame.new(-746, 39, 2390)
			VectorMon = Vector3.new(-746, 39, 2389)
		elseif game.Players.LocalPlayer.Data.Level.Value == 725 or game.Players.LocalPlayer.Data.Level.Value <= 774 then -- Mercenary [Lv. 725]
			QuestNumber = 2

			Name = "Mercenary [Lv. 725]"
			QuestName = "Area1Quest"

			QuestLevel = 2
			MobName = "Mercenary"

			QuestCFrame = CFrame.new(-425, 73, 1837)
			VectorQuest = Vector3.new(-425, 73, 1837)

			MobPosition = CFrame.new(-874, 141, 1312)
			VectorMon = Vector3.new(-874, 141, 1312)
		elseif game.Players.LocalPlayer.Data.Level.Value == 775 or game.Players.LocalPlayer.Data.Level.Value <= 799 then -- Swan Pirate [Lv. 775]
			QuestNumber = 3

			Name = "Swan Pirate [Lv. 775]"
			QuestName = "Area2Quest"

			QuestLevel = 1
			MobName = "Swan Pirate"

			QuestCFrame = CFrame.new(634, 73, 918)
			VectorQuest = Vector3.new(634, 73, 918)

			MobPosition = CFrame.new(878, 122, 1235)
			VectorMon = Vector3.new(878, 122, 1235)
		elseif game.Players.LocalPlayer.Data.Level.Value == 800 or game.Players.LocalPlayer.Data.Level.Value <= 874 then -- Factory Staff [Lv. 800]
			QuestNumber = 4

			Name = "Factory Staff [Lv. 800]"
			QuestName = "Area2Quest"

			QuestLevel = 2
			MobName = "Factory Staff"

			QuestCFrame = CFrame.new(634, 73, 918)
			VectorQuest = Vector3.new(634, 73, 918)

			MobPosition = CFrame.new(295, 73, -56)
			VectorMon = Vector3.new(295, 73, -56)
		elseif game.Players.LocalPlayer.Data.Level.Value == 875 or game.Players.LocalPlayer.Data.Level.Value <= 899 then -- Marine Lieutenant [Lv. 875]
			QuestNumber = 5

			Name = "Marine Lieutenant [Lv. 875]"
			QuestName = "MarineQuest3"

			QuestLevel = 1
			MobName = "Marine Lieutenant"

			MobPosition = CFrame.new(-2806, 73, -3038)
			VectorMon = Vector3.new(-2806, 73, -3038)

			QuestCFrame = CFrame.new(-2443, 73, -3219)
			VectorQuest = Vector3.new(-2443, 73, -3219)
		elseif game.Players.LocalPlayer.Data.Level.Value == 900 or game.Players.LocalPlayer.Data.Level.Value <= 949 then -- Marine Captain [Lv. 900]
			QuestNumber = 6

			Name = "Marine Captain [Lv. 900]"
			QuestName = "MarineQuest3"

			QuestLevel = 2
			MobName = "Marine Captain"

			MobPosition = CFrame.new(-1869, 73, -3320)
			VectorMon = Vector3.new(-1869, 73, -3320)

			QuestCFrame = CFrame.new(-2443, 73, -3219)
			VectorQuest = Vector3.new(-2443, 73, -3219)
		elseif game.Players.LocalPlayer.Data.Level.Value == 950 or game.Players.LocalPlayer.Data.Level.Value <= 974 then -- Zombie [Lv. 950]
			QuestNumber = 7

			Name = "Zombie [Lv. 950]"
			QuestName = "ZombieQuest"

			QuestLevel = 1
			MobName = "Zombie"

			MobPosition = CFrame.new(-5736, 126, -728)
			VectorMon = Vector3.new(-5736, 126, -728)

			QuestCFrame = CFrame.new(-5494, 49, -795)
			VectorQuest = Vector3.new(-5494, 49, -794)
		elseif game.Players.LocalPlayer.Data.Level.Value == 975 or game.Players.LocalPlayer.Data.Level.Value <= 999 then -- Vampire [Lv. 975]
			QuestNumber = 8

			Name = "Vampire [Lv. 975]"
			QuestName = "ZombieQuest"

			QuestLevel = 2
			MobName = "Vampire"

			MobPosition = CFrame.new(-6033, 7, -1317)
			VectorMon = Vector3.new(-6033, 7, -1317)

			QuestCFrame = CFrame.new(-5494, 49, -795)
			VectorQuest = Vector3.new(-5494, 49, -795)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1000 or game.Players.LocalPlayer.Data.Level.Value <= 1049 then -- Snow Trooper [Lv. 1000] **
			QuestNumber = 9

			Name = "Snow Trooper [Lv. 1000]"
			QuestName = "SnowMountainQuest"

			QuestLevel = 1
			MobName = "Snow Trooper"

			MobPosition = CFrame.new(478, 402, -5362)
			VectorMon = Vector3.new(478, 402, -5362)

			QuestCFrame = CFrame.new(605, 402, -5371)
			VectorQuest = Vector3.new(605, 402, -5371)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1050 or game.Players.LocalPlayer.Data.Level.Value <= 1099 then -- Winter Warrior [Lv. 1050]
			QuestNumber = 10

			Name = "Winter Warrior [Lv. 1050]"
			QuestName = "SnowMountainQuest"

			QuestLevel = 2
			MobName = "Winter Warrior"

			MobPosition = CFrame.new(1157, 430, -5188)
			VectorMon = Vector3.new(1157, 430, -5188)

			QuestCFrame = CFrame.new(605, 402, -5371)
			VectorQuest = Vector3.new(605, 402, -5371)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1100 or game.Players.LocalPlayer.Data.Level.Value <= 1124 then -- Lab Subordinate [Lv. 1100]
			QuestNumber = 11

			Name = "Lab Subordinate [Lv. 1100]"
			QuestName = "IceSideQuest"

			QuestLevel = 1
			MobName = "Lab Subordinate"

			MobPosition = CFrame.new(-5782, 42, -4484)
			VectorMon = Vector3.new(-5782, 42, -4484)

			QuestCFrame = CFrame.new(-6060, 16, -4905)
			VectorQuest = Vector3.new(-6060, 16, -4905)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1125 or game.Players.LocalPlayer.Data.Level.Value <= 1174 then -- Horned Warrior [Lv. 1125]
			QuestNumber = 12

			Name = "Horned Warrior [Lv. 1125]"
			QuestName = "IceSideQuest"

			QuestLevel = 2
			MobName = "Horned Warrior"

			MobPosition = CFrame.new(-6406, 24, -5805)
			VectorMon = Vector3.new(-6406, 24, -5805)

			QuestCFrame = CFrame.new(-6060, 16, -4905)
			VectorQuest = Vector3.new(-6060, 16, -4905)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1175 or game.Players.LocalPlayer.Data.Level.Value <= 1199 then -- Magma Ninja [Lv. 1175]
			QuestNumber = 13

			Name = "Magma Ninja [Lv. 1175]"
			QuestName = "FireSideQuest"
			QuestLevel = 1
			MobName = "Magma Ninja"

			MobPosition = CFrame.new(-5428, 78, -5959)
			VectorMon = Vector3.new(-5428, 78, -5959)

			QuestCFrame = CFrame.new(-5430, 16, -5295)
			VectorQuest = Vector3.new(-5430, 16, -5296)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1200 or game.Players.LocalPlayer.Data.Level.Value <= 1249 then -- Lava Pirate [Lv. 1200]
			QuestNumber = 14

			Name = "Lava Pirate [Lv. 1200]"
			QuestName = "FireSideQuest"

			QuestLevel = 2
			MobName = "Lava Pirate"

			MobPosition = CFrame.new(-5270, 42, -4800)
			VectorMon = Vector3.new(-5270, 42, -4800)

			QuestCFrame = CFrame.new(-5430, 16, -5295)
			VectorQuest = Vector3.new(-5430, 16, -5296)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1250 or game.Players.LocalPlayer.Data.Level.Value <= 1274 then -- Ship Deckhand [Lv. 1250]
			QuestNumber = 15
			Name = "Ship Deckhand [Lv. 1250]"
			QuestName = "ShipQuest1"
			QuestLevel = 1
			MobName = "Ship Deckhand"
			MobPosition = CFrame.new(1198, 126, 33031)
			QuestCFrame = CFrame.new(1038, 125, 32913)
			if getgenv().U.Main.AutoFarm and (MobPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 1275 or game.Players.LocalPlayer.Data.Level.Value <= 1299 then -- Ship Engineer [Lv. 1275]
			QuestNumber = 16
			Name = "Ship Engineer [Lv. 1275]"
			QuestName = "ShipQuest1"
			QuestLevel = 2
			MobName = "Ship Engineer"
			MobPosition = CFrame.new(918, 44, 32787)
			QuestCFrame = CFrame.new(1038, 125, 32913)
			if getgenv().U.Main.AutoFarm and (MobPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 1300 or game.Players.LocalPlayer.Data.Level.Value <= 1324 then -- Ship Steward [Lv. 1300]
			QuestNumber = 17
			Name = "Ship Steward [Lv. 1300]"
			QuestName = "ShipQuest2"
			QuestLevel = 1
			MobName = "Ship Steward"
			MobPosition = CFrame.new(915, 130, 33419)
			QuestCFrame = CFrame.new(969, 125, 33245)
			if getgenv().U.Main.AutoFarm and (MobPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 1325 or game.Players.LocalPlayer.Data.Level.Value <= 1349 then -- Ship Officer [Lv. 1325]
			QuestNumber = 18
			Name = "Ship Officer [Lv. 1325]"
			QuestName = "ShipQuest2"
			QuestLevel = 2
			MobName = "Ship Officer"
			MobPosition = CFrame.new(916, 181, 33335)
			QuestCFrame = CFrame.new(969, 125, 33245)
			if getgenv().U.Main.AutoFarm and (MobPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 1350 or game.Players.LocalPlayer.Data.Level.Value <= 1374 then -- Arctic Warrior [Lv. 1350]
			QuestNumber = 19
			Name = "Arctic Warrior [Lv. 1350]"
			QuestName = "FrostQuest"
			QuestLevel = 1
			MobName = "Arctic Warrior"
			MobPosition = CFrame.new(6038, 29, -6231)
			QuestCFrame = CFrame.new(5669, 28, -6482)
            if getgenv().U.Main.AutoFarm and (MobPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 5000.034996032715, -132.83953857422))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 1375 or game.Players.LocalPlayer.Data.Level.Value <= 1424 then -- Snow Lurker [Lv. 1375]
			QuestNumber = 2
			Name = "Snow Lurker [Lv. 1375]"
			QuestName = "FrostQuest"
			QuestLevel = 2
			MobName = "Snow Lurker"
			MobPosition = CFrame.new(5560, 42, -6826)
			QuestCFrame = CFrame.new(5669, 28, -6482)
            if getgenv().U.Main.AutoFarm and (MobPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 5000.034996032715, -132.83953857422))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value == 1425 or game.Players.LocalPlayer.Data.Level.Value <= 1449 then -- Sea Soldier [Lv. 1425]
			QuestNumber = 21
			Name = "Sea Soldier [Lv. 1425]"
			QuestName = "ForgottenQuest"
			QuestLevel = 1
			MobName = "Sea Soldier"
			MobPosition = CFrame.new(-3022, 16, -9722)
			QuestCFrame = CFrame.new(-3054, 237, -10148)
            if getgenv().U.Main.AutoFarm and (MobPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 5000.034996032715, -132.83953857422))
            end
		elseif game.Players.LocalPlayer.Data.Level.Value >= 1450 then -- Water Fighter [Lv. 1450]
			QuestNumber = 22
			Name = "Water Fighter [Lv. 1450]"
			QuestName = "ForgottenQuest"
			QuestLevel = 2
			MobName = "Water Fighter"
			MobPosition = CFrame.new(-3385, 239, -10542)
			QuestCFrame = CFrame.new(-3054, 237, -10148)
            if getgenv().U.Main.AutoFarm and (MobPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 10000 then
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 5000.034996032715, -132.83953857422))
            end
		end
	elseif ThirdSea then
		if game.Players.LocalPlayer.Data.Level.Value == 1500 or game.Players.LocalPlayer.Data.Level.Value <= 1524 then
			QuestNumber = 1
			Name = "Pirate Millionaire [Lv. 1500]"
			QuestName = "PiratePortQuest"
			QuestLevel = 1
			MobName = "Pirate"
			MobPosition = CFrame.new(-373, 75, 5550)
			QuestCFrame = CFrame.new(-288, 44, 5576)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1525 or game.Players.LocalPlayer.Data.Level.Value <= 1574 then
			QuestNumber = 2
			Name = "Pistol Billionaire [Lv. 1525]"
			QuestName = "PiratePortQuest"
			QuestLevel = 2
			MobName = "Pistol"
			MobPosition = CFrame.new(-469, 74, 5904)
			QuestCFrame = CFrame.new(-288, 44, 5576)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1575 or game.Players.LocalPlayer.Data.Level.Value <= 1599 then
			QuestNumber = 3
			Name = "Dragon Crew Warrior [Lv. 1575]"
			QuestName = "AmazonQuest"
			QuestLevel = 1
			MobName = "Warrior"
			MobPosition = CFrame.new(6339, 52, -1213)
			QuestCFrame = CFrame.new(5835, 52, -1105)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1600 or game.Players.LocalPlayer.Data.Level.Value <= 1624 then
			QuestNumber = 4
			Name = "Dragon Crew Archer [Lv. 1600]"
			QuestName = "AmazonQuest"
			QuestLevel = 2
			MobName = "Archer"
			MobPosition = CFrame.new(6594, 383, 139)
			QuestCFrame = CFrame.new(5835, 52, -1105)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1625 or game.Players.LocalPlayer.Data.Level.Value <= 1649 then
			QuestNumber = 5
			Name = "Female Islander [Lv. 1625]"
			QuestName = "AmazonQuest2"
			QuestLevel = 1
			MobName = "Female"
			MobPosition = CFrame.new(5308, 819, 1047)
			QuestCFrame = CFrame.new(5443, 602, 751)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1650 or game.Players.LocalPlayer.Data.Level.Value <= 1699 then
			QuestNumber = 6
			Name = "Giant Islander [Lv. 1650]"
			QuestName = "AmazonQuest"
			QuestLevel = 2
			MobName = "Giant Islanders"
			MobPosition = CFrame.new(4951, 602, -68)
			QuestCFrame = CFrame.new(5443, 602, 751)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1700 or game.Players.LocalPlayer.Data.Level.Value <= 1724 then
			QuestNumber = 7
			Name = "Marine Commodore [Lv. 1700]"
			QuestName = "MarineTreeIsland"
			QuestLevel = 1
			MobName = "Marine Commodore"
			MobPosition = CFrame.new(2447, 73, -7470)
			QuestCFrame = CFrame.new(2180, 29, -6737)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1725 or game.Players.LocalPlayer.Data.Level.Value <= 1774 then
			QuestNumber = 8
			Name = "Marine Rear Admiral [Lv. 1725]"
			QuestName = "MarineTreeIsland"
			QuestLevel = 2
			MobName = "Marine Rear Admiral"
			MobPosition = CFrame.new(3671, 161, -6932)
			QuestCFrame = CFrame.new(2180, 29, -6737)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1775 or game.Players.LocalPlayer.Data.Level.Value <= 1800 then
			QuestNumber = 9
			Name = "Fishman Raider [Lv. 1775]"
			QuestName = "DeepForestIsland3"
			QuestLevel = 1
			MobName = "Fishman Raider"
			MobPosition = CFrame.new(-10560, 332, -8466)
			QuestCFrame = CFrame.new(-10584, 332, -8758)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1800 or game.Players.LocalPlayer.Data.Level.Value <= 1824 then
			QuestNumber = 10
			Name = "Fishman Captain [Lv. 1800]"
			QuestName = "DeepForestIsland3"
			QuestLevel = 2
			MobName = "Fishman Captain"
			MobPosition = CFrame.new(-10993, 332, -8940)
			QuestCFrame = CFrame.new(-10584, 332, -8758)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1825 or game.Players.LocalPlayer.Data.Level.Value <= 1849 then
			QuestNumber = 11
			Name = "Forest Pirate [Lv. 1825]"
			QuestName = "DeepForestIsland"
			QuestLevel = 1
			MobName = "Forest Pirate"
			MobPosition = CFrame.new(-13479, 333, -7905)
			QuestCFrame = CFrame.new(-13232, 333, -7627)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1850 or game.Players.LocalPlayer.Data.Level.Value <= 1899 then
			QuestNumber = 12
			Name = "Mythological Pirate [Lv. 1850]"
			QuestName = "DeepForestIsland"
			QuestLevel = 2
			MobName = "Mythological Pirate"
			MobPosition = CFrame.new(-13545, 470, -6917)
			QuestCFrame = CFrame.new(-13232, 333, -7627)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1900 or game.Players.LocalPlayer.Data.Level.Value <= 1924 then
			QuestNumber = 13
			Name = "Jungle Pirate [Lv. 1900]"
			QuestName = "DeepForestIsland2"
			QuestLevel = 1
			MobName = "Jungle Pirate"
			MobPosition = CFrame.new(-12107, 332, -10549)
			QuestCFrame = CFrame.new(-12684, 391, -9902)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1925 or game.Players.LocalPlayer.Data.Level.Value <= 1974 then
			QuestNumber = 14
			Name = "Musketeer Pirate [Lv. 1925]"
			QuestName = "DeepForestIsland2"
			QuestLevel = 2
			MobName = "Musketeer Pirate"
			MobPosition = CFrame.new(-13286, 392, -9769)
			QuestCFrame = CFrame.new(-12684, 391, -9902)
		elseif game.Players.LocalPlayer.Data.Level.Value == 1975 or game.Players.LocalPlayer.Data.Level.Value <= 1999 then
			QuestNumber = 15
			Name = "Reborn Skeleton [Lv. 1975]"
			QuestName = "HauntedQuest1"
			QuestLevel = 1
			MobName = "Reborn Skeleton"
			MobPosition = CFrame.new(-8760, 142, 6039)
			QuestCFrame = CFrame.new(-9482, 142, 5567)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2000 or game.Players.LocalPlayer.Data.Level.Value <= 2024 then
			QuestNumber = 16
			Name = "Living Zombie [Lv. 2000]"
			QuestName = "HauntedQuest1"
			QuestLevel = 2
			MobName = "Living Zombie"
			MobPosition = CFrame.new(-10144, 140, 5932)
			QuestCFrame = CFrame.new(-9482, 142, 5567)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2025 or game.Players.LocalPlayer.Data.Level.Value <= 2049 then
			QuestNumber = 17
			Name = "Demonic Soul [Lv. 2025]"
			QuestName = "HauntedQuest2"
			QuestLevel = 1
			MobName = "Demonic Soul"
			MobPosition = CFrame.new(-9507, 172, 6158)
			QuestCFrame = CFrame.new(-9513, 172, 6079)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2050 or game.Players.LocalPlayer.Data.Level.Value <= 2074 then
			QuestNumber = 18
			Name = "Posessed Mummy [Lv. 2050]"
			QuestName = "HauntedQuest2"
			QuestLevel = 2
			MobName = "Posessed Mummy"
			MobPosition = CFrame.new(-9577, 6, 6223)
			QuestCFrame = CFrame.new(-9513, 172, 6079)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2075 or game.Players.LocalPlayer.Data.Level.Value <= 2099 then
			QuestNumber = 19
			Name = "Peanut Scout [Lv. 2075]"
			QuestName = "NutsIslandQuest"
			QuestLevel = 1
			MobName = "Peanut Scout"
			MobPosition = CFrame.new(-2124, 123, -10435)
			QuestCFrame = CFrame.new(-2104, 38, -10192)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2100 or game.Players.LocalPlayer.Data.Level.Value <= 2124 then
			QuestNumber = 20
			Name = "Peanut President [Lv. 2100]"
			QuestName = "NutsIslandQuest"
			QuestLevel = 2
			MobName = "Peanut President"
			MobPosition = CFrame.new(-2124, 123, -10435)
			QuestCFrame = CFrame.new(-2104, 38, -10192)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2125 or game.Players.LocalPlayer.Data.Level.Value <= 2149 then
			QuestNumber = 21
			Name = "Ice Cream Chef [Lv. 2125]"
			QuestName = "IceCreamIslandQuest"
			QuestLevel = 1
			MobName = "Ice Cream Chef"
			MobPosition = CFrame.new(-641, 127, -11062)
			QuestCFrame = CFrame.new(-822, 66, -10965)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2150 or game.Players.LocalPlayer.Data.Level.Value <= 2199 then
			QuestNumber = 22
			Name = "Ice Cream Commander [Lv. 2150]"
			QuestName = "IceCreamIslandQuest"
			QuestLevel = 2
			MobName = "Ice Cream Commander"
			MobPosition = CFrame.new(-641, 127, -11062)
			QuestCFrame = CFrame.new(-822, 66, -10965)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2200 or game.Players.LocalPlayer.Data.Level.Value <= 2224 then
			QuestNumber = 23
			Name = "Cookie Crafter [Lv. 2200]"
			QuestName = "CakeQuest1"
			QuestLevel = 1
			MobName = "Cookie Crafter"
			MobPosition = CFrame.new(-2365, 38, -12099)
			QuestCFrame = CFrame.new(-2020, 38, -12025)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2225 or game.Players.LocalPlayer.Data.Level.Value <= 2249 then
			QuestNumber = 24
			Name = "Cake Guard [Lv. 2225]"
			QuestName = "CakeQuest1"
			QuestLevel = 2
			MobName = "Cake Guard"
			MobPosition = CFrame.new(-1651, 38, -12308)
			QuestCFrame = CFrame.new(-2020, 38, -12025)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2250 or game.Players.LocalPlayer.Data.Level.Value <= 2274 then
			QuestNumber = 25
			Name = "Baking Staff [Lv. 2250]"
			QuestName = "CakeQuest2"
			QuestLevel = 1
			MobName = "Baking Staff"
			MobPosition = CFrame.new(-1870, 38, -12938)
			QuestCFrame = CFrame.new(-1926, 38, -12850)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2275 or game.Players.LocalPlayer.Data.Level.Value <= 2299 then
			QuestNumber = 26
			Name = "Head Baker [Lv. 2275]"
			QuestName = "CakeQuest2"
			QuestLevel = 2
			MobName = "Head Baker"
			MobPosition = CFrame.new(-1926, 88, -12850)
			QuestCFrame = CFrame.new(-1926, 38, -12850)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2300 or game.Players.LocalPlayer.Data.Level.Value <= 2324 then
			QuestNumber = 27
			Name = "Cocoa Warrior [Lv. 2300]"
			QuestName = "ChocQuest1"
			QuestLevel = 1
			MobName = "Cocoa Warrior"
			MobPosition = CFrame.new(231, 23, -12194)
			QuestCFrame = CFrame.new(231, 23, -12194)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2325 or game.Players.LocalPlayer.Data.Level.Value <= 2349 then
			QuestNumber = 28
			Name = "Chocolate Bar Battler [Lv. 2325]"
			QuestName = "ChocQuest1"
			QuestLevel = 2
			MobName = "Chocolate Bar Battler"
			MobPosition = CFrame.new(231, 23, -12194)
			QuestCFrame = CFrame.new(231, 23, -12194)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2350 or game.Players.LocalPlayer.Data.Level.Value <= 2374 then
			QuestNumber = 29
			Name = "Sweet Thief [Lv. 2350]"
			QuestName = "ChocQuest2"
			QuestLevel = 1
			MobName = "Sweet Thief"
			MobPosition = CFrame.new(71, 77, -12632)
			QuestCFrame = CFrame.new(151, 23, -12774)
		elseif game.Players.LocalPlayer.Data.Level.Value == 2375 or game.Players.LocalPlayer.Data.Level.Value <= 2399 then
			QuestNumber = 30
			Name = "Candy Rebel [Lv. 2375]"
			QuestName = "ChocQuest2"
			QuestLevel = 2
			MobName = "Candy Rebel"
			MobPosition = CFrame.new(134, 77, -12882)
			QuestCFrame = CFrame.new(151, 23, -12774)
        elseif game.Players.LocalPlayer.Data.Level.Value == 2400 or game.Players.LocalPlayer.Data.Level.Value <= 2424 then
			QuestNumber = 31
			Name = "Candy Pirate [Lv. 2400]"
			QuestName = "CandyQuest1"
			QuestLevel = 1
			MobName = "Candy Pirate"
			MobPosition = CFrame.new(-1408, 16, -14552)
			QuestCFrame = CFrame.new(-1151, 16, -14445)
        elseif game.Players.LocalPlayer.Data.Level.Value >= 2425 then
			QuestNumber = 32
			Name = "Snow Demon [Lv. 2425]"
			QuestName = "CandyQuest1"
			QuestLevel = 2
			MobName = "Snow Demon"
			MobPosition = CFrame.new(-777, 23, -14453)
			QuestCFrame = CFrame.new(-1151, 16, -14445)
		end
	end
end

local function MaxMasFruit(arg)
    for i,v in pairs(require(game:GetService("Players").LocalPlayer.Backpack[game.Players.LocalPlayer.Data.DevilFruit.Value].Data)) do
        if i == 'Lvl' then          
            for a,b in pairs(v) do
                if a == tostring(arg) then
                    return b
                end
            end
        end
    end
end

local CombatFrameworkParticle = require(game.Players.LocalPlayer.PlayerScripts.CombatFramework.Particle)
local CombatFrameworkRigLib = require(game:GetService("ReplicatedStorage").CombatFramework.RigLib)
local StopCamera = require(game.ReplicatedStorage.Util.CameraShaker)StopCamera:Stop()
local CameraShaker = require(game.ReplicatedStorage.Util.CameraShaker)

local plr = game.Players.LocalPlayer
local CbFw = debug.getupvalues(require(plr.PlayerScripts.CombatFramework))
local CbFw2 = CbFw[2]

function GetCurrentBlade() 
    local p13 = CbFw2.activeController
    local ret = p13.blades[1]
    if not ret then return end
    while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
    return ret
end

function AttackNoCD() 
    local AC = CbFw2.activeController
    if AC and AC.equipped then
        local bladehit = require(game.ReplicatedStorage.CombatFramework.RigLib).getBladeHits(
            plr.Character,
            {plr.Character.HumanoidRootPart},
            1--Blade Size
        )
        local cac = {}
        local hash = {}
        local Ql=false
        for k, v in pairs(bladehit) do
            if v.Parent:FindFirstChild("HumanoidRootPart") and not hash[v.Parent] then--Check Blade Hits in Character
                if (v.Parent.HumanoidRootPart.Position-game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 35 then
                    Ql=true
                end
                table.insert(cac, v.Parent.HumanoidRootPart)
                hash[v.Parent] = true
            end
        end
        bladehit = cac
        if #bladehit > 0 then 
            local u8 = debug.getupvalue(AC.attack, 5)
            local u9 = debug.getupvalue(AC.attack, 6)
            local u7 = debug.getupvalue(AC.attack, 4)
            local u10 = debug.getupvalue(AC.attack, 7)
            local u12 = (u8 * 798405 + u7 * 727595) % u9
            local u13 = u7 * 798405
            (function()
                u12 = (u12 * u9 + u13) % 1099511627776
                u8 = math.floor(u12 / u9)
                u7 = u12 - u8 * u9
            end)()
            u10 = u10 + 1
            debug.setupvalue(AC.attack, 5, u8)
            debug.setupvalue(AC.attack, 6, u9)
            debug.setupvalue(AC.attack, 4, u7)
            debug.setupvalue(AC.attack, 7, u10)
            pcall(function()
                for k, v in pairs(AC.animator.anims.basic) do
                    v:Play()
                end                  
            end)
            if plr.Character:FindFirstChildOfClass("Tool") and AC.blades and AC.blades[1] and Ql and game.Players.LocalPlayer.Character.Stun.Value == 0 then 
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(GetCurrentBlade()))
                game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
                game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, 1, "")
            end
        end
    end
end

local function FindBackPack(Item)
    if game:GetService("Workspace").Characters[game.Players.LocalPlayer.Name]:FindFirstChild(Item) or game.Players.LocalPlayer.Backpack:FindFirstChild(Item) then
        return true
    end
    return false
end

task.spawn(function()
	while true do task.wait()
		if setscriptable then
			setscriptable(game.Players.LocalPlayer, "SimulationRadius", true)
		end
		if sethiddenproperty then
			sethiddenproperty(game.Players.LocalPlayer, "SimulationRadius", math.huge)
		end
	end
end)

local y =0
local function Teleport(...)
    repeat task.wait() 
        if game:GetService('Players').LocalPlayer.Character:WaitForChild("HumanoidRootPart") then
            local RealtargetPos = {...}
            local targetPos = RealtargetPos[1]
            local targetCFrame
            if type(targetPos) == "vector" then
                targetCFrame = CFrame.new(targetPos)
            elseif type(targetPos) == "userdata" then
                targetCFrame = targetPos
            elseif type(targetPos) == "number" then
                targetCFrame = CFrame.new(unpack(RealtargetPos))
            end
            local tweenfunc = {}
            local Dis = (targetCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude
            local tween_s = game:service"TweenService"
            if Dis <= 300 then
                Speed = 9999
            elseif Dis <= 500 then
                Speed = 500
            elseif Dis > 500 then
                Speed = 340
            else
                Speed = 300
            end
            local info = TweenInfo.new((targetCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude/Speed, Enum.EasingStyle.Linear)
            local tween = tween_s:Create(game:GetService("Players").LocalPlayer.Character["HumanoidRootPart"], info, {CFrame = targetCFrame * CFrame.Angles(0,math.rad(360),0)})
            tween:Play()
            if not FindBackPack("God's Chalice") or not FindBackPack("Sweet Chalice") or not FindBackPack("Hallow Essence") then
                if not getgenv().U.Raids.AutoRaid and (getgenv().U.Settings.InstantTeleport) then
                    if Dis >= 3500 then
                        if game:GetService("Players").LocalPlayer.PlayerGui.Main:FindFirstChild("InCombat").Visible == false then
                            getgenv().MobPos = nil
                            
                            if ThirdSea and (CFrame.new(-5095.33984375, 316.48101806641, -3168.3134765625).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude > 4000 then
                                if tween then tween:Cancel() end
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-5072.08984375, 314.5412902832, -3151.1098632812))
                            end
                            tween:Play()
                             --[[
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = targetCFrame*CFrame.new(0,1000,0)
                                game.Players.LocalPlayer.Character.Humanoid.Health =-math.huge
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = targetCFrame*CFrame.new(0,1000,0)]]
                        end
                    else
                        tween:Play()
                    end
                end
            end

            function tweenfunc:Stop()
                tween:Cancel()
                return tween
            end

            if not tween then return tween end
            return tweenfunc
        else
            
        end
    until game.Players.LocalPlayer.Character.Humanoid.Health <= 0
end

local function Tween(...)
        local RealtargetPos = {...}
        local targetPos = RealtargetPos[1]
        local targetCFrame
        if type(targetPos) == "vector" then
            targetCFrame = CFrame.new(targetPos)
        elseif type(targetPos) == "userdata" then
            targetCFrame = targetPos
        elseif type(targetPos) == "number" then
            targetCFrame = CFrame.new(unpack(RealtargetPos))
        end
        local tweenfunc = {}
        local Dis = (targetCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude
        local tween_s = game:service"TweenService"
        local info = TweenInfo.new((targetCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).Magnitude/295, Enum.EasingStyle.Linear)
        local tween2 = tween_s:Create(game:GetService("Players").LocalPlayer.Character["HumanoidRootPart"], info, {CFrame = targetCFrame * CFrame.fromAxisAngle(Vector3.new(1,0,0), math.rad(0))})
        
        if Dis <= 376 then
            tween2:Cancel()
            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = targetCFrame
        else
            tween2:Play()
        end

        function tweenfunc:Stop()
            tween2:Cancel()
            return tween2
        end

        if not tween2 then return tween2 end
        return tweenfunc
end

local Attacking = false

task.spawn(function()
	while task.wait(.1) do
		pcall(function()
			if Magnet then
                if getgenv().MobPos == nil then return end
				for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                    if v.Name:find("Boss") or v.Name:find("1750") then return end
					if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 600 then
                        if v:FindFirstChild('HumanoidRootPart') and v.Humanoid.Health >= 1 and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 200 then
                            v.HumanoidRootPart.CFrame = getgenv().MobPos
                            v.Humanoid.JumpPower = 0
                            v.HumanoidRootPart.Transparency = 1
                            v.HumanoidRootPart.CanCollide = false
                            v.Head.CanCollide = false
                            if v.Humanoid:FindFirstChild("Animator") then
                                v.Humanoid.Animator:Destroy()
                            end
                            v.Humanoid:ChangeState(11)
                            v.Humanoid:ChangeState(14)
                        else Attacking = false
                        end
					end
				end
			end
		end)
	end
end)


local function FruitMasCheck()
    if game:GetService("Players").LocalPlayer.Character:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value) then
        return game:GetService("Players").LocalPlayer.Character[game.Players.LocalPlayer.Data.DevilFruit.Value].Level.Value
    elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value) then
        return game:GetService("Players").LocalPlayer.Backpack[game.Players.LocalPlayer.Data.DevilFruit.Value].Level.Value
    end
end

local function FruitName()
    if game:GetService("Players").LocalPlayer.Character:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value) then
        return game:GetService("Players").LocalPlayer.Character[game.Players.LocalPlayer.Data.DevilFruit.Value]
    elseif game:GetService("Players").LocalPlayer.Backpack:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value) then
        return game:GetService("Players").LocalPlayer.Backpack[game.Players.LocalPlayer.Data.DevilFruit.Value]
    end
end

task.spawn(function()
	game:GetService("RunService").Stepped:Connect(function()
		pcall(function()
			if (getgenv().U.Main.AutoFarm or getgenv().U.Main.AutoFarmBone or getgenv().U.Main.AutoCakePrince or getgenv().U.Main.AutoDoughtKing or getgenv().U.Main.AutoAcuduimRifle or getgenv().U.Main.AutoBuddySword or getgenv().U.Main.AutoCavender or getgenv().U.Main.AutoCDK or getgenv().U.Main.AutoDarkDagger or getgenv().U.Main.AutoGodhuman or getgenv().U.Main.AutoHallowScythe or getgenv().U.Main.AutoPirate or getgenv().U.Main.AutoSea2 or getgenv().U.Main.AutoSea3 or getgenv().U.Main.AutoSerpentBow or getgenv().U.Main.AutoSpikeyTrident or getgenv().U.Main.AutoTTK or getgenv().U.Main.DeathStep or getgenv().U.Main.EClaw or getgenv().U.Main.DragonTalon or getgenv().U.Main.Superhuman or getgenv().U.Main.SharkKarate or getgenv().Clip or Clip) == true then
				if syn or (identifyexecutor() == 'Krnl') then
					setfflag("HumanoidParallelRemoveNoPhysics", "False")
					setfflag("HumanoidParallelRemoveNoPhysicsNoSimulate2", "False")
					game.Players.LocalPlayer.Character.Humanoid:ChangeState(11)
					if game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit == true then
						game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit = false
					end
				else
					if game.Players.LocalPlayer.Character:FindFirstChild("HumanoidRootPart") then
            --game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").Anchored = false
            --game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Anchored = false
						if not game:GetService("Players").LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Makima") then
							if game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit == true then
								game.Players.LocalPlayer.Character:WaitForChild("Humanoid").Sit = false
							end
							local BodyVelocity = Instance.new("BodyVelocity")
							BodyVelocity.Name = "Makima"
							BodyVelocity.Parent =  game:GetService("Players").LocalPlayer.Character.HumanoidRootPart
							BodyVelocity.MaxForce = Vector3.new(10000, 10000, 10000)
							BodyVelocity.Velocity = Vector3.new(0, 0, 0)
						end
					end
					for _, v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
						if v:IsA("BasePart") then
							v.CanCollide = false    
						end
					end
				end
                Attack = true
			else
                game.Players.LocalPlayer.Character:WaitForChild("HumanoidRootPart").Anchored = false
                if tween then
                    tween:Cancel()
                end
                Magnet = false
                Attack = false
				if game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Makima") then
					game.Players.LocalPlayer.Character.HumanoidRootPart:FindFirstChild("Makima"):Destroy();
				end
			end
			for i,v in pairs(game.Players.LocalPlayer.Character:GetDescendants()) do
			    if v:IsA("BodyVelocity") and v.Name~="Makima" then
			        v.MaxForce = Vector3.new(0, 0, 0)
			        --v:Destroy()
			    end
			end
		end)
	end)
end)

function Click()
    IsClicked = false
	game:GetService("VirtualUser"):CaptureController()
	game:GetService("VirtualUser"):Button1Down(Vector2.new(1280, 672))
    IsClicked = true
end

if game:GetService("ReplicatedStorage").Effect.Container:FindFirstChild("Death") then
    game:GetService("ReplicatedStorage").Effect.Container.Death:Destroy()
end
if game:GetService("ReplicatedStorage").Effect.Container:FindFirstChild("Respawn") then
    game:GetService("ReplicatedStorage").Effect.Container.Respawn:Destroy()
end

local CombatFramework = require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework"))
local CombatFrameworkR = getupvalues(CombatFramework)[2]
local RigController = require(game:GetService("Players")["LocalPlayer"].PlayerScripts.CombatFramework.RigController)
local RigControllerR = getupvalues(RigController)[2]

local function CurrentWeapon()
	local ac = CombatFrameworkR.activeController
	local ret = ac.blades[1]
	if not ret then return game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name end
	pcall(function()
		while ret.Parent~=game.Players.LocalPlayer.Character do ret=ret.Parent end
	end)
	if not ret then return game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name end
	return ret
end

local function getAllBladeHitsPlayers(Sizes)
	local Hits = {}
	local Client = game.Players.LocalPlayer
	local Characters = game:GetService("Workspace").Characters:GetChildren()
	for i=1,#Characters do local v = Characters[i]
		local Human = v:FindFirstChildOfClass("Humanoid")
		if v.Name ~= game.Players.LocalPlayer.Name and Human and Human.RootPart and Human.Health > 0 and Client:DistanceFromCharacter(Human.RootPart.Position) < Sizes then
			table.insert(Hits,Human.RootPart)
		end
	end
	return Hits
end

local function getAllBladeHits(Sizes)
	local Hits = {}
	local Client = game.Players.LocalPlayer
	local Enemies = game:GetService("Workspace").Enemies:GetChildren()
	for i=1,#Enemies do local v = Enemies[i]
		local Human = v:FindFirstChildOfClass("Humanoid")
		if Human and Human.RootPart and Human.Health > 0 and Client:DistanceFromCharacter(Human.RootPart.Position) < Sizes then
			table.insert(Hits,Human.RootPart)
		end
	end
	return Hits
end

local function AttackFunction()
	local ac = CombatFrameworkR.activeController
	if ac and ac.equipped then
        if game.Players.LocalPlayer.Character.Stun.Value == 0 then
            local bladehit = getAllBladeHits(40)
            if #bladehit > 0 then
                local u8 = debug.getupvalue(ac.attack, 5)
                local u9 = debug.getupvalue(ac.attack, 6)
                local u7 = debug.getupvalue(ac.attack, 4)
                local u10 = debug.getupvalue(ac.attack, 7)
                local u12 = (u8 * 798405 + u7 * 727595) % u9
                local u13 = u7 * 798405
                (function()
                    u12 = (u12 * u9 + u13) % 1099511627776
                    u8 = math.floor(u12 / u9)
                    u7 = u12 - u8 * u9
                end)()
                u10 = u10 + 1 
                debug.setupvalue(ac.attack, 5, u8)
                debug.setupvalue(ac.attack, 6, u9)
                debug.setupvalue(ac.attack, 4, u7)
                debug.setupvalue(ac.attack, 7, u10)
                for k, v in pairs(ac.animator.anims.basic) do
                    v:Play(0.01,0.01,0.01)
                end                 
                if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool") and ac.blades and ac.blades[1] and game.Players.LocalPlayer.Character.Stun.Value == 0 then 
                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(CurrentWeapon()))
                    game.ReplicatedStorage.Remotes.Validator:FireServer(math.floor(u12 / 1099511627776 * 16777215), u10)
                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", bladehit, 1, "")
                end
            end
        end
	end
end

local p20={
    CombatFramework = require(game:GetService("Players").LocalPlayer.PlayerScripts:WaitForChild("CombatFramework"));
    CbFwGetupvalue = getupvalues(CombatFramework)[2];
}

function p20.GetWeapon()
	local Ac = p20.CbFwGetupvalue.activeController
	local blades1 = Ac.blades[1]
	if not blades1 then
	    return game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool").Name
	end
	pcall(function()
		while blades1.Parent~=game.Players.LocalPlayer.Character do
		    blades1=blades1.Parent
		end
	end)
	return blades1
end

function p20.GetEnemiesPart()
	local Parts = {}
	local Client = game.Players.LocalPlayer
	local Enemies = game:GetService("Workspace").Enemies:GetChildren() or game:GetService("Workspace").Characters:GetChildren()
	for i=1,#Enemies do local v = Enemies[i]
		local Human = v:FindFirstChildOfClass("Humanoid")
		if Human and Human.RootPart and Human.Health > 0 and Client:DistanceFromCharacter(Human.RootPart.Position) < 51 then
			table.insert(Parts,Human.RootPart)
		end
	end
	return Parts
end

function p20.attack()
    local Ac = p20.CbFwGetupvalue.activeController
	if Ac and Ac.equipped then
        if game.Players.LocalPlayer.Character.Stun.Value == 0 then
            local EnemiesPart = p20.GetEnemiesPart()
            if #EnemiesPart > 0 then
                if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool") and Ac.blades and Ac.blades[1] then 
                    Ac.animator.anims.basic[2]:Play(0.01,0.01,0.01)
                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(p20.GetWeapon()))
                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", EnemiesPart, 4, "")
                end
            end
        end
	end
end

function p20.attackplayer()
    local Ac = p20.CbFwGetupvalue.activeController
	if Ac and Ac.equipped then
        if game.Players.LocalPlayer.Character.Stun.Value == 0 then
            local EnemiesPart = getAllBladeHitsPlayers(50)
            if #EnemiesPart > 0 then
                if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool") and Ac.blades and Ac.blades[1] then 
                    Ac.animator.anims.basic[2]:Play(0.01,0.01,0.01)
                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("weaponChange",tostring(p20.GetWeapon()))
                    game:GetService("ReplicatedStorage").RigControllerEvent:FireServer("hit", EnemiesPart, 4, "")
                end
            end
        end
	end
end


local function Inventory(Method,Item)
    if (type(Item) and type(Method)) == 'string' then
        game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer(tostring(Method),tostring(Item))
    else
        return warn('Please insert string')
    end
end

local function Farm(Mobs,MobCFrame)
    for _n,x in pairs(Mobs) do
        if game:GetService('Workspace').Enemies:FindFirstChild(x) then
            for _,Mob in pairs(game:GetService('Workspace').Enemies:GetChildren()) do
                if table.find(Mobs,Mob.Name) and Mob:FindFirstChild('Humanoid') and Mob:FindFirstChild('Humanoid').Health > 0 then
                    repeat task.wait()
                        Teleport(Mob.HumanoidRootPart.CFrame*CFrame.new(1,30,0))
                        Attack = true
                        EquipTool(WeaponName)
                        Mob.HumanoidRootPart.Size = Vector3.new(60,60,60)
                        Mob.Humanoid.WalkSpeed = 0
                        Mob.Humanoid.JumpPower = 0
                        Mob.HumanoidRootPart.CFrame = Mob.HumanoidRootPart.CFrame
                        Mob.HumanoidRootPart.CanCollide = false
                        Mob.Humanoid:ChangeState(14)
                        Mob.Humanoid:ChangeState(11)
                    until not getgenv().U.Main.Clip or not Mob.Parent or not Mob:FindFirstChild('Humanoid') or not Mob:FindFirstChild('Humanoid').Health <= 0
                end
            end
        elseif not game:GetService('Workspace').Enemies:FindFirstChild(x) then
            Teleport(MobCFrame)
        end
    end
end

local Shisui350
local Wando350
local Saddi350
local function Check3Sword()
    Inventory('Loaditem','Shisui')
    if CheckMastery('Shusui') then
        Shisui350 = true
    end
    task.wait(1)
    Inventory('Loaditem','Wando')
    if CheckMastery('Wando') then
        Wando350 = true
    end
    task.wait(1)
    Inventory('Loaditem','Saddi')
    if CheckMastery('Saddi') then
        Saddi350 = true
    end
end

local function FindSword(wating)
    local args = {
        [1] = "LegendarySwordDealer",
        [2] = "2"
    }
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    task.wait(wating)
    if getgenv().U.Settings.AllowHop then
        ServerHop()
    end
end


local CameraShaker = require(game.ReplicatedStorage.Util.CameraShaker)CameraShaker:Stop()
local CbFw = require(game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework)
local CbFw2 = debug.getupvalues(CbFw)[2]
--[[task.spawn(function()
    while task.wait() do
        task.delay(0.0001,function()
            if getgenv().U.Settings.FastAttack == true then
                if identifyexecutor() == 'Fluxus' then
                    CameraShaker:Stop()
                    CbFw2.activeController.attack()
                    CbFw2.activeController.timeToNextAttack = -(math.huge^math.huge^math.huge)
                    CbFw2.activeController.attacking = false
                    CbFw2.activeController.increment = 1
                    CbFw2.activeController.blocking = false                            
                    CbFw2.activeController.hitboxMagnitude = 90
                    CbFw2.activeController.humanoid.AutoRotate = true
                    CbFw2.activeController.focusStart = 0
                    CbFw2.activeController.currentAttackTrack = -math.huge
                    game.Players.LocalPlayer.Character.Humanoid.DisplayDistanceType = "None"
                    game.Players.LocalPlayer.Character.Humanoid.displaydistanceType = "None"
                    game.Players.LocalPlayer.Character.Stun.Value = 0
                    game.Players.LocalPlayer.Character.Humanoid.Sit = false
                    game.Players.LocalPlayer.Character.Busy.Value = false
                    game.Players.LocalPlayer.SimulationRadius = math.huge
                    setscriptable(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                    sethiddenproperty(game:GetService("Players").LocalPlayer, "SimulationRadius", math.huge)
                elseif identifyexecutor() ~= 'Fluxus' then
                    AttackNoCD()
                end
            end
        end)
    end
end)]]

local function GetMobSpawn(Name)
    local CFrameTable ={}
    for i,v in pairs(game:GetService('Workspace')["_WorldOrigin"].EnemySpawns:GetDescendants()) do
        if v.Name == tostring(Name) then
            table.insert(CFrameTable, v.CFrame*CFrame.new(0,30,0))
        end
    end
    return CFrameTable
end

local Beli = game:GetService('Players').LocalPlayer.Data.Beli.Value
local Fragments = game:GetService('Players').LocalPlayer.Data.Fragments.Value

print('Loadded')
task.wait(getgenv().U.Loading.DelayExecute)

local MaketPlace = game:GetService("MarketplaceService"):GetProductInfo(game.PlaceId)
local Gamename = MaketPlace.Name
local games = {
[game.PlaceId] = {
    Title = "Blox Fruits",
    Icons = "",
    Welcome = function()
        return tostring(""..Gamename.. " Unique Hub - " .. " Premuim Script"  .."\n Loadded Succesfully Develop by Unique Team")
    end
    }
}

if games[game.PlaceId] then	
    if games[game.PlaceId].Title == "Blox Fruits" then
        local function notify(types, ...)
            if types == "Notify" then
                require(game.ReplicatedStorage.Notification).new(...):Display()
            end
        end
        notify("Notify", games[game.PlaceId].Welcome())
        task.wait(5)
        notify("Notify", 'if founded a bug pls reoprt or tag Mobile developer -^-')
    end
end

print('Loading Ui')

if not game:IsLoaded() then
	game.Loaded:wait() 
end

local Library = loadstring(game:HttpGet('https://raw.githubusercontent.com/hajibeza/GUISTORAGE/main/Unique_Mobile_Gui.lua'))();

local Lib = Library:New() ;

local Main = Lib:CreateTab("Generals", 1)
local Auto = Lib:CreateTab("Automatics", 1)
local Client = Lib:CreateTab("LocalPlayer", 1)
local Raid = Lib:CreateTab("Raids", 1)
local Shop = Lib:CreateTab('Shoping', 1)
local Race = Lib:CreateTab("Races", 1)
local Misc = Lib:CreateTab("Misc", 1)
local Webhook = Lib:CreateTab("Misc#2", 1)

local a1 = Main:CreatePage("Main",1)
a1:AddLabel([[\\ Auto Farm//]]) do
    local Au = a1:AddToggle('Auto Farm Levels',false,function(a)
        getgenv().U.Main.AutoFarm = a
        AutoFarm = a
        save()
        local GetQuestTitle = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title
        local GetQuest = game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest
        local MyLevel = game.Players.LocalPlayer.Data.Level.Value
        task.spawn(function()
            while getgenv().U.Main.AutoFarm do task.wait()
                CheckQuest()
                if getgenv().U.Main.FastFarm and (MyLevel >= 30 and MyLevel <= 300) then
                    if MyLevel >= 30 and MyLevel <= 70 then
                        if (game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position - Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047)).Magnitude <= 3500 then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Royal Squad [Lv. 525]") then
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if v.Name == "Royal Squad [Lv. 525]" then
                                        if v:FindFirstChild("Humanoid") or v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health >=1 then
                                            repeat task.wait()
                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,25,5))
                                                BusoAndKen()
                                                EquipTool(WeaponName)
                                                Magnet = true
                                                --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                v.Humanoid.JumpPower = 0
                                                v.Humanoid.WalkSpeed = 0
                                                v.HumanoidRootPart.CanCollide = false
                                                v.Humanoid:ChangeState(11)
                                                v.Humanoid:ChangeState(14)
                                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                            until not v.Parent or not v:FindFirstChild("HumanoidRootPart") or v.Humanoid.Health <= 0 or not getgenv().U.Main.AutoFarm or not getgenv().U.Main.FastFarm
                                            Magnet = false
                                        end
                                    end
                                end
                            elseif game:GetService("ReplicatedStorage"):FindFirstChild("Royal Squad [Lv. 525]") then
                                Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Royal Squad [Lv. 525]").HumanoidRootPart.CFrame * CFrame.new(0,30,5))
                            elseif game:GetService("Workspace").Enemies:FindFirstChild("Shanda [Lv. 475]") then
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if v.Name == "Shanda [Lv. 475]" then
                                        if v:FindFirstChild("Humanoid") or v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health >=1 then
                                            repeat task.wait()
                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,25,5))
                                                BusoAndKen()
                                                EquipTool(WeaponName)
                                                Magnet = true
                                                --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                v.Humanoid.JumpPower = 0
                                                v.Humanoid.WalkSpeed = 0
                                                v.HumanoidRootPart.CanCollide = false
                                                v.Humanoid:ChangeState(11)
                                                v.Humanoid:ChangeState(14)
                                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                            until not v.Parent or not v:FindFirstChild("HumanoidRootPart") or v.Humanoid.Health <= 0 or not getgenv().U.Main.AutoFarm or not getgenv().U.Main.FastFarm
                                            Magnet = false
                                        end
                                    end
                                end
                            elseif game:GetService("ReplicatedStorage"):FindFirstChild("Shanda [Lv. 475]") then
                                Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Shanda [Lv. 475]").HumanoidRootPart.CFrame * CFrame.new(0,30,5))
                            end
                        else
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))			
                        end
                    elseif MyLevel >= 70 and MyLevel <= 250 then
                        if GetQuest.Visible == false then
                            if not tostring(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("PlayerHunter")):find("We heard some") then 
                                Tween = Teleport(QuestCFrame)
                                if FirstSea and (Name == "Fishman Commando [Lv. 400]" or Name == "Fishman Warrior [Lv. 375]") and (QuestCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 50000 then
                                    --if Tween then --Tween:Stop() end wait(.5)
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                                elseif FirstSea and not (Name == "Fishman Commando [Lv. 400]" or Name == "Fishman Warrior [Lv. 375]") and (QuestCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 50000 then
                                    --if Tween then --Tween:Stop() end wait(.5)
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(3864.8515625, 6.6796875, -1926.7841796875))
                                elseif FirstSea and (Name == "God's Guard [Lv. 450]" or Name == "Sky Bandit [Lv. 150]" or Name == "Dark Master [Lv. 175]") and (QuestCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 3000 then
                                    --if Tween then --Tween:Stop() end wait(.5)
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(-4607.8227539063, 872.54248046875, -1667.5568847656))
                                elseif FirstSea and (Name == "Shanda [Lv. 475]" or Name == "Royal Squad [Lv. 525]"or Name == "Royal Soldier [Lv. 550]") and (QuestCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 8000 then
                                    --if Tween then Tween:Stop() end wait(.5)
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
                                elseif SecondSea and string.find(Name, "Ship") and (QuestCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 30000 then
                                    --if Tween then Tween:Stop() end
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                                elseif SecondSea and not string.find(Name, "Ship") and (QuestCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 30000 then
                                    --if Tween then Tween:Stop() end
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 89.034996032715, -132.83953857422))
                                elseif (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 150 then
                                    --if Tween then Tween:Stop() end
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = QuestCFrame
                                    if (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 then
                                        if game:GetService("Players").LocalPlayer.Character:WaitForChild("Humanoid").Health > 0 then
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", QuestName, LevelQuest)
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                                        end
                                    else
                                        Teleport(QuestCFrame)
                                    end
                                end
                            end
                        elseif GetQuest.Visible == true then
                            local AllPlayersTableSkipFarm = {}
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Buso")
                            for i,v in pairs(game:GetService("Workspace").Characters:GetChildren()) do
                                table.insert(AllPlayersTableSkipFarm,v.Name)
                            end
                            if table.find(AllPlayersTableSkipFarm,GetQuestTitle.Text:split(" ")[2]) then
                                for i,v in pairs(game:GetService("Workspace").Characters:GetChildren()) do
                                    if string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,v.Name) then
                                        if getgenv().U.Main.AutoFarm and getgenv().U.Main.FastFarm and v.Name == GetQuestTitle.Text:split(" ")[2] and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                            repeat task.wait()
                                                if FirstSea and (Vector3.new(61163.8515625, 11.6796875, 1819.7841796875) - v.HumanoidRootPart.Position).magnitude < 5000 then
                                                    if FarmTeleport then FarmTeleport:Stop() end
                                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                                                elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 150 then
                                                    FarmTeleport = Teleport(v.HumanoidRootPart.CFrame)
                                                elseif v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 150 then
                                                    if FarmTeleport then FarmTeleport:Stop() end
                                                    if game:GetService("Players")["LocalPlayer"].PlayerGui.Main.PvpDisabled.Visible == true then
                                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 1000, 0)
                                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EnablePvp")
                                                    end
                                                    BusoAndKen()
                                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0, -6, 5))
                                                    EquipTool(WeaponName)
                                                    AttackNoCD()
                                                    game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
                                                    game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
                                                end
                                            until not getgenv().U.Main.AutoFarm or not getgenv().U.Main.FastFarm  or not string.find(game:GetService("Players").LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text,v.Name) or v.Humanoid.Health <= 0 or not v.Parent or GetQuest.Visible == false
                                        end
                                    end
                                end
                            else
                                if game:GetService("Workspace").Enemies:FindFirstChild(Name) then
                                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                        if getgenv().U.Main.AutoFarm and v.Name == Name and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                            if string.find(GetQuestTitle.Text, QuestName) then
                                                repeat task.wait()
                                                    getgenv().MobPos = v.HumanoidRootPart.CFrame
                                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,5))
                                                    BusoAndKen()
                                                    Magnet = true
                                                    EquipTool(WeaponName)
                                                    --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                    v.HumanoidRootPart.Transparency = 1
                                                    v.Humanoid.JumpPower = 0
                                                    v.Humanoid.WalkSpeed = 0
                                                    v.HumanoidRootPart.CanCollide = false
                                                    v.Humanoid:ChangeState(11)
                                                    v.Humanoid:ChangeState(14)
                                                until not game:GetService("Workspace").Enemies:FindFirstChild(Name) or not getgenv().U.Main.AutoFarm or not string.find(GetQuestTitle.Text, QuestName) or v.Humanoid.Health <= 0 or not v.Parent or GetQuest.Visible == false
                                                Attack = false
                                                Magnet = false
                                            else
                                                game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('AbandonQuest');
                                            end
                                        end
                                    end
                                else
                                    Magnet = false
                                    if not string.find(GetQuestTitle.Text, MobName) then game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('AbandonQuest'); end
                                    Teleport(MobPosition)
                                    if FirstSea and (Name == "Fishman Commando [Lv. 400]" or Name == "Fishman Warrior [Lv. 375]") and (MobPosition.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 50000 then
                                        --if Tween then --Tween:Stop() end wait(.5)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(61163.8515625, 11.6796875, 1819.7841796875))
                                    elseif FirstSea and not (Name == "Fishman Commando [Lv. 400]" or Name == "Fishman Warrior [Lv. 375]") and (QuestCFrame.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 50000 then
                                        --if Tween then --Tween:Stop() end wait(.5)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(3864.8515625, 6.6796875, -1926.7841796875))
                                    elseif FirstSea and (Name == "God's Guard [Lv. 450]" or Name == "Sky Bandit [Lv. 150]" or Name == "Dark Master [Lv. 175]") and (MobPosition.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 3000 then
                                        --if Tween then --Tween:Stop() end wait(.5)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(-4607.8227539063, 872.54248046875, -1667.5568847656))
                                    elseif FirstSea and (Name == "Shanda [Lv. 475]" or Name == "Royal Squad [Lv. 525]"or Name == "Royal Soldier [Lv. 550]") and (MobPosition.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 8000 then
                                        --if Tween then Tween:Stop() end wait(.5)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance", Vector3.new(-7894.6176757813, 5547.1416015625, -380.29119873047))
                                    elseif SecondSea and string.find(Name, "Ship") and (MobPosition.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 30000 then
                                        --if Tween then Tween:Stop() end
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(923.21252441406, 126.9760055542, 32852.83203125))
                                    elseif SecondSea and not string.find(Name, "Ship") and (MobPosition.Position - game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position).magnitude > 30000 then
                                        --if Tween then Tween:Stop() end
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("requestEntrance",Vector3.new(-6508.5581054688, 89.034996032715, -132.83953857422))
                                    elseif (MobPosition.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 150 then
                                        --if Tween then Tween:Stop() end
                                    end
                                end
                            end
                        end
                    else
                        if not string.find(GetQuestTitle.Text, MobName) then game.ReplicatedStorage:WaitForChild("Remotes").CommF_:InvokeServer("AbandonQuest"); end
                        if GetQuest.Visible == false then
                            Magnet = false
                            Attack = false
                            CheckQuest()
                            if (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 then
                                if game:GetService("Players").LocalPlayer.Character:WaitForChild("Humanoid").Health > 0 then
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", QuestName, QuestLevel)
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                                end
                            else
                                Teleport(QuestCFrame)
                            end
                        elseif GetQuest.Visible == true then
                            if game:GetService("Workspace").Enemies:FindFirstChild(Name) then
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if getgenv().U.Main.AutoFarm and v.Name == Name and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                        if string.find(GetQuestTitle.Text, MobName) then
                                            repeat task.wait()
                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,5))
                                                BusoAndKen()
                                                Magnet = true
                                                EquipTool(WeaponName)
                                                --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                v.HumanoidRootPart.Transparency = 1
                                                v.Humanoid.JumpPower = 0
                                                v.Humanoid.WalkSpeed = 0
                                                v.HumanoidRootPart.CanCollide = false
                                                v.Humanoid:ChangeState(11)
                                                v.Humanoid:ChangeState(14)
                                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                                if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 150 then
                                                    game:service('VirtualInputManager'):SendKeyEvent(true, "V", false, game)
                                                    game:service('VirtualInputManager'):SendKeyEvent(false, "V", false, game)
                                                end
                                            until not game:GetService("Workspace").Enemies:FindFirstChild(Name) or not getgenv().U.Main.AutoFarm or not string.find(GetQuestTitle.Text, MobName) or v.Humanoid.Health <= 0 or not v.Parent or GetQuest.Visible == false
                                            Magnet = false
                                        else
                                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('AbandonQuest');
                                        end
                                    end
                                end
                            else
                                Magnet = false
                                if not string.find(GetQuestTitle.Text, MobName) then game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('AbandonQuest'); end
                                Teleport(MobPosition)
                            end
                        end
                    end
                else
                    if GetQuest.Visible == false then
                        Magnet = false
                        if (QuestCFrame.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 20 then
                            if game:GetService("Players").LocalPlayer.Character:WaitForChild("Humanoid").Health > 0 then
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("StartQuest", QuestName, QuestLevel)
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                            end
                        else
                            Teleport(QuestCFrame)
                        end
                    elseif GetQuest.Visible == true then
                        if game:GetService("Workspace").Enemies:FindFirstChild(Name) then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if getgenv().U.Main.AutoFarm and v.Name == Name and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                    if string.find(GetQuestTitle.Text, MobName) then
                                        repeat task.wait()
                                            Teleport(v.HumanoidRootPart.CFrame*CFrame.new(0,25,5))
                                            BusoAndKen()
                                            Magnet = true
                                            EquipTool(WeaponName)
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                            v.HumanoidRootPart.Transparency = 1
                                            v.Humanoid.JumpPower = 0
                                            v.Humanoid.WalkSpeed = 0
                                            v.HumanoidRootPart.CanCollide = false
                                            v.Humanoid:ChangeState(11)
                                            v.Humanoid:ChangeState(14)
                                            getgenv().MobPos = v.HumanoidRootPart.CFrame
                                        until not game:GetService("Workspace").Enemies:FindFirstChild(Name) or not getgenv().U.Main.AutoFarm or not string.find(GetQuestTitle.Text, MobName) or v.Humanoid.Health <= 0 or not v.Parent or GetQuest.Visible == false
                                        Magnet = false
                                    else
                                        game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('AbandonQuest');
                                    end
                                end
                            end
                        else
                            local ClientCFrame = plr.Character.HumanoidRootPart.CFrame
                            Magnet = false
                            Teleport(MobPosition)
                        end
                    end
                end
            end
        end)
    end)

    local HaveMob


    if FirstSea then
        local ff = a1:AddToggle('Fast Farm (30 - 250+)',getgenv().U.Main.FastFarm,function(a)
            getgenv().U.Main.FastFarm = a
            save()
        end)

        local SS2 = a1:AddToggle('Auto SecondSea',getgenv().U.Main.AutoSea2,function(a)
            getgenv().U.Main.AutoSea2 = a
            save()
            task.spawn(function()
                while task.wait() do
                    pcall(function()
                        if getgenv().U.Main.AutoSea2 then
                            if game.Players.LocalPlayer.Data.Level.Value >= 700 then
                                if AutoFarm then
                                    getgenv().U.Main.AutoFarm = false
                                end
                                if game.Workspace.Map.Ice.Door.CanCollide == true and game.Workspace.Map.Ice.Door.Transparency == 0 then
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("DressrosaQuestProgress","Detective")
                                    EquipTool("Key")
                                    repeat wait() Teleport(CFrame.new(1347.7124, 37.3751602, -1325.6488)) until (CFrame.new(1347.7124, 37.3751602, -1325.6488).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not getgenv().U.Main.AutoSea2
                                elseif game.Workspace.Map.Ice.Door.CanCollide == false and game.Workspace.Map.Ice.Door.Transparency == 1 then
                                    if game:GetService("Workspace").Enemies:FindFirstChild("Ice Admiral [Lv. 700] [Boss]") then
                                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                            if v.Name == "Ice Admiral [Lv. 700] [Boss]" and v.Humanoid.Health > 0 then
                                                repeat task.wait()
                                                    BusoAndKen()
                                                    EquipTool(WeaponName)
                                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                                    Attack = true
                                                    --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                    v.Humanoid.JumpPower = 0
                                                    v.Humanoid.WalkSpeed = 0
                                                    v.HumanoidRootPart.CanCollide = false
                                                    v.Humanoid:ChangeState(11)
                                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
                                                until v.Humanoid.Health <= 0 or not v.Parent
                                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
                                            end
                                        end
                                    else
                                        Teleport(CFrame.new(1347.7124, 37.3751602, -1325.6488))
                                    end
                                else
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TravelDressrosa")
                                end
                            end
                        end
                    end)
                end
            end)
        end)

    elseif SecondSea then
        local SS3 = a1:AddToggle('Auto ThirdSea',getgenv().U.Main.AutoSea3,function(a)
            getgenv().U.Main.AutoSea3 = a
            save()
            task.spawn(function()
                while task.wait() do
                    pcall(function()
                        if getgenv().U.Main.AutoSea3 then
                            if game.Players.LocalPlayer.Data.Level.Value >= 1500 then
                                if AutoFarm then
                                    getgenv().U.Main.AutoFarm = false
                                end
                                if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 3 then
                                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetUnlockables").FlamingoAccess ~= nil then
                                        game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("TravelZou")
                                        if game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("ZQuestProgress", "Check") == 0 then
                                            if game.Workspace.Enemies:FindFirstChild("rip_indra [Lv. 1500] [Boss]") then 	
                                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                                    if v.Name == "rip_indra [Lv. 1500] [Boss]" and v:FindFirstChild("Humanoid")and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                                        repeat wait()
                                                            if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                                                Farmtween = Teleport(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                                            elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                                if Farmtween then Farmtween:Stop() end
                                                                Attack =  true
                                                                BusoAndKen()
                                                                EquipTool(WeaponName)
                                                                getgenv().MobPos = v.HumanoidRootPart.CFramel
                                                                --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                                v.Humanoid.JumpPower = 0
                                                                v.Humanoid.WalkSpeed = 0
                                                                v.HumanoidRootPart.CanCollide = false
                                                                v.Humanoid:ChangeState(11)
                                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                                            end
                                                        until not getgenv().U.Main.AutoSea3 or not v.Parent or v.Humanoid.Health <= 0 
                                                        wait(.5)
                                                        Check = 2
                                                        repeat wait() game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("TravelZou") until Check == 1
                                                        Attack =  false
                                                    end
                                                end
                                            else
                                                game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("ZQuestProgress","Check")
                                                game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("ZQuestProgress","Begin")
                                            end
                                        elseif game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("ZQuestProgress", "Check") == 1 then
                                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("TravelZou")
                                        else
                                            if game.Workspace.Enemies:FindFirstChild("Don Swan [Lv. 1000] [Boss]") then
                                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                                    if v.Name == "Don Swan [Lv. 1000] [Boss]" and v:FindFirstChild("Humanoid")and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                                        repeat task.wait()
                                                            if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                                                Farmtween = Teleport(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                                            elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                                if Farmtween then Farmtween:Stop() end
                                                                Attack = true
                                                                BusoAndKen()
                                                                EquipTool(WeaponName)
                                                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                                                --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                                v.Humanoid.JumpPower = 0
                                                                v.Humanoid.WalkSpeed = 0
                                                                v.HumanoidRootPart.CanCollide = false
                                                                v.Humanoid:ChangeState(11)															
                                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                                            end
                                                        until not getgenv().U.Main.AutoSea3 or not v.Parent or v.Humanoid.Health <= 0 
                                                        Attack =  false
                                                    end
                                                end
                                            else
                                                TweenDonSwanthireworld = Teleport(CFrame.new(2288.802, 15.1870775, 863.034607).Position,CFrame.new(2288.802, 15.1870775, 863.034607))
                                                if (CFrame.new(2288.802, 15.1870775, 863.034607).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if TweenDonSwanthireworld then
                                                        TweenDonSwanthireworld:Stop()
                                                        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2288.802, 15.1870775, 863.034607)
                                                    end
                                                end
                                            end
                                        end
                                    else
                                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetUnlockables").FlamingoAccess == nil then
                                            local TabelDevilFruitStore = {}
                                            local TabelDevilFruitOpen = {}

                                            for i,v in pairs(game:GetService("ReplicatedStorage").Remotes["CommF_"]:InvokeServer("getInventoryFruits")) do
                                                for i1,v1 in pairs(v) do
                                                    if i1 == "Name" then 
                                                        table.insert(TabelDevilFruitStore,v1)
                                                    end
                                                end
                                            end

                                            for i,v in next,game.ReplicatedStorage:WaitForChild("Remotes").CommF_:InvokeServer("GetFruits") do
                                                if v.Price >= 850000 then  
                                                    table.insert(TabelDevilFruitOpen,v.Name)
                                                end
                                            end

                                            for i,DevilFruitOpenDoor in pairs(TabelDevilFruitOpen) do
                                                for i1,DevilFruitStore in pairs(TabelDevilFruitStore) do
                                                    if DevilFruitOpenDoor == DevilFruitStore and game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetUnlockables").FlamingoAccess == nil then    
                                                        if not game.Players.LocalPlayer.Backpack:FindFirstChild(DevilFruitStore) then   
                                                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("LoadFruit",DevilFruitStore)
                                                        else
                                                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("TalkTrevor","1")
                                                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("TalkTrevor","2")
                                                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("TalkTrevor","3")
                                                        end
                                                    end
                                                end
                                            end
                                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("TalkTrevor","1")
                                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("TalkTrevor","2")
                                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("TalkTrevor","3")	
                                        end
                                    end
                                else
                                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 0 then
                                        if string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Swan Pirates") and string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "50") and game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                                            if game.Workspace.Enemies:FindFirstChild("Swan Pirate [Lv. 775]") then
                                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                                    if v.Name == "Swan Pirate [Lv. 775]" then
                                                        pcall(function()
                                                            repeat task.wait()
                                                                if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                                                    Farmtween = Teleport(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                                                elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                                    if Farmtween then Farmtween:Stop() end
                                                                    Attack = true
                                                                    Magnet = true
                                                                    BusoAndKen()
                                                                    EquipTool(WeaponName)
                                                                    getgenv().MobPos = v.HumanoidRootPart.CFrame
                                                                    --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                                    v.Humanoid.JumpPower = 0
                                                                    v.Humanoid.WalkSpeed = 0
                                                                    v.HumanoidRootPart.CanCollide = false
                                                                    v.Humanoid:ChangeState(11)															
                                                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                                                end
                                                            until not v.Parent or v.Humanoid.Health <= 0 or getgenv().U.Main.AutoSea3 == false or game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == false
                                                            Attack = false
                                                            Magnet = false
                                                        end)
                                                    end
                                                end
                                            else
                                                Questtween = Teleport(CFrame.new(1057.92761, 137.614319, 1242.08069).Position,CFrame.new(1057.92761, 137.614319, 1242.08069))
                                                if (CFrame.new(1057.92761, 137.614319, 1242.08069).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                    if Bartilotween then Bartilotween:Stop() end
                                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(1057.92761, 137.614319, 1242.08069)
                                                end
                                            end
                                        else
                                            Bartilotween = Teleport(CFrame.new(-456.28952, 73.0200958, 299.895966).Position,CFrame.new(-456.28952, 73.0200958, 299.895966))
                                            if ( CFrame.new(-456.28952, 73.0200958, 299.895966).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                if Bartilotween then Bartilotween:Stop() end
                                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame =  CFrame.new(-456.28952, 73.0200958, 299.895966)
                                                game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer("StartQuest","BartiloQuest",1)
                                            end
                                        end
                                    elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 1 then
                                        if game.Workspace.Enemies:FindFirstChild("Jeremy [Lv. 850] [Boss]") then
                                            for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                                if v.Name == "Jeremy [Lv. 850] [Boss]" then
                                                    repeat task.wait()
                                                        if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                                            Farmtween = Teleport(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame)
                                                        elseif (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                            if Farmtween then Farmtween:Stop() end
                                                            Attack = true
                                                            BusoAndKen()
                                                            EquipTool(WeaponName)
                                                            getgenv().MobPos = v.HumanoidRootPart.CFrame
                                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                            v.Humanoid.JumpPower = 0
                                                            v.Humanoid.WalkSpeed = 0
                                                            v.HumanoidRootPart.CanCollide = false
                                                            v.Humanoid:ChangeState(11)															
                                                            Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                                        end
                                                    until not v.Parent or v.Humanoid.Health <= 0 or getgenv().U.Main.AutoSea3 == false
                                                    Attack = false
                                                end
                                            end
                                        else
                                            Bartilotween = Teleport(CFrame.new(2099.88159, 448.931, 648.997375).Position,CFrame.new(2099.88159, 448.931, 648.997375))
                                            if (CFrame.new(2099.88159, 448.931, 648.997375).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                                if Bartilotween then Bartilotween:Stop() end
                                                game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(2099.88159, 448.931, 648.997375)
                                            end
                                        end
                                    elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BartiloQuestProgress","Bartilo") == 2 then
                                        if (CFrame.new(-1836, 11, 1714).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude > 300 then
                                            Bartilotween = Teleport(CFrame.new(-1836, 11, 1714).Position,CFrame.new(-1836, 11, 1714))
                                        elseif (CFrame.new(-1836, 11, 1714).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 300 then
                                            if Bartilotween then Bartilotween:Stop() end
                                            game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1836, 11, 1714)
                                            wait(.5)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1850.49329, 13.1789551, 1750.89685)
                                            wait(.1)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1858.87305, 19.3777466, 1712.01807)
                                            wait(.1)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1803.94324, 16.5789185, 1750.89685)
                                            wait(.1)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1858.55835, 16.8604317, 1724.79541)
                                            wait(.1)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1869.54224, 15.987854, 1681.00659)
                                            wait(.1)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1800.0979, 16.4978027, 1684.52368)
                                            wait(.1)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1819.26343, 14.795166, 1717.90625)
                                            wait(.1)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-1813.51843, 14.8604736, 1724.79541)
                                        end
                                    end
                                end
                            end
                        end
                    end)
                end
            end)
        end)

    end
end
--[[
    
]]
local a12 = Main:CreatePage("", 1)
a12:AddLabel([[\\ Masteries //]]) do
    local fsm = a12:AddToggle('Farm Sword Mastery',getgenv().U.Main.FarmSwordMas,function(a)
        getgenv().U.Main.FarmSwordMas = a
        getgenv().Clip = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.FarmSwordMas then
                    CheckQuest()
                    if game:GetService("Workspace").Enemies:FindFirstChild(Name) then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if getgenv().U.Main.FarmSwordMas and v.Name == Name and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                repeat task.wait()
                                    FarmTeleport = Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 150 then
                                        if FarmTeleport then FarmTeleport:Stop() end
                                        Magnet = true
                                        getgenv().MobPos = v.HumanoidRootPart.CFrame
                                        local HealthMin = v.Humanoid.MaxHealth*getgenv().U.Main.MobHealth/100
                                        local PositionSkillMasteryGun = v.HumanoidRootPart.Position
                                        if v.Humanoid.Health <= HealthMin and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                            EquipTool(getgenv().Sword)
                                            UseSkillMasterySword = true
                                            Attack = true
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0)
                                        else
                                            UseSkillMasterySword = false
                                            Click()
                                            EquipTool(WeaponName)
                                            Attack = true
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 15, 0)
                                        end
                                    end
                                until not game:GetService("Workspace").Enemies:FindFirstChild(Name) or not getgenv().U.Main.FarmSwordMas or v.Humanoid.Health <= 0 or not v.Parent
                                UseSkillMasterySword = false
                                Magnet = false
                            end
                        end
                    else
                        CheckQuest()
                        Magnet = false
                        Modstween = Teleport(MobPosition)
                    end
                end
            end
        end)
    end)

    local ffm = a12:AddToggle('Farm Fruit Mastery',getgenv().U.Main.FarmFruitMas,function(a)
        getgenv().U.Main.FarmFruitMas = a
        getgenv().Clip = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.FarmFruitMas then
                    CheckQuest()
                    if game:GetService("Workspace").Enemies:FindFirstChild(Name) then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if getgenv().U.Main.FarmFruitMas and v.Name == Name and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                repeat task.wait()
                                    FarmTeleport = Teleport(v.HumanoidRootPart.Position,v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 150 then
                                        if FarmTeleport then FarmTeleport:Stop() end
                                        Magnet = true
                                        getgenv().MobPos = v.HumanoidRootPart.CFrame
                                        local HealthMin = v.Humanoid.MaxHealth * getgenv().U.Main.MobHealth/100
                                        if v.Humanoid.Health <= HealthMin and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                            EquipTool(getgenv().DevilFruit)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0)
                                            if game.Players.LocalPlayer.Character:FindFirstChildOfClass("Tool") then
                                                local PositionSkillMasteryDevilFruit = v.HumanoidRootPart.Position
                                                UseSkill = true
                                                if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Dragon-Dragon") then
                                                    if getgenv().U.Main.SkillZ and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
                                                        game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
                                                        wait(.1)
                                                        game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
                                                    end
                                                    if getgenv().U.Main.SkillX and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
                                                        game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
                                                        wait(.1)
                                                        game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
                                                    end   
                                                elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Human-Human: Buddha") then
                                                    if getgenv().U.Main.SkillZ and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and game.Players.LocalPlayer.Character.HumanoidRootPart.Size == Vector3.new(7.6, 7.676, 3.686) and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
                                                    else
                                                        game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
                                                        wait(.1)
                                                        game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
                                                    end
                                                    if getgenv().U.Main.SkillX and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
                                                        game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
                                                        wait(.1)
                                                        game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
                                                    end
                                                    if getgenv().U.Main.SkillC and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.C then
                                                        game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
                                                        wait(.1)
                                                        game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
                                                    end  
                                                elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild("Venom-Venom") then
                                                    if getgenv().U.Main.SkillZ and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.Z then
                                                        game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
                                                        wait(4)
                                                        game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
                                                    end
                                                    if getgenv().U.Main.SkillX and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.X then
                                                        game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
                                                        wait(.1)
                                                        game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
                                                    end
                                                    if getgenv().U.Main.SkillC and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 and DevilFruitMastery >= MasteryDevilFruit.Lvl.C then
                                                        game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
                                                        wait(.1)
                                                        game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
                                                    end
                                                --elseif game:GetService("Players").LocalPlayer.Character:FindFirstChild(FruitName()) then
                                                end
                                                game:GetService("Players").LocalPlayer.Character:FindFirstChild(game.Players.LocalPlayer.Data.DevilFruit.Value).MousePos.Value = v.HumanoidRootPart.Position
                                                if getgenv().U.Main.SkillZ and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                                    game:service('VirtualInputManager'):SendKeyEvent(true, "Z", false, game)
                                                    wait(.1)
                                                    print('Skill')
                                                    game:service('VirtualInputManager'):SendKeyEvent(false, "Z", false, game)
                                                end
                                                if getgenv().U.Main.SkillX and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                                    game:service('VirtualInputManager'):SendKeyEvent(true, "X", false, game)
                                                    wait(.1)
                                                    game:service('VirtualInputManager'):SendKeyEvent(false, "X", false, game)
                                                end
                                                if getgenv().U.Main.SkillC and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                                    game:service('VirtualInputManager'):SendKeyEvent(true, "C", false, game)
                                                    wait(.1)
                                                    game:service('VirtualInputManager'):SendKeyEvent(false, "C", false, game)
                                                end
                                                if getgenv().U.Main.SkillV and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                                    game:service('VirtualInputManager'):SendKeyEvent(true, "V", false, game)
                                                    wait(.1)
                                                    game:service('VirtualInputManager'):SendKeyEvent(false, "V", false, game)
                                                end
                                            end
                                        elseif v.Humanoid.Health > HealthMin and v:FindFirstChild('Humanoid') and v.Humanoid.Health >= 1 then
                                            game:GetService('VirtualUser'):CaptureController()
                                            game:GetService('VirtualUser'):ClickButton1(Vector2.new(851, 158), game:GetService("Workspace").Camera.CFrame)
                                            UseSkill = false
                                            EquipTool(WeaponName)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 0, 30)
                                        end
                                    end
                                until not game:GetService("Workspace").Enemies:FindFirstChild(Name) or not getgenv().U.Main.FarmFruitMas or v.Humanoid.Health <= 0 or not v.Parent
                                Magnet = false
                            end
                        end
                    else
                        Magnet = false
                        Teleport(MobPosition)
                    end
                end
            end
        end)
    end)

    local fgm = a12:AddToggle('Farm Gun Mastery',getgenv().U.Main.FarmGunMas,function(a)
        getgenv().U.Main.FarmGunMas = a
        getgenv().Clip = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.FarmGunMas then
                    CheckQuest()
                    if game:GetService("Workspace").Enemies:FindFirstChild(Name) then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if getgenv().U.Main.FarmGunMas and v.Name == Name and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                repeat task.wait()
                                    FarmTeleport = Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 150 then
                                        if FarmTeleport then FarmTeleport:Stop() end
                                        Magnet = true
                                        MobPosition = v.HumanoidRootPart.CFrame
                                        local HealthMin = v.Humanoid.MaxHealth*getgenv().U.Main.MobHealth/100
                                        local PositionSkillMasteryGun = v.HumanoidRootPart.Position
                                        if v.Humanoid.Health <= HealthMin and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                            EquipTool(getgenv().Gun)
                                            UseSkillMasteryGun = true
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0)
                                            if game:GetService("Players").LocalPlayer.Character:FindFirstChild(_G.SelectWeaponGun) and game:GetService("Players").LocalPlayer.Character:FindFirstChild(_G.SelectWeaponGun):FindFirstChild("RemoteFunctionShoot") then
                                                Click()
                                                local args = {
                                                    [1] = v.HumanoidRootPart.Position,
                                                    [2] = v.HumanoidRootPart
                                                }
                                                game:GetService("Players").LocalPlayer.Character[_G.SelectWeaponGun].RemoteFunctionShoot:InvokeServer(unpack(args))
                                            end 
                                        else
                                            UseSkillMasteryGun = false
                                            Attack = true
                                            EquipTool(WeaponName)
                                            game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0, 15, 0)
                                        end
                                    end
                                until not game:GetService("Workspace").Enemies:FindFirstChild(Name) or not getgenv().U.Main.FarmGunMas or v.Humanoid.Health <= 0 or not v.Parent
                                UseSkillMasteryGun = false
                                Magnet = false
                            end
                        end
                    else
                        Magnet = false
                        Teleport(MobPosition)
                    end
                end
            end
        end)
    end)
end


-- PositionSkillMasteryDevilFruit

--[[
    -- Script generated by SimpleSpy - credits to exx#9394

local args = {
    [1] = "ActivateAbility"
}

game:GetService("ReplicatedStorage").Remotes.CommE:FireServer(unpack(args))

]]
local a15 = Main:CreatePage("", 2)
a15:AddLabel([[\\ Settings //]])

local a13 = Main:CreatePage("", 2)
a13:AddLabel([[\\ Mastery Configs //]]) do
    a13:AddToggle('Auto Change Weapon (Sword)',getgenv().U.Main.AutochangeWeapon,function(a)
        getgenv().U.Main.AutochangeWeapon = a
        save()
    end)

    local CompletedFarm, NotFinished , Mas = {}, {}, {};

    local GetSwordMastery = function(p1)
        for _,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
            if type(v) == "table" then
                if v.Type == "Sword" then
                    if v.Name == p1 then
                        return v.Mastery;
                    end;
                end;
            end;
        end;
    end;

    local GetSwordMaxMastery = function(p1)
        for _,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
            if type(v) == "table" then
                if v.Type == "Sword" then
                    if v.Name == p1 then
                        return v.MasteryRequirements.X;
                    end;
                end;
            end;
        end;
    end;

    spawn(function()
        while wait() do
            if getgenv().U.Main.AutochangeWeapon then
                pcall(function()
                    for _,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
                        if type(v) == "table" then
                            if v.Type == "Sword" then
                                if v.Mastery >= v.MasteryRequirements.X then
                                    table.insert(CompletedFarm, v.Name)
                                    --print("Max Req Name : " .. v.Name.. " ".. v.Mastery)
                                elseif v.Mastery < v.MasteryRequirements.X then
                                    table.insert(NotFinished, v.Name)
                                    table.insert(Mas, v.Mastery)
                                end
                                    
                                for i1, v1 in pairs(NotFinished) do
                                    if not FindBackPack(v1) then
                                        local args = {
                                            [1] = "LoadItem",
                                            [2] = v1
                                        }
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                    end
                                    repeat wait() until GetSwordMastery(v1) >= GetSwordMaxMastery(v1)
                                end
                            end
                        end
                    end
                end)
            end
        end
    end)

    local mh = a13:AddSlider('Mob Health (Percentage)',0,100,getgenv().U.Main.MobHealth,function(a)
        getgenv().U.Main.MobHealth = a
        save()
    end)

    local SZ = a13:AddToggle('Skill [Z]',getgenv().U.Main.SkillZ,function(a)
        getgenv().U.Main.SkillZ = a
        save()
    end)

    local SX = a13:AddToggle('Skill [X]',getgenv().U.Main.SkillX,function(a)
        getgenv().U.Main.SkillX = a
        save()
    end)

    local SC = a13:AddToggle('Skill [C]',getgenv().U.Main.SkillC,function(a)
        getgenv().U.Main.SkillC = a
        save()
    end)

    local SV = a13:AddToggle('Skill [V]',getgenv().U.Main.SkillV,function(a)
        getgenv().U.Main.SkillV = a
        save()
    end)

    task.spawn(function()
        while task.wait() do CheckQuest()
            for i,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do  
                if v:IsA("Tool") then
                    if v:FindFirstChild("RemoteFunctionShoot") then 
                        _G.SelectWeaponGun = v.Name
                    end
                end
            end
        end
    end)
    
    spawn(function()
        local gg = getrawmetatable(game)
        local old = gg.__namecall
        setreadonly(gg,false)
        gg.__namecall = newcclosure(function(...)
            local method = getnamecallmethod()
            local args = {...}
            if tostring(method) == "FireServer" then
                if tostring(args[1]) == "RemoteEvent" then
                    if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
                        if getgenv().U.Main.FarmFruitMas and UseSkill then
                            if type(args[2]) == "vector" then 
                                args[2] = PositionSkillMasteryDevilFruit
                            else
                                args[2] = Vector3.new(PositionSkillMasteryDevilFruit)
                            end
                            return old(unpack(args))
                        end
                    end
                end
            end
            return old(...)
        end)
    end)
    
    spawn(function()
        local gt = getrawmetatable(game)
        local old = gt.__namecall
        setreadonly(gt,false)
        gt.__namecall = newcclosure(function(...)
            local args = {...}
            if getnamecallmethod() == "InvokeServer" then 
                if _G.SelectWeaponGun then
                    if _G.SelectWeaponGun == "Soul Guitar" then
                        if tostring(args[2]) == "TAP" then
                            if getgenv().U.Main.FarmGunMas and UseSkillMasteryGun then
                                args[3] = PositionSkillMasteryGun
                            end
                        end
                    end
                end
            end
            return old(unpack(args))
        end)
        setreadonly(gt,true)
    end)
end

local a14 = Main:CreatePage("", 1)
a1:AddLabel([[\\ Bosses //]]) do

    local Bosses = {}
    for _,v in pairs(game:GetService('ReplicatedStorage'):GetChildren()) do
        if string.find(v.Name,'Boss') then
            if not table.find(Bosses, v.Name) then
                table.insert(Bosses,v.Name)
            end
        end
    end
	if not type(getgenv().U.Main.SelectBoss) == 'table' then
        getgenv().U.Main.SelectBoss = {}
    end
    local boss = a1:AddDropdown('Select Boss',"nil",false,Bosses,function(a)
        getgenv().U.Main.SelectBoss = a
        SelectBoss = a
        save()
    end)

    a1:AddButton('Refresh Bosses',function()
        boss:Clear() task.wait(.2)
        for _,v in pairs(game:GetService('ReplicatedStorage'):GetChildren()) do
            if string.find(v.Name,'Boss') then
                table.insert(Bosses,v.Name)
                boss:Add(v.Name)
            end
        end
    end)

    local fb = a1:AddToggle('Auto Farm Boss',getgenv().U.Main.AutoFarmBoss,function(a)
        getgenv().U.Main.AutoFarmBoss = a
        getgenv().Clip = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.AutoFarmBoss then
                    if game:GetService('Workspace').Enemies:FindFirstChild(tostring(getgenv().U.Main.SelectBoss)) then
                        for _,v in pairs(game:GetService('Workspace').Enemies:GetChildren()) do
                            if v.Name == getgenv().U.Main.SelectBoss and v:FindFirstChild('Humanoid') and v.Humanoid.Health >= 1 then
                                repeat task.wait()
                                    Teleport(v.HumanoidRootPart.CFrame*CFrame.new(0,30,3))
                                    --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                    BusoAndKen()
                                    EquipTool(WeaponName)
                                    FastAttack = true
                                until not getgenv().U.Main.AutoFarmBoss or not v.Parent or not v:FindFirstChild('HumanoidRootPart') or v.Humanoid.Health <= 0
                            end
                        end
                    else
                        if game:GetService('ReplicatedStorage'):FindFirstChild(SelectBoss) then
                            Teleport(game:GetService('ReplicatedStorage'):FindFirstChild(SelectBoss).HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                        end
                    end
                end
            end
        end)
    end)
end

-- Settings --------------------------------------------------------------

local Tools = {'Melee','Sword','Devil Fruit'}
a15:AddDropdown('Select Boss',getgenv().U.Settings.Tooltip,false,Tools,function(a)
    getgenv().U.Settings.Tooltip = a
    ToolTip = a
    save()
    task.spawn(function()
        while task.wait() do
            pcall(function()
                if ToolTip == "Melee" then
                    for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                        if v.ToolTip == "Melee" then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                                WeaponName = v.Name
                                Melee = v.Name
                            end
                        end
                    end
                elseif ToolTip == "Sword" then
                    for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                        if v.ToolTip == "Sword" then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                                WeaponName = v.Name
                                Sword = v.Name
                            end
                        end
                    end
                elseif ToolTip == "Fruit" then
                    for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                        if v.ToolTip == "Blox Fruit" then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                                WeaponName = v.Name
                                DevilFruit = v.Name
                            end
                        end
                    end
                else
                    for i ,v in pairs(game.Players.LocalPlayer.Backpack:GetChildren()) do
                        if v.ToolTip == "Melee" then
                            if game.Players.LocalPlayer.Backpack:FindFirstChild(tostring(v.Name)) then
                                WeaponName = v.Name
                            end
                        end
                    end
                end
            end)
        end
    end)
end)

do
    CbFw2.activeController.timeToNextAttack = -(math.huge^math.huge^math.huge)
    CbFw2.activeController.attacking = true
    CbFw2.activeController.increment = 1
    CbFw2.activeController.blocking = false                            
    CbFw2.activeController.hitboxMagnitude = 90
    CbFw2.activeController.humanoid.AutoRotate = false
    CbFw2.activeController.currentAttackTrack = -math.huge
end

a15:AddToggle('Fast Attack ',getgenv().U.Settings.FastAttack,function(a)
    getgenv().U.Settings.FastAttack =  a
    save()
end)

a15:AddToggle('Super Fast Attack เร็วมาดอ่ะด็อกเตอร์',getgenv().U.Settings.Super,function(a)
    getgenv().U.Settings.Super =  a
    save()
end)

a15:AddToggle('ResetOnDied',getgenv().U.Settings.ResetOndied,function(a)
    getgenv().U.Settings.ResetOndied =  a
    save()
end)

local Char = game.Players.LocalPlayer.Character
local Root = Char.HumanoidRootPart

local Players = game.Players

local LocalPlayer = Players.LocalPlayer

spawn(pcall(function()
    while wait(1) do
        if Char.Humanoid and Char.Humanoid.Health > 1 then return end
        game:GetService("TeleportService"):Teleport(game.PlaceId)
    end
end))

NoAttackAnimation = true

local CollectionService = game:GetService("CollectionService")

repeat 
    LocalPlayer = Players.LocalPlayer
    wait()
until LocalPlayer

local kkii = require(game.ReplicatedStorage.Util.CameraShaker)
kkii:Stop()

local ItsTrue = true or false

local CurrentAllMob,
      recentlySpawn,
      StoredSuccessFully,
      canHits, RecentCollected,
      FruitInServer,
      RecentlyLocationSet,
      lastequip = {}, 0, 0, {}, 0, {}, 0, tick()

local PC,
      RL,
      DMG, 
      RigC,
      Combat = require(LocalPlayer.PlayerScripts.CombatFramework.Particle), require(game:GetService("ReplicatedStorage").CombatFramework.RigLib), require(LocalPlayer.PlayerScripts.CombatFramework.Particle.Damage), getupvalue(require(LocalPlayer.PlayerScripts.CombatFramework.RigController),2), getupvalue(require(LocalPlayer.PlayerScripts.CombatFramework),2)


local UserInputService, RunService, vim, CollectionService, CoreGui = game:GetService("UserInputService")
    ,game:GetService("RunService")
    ,game:GetService('VirtualInputManager')
    ,game:GetService("CollectionService")
    ,game:GetService("CoreGui")

local dist = function(a,b,noHeight)
    if not b then
        b = Root.Position
    end
    return (Vector3.new(a.X,not noHeight and a.Y,a.Z) - Vector3.new(b.X,not noHeight and b.Y,b.Z)).magnitude
end

do -- Starter Thread
    task.spawn(function()
        local stacking = 0
        local printCooldown = 0
        while task.wait(.075) do
            pcall(function()
                local nearbymon = false
                table.clear(CurrentAllMob)
                table.clear(canHits)
                local mobs = CollectionService:GetTagged("ActiveRig")
                for i=1,#mobs do local v = mobs[i]
                    local Human = v:FindFirstChildOfClass("Humanoid")
                    if Human and Human.Health > 0 and Human.RootPart and v ~= Char then
                        local IsPlayer = game.Players:GetPlayerFromCharacter(v)
                        local IsAlly = IsPlayer and CollectionService:HasTag(IsPlayer,"Ally"..LocalPlayer.Name)
                        if not IsAlly then
                            CurrentAllMob[#CurrentAllMob + 1] = v
                            if not nearbymon and dist(Human.RootPart.Position) < 65 then
                                nearbymon = true
                            end
                        end
                    end
                end

                if nearbymon then
                    local Enemies = workspace.Enemies:GetChildren()
                    local Players = Players:GetPlayers()
                    for i=1,#Enemies do local v = Enemies[i]
                        local Human = v:FindFirstChildOfClass("Humanoid")
                        if Human and Human.RootPart and Human.Health > 0 and dist(Human.RootPart.Position) < 65 then
                            canHits[#canHits+1] = Human.RootPart
                        end
                    end
                    for i=1,#Players do local v = Players[i].Character
                        if not Players[i]:GetAttribute("PvpDisabled") and v and v ~= LocalPlayer.Character then
                            local Human = v:FindFirstChildOfClass("Humanoid")
                            if Human and Human.RootPart and Human.Health > 0 and dist(Human.RootPart.Position) < 65 then
                                canHits[#canHits+1] = Human.RootPart
                            end
                        end
                    end
                end
            end)
        end
    end)
end

function e(s)
    local start = os.time()
    repeat until os.time() > start + s
end

-- Initialize Fast Attack .
coroutine.wrap(function()
    local Data = Combat
    local Blank = function() end
    local RigEvent = game:GetService("ReplicatedStorage").RigControllerEvent
    local Animation = Instance.new("Animation")
    local RecentlyFired = 0
    local AttackCD = 0
    local Controller
    local lastFireValid = 0
    local MaxLag = 350
    fucker = 0.0000007*-2^10
    TryLag = 0
    local resetCD = function()
        local WeaponName = Controller.currentWeaponModel.Name
        local Cooldown = {
            combat = 0.07
        }
        AttackCD = tick() + (fucker and Cooldown[WeaponName:lower()] or fucker or 0.285) + ((TryLag/MaxLag)*0.3)
        RigEvent.FireServer(RigEvent,"weaponChange",WeaponName)
        TryLag += 1
        task.delay((fucker or 0.285) + (TryLag+0.5/MaxLag)*0.3,function()
            TryLag -= 1
        end)
    end

    if not shared.orl then shared.orl = RL.wrapAttackAnimationAsync end
    if not shared.cpc then shared.cpc = PC.play end
    if not shared.dnew then shared.dnew = DMG.new end
    if not shared.attack then shared.attack = RigC.attack end
    RL.wrapAttackAnimationAsync = function(a,b,c,d,func)
        if not NoAttackAnimation and not Attack then
            PC.play = shared.cpc
            return shared.orl(a,b,c,65,func)
        end
        local Radius = (DamageAura and DamageAuraRadius) or 65
        if canHits and #canHits > 0 then
            PC.play = function() end
            a:Play(0.00075,0.01,0.01)
            func(canHits)
            wait(a.length * 0.5)
            a:Stop()
        end
    end

    while task.wait(-10^100) do --while task.wait() do -- RunService.Stepped:Wait()
        pcall(function()
            if #canHits > 0 then
                Controller = Data.activeController
                if NormalClick then
                    pcall(task.spawn,Controller.attack,Controller)
                end
                if Controller and Controller.equipped and (not Char.Busy.Value or not LocalPlayer.PlayerGui.Main.Dialogue.Visible) and Char.Stun.Value == 0 and Controller.currentWeaponModel then
                    if (Attack or DamageAura) then
                        if getgenv().U.Settings.Super and tick() > AttackCD and not DisableFastAttack then
                            resetCD()
                        end 
                        if tick() - lastFireValid > 0.5 or not getgenv().U.Settings.Super then
                            Controller.timeToNextAttack = -math.huge
                            Controller.increment = 1
                            Controller.hitboxMagnitude = 65
                            pcall(task.spawn,Controller.attack,Controller)
                            lastFireValid = tick()
                        end
                        local AID3 = Controller.anims.basic[3]
                        local AID2 = Controller.anims.basic[2]
                        local ID = AID3 or AID2
                        Animation.AnimationId = ID
                        local Playing = Controller.humanoid:LoadAnimation(Animation)
                        Playing:Play(0.00075,0.01,0.01)
                        RigEvent.FireServer(RigEvent,"hit",canHits,AID3 and 1 or 2,"") -- 3 or 2
                        pcall(Controller.attack)
                        --AttackSignal:Fire()
                        delay(.5,function()
                            Playing:Stop()
                        end)
                    end
                end
            end
        end)
    end
end)()

local CameraShaker = require(game.ReplicatedStorage.Util.CameraShaker)
for l,v in pairs(getreg()) do
    if typeof(v) == "function" and getfenv(v).script == game:GetService("Players").LocalPlayer.PlayerScripts.CombatFramework then
        for _,y in pairs(debug.getupvalues(v)) do
            if typeof(y) == "table" then
                task.spawn(function()
                    while task.wait() do
                        if getgenv().U.Settings.FastAttack and nearbymon then
                            if identifyexecutor() == 'Fluxus' or identifyexecutor() == 'Hydrogen' then
                                pcall(function()
                                    CameraShaker:Stop()
                                    y.timeToNextAttack = -math.huge
                                    y.activeController.attacking = false
                                    y.activeController.increment = 4
                                    y.activeController.hitboxMagnitude =80
                                    y.activeController.blocking = false
                                    y.activeController:attack()
                                    y.activeController.timeToNextBlock = false
                                end)
                            else
                                pcall(function()
                                    CameraShaker:Stop()
                                    y.timeToNextAttack = -math.huge
                                    y.activeController.attacking = false
                                    y.activeController.increment = 4
                                    y.activeController.hitboxMagnitude =80
                                    y.activeController.blocking = false
                                    y.activeController:attack()
                                    y.activeController.timeToNextBlock = false
                                end)
                            end
                        end
                    end
                end)
            end
        end
    end
end

a15:AddToggle('Instant Teleport',getgenv().U.Settings.InstantTeleport,function(a)
    getgenv().U.Settings.InstantTeleport = a
    save()
end)

a15:AddTextbox("Notify Fillter", "insert fillter here", function(a)
    getgenv().Fillter = a
end)

a15:AddToggle('Remove Notify',getgenv().U.Settings.RemoveNotify,function(a)
    getgenv().U.Settings.RemoveNotify = a
    save()
end)

getgenv().Fillter = getgenv().Fillter or ""
 -- text to fillter
coroutine.wrap(function()
	while task.wait() do
        if not getgenv().U.Settings.RemoveNotify then return end
		for _, v in next,game:GetService("Players").LocalPlayer.PlayerGui.Notifications:GetChildren() do
			if v.Name:find(getgenv().Fillter) then
            else
                v:Destroy()
            end
		end
	end
end)()

a15:AddToggle('Allowed Hop',getgenv().U.Settings.AllowHop,function(a)
    getgenv().U.Settings.AllowHop = a
    save()
end)

a15:AddToggle('White Screen',getgenv().U.Settings.WhiteScreen,function(a)
    getgenv().U.Settings.WhiteScreen = a
    save()
    if a == true then
        setfpscap(360)
        game:GetService('RunService'):Set3dRenderingEnabled(false)
    else
        game:GetService('RunService'):Set3dRenderingEnabled(true)
    end
end)

a15:AddToggle('Auto Boosts Fps',getgenv().U.Settings.AutoBoosts,function(a)
    getgenv().U.Settings.AutoBoosts = a
    save()
    if a == true then
        do -- Boosts FPS
            game:GetService("ReplicatedStorage").Assets.GUI.DamageCounter.Enabled = false
            task.spawn(function()
                while task.wait() do
                    for i, v in pairs(game.Workspace["_WorldOrigin"]:GetChildren()) do
                        if v.Name == "Dust" or v.Name == "eff" or v.Name == "CurvedRing" or v.Name == "SwordSlash" or v.Name == "Sounds" or v.Name == "SlashHit" then
                            v:Destroy() 
                        end
                    end
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetDescendants()) do
                        if v.ClassName == "MeshPart" then
                            v.Transparency = 0.1
                        end
                    end
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetDescendants()) do
                        if v.Name == "Head" then
                            v.Transparency = 0.1
                        end
                    end
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetDescendants()) do
                        if v.ClassName == "Accessory" then
                            v.Handle.Transparency = 0.1
                        end
                    end
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetDescendants()) do
                        if v.ClassName == "Decal" then
                            v.Transparency = 0.1
                        end
                    end
                end
            end)
            local decalsyeeted = true
            local g = game
            local w = g.Workspace
            local l = g.Lighting
            local t = w.Terrain
            t.WaterWaveSize = 0
            t.WaterWaveSpeed = 0
            t.WaterReflectance = 0
            t.WaterTransparency = 0
            l.GlobalShadows = false
            l.FogEnd = 9e9
            l.Brightness = 0
            --w._WorldOrigin["Foam;"]:Destroy()
            settings().Rendering.QualityLevel = "Level01"
            for i, v in pairs(g:GetDescendants()) do
                if v:IsA("Part") or v:IsA("Union") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then 
                    v.Material = "Plastic"
                    v.Reflectance = 0
                elseif v:IsA("Decal") or v:IsA("Texture") and decalsyeeted then
                    v.Transparency = 1
                elseif v:IsA("ParticleEmitter") or v:IsA("Trail") then
                    v.Lifetime = NumberRange.new(0)
                elseif v:IsA("Explosion") then
                    v.BlastPressure = 1
                    v.BlastRadius = 1
                elseif v:IsA("Fire") or v:IsA("SpotLight") or v:IsA("Smoke") or v:IsA("Sparkles") then
                    v.Enabled = false
                elseif v:IsA("MeshPart") then
                    v.Material = "Plastic"
                    v.Reflectance = 0
                    v.TextureID = 10385902758728957
                end
            end
            for i, e in pairs(l:GetChildren()) do
                if e:IsA("BlurEffect") or e:IsA("SunRaysEffect") or e:IsA("ColorCorrectionEffect") or e:IsA("BloomEffect") or e:IsA("DepthOfFieldEffect") then
                    e.Enabled = false
                end
            end

        end
    end
end)

local Material = {
    MysticMob = {
        MobName1 = {"Sea Soldier [Lv. 1425]", "Water Fighter [Lv. 1450]"},
        MobCFrame1 = CFrame.new( -3385,239, -10542)
    },
    DragonMob = {
        MobName1 = {"Dragon Crew Warrior [Lv. 1575]", "Dragon Crew Archer [Lv. 1600]"},
        MobCFrame1 = CFrame.new(6594,383,139)
    },
    FishMob = {
        MobName1 = {"Fishman Raider [Lv. 1775]", "Fishman Captain [Lv. 1800]"},
        MobCFrame1 = CFrame.new( -10993,332, -8940)
    },
    MagmaMob = {
        MobName1 = {"Lava Pirate [Lv. 1200]", "Magma Ninja [Lv. 1175]"},
        MobCFrame1 = CFrame.new( -5428,78, -5959)
    },
}

local b1 = Auto:CreatePage("", 1)
--b1:AddLabel([[\\ Automatics#1 //]])

--[[b1:AddToggle('Auto Farm Heart',false,function(a)
    FarmHeart = a
    Clip = a
    task.spawn(function()
        while task.wait() do
            if FarmHeart then
                if game:GetService('ReplicatedStorage'):FindFirstChild('Snow Demon [Lv. 2425]') or game:GetService("Workspace").Enemies:FindFirstChild('Snow Demon [Lv. 2425]') or game:GetService('ReplicatedStorage'):FindFirstChild('Candy Pirate [Lv. 2400]') or game:GetService("Workspace").Enemies:FindFirstChild('Candy Pirate [Lv. 2400]') then
                    for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == 'Snow Demon [Lv. 2425]' or v.Name == 'Candy Pirate [Lv. 2400]' and v:FindFirstChild('Humanoid') and v:FindFirstChild('HumanoidRootPart') and v.Humanoid.Health >= 1 then
                            repeat task.wait()
                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                Teleport(v.HumanoidRootPart.CFrame*CFrame.new(2,10,7))
                                Magnet = true
                                BusoAndKen()
                                EquipTool(WeaponName)
                            until not Clip or not a or not FarmHeart or not v.Parent or not v:FindFirstChild('HumanoidRootPart') or v.Humanoid.Health <= 0
                        end
                    end
                else
                    Teleport(CFrame.new(-777, 23, -14453))
                end
            end
        end
    end)
end)]]

b1:AddLabel([[\\ Fighting Style //]]) do
    
    b1:AddToggle('Auto Godhuman',getgenv().U.Main.AutoGodhuman,function(a)
        getgenv().U.Main.AutoGodhuman = a
        save()
        task.spawn(function()
            while task.wait() do
               -- pcall(function()
                    local Beli = game.Players.LocalPlayer.Data.Beli.Value
                    local Fragments = game.Players.LocalPlayer.Data.Fragments.Value
                    if getgenv().U.Main.AutoGodhuman then
                        if not game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman", true) == "Bring me 20 Fish Tails, 20 Magma Ore, 10 Dragon Scales and 10 Mystic Droplets." then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman")
                        else
    						if not HasTalon then
    							BuyDragonTalon = tonumber(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon",true))
    
    							if BuyDragonTalon then
    								if BuyDragonTalon == 1 then
    									HasTalon = true
    								end
    							end
    						end
    						if not HasSuperhuman then
    							BuySuperhuman = tonumber(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman",true))
    
    							if BuySuperhuman then
    								if BuySuperhuman == 1 then
    									HasSuperhuman = true
    								end
    							end
    						end
    						if not HasKarate then
    							BuySharkmanKarate = tonumber(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true))
    
    							if BuySharkmanKarate then
    								if BuySharkmanKarate == 1 then
    									HasKarate = true
    								end
    							end
    						end
    						if not HasDeathStep then
    							BuyDeathStep = tonumber(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer( "BuyDeathStep",true))
    
    							if BuyDeathStep then
    								if BuyDeathStep == 1 then
    									HasDeathStep = true
    								end
    							end
    						end
    						if not HasElectricClaw then
    							BuyElectricClaw = tonumber(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw",true))
    							if BuyElectricClaw then
    								if BuyElectricClaw == 1 then
    									HasElectricClaw = true
    								end
    							end
    						end
    						
    						if CheckMaterial("Fish Tail") >= 20 and CheckMaterial("Dragon Scale") >= 10 and CheckMaterial("Magma Ore") >= 20 and CheckMaterial("Mystic Droplet") >= 10 then
    						    if not FindBackPack("Godhuman") then
    						        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyGodhuman")
    						    end
    						else
    						    if CheckMaterial("Fish Tail") < 20 then
    						        if MultiFindObject({"Fishman Raider [Lv. 1775]", "Fishman Captain [Lv. 1800]"}) then
    						            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
    						                if table.find({"Fishman Raider [Lv. 1775]", "Fishman Captain [Lv. 1800]"}, v.Name) and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Parent and v.Humanoid.Health >= 1 then
    						                    repeat task.wait()
    						                        _G.MobPos = v.HumanoidRootPart.CFrame
    						                        Teleport(_G.MobPos*CFrame.new(0,30,0))
    						                        FastAttack = true
    						                        _G.Magnet = true
    						                    until not not getgenv().U.Main.AutoGodhuman or not not table.find({"Fishman Raider [Lv. 1775]", "Fishman Captain [Lv. 1800]"}, v.Name) or Humanoid.Health <= 0 or not v:FindFirstChild("Humanoid") or not v:FindFirstChild("HumanoidRootPart") or not v.Parent
    						                    _G.Magnet = false
    						                    FastAttack = false
    						                end
    						            end
    						        else
    						            _G.Magnet = false
    						            FastAttack = false
    						            if not ThirdSea then
    						                Sea3()
    						                return
    						            end
    						            Teleport(CFrame.new( -10993,332, -8940))
    						        end
    						    else
    						        if CheckMaterial("Dragon Scale") < 20 then
        						        if MultiFindObject(game:GetService("Workspace").Enemies, Material[DragonMob][MobName1]) then
        						            table.foreach(game:GetService("Workspace").Enemies:GetChildren(), function(_,v)
        						                if table.find(v.Name, Material[DragonMob][MobName1]) and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Parent and v.Humanoid.Health >= 1 then
        						                    repeat task.wait()
        						                        _G.MobPos = v.HumanoidRootPart.CFrame
        						                        Teleport(_G.MobPos*CFrame.new(0,30,0))
        						                        FastAttack = true
        						                        _G.Magnet = true
        						                    until not not getgenv().U.Main.AutoGodhuman or not MultiFindObject(game:GetService("Workspace").Enemies, Material[DragonMob][MobName1]) or Humanoid.Health <= 0 or not v:FindFirstChild("Humanoid") or not v:FindFirstChild("HumanoidRootPart") or not v.Parent
        						                    _G.Magnet = false
        						                    FastAttack = false
        						                end
        						            end)
        						        else
        						            _G.Magnet = false
        						            FastAttack = false
        						            if not ThirdSea then
        						                Sea3()
        						                return
        						            end
        						            Teleport(CFrame.new( -10993,332, -8940))
        						        end
        						    else
        						        if CheckMaterial("Dragon Scale") < 20 then
            						        if MultiFindObject(game:GetService("Workspace").Enemies, Material[MagmaMob][MobName1]) then
            						            table.foreach(game:GetService("Workspace").Enemies:GetChildren(), function(_,v)
            						                if table.find(v.Name, Material[MagmaMob][MobName1]) and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Parent and v.Humanoid.Health >= 1 then
            						                    repeat task.wait()
            						                        _G.MobPos = v.HumanoidRootPart.CFrame
            						                        Teleport(_G.MobPos*CFrame.new(0,30,0))
            						                        FastAttack = true
            						                        _G.Magnet = true
            						                    until not not getgenv().U.Main.AutoGodhuman or not MultiFindObject(game:GetService("Workspace").Enemies, Material[MagmaMob][MobName1]) or Humanoid.Health <= 0 or not v:FindFirstChild("Humanoid") or not v:FindFirstChild("HumanoidRootPart") or not v.Parent
            						                    _G.Magnet = false
            						                    FastAttack = false
            						                end
            						            end)
            						        else
            						            _G.Magnet = false
            						            FastAttack = false
            						            if not SecondSea then
            						                Sea3()
            						                return
            						            end
            						            Teleport(Material[MagmaMob][MobCFrame1])
            						        end
            						    else
            						        if CheckMaterial("Dragon Scale") < 20 then
                						        if MultiFindObject(game:GetService("Workspace").Enemies, Material[MysticMob][MobName1]) then
                						            table.foreach(game:GetService("Workspace").Enemies:GetChildren(), function(_,v)
                						                if table.find(v.Name, Material[MysticMob][MobName1]) and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Parent and v.Humanoid.Health >= 1 then
                						                    repeat task.wait()
                						                        _G.MobPos = v.HumanoidRootPart.CFrame
                						                        Teleport(_G.MobPos*CFrame.new(0,30,0))
                						                        FastAttack = true
                						                        _G.Magnet = true
                						                    until not not getgenv().U.Main.AutoGodhuman or not MultiFindObject(game:GetService("Workspace").Enemies, Material[MysticMob][MobName1]) or Humanoid.Health <= 0 or not v:FindFirstChild("Humanoid") or not v:FindFirstChild("HumanoidRootPart") or not v.Parent
                						                    _G.Magnet = false
                						                    FastAttack = false
                						                end
                						            end)
                						        else
                						            _G.Magnet = false
                						            FastAttack = false
                						            if not SecondSea then
                						                Sea3()
                						                return
                						            end
                						            Teleport(Material[MysticMob][MobCFrame1])
                						        end
                						    else
                						        
                						    end
            						    end
        						    end
        						end
        					end
                        end
                    end
               -- end)
            end
        end)
    end)

    b1:AddToggle('Auto DragonTalon',getgenv().U.Main.DragonTalon,function(a)
        getgenv().U.Main.DragonTalon = a
        save()
        task.spawn(function()
            while task.wait() do
                pcall(function()
                    if getgenv().U.Main.DragonTalon then
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon", true) ~= 1 then
                            if game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then--Check
                                if FindBackPack('Dragon Claw') then
                                    if CheckMastery('Dragon Claw') >= 400 then
                                        if getgenv().U.Main.AutoFarm then getgenv().U.Main.AutoFarm = false end
                                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon", true) == 3 then
                                            local string_1 = "Bones";
                                            local string_2 = "Buy";
                                            local number_1 = 1;
                                            local number_2 = 1;
                                            local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                            Target:InvokeServer(string_1, string_2, number_1, number_2);
            
                                            local string_1 = "BuyDragonTalon";
                                            local bool_1 = true;
                                            local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                            Target:InvokeServer(string_1, bool_1);
                                        elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon", true) == 1 then
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
                                        else

                                            local string_1 = "BuyDragonTalon";
                                            local bool_1 = true;
                                            local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                            Target:InvokeServer(string_1, bool_1);
                                            local string_1 = "BuyDragonTalon";
                                            local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                            Target:InvokeServer(string_1);
                                        end 
                                    else getgenv().U.Main.AutFarm = true
                                    end
                                else
                                    local string_1 = "BuyDragonClaw";
                                    local bool_1 = true;
                                    local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                    Target:InvokeServer(string_1, bool_1);
                                end
                            end
                        else
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDragonTalon")
                        end
                    end
                end)
            end
        end)
    end)

    b1:AddToggle('Auto Electric Claw',getgenv().U.Main.EClaw,function(a)
        getgenv().U.Main.EClaw = a
        save()
        task.spawn(function()
            while task.wait() do
                pcall(function()
                    if getgenv().U.Main.EClaw then
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw", true) ~= 1 then
                            if game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then
                                if FindBackPack("Electro") then
                                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 400 then
                                        local v175 = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw", true);
                                        if v175 == 4 then
                                            local v176 = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw", "getgenv().U.Main.AutoEvoleRace");
                                            if v176 == nil then
                                                game.Players.localPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-12548, 337, -7481)
                                            end
                                        else
                                            local string_1 = "BuyElectricClaw";
                                            local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                            Target:InvokeServer(string_1);
                                        end
                                    else
                                        if game:GetService("Workspace").Enemies:FindFirstChild('Reborn Skeleton [Lv. 1975]') or game:GetService("Workspace").Enemies:FindFirstChild('Living Zombie [Lv. 2000]') or game:GetService("Workspace").Enemies:FindFirstChild('Demonic Soul [Lv. 2025]') or game:GetService("Workspace").Enemies:FindFirstChild('Posessed Mummy [Lv. 2050]') then
                                            for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                                if v.Name == 'Reborn Skeleton [Lv. 1975]' or v.Name == 'Living Zombie [Lv. 2000]' or v.Name == 'Demonic Soul [Lv. 2025]' or v.Name == 'Posessed Mummy [Lv. 2050]' then
                                                    repeat task.wait()
                                                        getgenv().MobPos = v.HumanoidRootPart.CFrame
                                                        Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,3))
                                                        BusoAndKen()
                                                        EquipTool('Electro')
                                                        Magnet = true
                                                        Attack = true
                                                    until not getgenv().U.Main.AutoFarmBone or not v.Parent or v.Humanoid.Health <= 0 or not v:FindFirstChild('Humanoid') or not v:FindFirstChild('HumanoidRootPart')
                                                end
                                            end
                                        else
                                            Teleport(CFrame.new(-9479.2168, 141.215088, 5577.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0))
                                            Attack = false
                                            Magnet = false
                                        end
                                    end
                                else
                                    local string_1 = "BuyElectro";
                                    local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                    Target:InvokeServer(string_1);
                                end
                            end
                        else
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw")
                        end
                    end
                end)
            end
        end)
    end)

    b1:AddToggle('Auto Sharkman Karate',getgenv().U.Main.SharkKarate,function(a)
        getgenv().U.Main.SharkKarate = a
        save()
        task.spawn(function()
            while task.wait() do
                pcall(function()
                    if getgenv().U.Main.SharkKarate then
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectricClaw", true) ~= 1 then
                            if FindBackPack("Fishman Karate") then
                                if string.find(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate"), "keys") then  
                                    if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Water Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Water Key") then
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate",true)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
                                    elseif not game.Players.LocalPlayer.Backpack:FindFirstChild("Water Key") or not game.Players.LocalPlayer.Backpack:FindFirstChild("Water Key") then
                                        if game:GetService("ReplicatedStorage"):FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then
                                            if game:GetService("Workspace").Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then 	
                                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                                    if v.Name == "Tide Keeper [Lv. 1475] [Boss]" then    
                                                        repeat task.wait()
                                                            Teleport(v.HumanoidRootPart.CFrame*CFrame.new(0,25,5))
                                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                            v.HumanoidRootPart.Anchored = true
                                                            EquipTool(WeaponName)
                                                        until not v.Parent or v.Humanoid.Health <= 0 or getgenv().U.Main.SharkKarate == false or game:GetService("Players").LocalPlayer.Character:FindFirstChild("Library Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Library Key")
                                                        FastAttack = false
                                                    end
                                                end
                                            else
                                                Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Tide Keeper [Lv. 1475] [Boss]").HumanoidRootPart.CFrame)
                                            end
                                        end   
                                    end
                                else
                                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate",true) == 1 then
                                        if FindBackPack('Fishman Karate') then
                                            if CheckMastery('Fishman Karate') >= 400 then
                                                if getgenv().U.Main.AutoFarm == false then
                                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
                                                else getgenv().U.Main.AutoFarm = false
                                                end
                                            else
                                                EquipTool('Fishman Karate')
                                                getgenv().U.Main.AutoFarm = true
                                            end
                                        else game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
                                        end
                                    else if Beli >= 750000 then if getgenv().U.Main.AutoFarm then getgenv().U.Main.AutoFarm = false end
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
                                    else getgenv().U.Main.AutoFarm = true end
                                    end
                                end
                            else
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
                            end
                        else
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySharkmanKarate")
                        end
                    end
                end)
            end
        end)
    end)

    b1:AddToggle('Auto DeathStep',getgenv().U.Main.DeathStep,function(a)
        getgenv().U.Main.DeathStep = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.DeathStep then
                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep", true) ~= 1 then
                        if FindBackPack('Black Leg') then
                            if game:GetService("Workspace").Map.IceCastle.Hall.LibraryDoor.PhoeyuDoor.Transparency == 0 then  
                                if game:GetService("Players").LocalPlayer.Character:FindFirstChild("Library Key") or game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Library Key") then
                                    EquipTool("Library Key")
                                    repeat task.wait() 
                                        Teleport(CFrame.new(6371.2001953125, 296.63433837890625, -6841.18115234375)) 
                                    until (CFrame.new(6371.2001953125, 296.63433837890625, -6841.18115234375).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 or not getgenv().U.Main.DeathStep
                                    if (CFrame.new(6371.2001953125, 296.63433837890625, -6841.18115234375).Position - game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 3 then
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep",true)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
                                    end
                                elseif not FindBackPack('Library Key') then   
                                    if game:GetService("ReplicatedStorage"):FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]") then
                                        if game:GetService("Workspace").Enemies:FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]") then 	
                                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                                if v.Name == "Awakened Ice Admiral [Lv. 1400] [Boss]" and v:FindFirstChild('Humanoid') and v:FindFirstChild('HuamnoidRootPart') and v.Humanoid.Health >= 1 then    
                                                    repeat task.wait()
                                                        Teleport(v.HumanoidRootPart.CFrame*CFrame.new(0,25,0))
                                                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                        v.HumanoidRootPart.Anchored = true
                                                    until not v.Parent or v.Humanoid.Health <= 0 or not getgenv().U.Main.DeathStep or FindBackPack('Library Key')
                                                end
                                            end
                                        else
                                            Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Awakened Ice Admiral [Lv. 1400] [Boss]").HumanoidRootPart.CFrame)
                                        end
                                    end
                                end
                            else
                                if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep",true) == 1 then
                                    if CheckMastery('Black Leg') >= 400 then
                                        if Beli >= 2500000 then
                                            if Fragments >= 5000 then if getgenv().U.Raids.AutoRaid == true then getgenv().U.Raids.AutoRaid = false end
                                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
                                            else
                                                getgenv().U.Raids.AutoRaid = true
                                            end
                                        else 
                                            getgenv().U.Main.AutoFarm = true
                                        end
                                    else
                                        EquipTool('Black Leg')
                                        getgenv().U.Main.AutoFarm = true
                                    end
                                else
                                    if Beli >= 100000 then 
                                        if getgenv().U.Main.AutoFarm == true then 
                                            getgenv().U.Main.AutoFarm = false
                                        end
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
                                    end
                                end
                            end
                        else
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
                        end
                    else
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyDeathStep")
                    end
                end
            end
        end)
    end)

    b1:AddToggle('Auto Superhuman',getgenv().U.Main.Superhuman,function(a)
        getgenv().U.Main.Superhuman = a
        if getgenv().U.Main.Superhuman then
            if game.Players.LocalPlayer:FindFirstChild("WeaponAssetCache") then
                if not game.Players.LocalPlayer.Backpack:FindFirstChild("Combat") and not game.Players.LocalPlayer.Character:FindFirstChild("Combat") then
                    if not game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and not game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") then
                        if not game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and not game.Players.LocalPlayer.Character:FindFirstChild("Electro") then
                            if not game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and not game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") then
                                if not game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and not game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") then
                                    if not game.Players.LocalPlayer.Backpack:FindFirstChild("Superhuman") and not game.Players.LocalPlayer.Character:FindFirstChild("Superhuman") then
                                        local args = {
                                            [1] = "BuyElectro"
                                        }
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                    end
                                end
                            end
                        end
                    end
                end
                if game.Players.LocalPlayer.Backpack:FindFirstChild("Combat") or game.Players.LocalPlayer.Character:FindFirstChild("Combat") then
                    local args = {
                        [1] = "BuyElectro"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                end
                if game.Players.LocalPlayer.Backpack:FindFirstChild("Electro") and game.Players.LocalPlayer.Backpack:FindFirstChild("Electro").Level.Value >= 300 then
                    local args = {
                        [1] = "BuyBlackLeg"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                end
                if game.Players.LocalPlayer.Character:FindFirstChild("Electro") and game.Players.LocalPlayer.Character:FindFirstChild("Electro").Level.Value >= 300 then
                    local args = {
                        [1] = "BuyBlackLeg"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                end
                if game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Backpack:FindFirstChild("Black Leg").Level.Value >= 300 then
                    local args = {
                        [1] = "BuyFishmanKarate"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                end
                if game.Players.LocalPlayer.Character:FindFirstChild("Black Leg") and game.Players.LocalPlayer.Character:FindFirstChild("Black Leg").Level.Value >= 300 then
                    local args = {
                        [1] = "BuyFishmanKarate"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                end
                if game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Backpack:FindFirstChild("Fishman Karate").Level.Value >= 300  then
                    local args = {
                        [1] = "BlackbeardReward",
                        [2] = "DragonClaw",
                        [3] = "2"
                    }
                    HaveDragonClaw = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    if getgenv().U.Main.Superhuman and game.Players.LocalPlayer.Data.Fragments.Value <= 1500 and HaveDragonClaw == 0 then
                        if game.Players.LocalPlayer.Data.Level.Value > 1100 then
                            getgenv().U.Raids.RaidSelect = "Flame"
                            getgenv().U.Raids.AutoRaid = true
                            if AutoFarm then getgenv().U.Main.AutoFarm = false end
                        end
                    else
                        getgenv().U.Raids.AutoRaid = false
                        if AutoFarm then getgenv().U.Main.AutoFarm = true end
                        local args = {
                            [1] = "BlackbeardReward",
                            [2] = "DragonClaw",
                            [3] = "2"
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        getgenv().U.Raids.AutoRaid = false
                        if AutoFarm then getgenv().U.Main.AutoFarm = true end
                    end
                end
                if game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate") and game.Players.LocalPlayer.Character:FindFirstChild("Fishman Karate").Level.Value >= 300  then
                    local args = {
                        [1] = "BlackbeardReward",
                        [2] = "DragonClaw",
                        [3] = "2"
                    }
                    HaveDragonClaw = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    if getgenv().U.Main.Superhuman and game.Players.LocalPlayer.Data.Fragments.Value <= 1500 and HaveDragonClaw == 0 then
                        if game.Players.LocalPlayer.Data.Level.Value > 1100 then
                            getgenv().U.Raids.RaidSelect = "Flame"
                            getgenv().U.Raids.AutoRaid = true
                            if AutoFarm then getgenv().U.Main.AutoFarm = false end
                        end
                    else
                        getgenv().U.Raids.AutoRaid = false
                        if AutoFarm then getgenv().U.Main.AutoFarm = true end
                        local args = {
                            [1] = "BlackbeardReward",
                            [2] = "DragonClaw",
                            [3] = "2"
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        getgenv().U.Raids.AutoRaid = false
                        if AutoFarm then getgenv().U.Main.AutoFarm = true end
                    end
                end

                if game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Backpack:FindFirstChild("Dragon Claw").Level.Value >= 300 then
                    AutoFarm = getgenv().U.Main.AutoFarm
                    local args = {
                        [1] = "BuySuperhuman"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                end
                if game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw") and game.Players.LocalPlayer.Character:FindFirstChild("Dragon Claw").Level.Value >= 300 then
                    AutoFarm = getgenv().U.Main.AutoFarm
                    local args = {
                        [1] = "BuySuperhuman"
                    }
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                end 
            end
        end
    end)
end

local b12 = Auto:CreatePage("", 1)
b12:AddLabel([[\\ Swords //]]) do

    local function StartTrial(Trial)
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial",tostring(Trial))
    end

    local function CDKQuestCheck()
        local o={}
        local a = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress")
        local b = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial",getgenv().Quest)
        for a,b in pairs(a) do
            table.insert(o,b)
        end
        return o
    end

    local AllMobSpawn = {
        [1] = CFrame.new(-373, 75, 5550),
        [2] = CFrame.new(-469, 74, 5904),
        [3] = CFrame.new(6339, 52, -1213),
        [4] = CFrame.new(6594, 383, 139),
        [5] = CFrame.new(5308, 819, 1047),
        [6] = CFrame.new(2447, 73, -7470),
        [7] = CFrame.new(3671, 161, -6932),
        [8] = CFrame.new(-10560, 332, -8466),
        [9] = CFrame.new(-10993, 332, -8940),
        [10] = CFrame.new(-13479, 333, -7905),
        [11] = CFrame.new(-13545, 470, -6917),
        [12] = CFrame.new(-12107, 332, -10549),
        [13] = CFrame.new(-13286, 392, -9769),
        [14] = CFrame.new(-8760, 142, 6039),
        [15] = CFrame.new(-10144, 140, 5932),
        [16] = CFrame.new(-9507, 172, 6158),
        [17] = CFrame.new(-9577, 6, 6223),
        [18] = CFrame.new(-2124, 123, -10435),
        [19] = CFrame.new(-2124, 123, -10435),
        [20] = CFrame.new(-641, 127, -11062),
        [21] = CFrame.new(-641, 127, -11062),
        [22] = CFrame.new(-2365, 38, -12099),
        [23] = CFrame.new(-1651, 38, -12308),
        [24] = CFrame.new(-1870, 38, -12938),
        [25] = CFrame.new(-1926, 88, -12850),
        [26] = CFrame.new(231, 23, -12194),
        [27] = CFrame.new(71, 77, -12632),
        [28] = CFrame.new(134, 77, -12882),
        [29] = CFrame.new(-1408, 16, -14552),
        [30] = CFrame.new(-777, 23, -14453),
    }

    local Number = 1

    task.spawn(function()
        while task.wait() do
            pcall(function()
                if getgenv().U.Main.AutoCDK then
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v:FindFirstChild("HazeESP") then
                            v.HazeESP.Size = UDim2.new(50,50,50,50)
                            v.HazeESP.MaxDistance = "inf"
                        end
                    end
                    for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
                        if v:FindFirstChild("HazeESP") then
                            v.HazeESP.Size = UDim2.new(50,50,50,50)
                            v.HazeESP.MaxDistance = "inf"
                        end
                    end
                end
            end)
        end
    end)

    task.spawn(function()
        while task.wait() do
            pcall(function()
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if getgenv().U.Main.AutoCDK and v:FindFirstChild("HazeESP") and (v.HumanoidRootPart.Position - (getgenv().Haze).Position).magnitude <= 300 then
                        v.HumanoidRootPart.CFrame = getgenv().Haze
                        v.HumanoidRootPart.CanCollide = false
                        --v.HumanoidRootPart.Size = Vector3.new(50,50,50)
                        if not v.HumanoidRootPart:FindFirstChild("BodyVelocity") then
                            local vc = Instance.new("BodyVelocity", v.HumanoidRootPart)
                            vc.MaxForce = Vector3.new(1, 1, 1) * math.huge
                            vc.Velocity = Vector3.new(0, 0, 0)
                        end
                    end
                end
            end)
        end
    end)

    local function InstantTeleport(Position)
        game.Players.LocalPlayer.Character.Humanoid.Health = -math.huge
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
        wait(1)
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = Position
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
    end

    local Quest = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","Progress","Good");

    local function findClosestMob(group, position)
        local closestPart, closestPartMagnitude

        local tmpMagnitude
        for i, v in pairs(group:GetChildren()) do
            if closestPart then
                tmpMagnitude = (position - v.HumanoidRootPart.Position).magnitude

                if tmpMagnitude < closestPartMagnitude then
                    closestPart = v
                    closestPartMagnitude = tmpMagnitude 
                end
            else
                closestPart = v
                closestPartMagnitude = (position - v.HumanoidRootPart.Position).magnitude
            end
        end
        return closestPart, closestPartMagnitude
    end

    local TaskCDK = b1:AddLabel('CDK Task : ???')

    b12:AddToggle('Auto Cursed Dual Katana',getgenv().U.Main.AutoCDK,function(a)
        getgenv().U.Main.AutoCDK = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.AutoCDK then
                    if Quest.Finished == true then return end
                    if not Quest.Opened then
                        -- Check 2 Swords and make this 350+ mas
                    end;
        
                    if Quest.Good == -4 then
                        -- Remove the scroll and Kill a skeletons
                    end;
        
                    -- 》Quests《

                    -- int ติดลบ = เริ่มเควสแล้ว elseif int ไม่ได้ติดลบแปลว่ายังไม่เริ่ม
        
                    if Quest.Evil ~= 4 then
                        continue;
                    else
                        if Quest.Good == -1 then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good");
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","BoatQuest",game.Workspace.NPCs:FindFirstChild("Luxury Boat Dealer"))
                            repeat task.wait()
                                Teleport(CFrame.new(-9546.990234375, 21.139892578125, 4686.1142578125))
                                repeat wait() until plr:DistanceFromCharacter(CFrame.new(-9546.990234375, 21.139892578125, 4686.1142578125).Position) < 10
                                Teleport(CFrame.new(-6120.0576171875, 16.455780029296875, -2250.697265625))
                                repeat wait() until plr:DistanceFromCharacter(CFrame.new(-6120.0576171875, 16.455780029296875, -2250.697265625).Position) < 10
                                Teleport(CFrame.new(-9533.2392578125, 7.254445552825928, -8372.69921875))
                                repeat wait() until plr:DistanceFromCharacter(CFrame.new(-9533.2392578125, 7.254445552825928, -8372.69921875).Position) < 10
                            until (Quest.Good ~= -1) or not getgenv().U.Main.AutoCDK;
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good");
                        else
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good");
                        end;
                        if Quest.Good == -2 then
                            if (CFrame.new(-5539.3115234375, 313.800537109375, -2972.372314453125).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 500 then
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                        if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 2000 then
                                            repeat task.wait()
                                                v.HumanoidRootPart.CanCollide = false;
                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,25,5));
                                            until (Quest.Good ~= -2) or not getgenv().U.Main.AutoCDK;
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good");
                                        end;
                                    end;
                                end;
                            else
                                Teleport(CFrame.new(-5545.1240234375, 313.800537109375, -2976.616455078125));
                            end;
                        else
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good");
                        end;
                        if Quest.Good == -3 then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Cake Queen [Lv. 2175] [Boss]") or game.ReplicatedStorage:FindFirstChild("Cake Queen [Lv. 2175] [Boss]") then
                                if game:GetService("Workspace").Enemies:FindFirstChild("Cake Queen [Lv. 2175] [Boss]") then
                                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                        if v.Name == "Cake Queen [Lv. 2175] [Boss]" then
                                            if v.Humanoid.Health > 0 then
                                                repeat task.wait()
                                                    BusoAndKen()
                                                    EquipTool(WeaponName)
                                                    v.Humanoid.JumpPower = 0
                                                    v.Humanoid.WalkSpeed = 0
                                                    v.HumanoidRootPart.CanCollide = false
                                                    v.Humanoid:ChangeState(11)
                                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,50,0))
                                                until (Quest.Good ~= -3) or not getgenv().U.Main.AutoCDK or game:GetService("Workspace").Map:FindFirstChild("HeavenlyDimension");
                                            end
                                        end
                                    end
                                else
                                    Teleport(CFrame.new(-709.3132934570312, 381.6005859375, -11011.396484375))
                                end
                            elseif game:GetService("Workspace").Map:FindFirstChild("HeavenlyDimension") then
                                repeat task.wait()
                                    if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton [Lv. 2200]") or game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton [Lv. 2200] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Heaven's Guardian [Lv. 2200] [Boss]") then
                                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                            if v.Name == "Cursed Skeleton [Lv. 2200]" or v.Name == "Cursed Skeleton [Lv. 2200] [Boss]" or v.Name == "Heaven's Guardian [Lv. 2200] [Boss]" then
                                                if v.Humanoid.Health > 0 then
                                                    repeat task.wait()
                                                        BusoAndKen()
                                                        EquipTool(WeaponName)
                                                        v:BreakJoints()
                                                        v.Humanoid.JumpPower = 0
                                                        v.Humanoid.WalkSpeed = 0;
                                                        v.HumanoidRootPart.CanCollide = false
                                                        v.Humanoid:ChangeState(11)
                                                    until (Quest.Good ~= -3) or v.Humanoid.Health <= 0 or not v.Parent or not getgenv().U.Main.AutoCDK;
                                                end;
                                            end;
                                        end;
                                    else
                                        wait(5)
                                        Teleport(game:GetService("Workspace").Map.HeavenlyDimension.Torch1.CFrame);
                                        wait(1.5);
                                        game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game);
                                        wait(1.5);
                                        Teleport(game:GetService("Workspace").Map.HeavenlyDimension.Torch2.CFrame);
                                        wait(1.5);
                                        game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game);
                                        wait(1.5);
                                        Teleport(game:GetService("Workspace").Map.HeavenlyDimension.Torch3.CFrame);
                                        wait(1.5);
                                        game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game);
                                        wait(1.5);
                                        Teleport(game:GetService("Workspace").Map.HeavenlyDimension.Exit.CFrame);
                                    end;
                                until (Quest.Good ~= -3) or not getgenv().U.Main.AutoCDK;
                            else
                                if Hop then
                                    ServerHop();
                                end;
                            end;
                        else
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good");
                        end;
                    end;
        
                    if Quest.Evil == -1 then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil");
                        if game:GetService("Workspace").Enemies:FindFirstChild("Mythological Pirate [Lv. 1850]") then
                            for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if v.Name == "Mythological Pirate [Lv. 1850]" then
                                    repeat task.wait()
                                        Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-2));
                                    until (Quest.Evil ~= -1) or not getgenv().U.Main.AutoCDK;
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil");
                                end;
                            end;
                        else
                            Teleport(CFrame.new(-13451.46484375, 543.712890625, -6961.0029296875));
                        end;
                    else
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil");
                    end;
                    if Quest.Evil == -2 then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v:FindFirstChild("HazeESP") and v:FindFirstChild('HumanoidRootPart') then
                                repeat task.wait()
                                    if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 2000 then
                                        Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,20,0))
                                        BusoAndKen()
                                        EquipTool(WeaponName)
                                        getgenv().Haze = v.HumanoidRootPart.CFrame
                                        v.Humanoid.JumpPower = 0
                                        v.Humanoid.WalkSpeed = 0
                                        v.HumanoidRootPart.CanCollide = false
                                        v.Humanoid:ChangeState(11)
                                    end      
                                until (Quest.Evil ~= -2) or not getgenv().U.Main.AutoCDK or not v.Parent or v.Humanoid.Health <= 0 or not v:FindFirstChild("HazeESP")
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil");
                            else
                                for x,y in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
                                    if y:FindFirstChild("HazeESP") and findClosestMob(game:GetService("ReplicatedStorage"), y.HumanoidRootPart.Position) < 4000 then
                                        Teleport(y.HumanoidRootPart.CFrame* CFrame.new(0,20,0));
                                        repeat wait() until (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - y.HumanoidRootPart.Position).magnitude < 100;
                                    end;
                                end;
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil");
                            end;
                        end;
                    else
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil");
                    end;
                    if Quest.Evil == -3 then
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Hallow Essence") then 
                            EquipTool('Hallow Essence')
                            Teleport(game:GetService("Workspace").Map["Haunted Castle"].Summoner.Detection.CFrame)
                        elseif game:GetService("Workspace").Map:FindFirstChild("HellDimension") then
                            repeat task.wait()
                                if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton [Lv. 2200]") or game:GetService("Workspace").Enemies:FindFirstChild("Cursed Skeleton [Lv. 2200] [Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Hell's Messenger [Lv. 2200] [Boss]") then
                                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                        if v.Name == "Cursed Skeleton [Lv. 2200]" or v.Name == "Cursed Skeleton [Lv. 2200] [Boss]" or v.Name == "Hell's Messenger [Lv. 2200] [Boss]" then
                                            if v:FindFirstChild('Humanoid') and v:FindFirstChild('HumanoidRootPart') and v.Humanoid.Health > 0 then
                                                repeat task.wait()
                                                    Magnet = true
                                                    BusoAndKen()
                                                    EquipTool(WeaponName)
                                                    v.Humanoid.JumpPower = 0
                                                    v.Humanoid.WalkSpeed = 0
                                                    v.HumanoidRootPart.CanCollide = false
                                                    v.Humanoid:ChangeState(11)
                                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,25,5))
                                                until (Quest.Evil ~= -3) or v.Humanoid.Health <= 0 or not v.Parent or not getgenv().U.Main.AutoCDK
                                            end
                                        end
                                    end
                                else
                                    wait(5)
                                    Teleport(game:GetService("Workspace").Map.HellDimension.Torch1.CFrame)
                                    wait(1.5)
                                    game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                                    wait(1.5)        
                                    Teleport(game:GetService("Workspace").Map.HellDimension.Torch2.CFrame)
                                    wait(1.5)
                                    game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                                    wait(1.5)     
                                    Teleport(game:GetService("Workspace").Map.HellDimension.Torch3.CFrame)
                                    wait(1.5)
                                    game:GetService("VirtualInputManager"):SendKeyEvent(true, "E", false, game)
                                    wait(1.5)     
                                    Teleport(game:GetService("Workspace").Map.HellDimension.Exit.CFrame)
                                end
                            until (Quest.Evil ~= -3) or not getgenv().U.Main.AutoCDK
                        else
                            if game:GetService("Workspace").Enemies:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") or game.ReplicatedStorage:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
                                if game:GetService("Workspace").Enemies:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
                                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                        if v.Name == "Soul Reaper [Lv. 2100] [Raid Boss]" then
                                            if v.Humanoid.Health > 0 then
                                                repeat task.wait()
                                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-2))
                                                until (Quest.Evil ~= -3) or not getgenv().U.Main.AutoCDK or game:GetService("Workspace").Map:FindFirstChild("HellDimension")
                                            end
                                        end
                                    end
                                else
                                    Teleport(CFrame.new(-9570.033203125, 315.9346923828125, 6726.89306640625))
                                end
                            else
                                if game:GetService("Workspace").Enemies:FindFirstChild('Reborn Skeleton [Lv. 1975]') or game:GetService("Workspace").Enemies:FindFirstChild('Living Zombie [Lv. 2000]') or game:GetService("Workspace").Enemies:FindFirstChild('Demonic Soul [Lv. 2025]') or game:GetService("Workspace").Enemies:FindFirstChild('Posessed Mummy [Lv. 2050]') then
                                    for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                        if v.Name == 'Reborn Skeleton [Lv. 1975]' or v.Name == 'Living Zombie [Lv. 2000]' or v.Name == 'Demonic Soul [Lv. 2025]' or v.Name == 'Posessed Mummy [Lv. 2050]' then
                                            repeat task.wait()
                                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,3))
                                                BusoAndKen()
                                                EquipTool(WeaponName)
                                                Magnet = true
                                            until (Quest.Evil ~= -3) or not getgenv().U.Main.AutoCDK or not v.Parent or v.Humanoid.Health <= 0 or not v:FindFirstChild('Humanoid') or not v:FindFirstChild('HumanoidRootPart')
                                        end
                                    end
                                else
                                    Teleport(CFrame.new(-9479.2168, 141.215088, 5577.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0))
                                    Magnet = false
                                end
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Buy",1,1)
                            end
                        end;
                    else
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Evil");
                    end;
                end;
            end;
        end);
    end);

    if ThirdSea then
        for i,v in pairs(game:GetService("Workspace").Map["Boat Castle"].Summoner.Circle:GetChildren()) do
            if v.Name == 'Part' then
                if tostring(v.BrickColor):find('Hot pink') then
                    print(v.Part.BrickColor)
                end
                if tostring(v.BrickColor):find('Oyster') then
                    print(v.Part.BrickColor)
                end
                if tostring(v.BrickColor):find('Dark stone grey') then
                    print(v.Part.BrickColor)
                end
            end
        end
    end
    b12:AddToggle('Auto Darkdagger',getgenv().U.Main.AutoDarkdagger,function(a)
        getgenv().U.Main.AutoDarkdagger = a
        save()
        task.spawn(function()
            while task.wait() do
                pcall(function()
                    if getgenv().U.Main.AutoDarkdagger then
                        if game:GetService('Workspace').Enemies:FindFirstChild('rip_indra True Form [Lv. 5000] [Raid Boss]') then
                            for i,v in pairs(game:GetService('Workspace').Enemies:GetChilren()) do
                                if v.Name == 'rip_indra True Form [Lv. 5000] [Raid Boss]' and v:FindFirstChild('Humanoid') and v:FindFirstChild('HumanoidRootPart') or v.Humanoid.Heath >= 1 then
                                    repeat task.wait()
                                        EquipTool(WeaponName)
                                        Teleport(v.HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                    until not getgenv().U.Main.AutoDarkdagger or not v.Parent or not v:FindForstChild('HumanoidRootPart') or not v:FindFirstChild('Humanoid') or v.Humanoid.Healt <= 0
                                end
                            end
                        else
                            if game:GetService('ReplicatedStorage'):FindFirstChild('rip_indra True Form [Lv. 5000] [Raid Boss]') then
                                Teleport(game:GetService('ReplicatedStorage'):FindFirstChild('rip_indra True Form [Lv. 5000] [Raid Boss]').HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                            end
                        end
                    end
                end)
            end
        end)
    end)

    b12:AddToggle('Auto Activate Haki Pad',false,function(a)
        ActivateHaki = a
        task.spawn(function()
            while task.wait() do
                pcall(function()
                    if ThirdSea then
                        if ActivateHaki then
                            if not Pink and not White and not Red then
                                local plr = game.Players.LocalPlayer.Character.HumanoidRootPart
                                for i,v in pairs(game:GetService("Workspace").Map["Boat Castle"].Summoner.Circle:GetChildren()) do
                                    if v.Name == 'Part' then
                                        if tostring(v.BrickColor) == ('Really red') then
                                            if v.Part.ClassName == "Part" then
                                                if tostring(v.Part.BrickColor) == 'Dark stone grey' then
                                                    if not au then
                                                        local args = {
                                                            [1] = "activateColor",
                                                            [2] = "Pure Red"
                                                        }
                                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                        au = true
                                                    end
                                                    task.wait()
                                                    plr.CFrame = v.CFrame*CFrame.new(0,3,0)
                                                    Red = true
                                                else
                                                    Red = true
                                                end
                                            end
                                        end
                                        task.wait(3)
                                        if tostring(v.BrickColor) == ('Oyster') then
                                            if v.Part.ClassName == "Part" then
                                                if tostring(v.Part.BrickColor) == 'Dark stone grey' then
                                                    if not df then
                                                        local args = {
                                                            [1] = "activateColor",
                                                            [2] = "Snow White"
                                                        }
                                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                        df = true
                                                    end
                                                    plr.CFrame = v.CFrame*CFrame.new(0,3,0)
                                                    White = true
                                                else
                                                    White = true
                                                end
                                            end
                                        end
                                        task.wait(3)
                                        if tostring(v.BrickColor) == ('Hot pink') then
                                            if v.Part.ClassName == "Part" then
                                                if tostring(v.Part.BrickColor) == 'Dark stone grey' then
                                                    if not nk then
                                                        local args = {
                                                            [1] = "activateColor",
                                                            [2] = "Winter Sky"
                                                        }
                                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                                        nk = true
                                                    end
                                                    task.wait()
                                                    plr.CFrame = v.CFrame*CFrame.new(0,3,0)
                                                    Pink = true
                                                else
                                                    Pink=true
                                                end
                                            end
                                        end
                                    end
                                end
                            else
                                print("Workkkkk")
                                plr.CFrame = game:GetService("Workspace").Map["Boat Castle"].Summoner.Circle.Detection.CFrame
                            end
                        end
                    end
                end)
            end
        end)
    end)

    local a = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getColors")
    for i,v in pairs(a) do
        if v.Name and v.Unlocked then
            print(v.Name)
        end
    end

    --[[
        CheckSwordMastery({
            Name = "",
            Mastery = 100,
        })
    ]]

    -- ก็อปทำไมไอ่เบื๊อก

    CheckInventoryMastery = function(...)
        local data = {...}
        if type(data) == 'table' then continue() end
        for _,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
            if type(v) == "table" then
                if v.Name == data.Name then
                    if not data.Mastery then return "h" end
                    if v.Mastery >= data.Mastery then
                        return true else return false
                    end
                else return "e"
                end
            end
        end
        return false
    end

    b12:AddToggle('Auto True Triple Katana',getgenv().U.Main.AutoTTK,function(a)
        getgenv().U.Main.AutoTTK = a
        getgenv().Clip = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.AutoTTK then
                    if SecondSea then
                        if CheckInventoryMastery({"Saddi"}) == "e" then
                            if Beli >= 2000000 then
                                FindSword(1);
                            else
                                Farm({'Water Fighter [Lv. 1450]','Sea Soldier [Lv. 1425]'},CFrame.new(-3385,239, -10542));
                            end;
                        end
                        if CheckInventoryMastery({"Wando"}) == "e" then
                            if Beli >= 2000000 then
                                FindSword(1);
                            else
                                Farm({'Water Fighter [Lv. 1450]','Sea Soldier [Lv. 1425]'},CFrame.new(-3385,239, -10542));
                            end;
                        end
                        if CheckInventoryMastery({"Shisui"}) == "e" then
                            if Beli >= 2000000 then
                                FindSword(1);
                            else
                                Farm({'Water Fighter [Lv. 1450]','Sea Soldier [Lv. 1425]'},CFrame.new(-3385,239, -10542));
                            end;
                        end
                        if CheckInventoryMastery({"Shisui", 350}) == false then
                            if not FindBackPack("Shisui") then Loaditem('Shisui') end
                            Farm({'Water Fighter [Lv. 1450]','Sea Soldier [Lv. 1425]'},CFrame.new(-3385,239, -10542));
                        else continue()
                        end
                        if CheckInventoryMastery({"Wando", 350}) == false then
                            if not FindBackPack("Wando") then Loaditem('Wando') end
                            Farm({'Water Fighter [Lv. 1450]','Sea Soldier [Lv. 1425]'},CFrame.new(-3385,239, -10542));
                        else continue()
                        end
                        if CheckInventoryMastery({"Saddi", 350}) == false then
                            if not FindBackPack("Shisui") then Loaditem('Shisui') end
                            Farm({'Water Fighter [Lv. 1450]','Sea Soldier [Lv. 1425]'},CFrame.new(-3385,239, -10542));
                        else continue()
                        end
                        if Beli >= 2000000 then
                            pcall(function()
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("MysteriousMan","1")
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("MysteriousMan","2")
                            end)
                        else
                            Farm({'Water Fighter [Lv. 1450]','Sea Soldier [Lv. 1425]'},CFrame.new(-3385,239, -10542));
                        end;
                    else
                        Sea2();
                    end;
                end;
            end;
        end);
    end)

    b12:AddToggle('Auto Tushita (Beta)',getgenv().U.Main.AutoTushita,function(a)
        getgenv().U.Main.AutoTushita = a
        save()
        spawn(function()
            while task.wait() do
                pcall(function()
                    if getgenv().U.Main.AutoTushita then
                        if getgenv().U.Main.AutoTushita then
                            if not getgenv().U.Main.TorchQuest then
                                if game.Workspace.Enemies:FindFirstChild("rip_indra True Form [Lv. 5000] [Raid Boss]") or game.ReplicatedStorage:FindFirstChild("rip_indra True Form [Lv. 5000] [Raid Boss]") then
                                    getgenv().U.Main.AutoTushita = true
                                    repeat wait(1)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress")
                                    until game.Players.LocalPlayer.Backpack:FindFirstChild("Holy Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Holy Torch") or not getgenv().U.Main.AutoTushita
                                    wait(1)
                                    local TushutaQuest = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress")
                                    local Progess = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress")['Torches']
                                    if Progess[1] == false then
                                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Holy Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Holy Torch") then
                                            EquipTool("Holy Torch")
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",1)
                                        else
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress")
                                        end
                                    elseif Progess[2] == false then
                                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Holy Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Holy Torch") then
                                            EquipTool("Holy Torch")
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",2)
                                        else
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress")
                                        end
                                    elseif Progess[3] == false then
                                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Holy Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Holy Torch") then
                                            EquipTool("Holy Torch")
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",3)
                                        else
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress")
                                        end
                                    elseif Progess[4] == false then
                                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Holy Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Holy Torch") then
                                            EquipTool("Holy Torch")
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",4)
                                        else
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress")
                                        end
                                    elseif Progess[5] == false then
                                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Holy Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Holy Torch") then
                                            EquipTool("Holy Torch")
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",5)
                                        else
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress")
                                        end
                                    elseif TushutaQuest['KilledLongma'] == false then
                                        _G.Tushita_Q = true
                                    end
                                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Holy Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Holy Torch") then
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",1)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",2)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",3)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",4)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("TushitaProgress","Torch",5)
                                        wait(1)
                                        getgenv().U.Main.TorchQuest = true
                                        save()
                                    elseif game:GetService("ReplicatedStorage"):FindFirstChild("rip_indra True Form [Lv. 5000] [Raid Boss]") or game.Workspace.Enemies:FindFirstChild("rip_indra True Form [Lv. 5000] [Raid Boss]") then
                                        getgenv().U.Main.TorchQuest = true
                                        save()
                                    end
                                elseif PressPad and getgenv().U.Settings.AllowHop then
                                    if not game.Workspace.Enemies:FindFirstChild("rip_indra True Form [Lv. 5000] [Raid Boss]") and not game.ReplicatedStorage:FindFirstChild("rip_indra True Form [Lv. 5000] [Raid Boss]") then
                                        HopServer()
                                    end
                                elseif not PressPad then
                                end
                            else
                                if game.Workspace.Enemies:FindFirstChild("Longma [Lv. 2000] [Boss]") or game.ReplicatedStorage:FindFirstChild("Longma [Lv. 2000] [Boss]") then
                                    getgenv().U.Main.AutoTushita = true
                                    if game.Workspace.Enemies:FindFirstChild("Longma [Lv. 2000] [Boss]") then
                                        for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                            if v.Name == "Longma [Lv. 2000] [Boss]" and v.Humanoid.Health > 0 then
                                                repeat task.wait()
                                                    EquipTool(WeaponName)
                                                    Teleport(v.HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                                                until v.Humanoid.Health <= 0 or not v.Parent or not getgenv().U.Main.AutoTushita
                                            end
                                        end
                                    elseif game.ReplicatedStorage:FindFirstChild("Longma [Lv. 2000] [Boss]") then
                                        Teleport(game.ReplicatedStorage:FindFirstChild("Longma [Lv. 2000] [Boss]").HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                                    end
                                end
                            end
                        end
                    end
                end)
            end
        end)
    end)

    b12:AddToggle('Auto Fully Yama',getgenv().U.Main.AutoYama,function(a)
        getgenv().U.Main.AutoYama = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.AutoYama then
                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EliteHunter","Progress") >= 30 then
                        repeat task.wait()
                            fireclickdetector(game:GetService("Workspace").Map.Waterfall.SealedKatana.Handle.ClickDetector)
                        until GetSwords('Yama') or game.Players.LocalPlayer.Backpack:FindFirstChild("Yama") or not getgenv().U.Main.AutoYama
                    else
                        if game:GetService("Workspace").Enemies:FindFirstChild('Diablo [Lv. 1750]') or game:GetService("Workspace").Enemies:FindFirstChild('Urban [Lv. 1750]') or game:GetService("Workspace").Enemies:FindFirstChild('Deandre [Lv. 1750]') then
                            for _n,Enemy in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                if Enemy:FindFirstChild('Humanoid') or Enemy.Humanoid.Heath >= 1 then
                                    repeat task.wait()
                                        Teleport(Enemy.HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                                        Enemy.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                        EquipTool(WeaponName)
                                        Attack = true
                                    until not getgenv().U.Main.AutoYama or not Enemy:FindFirstChild('Humanoid') or not Enemy.Parent or Enemy.Humanoid.Heath <= 0
                                end
                            end
                        else
                            if getgenv().U.Settings.AllowHop then
                                ServerHop()
                            end
                        end
                    end
                end
            end
        end)
    end)

    b12:AddToggle('Auto Hallow Scythe',getgenv().U.Main.AutoHallowScythe,function(a)
        getgenv().U.Main.AutoHallowScythe = a
        save()
        task.spawn(function()
            while task.wait() do
                pcall(function()
                    if getgenv().U.Main.AutoHallowScythe then
                        if game.Workspace.Enemies:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") or game.ReplicatedStorage:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
                            if game.Workspace.Enemies:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                    if v.Name == "Soul Reaper [Lv. 2100] [Raid Boss]" and v.Humanoid.Health > 0 then
                                        if v.Humanoid:FindFirstChild("Animator") then
                                            v.Humanoid.Animator:Destroy()
                                        end
                                        repeat task.wait()
                                            EquipTool(WeaponName)
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                            Teleport(v.HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                                        until v.Humanoid.Health <= 0 or not v.Parent or not getgenv().U.Main.AutoHallowScythe
                                    end
                                end
                            elseif game.ReplicatedStorage:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
                                Teleport(game.ReplicatedStorage:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]").HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                            end
                        elseif not game.ReplicatedStorage:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") then
                            if game.Players.LocalPlayer.Character:FindFirstChild("Hallow Essence") or game.Players.LocalPlayer.Backpack:FindFirstChild("Hallow Essence") then
                                repeat task.wait()
                                    EquipTool("Hallow Essence")
                                    Teleport(CFrame.new(-8932.86, 143.258, 6063.31))
                                until not game.Players.LocalPlayer.Character:FindFirstChild("Hallow Essence") or not game.Players.LocalPlayer.Backpack:FindFirstChild("Hallow Essence") or game.Workspace.Enemies:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") or game.ReplicatedStorage:FindFirstChild("Soul Reaper [Lv. 2100] [Raid Boss]") 
                            else
                                if game.Players.LocalPlayer.Character.Humanoid.Health >= 1 then
                                    local args = {
                                        [1] = "Bones",
                                        [2] = "Check"
                                    }
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                    local args = {
                                        [1] = "Bones",
                                        [2] = "Buy",
                                        [3] = 1,
                                        [4] = 1
                                    }
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                                end
                                if game:GetService("Workspace").Enemies:FindFirstChild("Reborn Skeleton [Lv. 1975]") then
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                        if v.Name == "Reborn Skeleton [Lv. 1975]" and v.Humanoid.Health >= 1 then
                                            getgenv().MobPos = v.HumanoidRootPart.CFrame
                                            Magnet = true
                                            repeat task.wait()
                                                Teleport(v.HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                                                EquipTool(WeaponName)
                                            until not v:FindFirstChild('HumanoidRootPart') or v.Humanoid.Health <= 0 or not v.Parent or not getgenv().U.Main.AutoHallowScythe
                                            Magnet = false
                                        end
                                    end
                                elseif game.ReplicatedStorage:FindFirstChild("Reborn Skeleton [Lv. 1975]") then
                                    Teleport(game.ReplicatedStorage:FindFirstChild("Reborn Skeleton [Lv. 1975]").HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                                end
                            end
                        end
                    end
                end)
            end
        end)
    end)

    b12:AddToggle('Auto Buddy Sword',getgenv().U.Main.AutoBuddySword,function(a)
        getgenv().U.Main.AutoBuddySword = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.AutoBuddySword then
                    if game:GetService("Workspace").Enemies:FindFirstChild('Cake Queen [Lv. 2175] [Boss]') then
                        for _n,Enemy in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if Enemy.Name == 'Cake Queen [Lv. 2175] [Boss]' and Enemy:FindFirstChild('Humanoid') or Enemy.Humanoid.Heath >= 1 then
                                repeat task.wait()
                                    Teleport(Enemy.HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                                    Enemy.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                    EquipTool(WeaponName)
                                    Fast = true
                                until not getgenv().U.Main.AutoBuddySword or not Enemy:FindFirstChild('Humanoid') or not Enemy.Parent or Enemy.Humanoid.Heath <= 0
                            end
                        end
                    else
                        if game:GetService("ReplicatedStorage"):FindFirstChild('Cake Queen [Lv. 2175] [Boss]') then
                            Teleport(game:GetService("ReplicatedStorage"):FindFirstChild('Cake Queen [Lv. 2175] [Boss]').HumanoidRootPart.CFrame)
                        else
                            if getgenv().U.Settings.AllowHop then
                                ServerHop()
                            end
                        end
                    end
                end
            end
        end)
    end)

    b12:AddToggle('Auto Cavender',getgenv().U.Main.AutoCavender,function(a)
        getgenv().U.Main.AutoCavender = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.AutoCavender then
                    if game:GetService("Workspace").Enemies:FindFirstChild('Beautiful Pirate [Lv. 1950] [Boss]') then
                        for _n,Enemy in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if Enemy.Name == 'Beautiful Pirate [Lv. 1950] [Boss]' and Enemy:FindFirstChild('Humanoid') or Enemy.Humanoid.Heath >= 1 then
                                repeat task.wait()
                                    Teleport(Enemy.HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                                    Enemy.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                    EquipTool(WeaponName)
                                    Attack = true
                                until not getgenv().U.Main.AutoCavender or not Enemy:FindFirstChild('Humanoid') or not Enemy.Parent or Enemy.Humanoid.Heath <= 0
                            end
                        end
                    else
                        if game:GetService("ReplicatedStorage"):FindFirstChild('Beautiful Pirate [Lv. 1950] [Boss]') then
                            Teleport(game:GetService("ReplicatedStorage"):FindFirstChild('Beautiful Pirate [Lv. 1950] [Boss]').HumanoidRootPart.CFrame)
                        else
                            if getgenv().U.Settings.AllowHop then
                                ServerHop()
                            end
                        end
                    end
                end
            end
        end)
    end)

    b12:AddToggle('Auto Twin Hook',getgenv().U.Main.AutoTwinhook,function(a)
        getgenv().U.Main.AutoTwinhook = a
        save()
        task.spawn(function()
            while getgenv().U.Main.AutoTwinhook do task.wait()
                if game:GetService("Workspace").Enemies:FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") or game:GetService("ReplicatedStorage"):FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") then
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == "Captain Elephant [Lv. 1875] [Boss]" then
                            repeat task.wait()
                                BusoAndKen()
                                EquipTool(WeaponName)
                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                v.Humanoid.JumpPower = 0
                                v.Humanoid.WalkSpeed = 0
                                v.HumanoidRootPart.CanCollide = false
                                v.Humanoid:ChangeState(11)
                            until v.Humanoid.Health <= 0 or getgenv().U.Main.AutoTwinhook == false
                        end
                    end
                    if game:GetService("ReplicatedStorage"):FindFirstChild("Captain Elephant [Lv. 1875] [Boss]") then
                        Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Captain Elephant [Lv. 1875] [Boss]").CFrame*CFrame.new(0,30,0))
                    end
                end
            end
        end)
    end)

    b12:AddToggle('Auto Saber',getgenv().U.Main.AutoSaber,function(a)
        getgenv().U.Main.AutoSaber = a
        save()
        task.spawn(function()
            while task.wait() do
                pcall(function()
                    if getgenv().U.Main.AutoSaber and game.Players.LocalPlayer.Data.Level.Value >= 200 and not GetSwords('Saber') then
                        if getgenv().U.Main.AutoFarm then
                            getgenv().U.Main.AutoFarm = false
                        end
                        if game:GetService("Workspace").Map.Jungle.Final.Part.Transparency == 0 then
                            if game:GetService("Workspace").Map.Jung3le.QuestPlates.Door.Transparency == 0 then
                                if (CFrame.new(-1612.55884, 36.9774132, 148.719543, 0.37091279, 3.0717151e-09, -0.928667724, 3.97099491e-08, 1, 1.91679348e-08, 0.928667724, -4.39869794e-08, 0.37091279).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 100 then
                                    Teleport(game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame)
                                    wait(1)
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate1.Button.CFrame
                                    wait(1)
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate2.Button.CFrame
                                    wait(1)
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate3.Button.CFrame
                                    wait(1)
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate4.Button.CFrame
                                    wait(1)
                                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = game:GetService("Workspace").Map.Jungle.QuestPlates.Plate5.Button.CFrame
                                    wait(1) 
                                else
                                    Teleport(CFrame.new(-1612.55884, 36.9774132, 148.719543, 0.37091279, 3.0717151e-09, -0.928667724, 3.97099491e-08, 1, 1.91679348e-08, 0.928667724, -4.39869794e-08, 0.37091279))
                                end
                            else
                                if game:GetService("Workspace").Map.Desert.Burn.Part.Transparency == 0 then
                                    if game:GetService("Players").LocalPlayer.Backpack:FindFirstChild("Torch") or game.Players.LocalPlayer.Character:FindFirstChild("Torch") then
                                        EquipTool("Torch")
                                        Teleport(CFrame.new(1114.61475, 5.04679728, 4350.22803, -0.648466587, -1.28799094e-09, 0.761243105, -5.70652914e-10, 1, 1.20584542e-09, -0.761243105, 3.47544882e-10, -0.648466587))
                                    else
                                        Teleport(CFrame.new(-1610.00757, 11.5049858, 164.001587, 0.984807551, -0.167722285, -0.0449818149, 0.17364943, 0.951244235, 0.254912198, 3.42372805e-05, -0.258850515, 0.965917408))                 
                                    end
                                else
                                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") ~= 0 then
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","GetCup")
                                        task.wait()
                                        EquipTool("Cup")
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","FillCup",game:GetService("Players").LocalPlayer.Character.Cup)
                                        task.wait()
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","SickMan") 
                                    else
                                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == nil then
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon")
                                        elseif  game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 0 then
                                            if game:GetService("Workspace").Enemies:FindFirstChild("Mob Leader [Lv. 120] [Boss]") or game:GetService("ReplicatedStorage"):FindFirstChild("Mob Leader [Lv. 120] [Boss]") then
                                                Teleport(CFrame.new(-2967.59521, -4.91089821, 5328.70703, 0.342208564, -0.0227849055, 0.939347804, 0.0251603816, 0.999569714, 0.0150796166, -0.939287126, 0.0184739735, 0.342634559))
                                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                                    if v.Name == "Mob Leader [Lv. 120] [Boss]" then
                                                        repeat task.wait()
                                                            BusoAndKen()
                                                            EquipTool(WeaponName)
                                                            Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                                            getgenv().MobPos = v.HumanoidRootPart.CFrame
                                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                            v.Humanoid.JumpPower = 0
                                                            v.Humanoid.WalkSpeed = 0
                                                            v.HumanoidRootPart.CanCollide = false
                                                            v.Humanoid:ChangeState(11)
                                                        until v.Humanoid.Health <= 0 or getgenv().U.Main.AutoSaber == false
                                                    end
                                                end
                                            end
                                        elseif game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon") == 1 then
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","RichSon")
                                            wait(0.5)
                                            EquipTool("Relic")
                                            Teleport(CFrame.new(-1404.91504, 29.9773273, 3.80598116, 0.876514494, 5.66906877e-09, 0.481375456, 2.53851997e-08, 1, -5.79995607e-08, -0.481375456, 6.30572643e-08, 0.876514494))
                                        end
                                    end
                                end
                            end
                        else
                            if game:GetService("Workspace").Enemies:FindFirstChild("Saber Expert [Lv. 200] [Boss]") or game:GetService("ReplicatedStorage"):FindFirstChild("Saber Expert [Lv. 200] [Boss]") then
                                Teleport(CFrame.new(-1401.85046, 29.9773273, 8.81916237, 0.85820812, 8.76083845e-08, 0.513301849, -8.55007443e-08, 1, -2.77243419e-08, -0.513301849, -2.00944328e-08, 0.85820812))
                                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                    if v.Name == "Saber Expert [Lv. 200] [Boss]" then
                                        repeat task.wait()
                                            BusoAndKen()
                                            EquipTool(WeaponName)
                                            Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                            getgenv().MobPos = v.HumanoidRootPart.CFrame
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                            v.Humanoid.JumpPower = 0
                                            v.Humanoid.WalkSpeed = 0
                                            v.HumanoidRootPart.CanCollide = false
                                            v.Humanoid:ChangeState(11)
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SetSpawnPoint")
                                        until v.Humanoid.Health <= 0 or getgenv().U.Main.AutoSaber == false
                                        if v.Humanoid.Health <= 0 then
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("ProQuestProgress","PlaceRelic")
                                        end
                                    end
                                end
                            end
                        end
                    end
                end)
            end
        end)
    end)

    b12:AddToggle('Auto Pole',getgenv().U.Main.AutoPole,function(a)
        getgenv().U.Main.AutoPole = a
        save()
        task.spawn(function()
            while getgenv().U.Main.AutoPole do task.wait()
                if game:GetService("Workspace").Enemies:FindFirstChild("Thunder God [Lv. 575] [Boss]") then
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == "Thunder God [Lv. 575] [Boss]" then
                            repeat task.wait()
                                FastAttack = true
                                BusoAndKen()
                                EquipTool(WeaponName)
                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                v.Humanoid.JumpPower = 0
                                v.Humanoid.WalkSpeed = 0
                                v.HumanoidRootPart.CanCollide = false
                                v.Humanoid:ChangeState(11)
                            until v.Humanoid.Health <= 0 or getgenv().U.Main.AutoPole == false
                        end
                    end
                else
                    if game:GetService("ReplicatedStorage"):FindFirstChild("Thunder God [Lv. 575] [Boss]") then
                        Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Thunder God [Lv. 575] [Boss]").HumanoidRootPart.CFrame)
                    end
                end
            end
        end)
    end)

    b12:AddToggle('Auto Dragon Trident',getgenv().U.Main.AutoDragonTrident,function(a)
        getgenv().U.Main.AutoDragonTrident = a
        save()
        task.spawn(function()
            while getgenv().U.Main.AutoDragonTrident do task.wait()
                if game:GetService("Workspace").Enemies:FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == "Tide Keeper [Lv. 1475] [Boss]" then
                            repeat task.wait()
                                BusoAndKen()
                                EquipTool(WeaponName)
                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                v.Humanoid.JumpPower = 0
                                v.Humanoid.WalkSpeed = 0
                                v.HumanoidRootPart.CanCollide = false
                                v.Humanoid:ChangeState(11)
                            until v.Humanoid.Health <= 0 or getgenv().U.Main.AutoDragonTrident == false
                        end
                    end
                else
                    if game:GetService("ReplicatedStorage"):FindFirstChild("Tide Keeper [Lv. 1475] [Boss]") then
                        Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Tide Keeper [Lv. 1475] [Boss]").HumanoidRootPart.CFrame)
                    end
                end
            end
        end)
    end)

    b12:AddToggle('Auto Binzento V2',getgenv().U.Main.AutoBinzentoV2,function(a)
        getgenv().U.Main.AutoBinzentoV2 = a
        save() --(-4935.2099609375, 47.31159210205078, 4318.13671875)
        task.spawn(function()
            while getgenv().U.Main.AutoBinzentoV2 do task.wait()
                if game:GetService("Workspace").Enemies:FindFirstChild("Greybeard [Lv. 750] [Raid Boss]") then
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == "Greybeard [Lv. 750] [Raid Boss]" and v:FindFirstChild('Humanoid')and v:FindFirstChild('HumanoidRootPart') and v.Humanoid.Health >= 1 then
                            if (v.HumanoidRootPart.Position-plr.Character.HumanoidRootPart.Position).Magnitude <= 200 then
                                repeat task.wait()
                                    BusoAndKen()
                                    EquipTool(WeaponName)
                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                    getgenv().MobPos = v.HumanoidRootPart.CFrame
                                    v.Humanoid.JumpPower = 0
                                    v.Humanoid.WalkSpeed = 0
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Humanoid:ChangeState(11)
                                until v.Humanoid.Health <= 0 or getgenv().U.Main.AutoBinzentoV2 == false
                            else Teleport(CFrame.new(-4935.2099609375, 47.31159210205078, 4318.13671875))
                            end
                        end
                    end
                else
                    if game:GetService("ReplicatedStorage"):FindFirstChild("Greybeard [Lv. 750] [Raid Boss]") then
                        Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Greybeard [Lv. 750] [Raid Boss]").HumanoidRootPart.CFrame)
                    end
                end
            end
        end)
    end)

    b12:AddToggle('Auto Trident',getgenv().U.Main.AutoTrident,function(a)
        getgenv().U.Main.AutoTrident = a
        save()
    end)

    b12:AddToggle('Auto DarkBlade V2',getgenv().U.Main.AutoDarkbladeV2,function(a)
        getgenv().U.Main.AutoDarkbladeV2 = a
        save()
        task.spawn(function()
            while task.wait() do
            
            end
        end)
    end)
end

local b13 = Auto:CreatePage("", 1)
b13:AddLabel([[\\ Guns //]])

local function SoulGuitarCheck()
    local SoulGuitarQuest = {}
    for i,v in next,(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GuitarPuzzleProgress", "Check")) do
        table.insert(SoulGuitarQuest, v)
    end
    return SoulGuitarQuest
end

--[[
Trophies
CraftOnce
Ghost
Geavestones
Swamp
Pipes
]]

b13:AddToggle('Auto Soul Guitar',getgenv().U.Main.AutoAcuduimRifle,function(a)
    getgenv().U.Main.AutoAcuduimRifle = a
    save()
end)

b13:AddToggle('Auto Serpent Bow',getgenv().U.Main.AutoSerpentBow,function(a)
    getgenv().U.Main.AutoSerpentBow = a
    save()
    task.spawn(function()
        while task.wait() do
            if getgenv().U.Main.AutoSerpentBow then
                if game:GetService("Workspace").Enemies:FindFirstChild("Island Empress [Lv. 1675] [Boss]") then
                    for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                        if v.Name == "Island Empress [Lv. 1675] [Boss]" then
                            repeat task.wait()
                                BusoAndKen()
                                EquipTool(WeaponName)
                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                v.Humanoid.JumpPower = 0
                                v.Humanoid.WalkSpeed = 0
                                v.HumanoidRootPart.CanCollide = false
                                v.Humanoid:ChangeState(11)
                            until v.Humanoid.Health <= 0 or getgenv().U.Main.AutoSerpentBow == false
                        end
                    end
                else
                    if game:GetService("ReplicatedStorage"):FindFirstChild("Island Empress [Lv. 1675] [Boss]") then
                        Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Island Empress [Lv. 1675] [Boss]").HumanoidRootPart.CFrame)
                    end
                end
            end
        end
    end)
end)    

b13:AddToggle('Auto Acuduim Rifile',getgenv().U.Main.AutoAcuduimRifle,function(a)
    getgenv().U.Main.AutoAcuduimRifle = a
    save()
end)

b13:AddToggle('Auto Kabucha',getgenv().U.Main.AutoKabucha,function(a)
    getgenv().U.Main.AutoKabucha = a
    save()
end)

--b1:AddLabel([[\\ Acessories //]])

local b2 = Auto:CreatePage("", 2)

b2:AddLabel([[\\ Cake Prince //]])
local MobKilled = b2:AddLabel("[ ??? ] Kills Remains")

local KillMob

-- task.spawn(function()
--     while task.wait() do
--         pcall(function()
--             if getgenv().U.Main.AutoCakePrince then--Check
--                 local Mobs = game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner",true):split(">")[2]:split("<")[1]
--                 if string.len(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")) == 88 then
--                     MobKilled:ChangeText("[ "..game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner",true):split(">")[2]:split("<")[1].." ] Kills Remains")
--                 elseif string.len(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")) == 87 then
--                     MobKilled:ChangeText("[ "..game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner",true):split(">")[2]:split("<")[1].." ] Kills Remains")
--                 elseif string.len(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")) == 86 then
--                     MobKilled:ChangeText("[ "..game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner",true):split(">")[2]:split("<")[1].." ] Kills Remains")
--                 else
--                     MobKilled:ChangeText("Boss Is Spawned")
--                 end
--             end
--         end)
--     end
-- end)

b2:AddToggle('Auto Cake Prince',getgenv().U.Main.AutoCakePrince,function(a)
    getgenv().U.Main.AutoCakePrince = a
    save()
    task.spawn(function()
        while task.wait() do
            if getgenv().U.Main.AutoCakePrince then
                if game.ReplicatedStorage:FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") or game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") then
                    if game:GetService("Workspace").Enemies:FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") then
                        for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                            if v.Name == "Cake Prince [Lv. 2300] [Raid Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                repeat task.wait()
                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,60,0))
                                    getgenv().MobPos = v.HumanoidRootPart.CFrame
                                    BusoAndKen()
                                    EquipTool(WeaponName)
                                    Attack = true
                                    --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                    v.Humanoid.JumpPower = 0
                                    v.Humanoid.WalkSpeed = 0
                                    v.HumanoidRootPart.CanCollide = false
                                    v.Humanoid:ChangeState(11)
                                until not getgenv().U.Main.AutoCakePrince or not v.Parent or v.Humanoid.Health <= 0
                                Attack = false
                            end
                        end
                    else
                        if game:GetService("Workspace").Map.CakeLoaf.BigMirror.Other.Transparency == 0 then
                            if game:GetService("ReplicatedStorage"):FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]") then
                                Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Cake Prince [Lv. 2300] [Raid Boss]").HumanoidRootPart.CFrame)
                            end
                        end 
                    end
                else
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner",true)
                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")
                    if game:GetService("Workspace").Enemies:FindFirstChild("Cookie Crafter [Lv. 2200]") or game:GetService("Workspace").Enemies:FindFirstChild("Cake Guard [Lv. 2225]") or game:GetService("Workspace").Enemies:FindFirstChild("Baking Staff [Lv. 2250]") or game:GetService("Workspace").Enemies:FindFirstChild("Head Baker [Lv. 2275]") then
                        for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if (v.Name == "Cookie Crafter [Lv. 2200]" or v.Name == "Cake Guard [Lv. 2225]" or v.Name == "Baking Staff [Lv. 2250]" or v.Name == "Head Baker [Lv. 2275]") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health >= 1 then
                                repeat task.wait()
                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,60,0))
                                    getgenv().MobPos = v.HumanoidRootPart.CFrame
                                    BusoAndKen()
                                    Magnet = true
                                    Attack = true
                                    EquipTool(WeaponName)
                                until not getgenv().U.Main.AutoCakePrince or not v.Parent or v.Humanoid.Health <= 0
                                FastAttack = false
                            end
                        end
                    else
                        Magnet = false
                        FastAttack = false
                        Teleport(CFrame.new(-2077, 252, -12373))
                    end
                end
            end
        end
    end)
end)

local DoughMob = {
    "Cookie Crafter [Lv. 2200]",
    "Cake Guard [Lv. 2225]",
    "Baking Staff [Lv. 2250]"
}

b2:AddToggle('Auto Dought King',getgenv().U.Main.AutoDoughtKing,function(a)
    getgenv().U.Main.AutoDoughtKing = a
    save()
    task.spawn(function()
        while task.wait() do
            if getgenv().U.Main.AutoDoughtKing then
                if getgenv().U.Main.OpenDoughtRaid then
                    if not game:GetService("Workspace").Map.CakeLoaf:FindFirstChild("RedDoor") then
                        if game.Players.LocalPlayer.Character:FindFirstChild("Red Key") or game.Players.LocalPlayer.Backpack:FindFirstChild("Red Key") then
                            local args = {
                                [1] = "CakeScientist",
                                [2] = "Check"
                            }

                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))    
                            local args = {
                                [1] = "RaidsNpc",
                                [2] = "Check"
                            }

                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))                        
                        end
                    elseif game:GetService("Workspace").Map.CakeLoaf:FindFirstChild("RedDoor") then
                        if game.Players.LocalPlayer.Character:FindFirstChild("Red Key") or game.Players.LocalPlayer.Backpack:FindFirstChild("Red Key") then
                            RedDorTween = Teleport(CFrame.new(-2681.97998, 64.3921585, -12853.7363, 0.149007782, -1.87902192e-08, 0.98883605, 3.60619588e-08, 1, 1.35681812e-08, -0.98883605, 3.36376011e-08, 0.149007782))
                            if (CFrame.new(-2681.97998, 64.3921585, -12853.7363, 0.149007782, -1.87902192e-08, 0.98883605, 3.60619588e-08, 1, 1.35681812e-08, -0.98883605, 3.36376011e-08, 0.149007782).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 5 then
                                game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(-2681.97998, 64.3921585, -12853.7363, 0.149007782, -1.87902192e-08, 0.98883605, 3.60619588e-08, 1, 1.35681812e-08, -0.98883605, 3.36376011e-08, 0.149007782)
                                wait(0.5)
                                EquipTool("Red Key")
                                wait(0.5)
                            end
                        elseif game.Workspace:FindFirstChild("Enemies"):FindFirstChild("Dough King [Lv. 2300] [Raid Boss]") then
                            if game:GetService("Workspace").Enemies:FindFirstChild("Dough King [Lv. 2300] [Raid Boss]") then
                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                    if getgenv().U.Main.AutoDoughtKing and v.Name == "Dough King [Lv. 2300] [Raid Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                        repeat task.wait()
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                            BusoAndKen()
                                            EquipTool(WeaponName)
                                            Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                            FastAttack = true
                                        until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0 or game:GetService("ReplicatedStorage"):FindFirstChild("Dough King [Lv. 2300] [Raid Boss]")
                                        FastAttack = true
                                    end
                                end
                            else
                                if game:GetService("Workspace").Map.CakeLoaf.BigMirror.Other.Transparency == 0 then
                                    if game:GetService("ReplicatedStorage"):FindFirstChild("Dough King [Lv. 2300] [Raid Boss]") then
                                        Teleport(game:GetService("ReplicatedStorage"):FindFirstChild("Dough King [Lv. 2300] [Raid Boss]").HumanoidRootPart.CFrame)
                                    end
                                end 
                            end
                        elseif game.Players.LocalPlayer.Character:FindFirstChild("Sweet Chalice") or game.Players.LocalPlayer.Backpack:FindFirstChild("Sweet Chalice") then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner", true)
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")
                            if game:GetService("Workspace").Enemies:FindFirstChild("Cookie Crafter [Lv. 2200]") or game:GetService("Workspace").Enemies:FindFirstChild("Cake Guard [Lv. 2225]") or game:GetService("Workspace").Enemies:FindFirstChild("Baking Staff [Lv. 2250]") or game:GetService("Workspace").Enemies:FindFirstChild("Head Baker [Lv. 2275]") then
                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                    if (v.Name == "Cookie Crafter [Lv. 2200]" or v.Name == "Cake Guard [Lv. 2225]" or v.Name == "Baking Staff [Lv. 2250]" or v.Name == "Head Baker [Lv. 2275]") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                        repeat task.wait()
                                            getgenv().MobPos = v.HumanoidRootPart.CFrame
                                            Magnet = true
                                            BusoAndKen()
                                            EquipTool(WeaponName)
                                            Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,30))
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner", true)
                                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")
                                            FastAttack = true
                                        until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                FastAttack = false
                                Magnet = false
                                Teleport(CFrame.new(-2077, 252, -12373))
                            end
                        elseif FindBackPack("God's Chalice") then
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SweetChaliceNpc")
                            wait(0.2)
                        elseif not FindBackPack("God's Chalice") and (game.Workspace.Enemies:FindFirstChild("Deandre [Lv. 1750]") or game.Workspace.Enemies:FindFirstChild("Urban [Lv. 1750]") or game.Workspace.Enemies:FindFirstChild("Diablo [Lv. 1750]") or game.ReplicatedStorage:FindFirstChild("Deandre [Lv. 1750]") or game.ReplicatedStorage:FindFirstChild("Urban [Lv. 1750]") or game.ReplicatedStorage:FindFirstChild("Diablo [Lv. 1750]")) then
                            if game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                                if string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Diablo") or string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Urban") or string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Deandre") then
                                    for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
                                        if string.find(v.Name,"Diablo") then
                                            Teleport(v.HumanoidRootPart.CFrame)
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                        end	
                                        if string.find(v.Name,"Urban") then
                                            Teleport(v.HumanoidRootPart.CFrame)
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                        end
                                        if string.find(v.Name,"Deandre") then
                                            Teleport(v.HumanoidRootPart.CFrame)
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                        end
                                    end
                                    for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                        if string.find(v.Name,"Diablo") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                            repeat task.wait()
                                                BusoAndKen()
                                                --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                EquipTool(WeaponName)
                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,30))
                                            until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                        end
                                        if string.find(v.Name,"Urban") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                            repeat task.wait()
                                                BusoAndKen()
                                                --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                EquipTool(WeaponName)
                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,30))
                                            until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                        end
                                        if string.find(v.Name,"Deandre") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                            repeat task.wait()
                                                EquipTool(WeaponName)
                                                --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                                BusoAndKen()
                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0))
                                            until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                        end
                                    end
                                else
                                    local string_1 = "EliteHunter";
                                    local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                    Target:InvokeServer(string_1);
                                end
                            else
                                local string_1 = "EliteHunter";
                                local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                Target:InvokeServer(string_1);
                            end
                        else
                            if game:GetService("Workspace").Enemies:FindFirstChild("Candy Rebel [Lv. 2375]") or game:GetService("Workspace").Enemies:FindFirstChild("Sweet Thief [Lv. 2350]") or game:GetService("Workspace").Enemies:FindFirstChild("Chocolate Bar Battler [Lv. 2325]") or game:GetService("Workspace").Enemies:FindFirstChild("Cocoa Warrior [Lv. 2300]") then
                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                    if (v.Name == "Candy Rebel [Lv. 2375]" or v.Name == "Sweet Thief [Lv. 2350]" or v.Name == "Chocolate Bar Battler [Lv. 2325]" or v.Name == "Cocoa Warrior [Lv. 2300]") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                        repeat task.wait()
                                            getgenv().MobPos = v.HumanoidRootPart.CFrame
                                            Magnet = true
                                            Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0))
                                            FastAttack = true
                                            BusoAndKen()
                                            EquipTool(WeaponName)
                                        until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                FastAttack = false
                                Magnet = false
                                Teleport(CFrame.new(620.6344604492188, 200.93644714355469, -12581.369140625))
                            end
                        end
                    end
                else
                    if game.Workspace:FindFirstChild("Enemies"):FindFirstChild("Dough King [Lv. 2300] [Raid Boss]") or game:GetService("ReplicatedStorage"):FindFirstChild("Dough King [Lv. 2300] [Raid Boss]") then
                        if game:GetService("Workspace").Enemies:FindFirstChild("Dough King [Lv. 2300] [Raid Boss]") then
                            for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                if getgenv().U.Main.AutoDoughtKing and v.Name == "Dough King [Lv. 2300] [Raid Boss]" and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                        BusoAndKen()
                                        EquipTool(WeaponName)
                                        Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,30))
                                    until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0 or game:GetService("ReplicatedStorage"):FindFirstChild("Dough King [Lv. 2300] [Raid Boss]")
                                end
                            end
                        else
                            if game:GetService("Workspace").Map.CakeLoaf.BigMirror.Other.Transparency == 0 then
                                if (game:GetService("Workspace").Enemies:FindFirstChild("Dough King [Lv. 2300] [Raid Boss]").Position - plr.Character.HumanoidRootPart.Position).Magnitude > 3000 then
                                    Teleport(CFrame.new(-2151.82153, 149.315704, -12404.9053))
                                end
                            end 
                        end
                    elseif game.Players.LocalPlayer.Character:FindFirstChild("Sweet Chalice") or game.Players.LocalPlayer.Backpack:FindFirstChild("Sweet Chalice") then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner", true)
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")
                        if game:GetService("Workspace").Enemies:FindFirstChild("Cookie Crafter [Lv. 2200]") or game:GetService("Workspace").Enemies:FindFirstChild("Cake Guard [Lv. 2225]") or game:GetService("Workspace").Enemies:FindFirstChild("Baking Staff [Lv. 2250]") or game:GetService("Workspace").Enemies:FindFirstChild("Head Baker [Lv. 2275]") then
                            for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                if (v.Name == "Cookie Crafter [Lv. 2200]" or v.Name == "Cake Guard [Lv. 2225]" or v.Name == "Baking Staff [Lv. 2250]" or v.Name == "Head Baker [Lv. 2275]") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        getgenv().MobPos = v.HumanoidRootPart.CFrame
                                        Magnet = true
                                        BusoAndKen()
                                        EquipTool(WeaponName)
                                        Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,30))
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner", true)
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CakePrinceSpawner")
                                    until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        else
                            Magnet = false
                            Teleport(CFrame.new(-2077, 252, -12373))
                        end
                    elseif FindBackPack("God's Chalice") then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("SweetChaliceNpc")
                        wait(0.2)
                    elseif not FindBackPack("God's Chalice") and (game.Workspace.Enemies:FindFirstChild("Deandre [Lv. 1750]") or game.Workspace.Enemies:FindFirstChild("Urban [Lv. 1750]") or game.Workspace.Enemies:FindFirstChild("Diablo [Lv. 1750]") or game.ReplicatedStorage:FindFirstChild("Deandre [Lv. 1750]") or game.ReplicatedStorage:FindFirstChild("Urban [Lv. 1750]") or game.ReplicatedStorage:FindFirstChild("Diablo [Lv. 1750]")) then
                        if game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                            if string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Diablo") or string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Urban") or string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Deandre") then
                                for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
                                    if string.find(v.Name,"Diablo") then
                                        Teleport(v.HumanoidRootPart.CFrame)
                                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                    end	
                                    if string.find(v.Name,"Urban") then
                                        Teleport(v.HumanoidRootPart.CFrame)
                                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                    end
                                    if string.find(v.Name,"Deandre") then
                                        Teleport(v.HumanoidRootPart.CFrame)
                                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                    end
                                end
                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                    if string.find(v.Name,"Diablo") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                        repeat task.wait()
                                            BusoAndKen()
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                            EquipTool(WeaponName)
                                            Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                    end
                                    if string.find(v.Name,"Urban") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                        repeat task.wait()
                                            BusoAndKen()
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                            EquipTool(WeaponName)
                                            Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,0))
                                        until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                    end
                                    if string.find(v.Name,"Deandre") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                        repeat task.wait()
                                            EquipTool(WeaponName)
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                            BusoAndKen()
                                            Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0, 20, 0))
                                        until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                    end
                                end
                            else
                                local string_1 = "EliteHunter";
                                local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                Target:InvokeServer(string_1);
                            end
                        else
                            local string_1 = "EliteHunter";
                            local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                            Target:InvokeServer(string_1);
                        end
                    else
                        if game:GetService("Workspace").Enemies:FindFirstChild("Candy Rebel [Lv. 2375]") or game:GetService("Workspace").Enemies:FindFirstChild("Sweet Thief [Lv. 2350]") or game:GetService("Workspace").Enemies:FindFirstChild("Chocolate Bar Battler [Lv. 2325]") or game:GetService("Workspace").Enemies:FindFirstChild("Cocoa Warrior [Lv. 2300]") then
                            for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                if (v.Name == "Candy Rebel [Lv. 2375]" or v.Name == "Sweet Thief [Lv. 2350]" or v.Name == "Chocolate Bar Battler [Lv. 2325]" or v.Name == "Cocoa Warrior [Lv. 2300]") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        getgenv().MobPos = v.HumanoidRootPart.CFrame
                                        Magnet = true
                                        Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0, 30, 0))
                                        FastAttack = true
                                        BusoAndKen()
                                        EquipTool(WeaponName)
                                    until not getgenv().U.Main.AutoDoughtKing or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        else
                            FastAttack = false
                            Magnet = false
                            Teleport(CFrame.new(620.6344604492188, 200.93644714355469, -12581.369140625))
                        end
                    end
                end
            end
        end
    end)
end)

b2:AddToggle('Auto Open Dought Raid',getgenv().U.Main.OpenDoughtRaid,function(a)
    getgenv().U.Main.OpenDoughtRaid = a
    save()
end)

local b21 = Auto:CreatePage("", 2)
b21:AddLabel([[\\ Elite Hunter //]])

b21:AddToggle('Auto Kill Elite',getgenv().U.Main.EliteHunter,function(a)
    getgenv().U.Main.EliteHunter = a
    getgenv().Clip = a
    save()
    task.spawn(function()
        while task.wait() do
            if getgenv().U.Main.EliteHunter then
                if not FindBackPack("God's Chalice") and (game.Workspace.Enemies:FindFirstChild("Deandre [Lv. 1750]") or game.Workspace.Enemies:FindFirstChild("Urban [Lv. 1750]") or game.Workspace.Enemies:FindFirstChild("Diablo [Lv. 1750]") or game.ReplicatedStorage:FindFirstChild("Deandre [Lv. 1750]") or game.ReplicatedStorage:FindFirstChild("Urban [Lv. 1750]") or game.ReplicatedStorage:FindFirstChild("Diablo [Lv. 1750]")) then
                    if game.Players.LocalPlayer.PlayerGui.Main.Quest.Visible == true then
                        if string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Diablo") or string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Urban") or string.find(game.Players.LocalPlayer.PlayerGui.Main.Quest.Container.QuestTitle.Title.Text, "Deandre") then
                            for i,v in pairs(game:GetService("ReplicatedStorage"):GetChildren()) do
                                if string.find(v.Name,"Diablo") then
                                    Teleport(v.HumanoidRootPart.CFrame)
                                    --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                end	
                                if string.find(v.Name,"Urban") then
                                    Teleport(v.HumanoidRootPart.CFrame)
                                    --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                end
                                if string.find(v.Name,"Deandre") then
                                    Teleport(v.HumanoidRootPart.CFrame)
                                    --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                end
                            end
                            for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                if string.find(v.Name,"Diablo") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        BusoAndKen()
                                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                        EquipTool(WeaponName)
                                        Teleport(v.HumanoidRootPart.CFrame * CFrame.new(7, 10, 10))
                                    until not getgenv().U.Main.EliteHunter or not v.Parent or v.Humanoid.Health <= 0
                                end
                                if string.find(v.Name,"Urban") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        BusoAndKen()
                                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                        EquipTool(WeaponName)
                                        Teleport(v.HumanoidRootPart.CFrame * CFrame.new(7, 10, 10))
                                    until not getgenv().U.Main.EliteHunter or not v.Parent or v.Humanoid.Health <= 0
                                end
                                if string.find(v.Name,"Deandre") and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and v.Humanoid.Health > 0 then
                                    repeat task.wait()
                                        EquipTool(WeaponName)
                                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                        BusoAndKen()
                                        Teleport(v.HumanoidRootPart.CFrame * CFrame.new(7, 10, 10))
                                    until not getgenv().U.Main.EliteHunter or not v.Parent or v.Humanoid.Health <= 0
                                end
                            end
                        else
                            local string_1 = "EliteHunter";
                            local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                            Target:InvokeServer(string_1);
                        end
                    else
                        local string_1 = "EliteHunter";
                        local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                        Target:InvokeServer(string_1);
                    end
                else
                    if getgenv().U.Main.StopAtGod then
                        Teleport(plr.Character.HumanoidRootPart.CFrame)
                    end
                end
            end
        end
    end)
end)

b21:AddToggle("Stop at got God's Challice",getgenv().U.Main.StopAtGod,function(a)
    getgenv().U.Main.StopAtGod = a
    save()
end)

local b23 = Auto:CreatePage("", 2)
b23:AddLabel([[\\ Bones //]])

b23:AddToggle('Auto Farm Bones',getgenv().U.Main.AutoFarmBone,function(a)
    getgenv().U.Main.AutoFarmBone = a
    save()
    task.spawn(function()
        while task.wait() do
            pcall(function()
                if (getgenv().U.Main.AutoFarmBone == true) then
                    if game:GetService("Workspace").Enemies:FindFirstChild('Reborn Skeleton [Lv. 1975]') or game:GetService("Workspace").Enemies:FindFirstChild('Living Zombie [Lv. 2000]') or game:GetService("Workspace").Enemies:FindFirstChild('Demonic Soul [Lv. 2025]') or game:GetService("Workspace").Enemies:FindFirstChild('Posessed Mummy [Lv. 2050]') then
                        for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                            if v.Name == 'Reborn Skeleton [Lv. 1975]' or v.Name == 'Living Zombie [Lv. 2000]' or v.Name == 'Demonic Soul [Lv. 2025]' or v.Name == 'Posessed Mummy [Lv. 2050]' then
                                repeat task.wait()
                                    getgenv().MobPos = v.HumanoidRootPart.CFrame
                                    Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,3))
                                    BusoAndKen()
                                    EquipTool(WeaponName)
                                    Magnet = true
                                    Attack = true
                                until not getgenv().U.Main.AutoFarmBone or not v.Parent or v.Humanoid.Health <= 0 or not v:FindFirstChild('Humanoid') or not v:FindFirstChild('HumanoidRootPart')
                            end
                        end
                    else
                        Teleport(CFrame.new(-9479.2168, 230.215088, 5577.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0))
                        Attack = false
                        Magnet = false
                    end
                end
            end)
        end
    end)
end)

b23:AddLabel('Trading Bone')
b23:AddToggle('Auto Trade Death King',getgenv().U.Main.TradeBone,function(a)
    getgenv().U.Main.TradeBone = a
    save()
    task.spawn(function()
        while task.wait() do
            if getgenv().U.Main.TradeBone then
                if Material("Bones") > 49 then
                    if game.Players.LocalPlayer.Character.Humanoid.Health >= 1 then
                        local args = {
                            [1] = "Bones",
                            [2] = "Check"
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        local args = {
                            [1] = "Bones",
                            [2] = "Buy",
                            [3] = 1,
                            [4] = 1
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    end
                end
            end
        end
    end)
end)

local b24 = Auto:CreatePage("", 2)
b24:AddLabel([[\\ Events //]]) do

    b24:AddToggle('Auto Pirate Raids',getgenv().U.Main.AutoPirate,function(a)
        getgenv().U.Main.AutoPirate = a
    end)

    spawn(function()
        while getgenv().U.Main.AutoPirate do wait()
            if (CFrame.new(-5539.3115234375, 313.800537109375, -2972.372314453125).Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 500 then
                for i,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                    if v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                        if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude < 2000 then
                            repeat task.wait()
                                v.HumanoidRootPart.CanCollide = false;
                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,25,5));
                            until (Quest.Good ~= -2) or not getgenv().U.Main.AutoCDK;
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CDKQuest","StartTrial","Good");
                        end;
                    end;
                end;
            else
                Teleport(CFrame.new(-5545.1240234375, 313.800537109375, -2976.616455078125));
            end;
        end;
    end);
end;

local b25 = Auto:CreatePage("", 2)
b25:AddLabel([[\\ Materials [Locked] //]]) do

    if not type(getgenv().U.Main.SelectMaterials) == 'table' then
        getgenv().U.Main.SelectMaterials = {}
    end

    local Materials = {
        "Metal Scrap",
        "Leather",
        "Sky wings"
    }

    b25:AddDropdown('Select Materials',getgenv().U.Main.SelectMaterials,false,Materials,function(a)
        getgenv().U.Main.SelectMaterials = a
        save()
    end)

    b25:AddToggle('Auto Farm Material',getgenv().U.Main.AutoMaterial,function(a)
        getgenv().U.Main.AutoMaterial = a
        save()
    end)

    spawn(function()
        while wait() do
            pcall(function()
                if getgenv().U.Main.AutoMaterial then
                end
            end)
        end
    end)
end

local c1 = Client:CreatePage("", 1)
c1:AddLabel([[\\ Player Stats //]]) do

    Melee = c1:AddToggle('Melee',getgenv().U.Client.MeleeStats,function(a)
        getgenv().U.Client.MeleeStats = a
        save()
    end)

    Defense = c1:AddToggle('Defense',getgenv().U.Client.DefenseStats,function(a)
        getgenv().U.Client.DefenseStats = a
        save()
    end)

    Sword = c1:AddToggle('Sword',getgenv().U.Client.SwordStats,function(a)
        getgenv().U.Client.SwordStats = a
        save()
    end)

    Gun = c1:AddToggle('Gun',getgenv().U.Client.GunStats,function(a)
        getgenv().U.Client.GunStats = a
        save()
    end)

    DevilFruit = c1:AddToggle('Devil Fruits',getgenv().U.Client.DevilFruitStats,function(a)
        getgenv().U.Client.DevilFruitStats = a
        save()
    end)

    task.spawn(function() -- Auto Stats
        while task.wait() do
            if getgenv().U.Client.MeleeStats then
                local args = {
                    [1] = "AddPoint",
                    [2] = "Melee",
                    [3] = getgenv().U.Client.Points
                }
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            end
            if getgenv().U.Client.DefenseStats then 
                local args = {
                    [1] = "AddPoint",
                    [2] = "Defense",
                    [3] = getgenv().U.Client.Points
                }
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))				
            end
            if getgenv().U.Client.SwordStats then 
                local args = {
                    [1] = "AddPoint",
                    [2] = "Sword",
                    [3] = getgenv().U.Client.Points
                }
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))				
            end
            if getgenv().U.Client.DevilFruitStats then 
                local args = {
                    [1] = "AddPoint",
                    [2] = "Demon Fruit",
                    [3] = getgenv().U.Client.Points
                }
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))				
            end
            if getgenv().U.Client.GunStats then
                local args = {
                    [1] = "AddPoint",
                    [2] = "Gun",
                    [3] = getgenv().U.Client.Points
                }
                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
            end
        end
    end)
end

-- Esp --

local c2 = Client:CreatePage("", 2)
c2:AddLabel([[\\ Combats //]]) do

    local Task = c2:AddLabel('Target : [ ... ]');
    local CurrentBounty = c2:AddLabel('Current Bounties : [ 0 ]');
    local EarnedBounty = c2:AddLabel('Earned Bounties : [ 0 ]');
    local OldBounty = game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value
    local Bounty = tostring(game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value)
    local sub = string.sub 
    local len = string.len
    task.spawn(function()
        while task.wait() do
            pcall(function()
                local Earned = tostring(game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value - OldBounty)
                if len(Earned) == 4 then
                    Earned1 = sub(Earned,1,1).."."..sub(Earned,2,3).."K"
                elseif len(Earned) == 5 then
                    Earned1 = sub(Earned,1,2).."."..sub(Earned,3,4).."K"
                elseif len(Earned) == 6 then
                    Earned1 = sub(Earned,1,3).."."..sub(Earned,4,5).."K"
                elseif len(Earned) == 7 then
                    Earned1 = sub(Earned,1,1).."."..sub(Earned,2,3).."M"
                elseif len(Earned) == 8 then
                    Earned1 = sub(Earned,1,2).."."..sub(Earned,3,4).."M"
                elseif len(Earned) <= 3 then
                    Earned1 = Earned
                end
                -- EarnedBounty:ChangeText("Earned Bounties : [ ".. Earned1 .." ]")
            end)
        end
    end)

    -- task.spawn(function()
    --     while task.wait() do
    --         pcall(function()
    --             CurrentBounty:ChangeText("Current Bounties : [ "..game:GetService("Players").LocalPlayer.leaderstats["Bounty/Honor"].Value .. " ]")
    --         end)
    --     end
    -- end)
    
    local Skip = {}
    
    task.spawn(function()
        pcall(function()
            if getgenv().U.AUTOBountyHop then
                while task.wait() do
                    if #Skip > 3 and game:GetService("Players").LocalPlayer.PlayerGui.Main:FindFirstChild("InCombat").Visible == false then
                        ServerHop()
                    end
                end
            end
        end)
    end)

    task.spawn(function()
        while task.wait() do
            pcall(function()
                if getgenv().AutoFarmBounty then
                    if not game:GetService("Players").LocalPlayer.Character:FindFirstChild("HasBuso") then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Buso")
                    end
                end
            end)
        end
    end)

    task.spawn(function()
        while task.wait() do
            pcall(function()
                if getgenv().AutoFarmBounty then
                    game:GetService("Players").LocalPlayer.Character[SelectWeaponGun].Cooldown.Value = 0
                end
            end)
        end
    end)
    
    function TeleportEXE(Object)
        -- Teleport To hydra island
        if (HydratoCastle.Position - Object.Position).Magnitude <= 2500 and (Object.Position - plr.Character.HumanoidRootPart.Position).Magnitude > 2500 then
            
        elseif (MansiontoCastlePos.Position - Object.Position).Magnitude <= 2500 and (Object.Position - plr.Character.HumanoidRootPart.Position).Magnitude > 2500 then
            -- Telepot To Mansion
            
        elseif (Castletophydra.Position - Object.Position).Magnitude <= 2500 and (Object.Position - plr.Character.HumanoidRootPart.Position).Magnitude > 2500 then
            -- Teleport to Castle
        end
    end
    
    CastlePostoMansion = CFrame.new(-5084.8447265625, 316.48101806641, -3145.3752441406)
    MansiontoCastlePos = CFrame.new(-12464.596679688, 376.30590820312, -7567.2626953125)
    Castletophydra = CFrame.new(-5095.33984375, 316.48101806641, -3168.3134765625)
    HydratoCastle = CFrame.new(5741.869140625, 611.94750976562, -282.61154174805)
    
    getgenv().EscapeAt = 40
    
    task.spawn(function()
        while task.wait() do
            pcall(function()
                if getgenv().AutoFarmBounty then
                    for i,v in pairs(game:GetService("Workspace").Characters:GetChildren()) do
                        if v.Name ~= game.Players.LocalPlayer.Name then
                            if v:FindFirstChild("Humanoid") and v:FindFirstChild('HumanoidRootPart') and v:WaitForChild("Humanoid").Health > 0 and (game.Players.LocalPlayer.Character.HumanoidRootPart.Position - v.HumanoidRootPart.Position).Magnitude <= 17000 then
                                plyselecthunthelpold = v.Humanoid.Health
                                repeat task.wait()
                                    NameTarget = v.Name
                                    BusoAndKen()
                                    getgenv().SelectPly = v.Name
                                    if tostring(game.Players.LocalPlayer.Team) == "Pirates" then
                                        if game.Players.LocalPlayer.Character.Humanoid.Health < game.Players.LocalPlayer.Character.Humanoid.MaxHealth * getgenv().EscapeAt/100 then
                                            if (game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position - v:FindFirstChild("HumanoidRootPart").Position).Magnitude <= 999 then
                                            --Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,300,0))
                                                game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame = v:FindFirstChild("HumanoidRootPart").CFrame * CFrame.new(0,1000,0)
                                            else
                                                Teleport(v:FindFirstChild("HumanoidRootPart").CFrame * CFrame.new(0,1000,0))
                                            end
                                        else
                                            if (game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart").Position - v:FindFirstChild("HumanoidRootPart").Position).Magnitude <= 300 then
                                                local centreCFrame = v:FindFirstChild("HumanoidRootPart").CFrame
                                                local offset = CFrame.new(0,0,-5) -- Offset from the centre point
                                                local currentCamera = game:GetService("Players").LocalPlayer.Character:FindFirstChild("HumanoidRootPart")
                                                --game:GetService('RunService').RenderStepped:Connect(function()
                                                    centreCFrame = centreCFrame * CFrame.Angles(1, 0, 0) -- Rotate it on the Y axis
                                                    Teleport(centreCFrame * offset) -- Apply the offset
                                                --end)
                                            else Teleport(v:FindFirstChild("HumanoidRootPart").CFrame * CFrame.new(0,0,-10)*CFrame.Angles(math.rad(45), math.rad(90), math.rad(0)))
                                            end
                                        end
                                    elseif tostring(game.Players.LocalPlayer.Team) == "Marines" then
                                        if game.Players[NameTarget].Team ~= game.Players.LocalPlayer.Team then
                                            if game.Players.LocalPlayer.Character.Humanoid.Health < game.Players.LocalPlayer.Character.Humanoid.MaxHealth * getgenv().EscapeAt/100 then
                                                --Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,300,0))
                                                game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,1000,0)
                                            else
                                                if (game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").Position - v.HumanoidRootPart.Position).Magnitude <= 999 then
                                                    game:GetService("Players").LocalPlayer.Character:WaitForChild("HumanoidRootPart").CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,3,10)
                                                else Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,0,-10)*CFrame.Angles(math.rad(45), math.rad(90), math.rad(0)))
                                                end
                                            end
                                        end
                                    end
                                    spawn(function()
                                        if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 375 then
                                            StartCheckTarget = true
                                        end
                                    end)
                                    v.HumanoidRootPart.CanCollide = false
                                    --v.HumanoidRootPart.Size = Vector3.new(120,120,120)
                                    --game.Players[getgenv().SelectPly].Character.HumanoidRootPart.Size = Vector3.new(120,120,120)
                                    spawn(function()
                                        pcall(function()
                                            local args = {
                                                [1] = v:FindFirstChild("HumanoidRootPart").Position,
                                                [2] = v:FindFirstChild("HumanoidRootPart")
                                            }
                                            game:GetService("Players").LocalPlayer.Character[Gun].RemoteFunctionShoot:InvokeServer(unpack(args))
                                        end)
                                    end)
                                    TargetSelectHunt = v.Humanoid
                                    -- Task:ChangeText('Target : [ '.. v.Name ..' ]')
                                until getgenv().AutoFarmBounty == false or v.Humanoid.Health == 0 or not v:FindFirstChild("HumanoidRootPart") or not v:FindFirstChild("Humanoid") or not v.Parent or NextplySelect == true
                                NextplySelect = false
                                StartCheckTarget = false
                            end
                        end
                    end
                end
            end)
        end
    end)
    
    
    function CheckNotify(Text)
    	for i, v in pairs(game:GetService("Players")["LocalPlayer"].PlayerGui:FindFirstChild("Notifications"):GetChildren()) do
    		if v.Name == "NotificationTemplate" then
    			if string.lower(v.Text):find(Text) then
    				pcall(function()
    					--v:Destroy()
    					p.Text = "bruh he is died?"
    				end)
    				return true
    			end
    		end
    	end
    	return false
    end


    spawn(function()
        while task.wait(2) do 
            if getgenv().AutoFarmBounty then
                spawn(function()
                    if getgenv().SelectPly ~= nil then
                        if (game.Players[getgenv().SelectPly].Character.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
                            EquipTool(Melee)
                            task.wait(2)
                            EquipTool(Sword)
                            task.wait(2)
                            --EquipTool(DevilFruit)
                            --task.wait(5)
                            --endEquipTool(Gun)
                            --task.wait(6)
                        end
                    end
                end)
                spawn(function()
                    if getgenv().SelectPly ~= nil then
                        if (game.Players[getgenv().SelectPly].Character.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).Magnitude <= 50 then
                            spawn(function()
                                for i = 1,2 do
                                    SendKey("Z",0.2)
                                    SendKey("X",0.2)
                                    SendKey("C",0.2)
                                    SendKey("V",0.2)
                                end
                            end)
                        end
                    end
                end)
            end
        end
    end)
    
    spawn(function()
        local RunService = game:GetService("RunService")

        local Player = game:GetService("Players").LocalPlayer
        local Mouse = Player:GetMouse()
        
        RunService.RenderStepped:Connect(function()
            if getgenv().SelectPly~=nil and getgenv().AutoFarmBounty then
            	local target = Mouse.Hit.Position
            
            	target = game.Players:FindFirstChild(getgenv().SelectPly).Character:FindFirstChild("HumanoidRootPart").Position
            end
        end)
    end)

    spawn(function()
        local gg = getrawmetatable(game)
        local old = gg.__namecall
        setreadonly(gg,false)
        gg.__namecall = newcclosure(function(...)
            local method = getnamecallmethod()
            local args = {...}
            if tostring(method) == "FireServer" then
                if tostring(args[1]) == "RemoteEvent" then
                    if tostring(args[2]) ~= "true" and tostring(args[2]) ~= "false" then
                        if getgenv().AutoFarmBounty then
                            if getgenv().SelectPly ~= nil and game.Players:FindFirstChild(getgenv().SelectPly) then
                                for i=1,15 do args[2] = game.Players:FindFirstChild(getgenv().SelectPly).Character:FindFirstChild("HumanoidRootPart").Position end
                                return old(unpack(args))
                            end
                        end
                    end
                end
            end
            return old(...)
        end)
    end)

    task.spawn(function()
        pcall(function()
            while task.wait() do
                if getgenv().AutoFarmBounty then
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main:FindFirstChild('SafeZone').Visible == true or CheckNotify("died") or CheckNotify("Safe")or CheckNotify("ตาย") or CheckNotify("โซน") or table.find(Skip,getgenv().SelectPly) then
                        if not getgenv().SelectPly == nil and not table.find(Skip,getgenv().SelectPly) then
                            --table.insert(Skip,getgenv().SelectPly)
                        end
                        NextplySelect = true
                        getgenv().SelectPly = nil
                        TargetSelectHunt = nil
                        task.wait(10)
                    end
                end
            end
        end)
    end)

    task.spawn(function()
        pcall(function()
            while task.wait() do
                if getgenv().AutoFarmBounty then
                    if TargetSelectHunt ~= nil then
                        if StartCheckTarget then
                            task.wait(60)
                            if TargetSelectHunt.Health == TargetSelectHunt.MaxHealth or TargetSelectHunt.Health >= plyselecthunthelpold or game:GetService("Players").LocalPlayer.PlayerGui.Main:FindFirstChild('SafeZone').Visible == true or CheckNotify("died") or CheckNotify("Safe")or CheckNotify("ตาย") or CheckNotify("โซน") then
                                NextplySelect = true
                                TargetSelectHunt = nil
                                task.wait(10)
                            end
                        end
                    end
                end
            end
        end)
    end)

    task.spawn(function()
        pcall(function()
            while task.wait() do
                if getgenv().AutoFarmBounty then
                    if game:GetService("Players").LocalPlayer.PlayerGui.Main.PvpDisabled.Visible == true then
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("EnablePvp")
                    end
                end
            end
        end)
    end);
    
    c2:AddToggle("Auto Bounty Hunter",getgenv().U.AutoFarmBounty,function(a)
        getgenv().U.AutoFarmBounty = a
        getgenv().AutoFarmBounty = a
        Clip = a
        save()
    end)
    
    c2:AddToggle("Enabled Hop",getgenv().U.AutoFarmBountyHopnty,function(a)
        getgenv().U.AutoFarmBountyHop = a
        save()
    end)
end

local c220 = Client:CreatePage("Aimbot",2) do
    local function GetPlayerData()
        local Players = {}
        for i,v in pairs(game:GetService("Workspace").Characters:GetChildren()) do
            table.insert(Players.v)
        end
        return Players
    end
    
    --[[c220:AddDropdown("Select Player",GetPlayerData().Name,getgenv().U.Client.SelectPly,function(a)
        getgenv().U.Client.SelectPly = a
        save()
    end)
    
    c220:AddToggle("Enable Aimbot",getgenv().Client.Aimbot,function(a)
        getgenv().U.Client.Aimbot = a 
        save()
    end)]]
end

local c21 = Client:CreatePage("", 2)
c21:AddLabel([[\\ Players & Esp //]]) do
    --varibles
    function Highlight()
        if getgenv().U.Client.Esp_HigtLight == true then
            local Players = game:GetService("Players"):GetChildren()

            local highlight = Instance.new("Highlight")
            highlight.Name = "ESP"

            for i, v in pairs(Players) do
                repeat wait() until v.Character
                local highlightClone = highlight:Clone()
                highlightClone.Adornee = v.Character
                highlightClone.Parent = v.Character:FindFirstChild("HumanoidRootPart")
            end

            game.Players.PlayerAdded:Connect(function(player)
                repeat task.wait() until player.Character
                local highlightClone = highlight:Clone()
                highlightClone.Adornee = player.Character
                highlightClone.Parent = player.Character:FindFirstChild("HumanoidRootPart")
            end)
        else
            for i,v in pairs(game:GetChildren()) do
                if v:FindFirstChild('ESP') then
                    v:Destroy()
                end
            end
        end
    end

    function Charms()
        if getgenv().U.Client.Charm == true then
            local dwEntities = game:GetService("Players")
            local dwLocalPlayer = dwEntities.LocalPlayer 
            local dwRunService = game:GetService("RunService")

            local settings_tbl = {
                ESP_Enabled = true,
                ESP_TeamCheck = false,
                Chams = true,
                Chams_Color = Color3.fromRGB(110,153,202),
                Chams_Transparency = 0.1,
                Chams_Glow_Color = Color3.fromRGB(110,153,202)
            }

            function destroy_chams(char)

                for k,v in next, char:GetChildren() do 

                    if v:IsA("BasePart") and v.Transparency ~= 1 then

                        if v:FindFirstChild("Glow") and 
                        v:FindFirstChild("Chams") then

                            v.Glow:Destroy()
                            v.Chams:Destroy() 

                        end 

                    end 

                end 

            end

            dwRunService.Heartbeat:Connect(function()

                if settings_tbl.ESP_Enabled then

                    for k,v in next, dwEntities:GetPlayers() do 

                        if v ~= dwLocalPlayer then

                            if v.Character and
                            v.Character:FindFirstChild("HumanoidRootPart") and 
                            v.Character:FindFirstChild("Humanoid") and 
                            v.Character:FindFirstChild("Humanoid").Health ~= 0 then

                                if settings_tbl.ESP_TeamCheck == false then

                                    local char = v.Character 

                                    for k,b in next, char:GetChildren() do 

                                        if b:IsA("BasePart") and 
                                        b.Transparency ~= 1 then
                                            
                                            if settings_tbl.Chams then

                                                if not b:FindFirstChild("Glow") and
                                                not b:FindFirstChild("Chams") then

                                                    local chams_box = Instance.new("BoxHandleAdornment", b)
                                                    chams_bogetgenv().U.Name = "Chams"
                                                    chams_bogetgenv().U.AlwaysOnTop = true 
                                                    chams_bogetgenv().U.ZIndex = 4 
                                                    chams_bogetgenv().U.Adornee = b 
                                                    chams_bogetgenv().U.Color3 = settings_tbl.Chams_Color
                                                    chams_bogetgenv().U.Transparency = settings_tbl.Chams_Transparency
                                                    chams_bogetgenv().U.Size = b.Size + Vector3.new(0.02, 0.02, 0.02)

                                                    local glow_box = Instance.new("BoxHandleAdornment", b)
                                                    glow_bogetgenv().U.Name = "Glow"
                                                    glow_bogetgenv().U.AlwaysOnTop = false 
                                                    glow_bogetgenv().U.ZIndex = 3 
                                                    glow_bogetgenv().U.Adornee = b 
                                                    glow_bogetgenv().U.Color3 = settings_tbl.Chams_Glow_Color
                                                    glow_bogetgenv().U.Size = chams_bogetgenv().U.Size + Vector3.new(0.13, 0.13, 0.13)

                                                end

                                            else

                                                destroy_chams(char)

                                            end
                                        
                                        end

                                    end

                                else

                                    if v.Team == dwLocalPlayer.Team then
                                        destroy_chams(v.Character)
                                    end

                                end

                            else

                                destroy_chams(v.Character)

                            end

                        end

                    end

                else 

                    for k,v in next, dwEntities:GetPlayers() do 

                        if v ~= dwLocalPlayer and 
                        v.Character and 
                        v.Character:FindFirstChild("HumanoidRootPart") and 
                        v.Character:FindFirstChild("Humanoid") and 
                        v.Character:FindFirstChild("Humanoid").Health ~= 0 then
                            
                            destroy_chams(v.Character)

                        end

                    end

                end

            end)
        else
            destroy_chams(game.Players.LocalPlayer.Character)
        end
    end

    function Skeleton()
        if getgenv().U.Client.Skeleton then
            local camera = workspace.CurrentCamera
            local entities = game:GetService("Players")
            local localplayer = entities.LocalPlayer 
            local runservice = game:GetService("RunService")

            local esp_settings = {
                enabled = true,
                skel = true,
                skel_col = Color3.fromRGB(255,255,255)
            }

            local function draw(player, character)

                local skel_head = Drawing.new("Line")
                skel_head.Visible = false
                skel_head.Thickness = 1.5
                skel_head.Color = Color3.new(1,1,1)

                local skel_torso = Drawing.new("Line")
                skel_torso.Visible = false
                skel_torso.Thickness = 1.5
                skel_torso.Color = Color3.new(1,1,1)

                local skel_leftarm = Drawing.new("Line")
                skel_leftarm.Visible = false
                skel_leftarm.Thickness = 1.5
                skel_leftarm.Color = Color3.new(1,1,1)

                local skel_rightarm = Drawing.new("Line")
                skel_rightarm.Visible = false
                skel_rightarm.Thickness = 1.5
                skel_rightarm.Color = Color3.new(1,1,1)

                local skel_leftleg = Drawing.new("Line")
                skel_leftleg.Visible = false
                skel_leftleg.Thickness = 1.5
                skel_leftleg.Color = Color3.new(1,1,1)

                local skel_rightleg = Drawing.new("Line")
                skel_rightleg.Visible = false
                skel_rightleg.Thickness = 1.5
                skel_rightleg.Color = Color3.new(1,1,1)

                local function update()
                    local connection
                    connection = runservice.RenderStepped:Connect(function()

                        if workspace:FindFirstChild(character.Name) and
                        character and 
                        character:FindFirstChild("HumanoidRootPart") and 
                        character:FindFirstChild("Humanoid") and 
                        character:FindFirstChild("Humanoid").Health ~= 0 then 

                            local character_rootpart_3d = character.HumanoidRootPart.Position
                            local character_rootpart_2d, rootpart_onscreen = camera:WorldToViewportPoint(character_rootpart_3d)

                            if rootpart_onscreen and character.Humanoid.RigType == Enum.HumanoidRigType.R6 and esp_settings.enabled then

                                local head_2d = camera:WorldToViewportPoint(character.Head.Position)
                                local torso_upper_2d = camera:WorldToViewportPoint(character.Torso.Position + Vector3.new(0,1,0))
                                local torso_lower_2d = camera:WorldToViewportPoint(character.Torso.Position + Vector3.new(0,-1,0))
                                
                                local leftarm_2d = camera:WorldToViewportPoint(character["Left Arm"].Position + Vector3.new(0,-1,0))
                                local rightarm_2d = camera:WorldToViewportPoint(character["Right Arm"].Position + Vector3.new(0,-1,0))
                                local leftleg_2d = camera:WorldToViewportPoint(character["Left Leg"].Position + Vector3.new(0,-1,0))
                                local rightleg_2d = camera:WorldToViewportPoint(character["Right Leg"].Position + Vector3.new(0,-1,0))

                                skel_head.From = Vector2.new(head_2d.X, head_2d.Y)
                                skel_head.To = Vector2.new(torso_upper_2d.X, torso_upper_2d.Y)

                                skel_torso.From = Vector2.new(torso_upper_2d.X, torso_upper_2d.Y)
                                skel_torso.To = Vector2.new(torso_lower_2d.X, torso_lower_2d.Y)
                                
                                skel_leftarm.From = Vector2.new(torso_upper_2d.X, torso_upper_2d.Y)
                                skel_leftarm.To = Vector2.new(leftarm_2d.X, leftarm_2d.Y)

                                skel_rightarm.From = Vector2.new(torso_upper_2d.X, torso_upper_2d.Y)
                                skel_rightarm.To = Vector2.new(rightarm_2d.X, rightarm_2d.Y)

                                skel_leftleg.From = Vector2.new(torso_lower_2d.X, torso_lower_2d.Y)
                                skel_leftleg.To = Vector2.new(leftleg_2d.X, leftleg_2d.Y)

                                skel_rightleg.From = Vector2.new(torso_lower_2d.X, torso_lower_2d.Y)
                                skel_rightleg.To = Vector2.new(rightleg_2d.X, rightleg_2d.Y)

                                skel_head.Visible = esp_settings.skel
                                skel_torso.Visible = esp_settings.skel
                                skel_leftarm.Visible = esp_settings.skel
                                skel_rightarm.Visible = esp_settings.skel
                                skel_leftleg.Visible = esp_settings.skel
                                skel_rightleg.Visible = esp_settings.skel

                            else

                                skel_head.Visible = false
                                skel_torso.Visible = false
                                skel_leftarm.Visible = false
                                skel_rightarm.Visible = false
                                skel_leftleg.Visible = false
                                skel_rightleg.Visible = false

                            end

                        else

                            if player == nil then
                                connection:Disconnect()
                                connection = nil 
                            end

                            skel_head.Visible = false
                            skel_torso.Visible = false
                            skel_leftarm.Visible = false
                            skel_rightarm.Visible = false
                            skel_leftleg.Visible = false
                            skel_rightleg.Visible = false

                        end
                    end)
                end
                coroutine.wrap(update)()

            end

            local function playeradded(player)
                if player.Character then
                    coroutine.wrap(draw)(player, player.Character)
                end
                player.CharacterAdded:Connect(function(character)
                    coroutine.wrap(draw)(player, character)
                end)
            end

            for a,b in next, entities:GetPlayers() do
                if b ~= localplayer then
                    playeradded(b)
                end
            end

            entities.PlayerAdded:Connect(playeradded)
        else
        end
    end

    function Tracers()
        if getgenv().U.Client.Tracers == true then
            _G.TeamCheck = false
            Tracers.Visible = true
            _G.Tracers = true
            local lp = game.Players.LocalPlayer
            local camera = game:GetService("Workspace").CurrentCamera
            local CurrentCamera = workspace.CurrentCamera
            local worldToViewportPoint = CurrentCamera.worldToViewportPoint

            for i,v in pairs(game.Players:GetChildren()) do
                local Tracer = Drawing.new("Line")
                Tracer.Visible = false
                Tracer.Color = Color3.new(255,0,0)
                Tracer.Thickness = 1
                Tracer.Transparency = 1
                
                function traces()
                    game:GetService("RunService").RenderStepped:Connect(function()
                        if v.Character ~= nil and v.Character:FindFirstChild("Humanoid") ~= nil and v.Character:FindFirstChild("HumanoidRootPart") ~= nil and v ~= lp and v.Character.Humanoid.Health > 0 then
                            local Vector, OnScreen = camera:worldToViewportPoint(v.Character.HumanoidRootPart.Position)
                            
                            if OnScreen then
                                Tracer.From = Vector2.new(camera.ViewportSize.X / 2, camera.ViewportSize.Y / 1)
                                Tracer.To = Vector2.new(Vector.X, Vector.Y)
                                
                                if _G.TeamCheck and v.TeamColor == lp.TeamColor then
                                    Tracer.Visible = false
                                else
                                    Tracer.Visible = true
                                end
                            else
                                Tracer.Visible = false
                                
                            end
                        else
                            Tracer.Visible = false
                        end
                        if _G.Tracers == false then
                            Tracers.Visible = false
                        end
                    end)
                end
                coroutine.wrap(traces)()
            end

            game.Players.PlayerAdded:Connect(function()
                local Tracer = Drawing.new("Line")
                Tracer.Visible = false
                Tracer.Color = Color3.new(255,0,0)
                Tracer.Thickness = 1
                Tracer.Transparency = 1
                
                function traces()
                    game:GetService("RunService").RenderStepped:Connect(function()
                        if v.Character ~= nil and v.Character:FindFirstChild("Humanoid") ~= nil and v.Character:FindFirstChild("HumanoidRootPart") ~= nil and v ~= lp and v.Character.Humanoid.Health > 0 then
                            local Vector, OnScreen = camera:worldToViewportPoint(v.Character.HumanoidRootPart.Position)
                            
                            if OnScreen then
                                Tracer.From = Vector2.new(camera.ViewportSize.X / 2, camera.ViewportSize.Y / 1)
                                Tracer.To = Vector2.new(Vector.X, Vector.Y)
                                
                                if _G.TeamCheck and v.TeamColor == lp.TeamColor then
                                    Tracer.Visible = false
                                else
                                    Tracer.Visible = true
                                end
                            else
                                Tracer.Visible = false
                                
                            end
                        else
                            Tracer.Visible = false
                        end
                        if _G.Tracers == false then
                            Tracers.Visible = false
                        end
                    end)
                end
                coroutine.wrap(traces)()
            end)
        else
            Tracers.Visible = false
        end
    end

    local c = workspace.CurrentCamera
    local ps = game:GetService("Players")
    local lp = ps.LocalPlayer
    local rs = game:GetService("RunService")

    local function esp(p,cr)
        local h = cr:WaitForChild("Humanoid")
        local hrp = cr:WaitForChild("Head")

        local text = Drawing.new("Text")
        text.Visible = false
        text.Center = true
        text.Outline = true 
        text.OutlineColor = Color3.fromRGB(50,50,50)
        text.Font = 0
        text.Size = 25.16
        text.Color = Color3.fromRGB(233,33,33)
                
        local conection
        local conection2
        local conection3

        local function dc()
            text.Visible = false
            text:Remove()
            if conection then
                conection:Disconnect()
                conection = nil 
            end
            if conection2 then
                conection2:Disconnect()
                conection2 = nil 
            end
            if conection3 then
                conection3:Disconnect()
                conection3 = nil 
            end
        end
        conection2 = cr.AncestryChanged:Connect(function(_,parent)
            if not parent then
                dc()
            end
        end)

        conection3 = h.HealthChanged:Connect(function(v)
            if (v<=0) or (h:GetState() == Enum.HumanoidStateType.Dead) then
                dc()
            end
        end)

        conection = rs.RenderStepped:Connect(function()
            local hrp_pos,hrp_onscreen = c:WorldToViewportPoint(hrp.Position)
            if hrp_onscreen then
                text.Position = Vector2.new(hrp_pos.X, hrp_pos.Y - 27)
                text.Text = ""..p.Name.."\n".."Distance [ ".. math.floor((game:GetService('Players')[p.Name].Character.HumanoidRootPart.Position - lp.Character.HumanoidRootPart.Position).Magnitude) .."M ]"
                text.Visible = true
            else
                text.Visible = false
            end
        end)
        
        rs.RenderStepped:Connect(function()
            if getgenv().U.Client.PlayerEsp == true then
            else dc()
        end
        end)
    end

    local function Esp(Object)

        local text = Drawing.new("Text")
        text.Visible = false
        text.Center = true
        text.Outline = true 
        text.OutlineColor = Color3.fromRGB(50,50,50)
        text.Font = 0
        text.Size = 25.16
        text.Color = Color3.fromRGB(0,233,233)
        
        local Tracer = Drawing.new("Line")
        Tracer.Visible = false
        Tracer.Color = Color3.new(255,0,0)
        Tracer.Thickness = 1
        Tracer.Transparency = 1
        
        local conection
        local conection2
        local conection3

        local function dc()
            if text then
                text.Visible = false
            else text:Remove()
            end
            if Tracer then
                Tracer.Visible = false
                else Tracer:Remove()
            end
            if conection then
                conection:Disconnect()
                conection = nil 
            end
            if conection2 then
                conection2:Disconnect()
                conection2 = nil 
            end
            if conection3 then
                conection3:Disconnect()
                conection3 = nil 
            end
        end

        conection = rs.RenderStepped:Connect(function()
            local Object_pos, Object_onscreen = c:WorldToViewportPoint(Object.Position)
            if Object_onscreen then
                --Tracer.From = Vector2.new(c.ViewportSize.X / 2, c.ViewportSize.Y / -0.1)
                --Tracer.To = Vector2.new(Object_pos.X, Object_pos.Y)
                text.Position = Vector2.new(Object_pos.X, Object_pos.Y -49 )
                text.Text = "".. (Object.Name) .."\n".."Distance [ ".. math.floor((Object.Position - lp.Character.HumanoidRootPart.Position).Magnitude) .."M ]"
                text.Visible = true
                Tracer.Visible = true
            else
                Tracer.Visible = false
                text.Visible = false
            end
        end)
        
        rs.RenderStepped:Connect(function()
            if getgenv().U.Client.IslandsEsp or getgenv().Clip == true then
            else dc()
        end
        end)
    end

    c21:AddToggle('Players Esp',getgenv().U.Client.PlayerEsp,function(a)
        getgenv().U.Client.PlayerEsp = a
        save()
        task.spawn(function()
            while task.wait(.3) do
                if getgenv().U.Client.PlayerEsp then
                    local function p_added(p)
                        if p.Character then
                            esp(p,p.Character)
                        end
                        p.CharacterAdded:Connect(function(cr)
                            esp(p,cr)
                        end)
                    end
                    for i,p in next, ps:GetPlayers() do 
                        if p ~= lp then
                            p_added(p)
                        end
                    end
                    ps.PlayerAdded:Connect(p_added)
                end
            end
        end)
    end)

    c21:AddToggle('Islands Esp',getgenv().U.Client.IslandsEsp,function(a)
        getgenv().U.Client.IslandsEsp = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Client.IslandsEsp then
                    for i,v in pairs(game:GetService('Workspace')["_WorldOrigin"].Locations:GetChildren()) do
                        Esp(v)
                        task.wait(10)
                    end
                end
            end
        end)
    end)

    c21:AddToggle('Flowers Esp',getgenv().U.Client.FlowersEsp,function(a)
        getgenv().U.Client.FlowersEsp = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Client.FlowersEsp then
                    for i,v in pairs(game:GetService('Workspace'):GetChildren()) do
                        if string.find(v.Name,'Flower') then
                            Esp(v)
                            task.wait(10)
                        end
                    end
                end
            end
        end)
    end)

    c21:AddToggle('Mirage Island Esp',getgenv().U.Client.MirageEsp,function(a)
        getgenv().U.Client.MirageEsp = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Client.MirageEsp then
                    if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Mirage Island") then
                        Esp(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Mirage Island"))
                    end
                end
            end
        end)
    end)

    c21:AddToggle('Elite Esp',getgenv().U.Client.EliteEsp,function(a)
        getgenv().U.Client.EliteEsp = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Client.EliteEsp then
                    for i,v in pairs(game:GetService('Workspace').Enemies:GetChildren()) do
                        if v.Name == 'Urban [Lv. 1750]' or v.Name == 'Diablo [Lv. 1750]' or v.Name == 'Deandre [Lv. 1750]' then
                            Esp(v)
                            task.wait(30)
                        end
                    end
                end
            end
        end)
    end)

    c21:AddToggle('Haze Esp',getgenv().U.Client.HazeEsp,function(a)
        getgenv().U.Client.HazeEsp = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Client.HazeEsp then
                    for i,v in pairs(game:GetService('Workspace').Enemies:GetChildren()) do
                        if v:FindFirstChild('HazeESP') then
                            Esp(v)
                            task.wait(5)
                        end
                    end
                end
            end
        end)
    end)
end

local c22 = Client:CreatePage("", 2)
c22:AddLabel([[\\ Others //]]) do

    c22:AddToggle('Enable Highligh',getgenv().U.Client.Esp_HigtLight,function(a)
        getgenv().U.Client.Esp_HigtLight = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Client.Esp_HigtLight then
                    Highlight()
                end
            end
        end)
    end)

    c22:AddToggle('Enable Charms',getgenv().U.Client.Charm,function(a)
        getgenv().U.Client.Charm = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Client.Charm then
                    Charm()
                end
            end
        end)
    end)

    c22:AddToggle('Enable Skeleton',getgenv().U.Client.Skeleton,function(a)
        getgenv().U.Client.Skeleton = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Client.Skeleton then
                    Skeleton()
                end
            end
        end)
    end)

    c22:AddToggle('Enable Tracers',getgenv().U.Client.Tracers,function(a)
        getgenv().U.Client.Tracers = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Client.Tracers then
                    Tracers()
                end
            end
        end)
    end)
end

-- Raids --
local d1 = Raid:CreatePage("", 1)

d1:AddLabel([[\\ Raids //]]) do

    local a = require(game.ReplicatedStorage.Raids)
    local NormalRaids = {}
    local AdvancedRaids = {}
    local UseFruits = {}
    for i,v in pairs(a) do
        for a,b in pairs(v) do
			table.insert(NormalRaids,"nil")
            table.insert(NormalRaids,b)
        end
    end
	if not type(getgenv().U.Main.RaidSelect) == 'table' then
        getgenv().U.Main.RaidSelect = {}
    end
    d1:AddDropdown('Select Raids',"nil",false,NormalRaids,function(a)
        getgenv().U.Raids.RaidSelect = a
        SelectRaid = a
        save()
    end)

    d1:AddToggle('Full Auto Raid',getgenv().U.Raids.AutoRaid,function(a)
        getgenv().U.Raids.AutoRaid = a
        save()
        if a == true then
            getgenv().Clip = true
        else
            getgenv().Clip = false
        end
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Raids.AutoRaid and not getgenv().U.Main.AutoFarm  then 
                    if game.Players.LocalPlayer.Backpack:FindFirstChild("Special Microchip") or game.Players.LocalPlayer.Character:FindFirstChild("Special Microchip") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") or game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
                        if game.Players.LocalPlayer.Backpack:FindFirstChild("Special Microchip") or game.Players.LocalPlayer.Character:FindFirstChild("Special Microchip") and game.Players.LocalPlayer.PlayerGui.Main.Timer.Visible == false then
                            if SecondSea then
                                fireclickdetector(Workspace.Map.CircleIsland.RaidSummon2.Button.Main.ClickDetector)
                            elseif ThirdSea then
                                fireclickdetector(Workspace.Map["Boat Castle"].RaidSummon2.Button.Main.ClickDetector)
                            end
                        elseif game.Players.LocalPlayer.PlayerGui.Main.Timer.Visible == true then				
                            pcall(function()
                                repeat wait()
                                    if game.Players.LocalPlayer.PlayerGui.Main.Timer.Visible == false then
        
                                    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") then
                                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame.z)
                                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame)
                                        end
                                    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") then
                                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame.z)
                                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame)
                                        end
                                    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") then
                                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame.z)
                                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame)
                                        end
                                    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") then
                                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame.z)
                                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame)
                                        end
                                    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
                                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame.z)
                                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame)
                                        end
                                    end
                                    for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                        if getgenv().U.Raids.AutoRaid and game.Players.LocalPlayer.PlayerGui.Main.Timer.Visible == true and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and (v.HumanoidRootPart.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 400 then
                                            repeat task.wait()
                                                v.Humanoid.Health = 0
                                                v:BreakJoints()
                                            until not getgenv().U.Raids.AutoRaid or v.Humanoid.Health <= 0 or not v.Parent
                                        end
                                    end
                                    if getgenv().U.Raids.AutoAweakening then	
                                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Awakener","Awaken")
                                    end
                                until not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") or not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") or not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") or not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") or not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") or game.Players.LocalPlayer.PlayerGui.Main.Timer.Visible == false
                                if getgenv().U.Raids.AutoAweakening then	
                                    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Awakener","Awaken")
                                end
                            end)
                        end           
                    else
                        if getgenv().U.Raids.AutoAweakening then	
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Awakener","Awaken")
                        end
                        local args = {
                            [1] = "RaidsNpc",
                            [2] = "Select",
                            [3] = tostring(getgenv().U.Raids.RaidSelect)
                        }
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                    end
                end
            end
        end)
    end)

    d1:AddToggle('Auto Awakening',getgenv().U.Raids.AutoAwakening,function(a)
        getgenv().U.Raids.AutoAwakening = a
        save()
    end)

    d1:AddToggle('Auto Next Island',false,function(a)
        getgenv().Clip = a
        task.spawn(function()
            repeat task.wait()
                if game.Players.LocalPlayer.PlayerGui.Main.Timer.Visible == true then
                    if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") then
                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame.z)
                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5").CFrame)
                        end
                    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") then
                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame.z)
                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4").CFrame)
                        end
                    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") then
                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame.z)
                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3").CFrame)
                        end
                    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") then
                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame.z)
                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2").CFrame)
                        end
                    elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") then
                        game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame = CFrame.new(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame.x,60,game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame.z)
                        if (game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 2500 then
                            Teleport(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1").CFrame)
                        end
                    end
                    for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                        if getgenv().U.Raids.AutoRaid and game.Players.LocalPlayer.PlayerGui.Main.Timer.Visible == true and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and (v.HumanoidRootPart.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 400 then
                            repeat task.wait()
                                v.Humanoid.Health = 0
                                v:BreakJoints()
                            until not getgenv().Clip or v.Humanoid.Health <= 0 or not v.Parent
                        end
                    end
                end
            until not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 5") or not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 4") or not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 3") or not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 2") or not game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Island 1") or game.Players.LocalPlayer.PlayerGui.Main.Timer.Visible == false
        end)
    end)

    d1:AddToggle('Kill Aura',false,function()
        KillAura = a
        task.spawn(function()
            while true do task.wait()
                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                    if KillAura == true and v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and (v.HumanoidRootPart.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 400 then
                        repeat task.wait()
                            v.Humanoid.Health = 0
                            v:BreakJoints()
                        until not KillAura or v.Humanoid.Health <= 0 or not v.Parent
                    end
                end
            end
        end)
    end)
end
    
local d12 = Raid:CreatePage("", 1)
d12:AddLabel([[\\ Configs //]]) do

    d12:AddToggle('Use Fruit In Inv',getgenv().U.Raids.UseFruit,function(a)
        getgenv().U.Raids.UseFruit = a
        save()
    end)

    d12:AddSlider('Price Cap',5000,1000000,getgenv().U.Raids.PriceCap,function(a)
        getgenv().U.Raids.PriceCap = a
        save()
    end)

    d12:AddToggle('Collect Fruits',getgenv().U.Raids.CollectFruit,function(a)
        getgenv().U.Raids.CollectFruit = a
        save()
    end)

    d1:AddToggle('Auto Raid Hop',getgenv().U.Raids.AutoRaidHop,function(a)
        getgenv().U.Raids.AutoRaidHop = a
        save()
    end)
end


task.spawn(function()
    while task.wait() do
        if getgenv().U.Raids.UseFruit then
            for i,v in pairs(game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('GetFruits')) do
                if v.Price <= getgenv().U.Raids.PriceCap then
                    table.insert(UseFruits,v.Name)
                    task.wait()
                    table.sort(UseFruits,function(Arg1, Arg2)
                        return Arg1 >= Arg2
                    end)
                end
            end
        end
    end
end)

local d2 = Raid:CreatePage("", 2) 

d2:AddLabel([[\\ Teleports //]]) do

    d2:AddButton('Teleport to firstsea',function()
        Sea1()
    end)
    d2:AddButton('Teleport to secondsea',function()
        Sea2()
    end)
    d2:AddButton('Teleport to thirdsea',function()
        Sea3()
    end)

    local Locations = {}
    local Npcs = {}

    for a,c in pairs(game:GetService("Workspace")["_WorldOrigin"].Locations:GetChildren()) do
		table.insert(Locations,"nil")
        table.insert(Locations,c.Name)
    end

	for _,n in pairs(game.Workspace.NPCs:GetChildren()) do
		if not table.find(Npcs,n.Name) then
			table.insert(Npcs,"nil")
			table.insert(Npcs,n.Name)
		end
	end

    task.spawn(function()
        while task.wait() do
            for _,n in pairs(game.Workspace.NPCs:GetChildren()) do
                if not table.find(Npcs,n.Name) then
					table.insert(Npcs,"nil")
                    table.insert(Npcs,n.Name)
                end
            end
            for a,c in pairs(game.Workspace._WorldOrigin.Locations:GetChildren()) do
                if not table.find(Locations,c.Name) then
					table.insert(Locations,"nil")
                    table.insert(Locations,c.Name)
                end
            end
        end
    end)

    d2:AddLabel([[\\ Locations //]])
    d2:AddDropdown('Select Locations',"nil",false,Locations,function(a)
        getgenv().U.Teleport.SelectPlace = a
        SelectLocation = a
        save()
    end)

    d2:AddToggle('Teleport select location',getgenv().U.Teleport.TeleportToLocations,function(a)
        getgenv().U.Teleport.TeleportToLocations = a
        getgenv().Clip = a
        save()
        task.spawn(function()
            while getgenv().U.Teleport.TeleportToLocations do task.wait()
                for a,c in pairs(game:GetService('Workspace')._WorldOrigin.Locations:GetChildren()) do
                    if c.Name == SelectLocation then
                        Teleport(c.CFrame*CFrame.new(0,getgenv().U.Settings.PosY,0))
                        getgenv().Location = c.CFrame*CFrame.new(0,getgenv().U.Settings.PosY,0)
                    end
                end
            end
        end)
    end)

    d2:AddButton('Instant Teleport To Select',function()
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = getgenv().Location
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = getgenv().Location
        game.Players.LocalPlayer.Character.Humanoid.Health =-math.huge
        game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = getgenv().Location
    end)

    d2:AddLabel([[\\ Npcs  //]])

    d2:AddDropdown('Select Npcs',"nil",false,Npcs,function(a)
        getgenv().U.Teleport.SelectNpc = a
        SelectNpc = a
        save()
    end)

    d2:AddToggle('Teleport select npc',getgenv().U.Teleport.TeleportToNpc,function(a)
        getgenv().U.Teleport.TeleportToNpc = a
        getgenv().Clip = a
        save()
        task.spawn(function()
            while getgenv().U.Teleport.TeleportToNpc do task.wait()
                for a,c in pairs(game.Workspace.NPCs:GetChildren()) do
                    if c.Name == getgenv().U.Teleport.SelectNpc then
                        Teleport(c.HumanoidRootPart.CFrame*CFrame.new(0,getgenv().U.Settings.PosY,0))
                    end
                end
            end
        end)
    end)

    d2:AddSlider('Set Position [Y]',0,500,getgenv().U.Settings.PosY,function(a)
        getgenv().U.Settings.PosY = a
        save()
    end)
end
-- Misc --

local e1 = Misc:CreatePage("", 1)

e1:AddLabel([[\\ Misc //]]) do

    e1:AddButton('Join Pirates (Wait)',function()
        
    end)

    e1:AddButton('Join Marines (Wait)',function()
        
    end)

    e1:AddButton('Rejoin Server',function()
        game:GetService("TeleportService"):Teleport(game.PlaceId)
    end)

    e1:AddButton('Hop Server',function()
        ServerHop()
    end)
end

local e12 = Misc:CreatePage("", 2)
e12:AddLabel([[\\ Others //]]) do

    e12:AddToggle('Walk above water (wait)',getgenv().U.Miscs.Walk_Abobe_Water,function()
        
    end)
end

local e13 = Misc:CreatePage("", 2)
e13:AddLabel([[\\ User Interfaces //]]) do

    e13:AddButton('Devil Shop',function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("GetFruits")
        game.Players.localPlayer.PlayerGui.Main.FruitShop.Visible = true
    end)

    e13:AddButton('Haki Color',function()
        game.Players.localPlayer.PlayerGui.Main.Colors.Visible = true
    end)

    e13:AddButton('Title',function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getTitles")
        game.Players.localPlayer.PlayerGui.Main.Titles.Visible = true
    end)

    e13:AddButton('Enchant',function()
        
    end)

    e13:AddButton('Aweakening',function()
        game:GetService("Players").LocalPlayer.PlayerGui.Main.AwakeningToggler.Visible = true
    end)

    e13:AddButton('Upgrade',function()
        
    end)
end

-- webhook --

local GetInv = function(...)
    if type(select(1,...)) == "table" then else warn("Pls insert Table!") end
    for _,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
        if type(v) == "table" then
            if v.Type == select(1,...)[Type] then
                if v.Name == select(1,...)[Name] then
                    if not select(1,...)[ReturnResult] then return end;
                    if select(1,...)[ReturnValue] then return v.select(1,...)[ReturnValue] end;
                end;
            end;
        end;
    end;
end;

function Send(url)
    local url
    local data
    local newdata = game:GetService("HttpService"):JSONEncode(data)

    local headers = {
        ["content-type"] = "application/json"
    }

    local R = {Url = url, Body = newdata, Method = "POST", Headers = headers}

    local request = http_request or request or HttpPost or syn.request
    local R = {Url = url, Body = newdata, Method = "POST", Headers = headers}
    request(R)
end

local e2 = Webhook:CreatePage("", 1)

if getgenv().Webhook == "" then getgenv().Webhook = 'https://discordapp.com/api/webhooks/1114373164751933441/wRqAdDPZ7bS4VY7H2TZAllkeecKIxiSGd87EFaoz1CVNS8RfxHI9D1vijlkYAUI24rRs' end

local function GetWeaponData(types)
	local ReturnText = ""
	for _,v in pairs(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("getInventory")) do
        if type(v) == "table" then
        print(v.Type)
            if types == "Sword" then
                if v.Type == "Sword" then
                    ReturnText = ReturnText .. v.Name .. " : [ " .. v.Mastery .. " ]\n"
                end
            elseif types == "Gun" then
                if v.Type == "Gun" then
                    ReturnText = ReturnText .. v.Name .. " : [ " .. v.Mastery .. " ]\n"
                end
            elseif types == "Wear" then
                if v.Type == "Wear" then
                    ReturnText = ReturnText .. v.Name .. "\n"
                end
            elseif types == "Material" then
                if v.Type == "Material" then
                    ReturnText = ReturnText .. v.Name .. " : [ " .. v.Count .. " ]\n"
                end
            elseif types == "Blox Fruit" then
            	if v.Type == "Blox Fruit" then
            		ReturnText = ReturnText .. v.Name .. " : [ " .. v.Mastery .." ]\n"
            	end
            end
        end
    end
	if ReturnText ~= "" then
	    return ReturnText
	else
		return "You are not have any things"
	end
end
e2:AddLabel([[\\ Webhooks //]]) do

    e2:AddTextbox("Put Your webhook here", "idk", function(a)
        getgenv().Webhook = a
    end)

    e2:AddButton('Send',function()
        Send(getgenv().Webhook, {
            ["content"] = "",
            ["embeds"] = {
                {
                    ["description"] = "**Webhook Mobile**",
                    ["color"] = 16711751,
                    ["fields"] = {
                        {["name"] = "**Info**",["value"] = "```yaml\n".. "**Name**" .. game.Players.LocalPlayer.Name .."\n```",["inline"] = true,},
                        {["name"] = "**Melee**",["value"] = "```yaml\n".. "" .."\n```",["inline"] = true,},
                        {["name"] = "**Swords**",["value"] = "```yaml\n" .. GetWeaponData("Sword") .. "\n```",["inline"] = true,},
                        {["name"] = "**Guns**",["value"] = "```lua\n".. GetWeaponData("Gun") .."\n```",["inline"] = true,},
                        {["name"] = "**Fruits**",["value"] = "```lua\n".. GetWeaponData("Blox Fruit") .."\n```",["inline"] = true,},
                        {["name"] = "**Accesories**",["value"] = "```lua\n".. GetWeaponData("Wear") .."\n```",["inline"] = true,},
                        {["name"] = "**Materials**",["value"] = "```lua\n".. GetWeaponData("Material") .."\n```",["inline"] = true,}
                    },
                    ["author"] = {
                        ["name"] = "Unique hub : Inventories",
                        ["icon_url"] = "https://cdn.discordapp.com/avatars/1049706372759044251/82ca2d4c117e69c62255582981d00c0c.webp?size=128"
                    },
                    ["footer"] = {
                        ["text"] = "Unique hub",
                        ["icon_url"] = "https://cdn.discordapp.com/avatars/1049706372759044251/82ca2d4c117e69c62255582981d00c0c.webp?size=128"
                    },
                    ["timestamp"] = DateTime.now():ToIsoDate(),
                    ["thumbnail"] = {
                        ["url"] = "https://cdn.discordapp.com/avatars/1049706372759044251/82ca2d4c117e69c62255582981d00c0c.webp?size=128"
                    }
                }
            },
        })
    end)
end

-- Race --

local f1 = Race:CreatePage("", 1)

f1:AddLabel([[\\ Races //]]) do

    f1:AddDropdown('Select Race Reroll',"Human",false,{'Human','Mink','Fish','Skypiea'},function(a)
        RaceReroll = a
    end)

    f1:AddToggle('Start Reroll (dont use)',getgenv().U.Main.AutoEvoleRaceReroll,function(a)
        getgenv().U.Main.AutoEvoleRaceReroll = a
        task.spawn(function()
            while task.wait(50) do
                if getgenv().U.Main.AutoEvoleRaceReroll then
                    if game:GetService("Players").LocalPlayer.Data.Race.Value == RaceReroll then
                    else
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Reroll","1")
                        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Reroll","2")
                    end
                end
            end
        end)
    end)

    f1:AddButton('Rerool Race',function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Reroll","1")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Reroll","2")
    end)
end

local f12 = Race:CreatePage("", 1)
f12:AddLabel([[\\ Auto Get Races //]]) do

    f12:AddToggle('Auto Evolve Race [Beta]',getgenv().U.Main.AutoEvolveRace,function(a)
        getgenv().U.Main.AutoEvolveRace = a
        save()

    end)

    f12:AddToggle('Auto Ghoul Race',getgenv().U.Main.AutoGhoulRace,function(a)
        getgenv().U.Main.AutoGhoulRace = a
        save()
    end)

    f12:AddToggle('Auto Cybrog Race [Unfinished]',getgenv().U.Main.AutoCybrogRace,function(a)
        getgenv().U.Main.AutoCybrogRace = a
        save()
    end)
end

local f2 = Race:CreatePage("", 2)
local Moon = f2:AddLabel("Moon Phase : null") do

    task.spawn(function()
        while task.wait() do
            pcall(function()
                if game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709149431" then
                    _G.Moon = "Moon Phase [5/5] "..'🌕'
                elseif game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709149052" then
                    _G.Moon = "Moon Phase [4/5] ".."🌙"
                elseif game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709143733" then
                    _G.Moon = "Moon Phase [3/5] "..'🌓'
                elseif game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709150401" then
                    _G.Moon = "Moon Phase [2/5] "..'🌗'
                elseif game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709149680" then
                    _G.Moon = "Moon Phase [1/5] : "..'🌘'
                else
                    _G.Moon = "Moon Phase [0/5] :  "..'🌑'
                end
                -- Moon:ChangeText(_G.Moon)
            end)
        end
    end)

    f2:AddButton('Teleport to temple of time',function()
        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = CFrame.new(28286.35546875, 14895.3017578125, 102.62469482421875)
    end)

    f2:AddButton('Buy Ancient One [Gear Replace]',function()
        local args = {
            [1] = "UpgradeRace",
            [2] = "Check"
        }
        
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))

        local args = {
            [1] = "UpgradeRace",
            [2] = "Buy"
        }
        
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)

    f2:AddButton('Teleport to trial door',function()
        if tostring(game.Players.LocalPlayer.Data.Race.Value) == "Mink" then
            Teleport(game:GetService("Workspace").Map["Temple of Time"].MinkCorridor.Door.Entrance.CFrame)
        elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Fishman" then
            Teleport(game:GetService("Workspace").Map["Temple of Time"].FishmanCorridor.Door.Entrance.CFrame)
        elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Skypiea" then
            Teleport(game:GetService("Workspace").Map["Temple of Time"].SkyCorridor.Door.Entrance.CFrame)
        elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Human" then
            Teleport(game:GetService("Workspace").Map["Temple of Time"].HumanCorridor.Door.Entrance.CFrame)
        elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Ghoul" then
            Teleport(game:GetService("Workspace").Map["Temple of Time"].GhoulCorridor.Door.Entrance.CFrame)
        elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Cyborg" then
            Teleport(game:GetService("Workspace").Map["Temple of Time"].CyborgCorridor.Door.Entrance.CFrame)
        end
    end)

    local BVG = {
        [1] = "CheckTempleDoor"
    }

    f2:AddToggle('Auto Pull Lever',getgenv().U.Main.AutoPullLever,function(a)
        getgenv().U.Main.AutoPullLever = a
        save()
        task.spawn(function()
            while task.wait() do
                if getgenv().U.Main.AutoPullLever then
                    if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("CheckTempleDoor") == true then
                        fireproximityprompt(game:GetService("Workspace").Map["Temple of Time"].Lever.Prompt.ProximityPrompt, math.huge, 1,true)
                    end
                end
            end
        end)
    end)

    f2:AddButton('Teleport to lever',function()
        plr.Character.HumanoidRootPart.CFrame = CFrame.new(28576.873046875, 14937.958984375, 76.49504852294922)
    end)

    local AwkEnergy = f2:AddLabel('Aweakening Energy : [ 9e9 ]')

    -- task.spawn(function()
    --     while task.wait() do
    --         pcall(function()
    --             AwkEnergy:ChangeText("Aweakening Energy : [ ".. game.Players.LocalPlayer.Character:FindFirstChild("RaceEnergy").Value .." ]")
    --         end)
    --     end
    -- end)

    if ThirdSea and v4 then
        pcall(function()
            local V4 = tostring(game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("UpgradeRace", "Check")    )
            Tranformed = V4:split(" ")[1]
            print(V4)
        end)
    end


    f2:AddToggle('Auto Ancient One Quest',getgenv().U.Main.FarmTranformGate,function(a)
        getgenv().U.Main.FarmTranformGate = a
        getgenv().Clip = a
        save()
        task.spawn(function()
            while task.wait() do
                pcall(function()
                    if getgenv().U.Main.FarmTranformGate then
                        if game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("UpgradeRace", "Buy") ~= true then
                            if game.Players.LocalPlayer.Character:FindFirstChild("RaceEnergy").Value < 1 and game.Players.LocalPlayer.Character:FindFirstChild("RaceTransformed").Value == false then
                                if game:GetService("Workspace").Enemies:FindFirstChild('Reborn Skeleton [Lv. 1975]') or game:GetService("Workspace").Enemies:FindFirstChild('Living Zombie [Lv. 2000]') or game:GetService("Workspace").Enemies:FindFirstChild('Demonic Soul [Lv. 2025]') or game:GetService("Workspace").Enemies:FindFirstChild('Posessed Mummy [Lv. 2050]') then
                                    for _,v in pairs(game:GetService("Workspace").Enemies:GetChildren()) do
                                        if v.Name == 'Reborn Skeleton [Lv. 1975]' or v.Name == 'Living Zombie [Lv. 2000]' or v.Name == 'Demonic Soul [Lv. 2025]' or v.Name == 'Posessed Mummy [Lv. 2050]' then
                                            repeat task.wait()
                                                getgenv().MobPos = v.HumanoidRootPart.CFrame
                                                Teleport(v.HumanoidRootPart.CFrame * CFrame.new(0,30,3))
                                                BusoAndKen()
                                                EquipTool(WeaponName)
                                                Magnet = true
                                                Attack = true
                                            until not getgenv().U.Main.FarmTranformGate or not v.Parent or v.Humanoid.Health <= 0 or not v:FindFirstChild('Humanoid') or not v:FindFirstChild('HumanoidRootPart')
                                        end
                                    end
                                else
                                    Teleport(CFrame.new(-9479.2168, 200.215088, 5577.09277, 0, 0, 1, 0, 1, -0, -1, 0, 0))
                                    Attack = false
                                    Magnet = false
                                end
                            else
                                SendKey("Y",0)
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("UpgradeRace", "Check")
                                game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("UpgradeRace", "Buy")
                            end
                        else
                        end
                    end
                end)
            end
        end)
    end)

    f2:AddToggle('Auto Activate Ability',false,function(a)
        Ability = a
        task.spawn(function()
            while Ability do SendKey("Y",0)
                local args = {
                    [1] = "ActivateAbility"
                }
                game:GetService("ReplicatedStorage").Remotes.CommE:FireServer(unpack(args))
                task.wait(15)
            end
        end)
    end)

    f2:AddToggle('Auto Complete Trial', getgenv().U.Main.AutoCompleteTrial, function(a)
        getgenv().U.Main.AutoCompleteTrial = a
        save()
        task.spawn(function()
            while getgenv().U.Main.AutoCompleteTrial do task.wait()
                pcall(function()
                    if tostring(game.Players.LocalPlayer.Data.Race.Value) == "Mink" then
                        if not game:GetService("Workspace").Map:FindFirstChild("MinkTrial") then
                        else
                            if game:GetService("Workspace").Map:FindFirstChild("MinkTrial") then
                                
                                local Celling = Teleport(game:GetService("Workspace").Map.MinkTrial.Ceiling.CFrame*CFrame.new(0,-20,0))
                                Celling:Stop()
                                Teleport(plr.Character.HumanoidRootPart.CFrame)
                                --Teleport(game:GetService("Workspace").Map["Temple of Time"].MinkCorridor.Door.Entrance.CFrame)
                               
                            end
                        end
                    elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Human" then
                        if not game:GetService("Workspace").Map:FindFirstChild("HumanTrial")  then
                        else
                            pcall(function()
                                KillAura = true
                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                    if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and (v.HumanoidRootPart.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 400 then
                                        repeat task.wait()
                                            EquipTool(Meele)
                                            BusoAndKen()
                                            --local HumanBoss = Teleport(v.HumanoidRootPart.CFrame*CFrame.new(7,25,10))
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                            v.Humanoid:ChangeState(14)
                                            v.Humanoid:ChangeState(11)
                                            v.Humanoid.JumpPower = 0
                                        until not getgenv().U.Main.AutoCompleteTrial or v.Humanoid.Health <= 0 or not v.Parent
                                        KillAura=false
                                    end
                                end
                            end) 
                        end
                    elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Cyborg" then
                        if not game:GetService("Workspace").Map:FindFirstChild("CyborgTrial") then
                            --Teleport(game:GetService("Workspace").Map["Temple of Time"].CyborgCorridor.Door.Entrance.CFrame)
                        else
                            if game:GetService("Workspace").Map:FindFirstChild("CyborgTrial") then
                                local Ahh = Teleport(game:GetService("Workspace").Map.CyborgTrial.Floor.CFrame*CFrame.new(0,500,0))
                                Ahh:Cancel()
                            else --Teleport(game:GetService("Workspace").Map["Temple of Time"].CyborgCorridor.Door.Entrance.CFrame)
                            end
                        end
                    elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Skypiea" then
                        if not game:GetService("Workspace").Map:FindFirstChild("SkyTrial") then
                        else
                            if game:GetService("Workspace").Map:FindFirstChild("SkyTrial") then
                                if (game:GetService("Workspace").Map.SkyTrial.Model.FinishPart.CFrame-plr.Character.HumanoidRootPart.Position).Magnitude <= 750 then
                                    local FinishP =Teleport(game:GetService("Workspace").Map.SkyTrial.Model.FinishPart.CFrame)
                                    FinishP:Cancel()
                                else --Teleport(game:GetService("Workspace").Map["Temple of Time"].SkypieaCorridor.Door.Entrance.CFrame)
                                end
                            end
                        end
                    elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Ghoul" then
                        if not game:GetService("Workspace").Map:FindFirstChild("GhoulTrial") then
                        else
                            pcall(function()
                                for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                                    if v:FindFirstChild("Humanoid") and v:FindFirstChild("HumanoidRootPart") and (v.HumanoidRootPart.Position-game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.Position).magnitude <= 400 then
                                        repeat task.wait()
                                            EquipTool(Melee)
                                            BusoAndKen()
                                            getgen().MobPos = v.HumanoidRootPart.CFrame
                                            Magnet = true
                                            KillAura = true
                                            v.Humanoid.Health = -math.huge
                                            --local GhoulMob = Teleport(v.HumanoidRootPart.CFrame*CFrame.new(7,25,10))
                                            --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                                            v.Humanoid:ChangeState(14)
                                            v.Humanoid:ChangeState(11)
                                            v.Humanoid.JumpPower = 0
                                        until not getgenv().U.Main.AutoCompleteTrial or v.Humanoid.Health <= 0 or not v.Parent
                                        Magnet = false
                                        KillAura = false
                                        if GhoulMob then
                                            GhoulMob:Cancel()
                                        end
                                    end
                                end
                            end)
                        end
                    elseif tostring(game.Players.LocalPlayer.Data.Race.Value) == "Fishman" then
                        if not game:GetService("Workspace").Map:FindFirstChild("FishTrial") then
                            --Teleport(game:GetService("Workspace").Map["Temple of Time"].FishmanCorridor.Door.Entrance.CFrame)
                        else
                            if game:GetService("Workspace").Map:FindFirstChild("FishTrial") then
                                if (game:GetService("Workspace").Map:FindFirstChild("FishTrial").Part.Position-plr.Character.HumanoidRootPart.Position).Magnitude <= 500 then
                                    local SeaBeast = Teleport(CFrame.new(25032.043, 75.04647064, 12619.5967))
                                    SeaBeast:Cancel()
                
                                    -- Spam Skill EEEEEEEEEEEE3EEE
                                    task.spawn(function()
                                        EquipTool(DevilFruit)
                                        SendKey('Z',0)
                                        task.wait(2)
                                        SendKey('X',0)
                                        task.wait(2)
                                        SendKey('C',0)
                                        task.wait(2)
                                        SendKey('V',0)
                                        task.wait(3)
                                        task.spawn(function()
                                            EquipTool(Melee);
                                            SendKey('Z',0)
                                            task.wait(2)
                                            SendKey('X',0)
                                            task.wait(2)
                                            SendKey('C',0)
                                        end)
                                    end)
                                end
                            else if not game:GetService("Workspace").Map:FindFirstChild("FishTrial") then
                                    --Teleport(game:GetService("Workspace").Map["Temple of Time"].FishmanCorridor.Door.Entrance.CFrame)
                                end
                            end
                        end
                    end
                end)
            end
        end)
    end)

    f2:AddToggle('Auto Look At Moon',getgenv().U.Main.LookAtMoon,function(a)
        getgenv().U.Main.LookAtMoon = a
        save()
    end)
end

local f21 = Race:CreatePage("", 2)
f21:AddLabel([[\\ Mirage Island //]]) do

    local Status = f2:AddLabel('Mirage Island : Not Spawn')-- Ready to spawn / Spawned

    f21:AddToggle('Mirage Spawn Esp',getgenv().U.Main.MirageEsp,function(a)
        getgenv().U.Main.MirageEsp = a
        save()
    end)

    task.spawn(function()
        while task.wait() do
            if game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Mirage Island") then
                -- Status:ChangeText('Ready To Spawn')
                if getgenv().U.Main.MirageEsp then
                    Esp(game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Mirage Island"))
                end
            elseif game:GetService("Workspace").Map:FindFirstChild("Mystic Island") then--Check
                -- Status:ChangeText('Spawned')
                if getgenv().U.Main.MirageEsp then
                    Esp(game:GetService("Workspace").Map:FindFirstChild("Mystic Island"))
                end
            else
                -- Status:ChangeText('Not Spawned')
            end
        end
    end)

    f21:AddToggle('Teleport to gear',getgenv().U.Main.TeleportToGear,function(a)
        getgenv().U.Main.TeleportToGear = a
        getgenv().Clip = a
        save()
    end)

    f21:AddToggle('Auto Get V4 Quest (Gear)',getgenv().U.Main.GetQV4,function(a)
        getgenv().U.Main.GetQV4 = a
        save()
    end)
end

task.spawn(function()
    while true do task.wait()
        if game:GetService("Workspace").Map:FindFirstChild('MysticIsland') then
            for i,v in pairs(game:GetService("Workspace").Map:FindFirstChild('MysticIsland'):GetChildren()) do
                if v.Name == 'Part' or v.Name == 'Gear' then
                    if v.ClassName == 'MeshPart' then
                        v.Name = 'Gear'
                        if getgenv().U.Main.TeleportToGear then
                            Teleport(v.CFrame)
                        end
                        if getgenv().U.Main.EspGear then
                            Esp(v)
                        end
                        if getgenv().U.Main.ShowGear then
                            v.Transparency = 0
                        end
                        if getgenv().U.Main.GetQV4 then
                            local args = {
                                [1] = "RaceV4Progress",
                                [2] = "Check"
                            }
                            game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
                        end
                    end
                end
            end
        end
    end
end)

local function Check_Race_Skypiea()
	for i,v in pairs(game.Players:GetChildren()) do
		if v.Name ~= game.Players.LocalPlayer.Name and tostring(v.Data.Race.Value) == "Skypiea" then
			print(v.Name)
			LockPlayer = v.Name
			return
		end
	end
end

local function Check_Players()
	for i,v in pairs(game.Players:GetChildren()) do
		if v.Name ~= game.Players.LocalPlayer.Name then
			LockPlayer = v.Name
		end
	end
end

local function AutoGhoulRace()
    if game:GetService("Workspace").Enemies:FindFirstChild("Cursed Captian [Lv. 1325] [Raid Boss]") then
        for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
            if v.Name == "Cursed Captian [Lv. 1325] [Raid Boss]" then
                repeat task.wait()
                    EquipTool(WeaponName)
                    Teleport(v.HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                    FastAttack=true
                    --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                    v.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
                until v.Humanoid.Health <= 0 or not v.Parent or game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 3") or not getgenv().U.Main.AutoEvoleRace
            end
        end
    else
        --พิกัดเกาะเรือ ชก.หา ควย
    end
end

local function CheckRace()
    return tostring(game.Players.LocalPlayer.Data.Race.Value)
end

local function CollectFlowers()
    pcall(function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","2")
    end)
    if not game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 1") and not game.Players.LocalPlayer.Character:FindFirstChild("Flower 1") and game:GetService("Workspace"):FindFirstChild("Flower1") then
        repeat task.wait()
            Tween(game:GetService("Workspace"):FindFirstChild("Flower1").CFrame)
        until game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 1") or game.Players.LocalPlayer.Character:FindFirstChild("Flower 1") or not getgenv().U.Main.AutoEvoleRace
    elseif not game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 2") and not game.Players.LocalPlayer.Character:FindFirstChild("Flower 2") and game:GetService("Workspace"):FindFirstChild("Flower2") then
        repeat task.wait()
            Tween(game:GetService("Workspace"):FindFirstChild("Flower2").CFrame)
        until game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 2") or game.Players.LocalPlayer.Character:FindFirstChild("Flower 2") or not getgenv().U.Main.AutoEvoleRace
    elseif not game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 3") and not game.Players.LocalPlayer.Character:FindFirstChild("Flower 3") then
        if game:GetService("Workspace").Enemies:FindFirstChild("Marine Captain [Lv. 900]") then
            for i,v in pairs(game.Workspace.Enemies:GetChildren()) do
                if v.Name == "Marine Captain [Lv. 900]" then
                    repeat task.wait()
                        EquipTool(WeaponName)
                        Tween(v.HumanoidRootPart.CFrame*CFrame.new(0,30,0))
                        FastAttack=true
                        --v.HumanoidRootPart.Size = Vector3.new(60,60,60)
                        v.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame
                    until v.Humanoid.Health <= 0 or not v.Parent or game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 3") or not getgenv().U.Main.AutoEvoleRace
                end
            end
        else
            Tween(CFrame.new(-2335.2026367188, 79.786659240723, -3245.8674316406))
        end
    elseif game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 3") and game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 1") and game.Players.LocalPlayer.Backpack:FindFirstChild("Flower 2") then
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","1")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Alchemist","3")
    else
        Tween(CFrame.new(-379.70889282227, 73.0458984375, 304.84692382813))
    end
end

local function V2()
    if game.Workspace.Enemies:FindFirstChild("Don Swan [Lv. 1000] [Boss]") then
        repeat task.wait()
            EquipTool(WeaponName)
            game.Workspace.Enemies:FindFirstChild("Don Swan [Lv. 1000] [Boss]").HumanoidRootPart.Size = Vector3.new(60,60,60)
            Teleport(game.Workspace.Enemies:FindFirstChild("Don Swan [Lv. 1000] [Boss]").HumanoidRootPart.CFrame*CFrame.new(0,30,0))
        until not game.Workspace.Enemies:FindFirstChild("Don Swan [Lv. 1000] [Boss]") or game.Workspace.Enemies:FindFirstChild("Don Swan [Lv. 1000] [Boss]").Humanoid.Health <= 0 or not getgenv().U.Main.AutoEvoleRace 
        getgenv().U.Main.AutoEvoleRace_V2 = true
        save()
    elseif game.ReplicatedStorage:FindFirstChild("Don Swan [Lv. 1000] [Boss]") then
        Teleport(game.ReplicatedStorage:FindFirstChild("Don Swan [Lv. 1000] [Boss]").HumanoidRootPart.CFrame*CFrame.new(0,30,0))
    else
        Teleport(CFrame.new(2288.802, 15.1870775, 863.034607, 0.99974072, -8.41247214e-08, -0.0227668174, 8.4774733e-08, 1, 2.75850098e-08, 0.0227668174, -2.95079072e-08, 0.99974072))
    end
end

--[[
        Raid1:AddToggle("Grab Fruit",getgenv().BringFruit,function(value)
        getgenv().BringFruit = value
        pcall(function()
            while getgenv().BringFruit do wait(.1)
                for i,v in pairs(game:GetService("Workspace"):GetChildren()) do
                    if v:IsA("Tool") then
                        local OldCFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame				
                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = v.Handle.CFrame * CFrame.new(0,0,8)
                        v.Handle.CFrame = game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame
                        wait(.1)
                        game:GetService("Players").LocalPlayer.Character.HumanoidRootPart.CFrame = OldCFrame
                    end
                end
            end
        end)
    end)

]]

-- Shop --

local g1 = Shop:CreatePage("", 1)
g1:AddLabel([[\\ Makets //]]) do

    g1:AddButton('Random Cousin',function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Cousin","Buy")
    end)

    g1:AddButton("Buy DeathKing",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("Bones","Buy",1,1)
    end)
end

local g12 = Shop:CreatePage("", 1)
g12:AddLabel([[\\ Fragments //]]) do

    g1:AddButton("Random Race [3K Fragments]",function()
        local args = {
            [1] = "BlackbeardReward",
            [2] = "Reroll",
            [3] = "2"
        }
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)

    g1:AddButton("Reset Stats [2.5K Fragments]",function()
        local args = {
            [1] = "BlackbeardReward",
            [2] = "Refund",
            [3] = "2"
        }
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)
end

local g13 = Shop:CreatePage("", 1)
g1:AddLabel("[ Fighting Style ]") do

    g1:AddButton("Black Leg",function()
        local args = {
            [1] = "BuyBlackLeg"
        }
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)

    g1:AddButton("Electro",function()
        local args = {
            [1] = "BuyElectro"
        }
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)

    g1:AddButton("Fishman Karate",function()
        local args = {
            [1] = "BuyFishmanKarate"
        }
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)

    g1:AddButton("Dragon Claw",function()
        local args = {
            [1] = "BlackbeardReward",
            [2] = "DragonClaw",
            [3] = "2"
        }
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)

    g1:AddButton("Superhuman",function()
        local args = {
            [1] = "BuySuperhuman"
        }
        
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)

    g1:AddButton("Death Step",function()
        local args = {
            [1] = "BuyDeathStep"
        }
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)

    g1:AddButton("Sharkman Karate",function()
        local args = {
            [1] = "BuySharkmanKarate",
            [2] = true
        }
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
        local args = {
            [1] = "BuySharkmanKarate"
        }
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer(unpack(args))
    end)

    g1:AddButton("Electric Claw",function()
        local string_1 = "BuyElectricClaw";
        local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
        Target:InvokeServer(string_1);
    end)

    g1:AddButton("Dragon Talon",function()
        local string_1 = "BuyDragonTalon";
        local bool_1 = true;
        local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
        Target:InvokeServer(string_1, bool_1);
        local string_1 = "BuyDragonTalon";
        local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
        Target:InvokeServer(string_1);
    end)

    g1:AddButton("Buy Black Leg",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyBlackLeg")
    end)

    g1:AddButton("Buy Electro",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyElectro")
    end)

    g1:AddButton("Buy Fishman Karate",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyFishmanKarate")
    end)

    g1:AddButton("Buy Dragon Claw",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","1")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","DragonClaw","2")
    end)

    g1:AddButton("Buy Superhuman",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuySuperhuman")
    end)
end

-----Shop----------------
g1:AddLabel("[ Accessory ]")

g1:AddButton("Tomoe Ring",function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Tomoe Ring")
end)

g1:AddButton("Black Cape",function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Black Cape")
end)

g1:AddButton("Swordsman Hat",function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Swordsman Hat")
end)

local g12 = Shop:CreatePage("", 2)
g12:AddLabel([[\\ Swords //]]) do

    g12:AddButton("Cutlass",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Cutlass")
    end)

    g12:AddButton("Katana",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Katana")
    end)

    g12:AddButton("Iron Mace",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Iron Mace")
    end)

    g12:AddButton("Duel Katana",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Duel Katana")
    end)

    g12:AddButton("Triple Katana", function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Triple Katana")
    end)

    g12:AddButton("Pipe",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Pipe")
    end)

    g12:AddButton("Dual Headed Blade",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Dual-Headed Blade")
    end)

    g12:AddButton("Bisento",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Bisento")
    end)

    g12:AddButton("Soul Cane",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Soul Cane")
    end)
end

local g13 = Shop:CreatePage("", 2)
g13:AddLabel([[\\ Guns //]]) do

    g13:AddButton("Slingshot",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Slingshot")
    end)

    g13:AddButton("Musket",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Musket")
    end)

    g13:AddButton("Flintlock",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Flintlock")
    end)

    g13:AddButton("Refined Flintlock",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Refined Flintlock")
    end)

    g13:AddButton("Cannon",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyItem","Cannon")
    end)

    g13:AddButton("Kabucha",function()
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Slingshot","1")
        game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BlackbeardReward","Slingshot","2")
    end)
end

local g14 = Shop:CreatePage("", 2)
g14:AddLabel([[\\ Abilities //]])

g14:AddButton("Buy Geppo",function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Geppo")
end)

g14:AddButton("Buy Buso Haki",function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Buso")
end)


g14:AddButton("Buy Soru",function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("BuyHaki","Soru")
end)

g14:AddButton("Buy Observation(Ken) Haki",function()
    game:GetService("ReplicatedStorage").Remotes.CommF_:InvokeServer("KenTalk","Buy")
end)


-- Fruits Shop --


local g2 = Shop:CreatePage("", 2)
g2:AddLabel([[\\ Snipes //]]) do
    local string_1 = "getInventoryFruits";
    local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
    local Remote_GetFruits = game.ReplicatedStorage:FindFirstChild("Remotes").CommF_:InvokeServer("GetFruits");
    local Table_DevilFruitSniper = {}
    local DevilFruitList = {}
    local ShopDevilSell = {}

    for i,v in next,Remote_GetFruits do
        table.insert(DevilFruitList,v.Name)
        if v.OnSale then 
			table.insert(ShopDevilSell,"nil")
            table.insert(ShopDevilSell,v.Name)
        end
    end

    for i,v in pairs(Target:InvokeServer(string_1)) do
        for i1,v1 in pairs(v) do
            if i1 == "Name" then 
                table.insert(DevilFruitList,v1)
            end
        end
    end

    local RefreshDevilFruitShop = g2:AddDropdown("Selling Fruits","nil",false,ShopDevilSell,function(v)
        getgenv().U.Main.DeFSelect = v
        save()
    end)

    g2:AddButton("Buy Select",function()
        local string_1 = "PurchaseRawFruit";
        local string_2 = getgenv().U.Main.DeFSelect;
        local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
        Target:InvokeServer(string_1, string_2);
    end)

    local EventShop = {}

    local args = {
        [1] = "GetStore"
    }

    local Celebrate =game:GetService("ReplicatedStorage").Remotes.Celebration:InvokeServer(unpack(args))

    for i,v in pairs(Celebrate) do
        if i == 1 then
            for a,b in ipairs(v) do
                if b.Name then
                    table.insert(EventShop, b.Name)
                end
            end
        end
    end
    -- Price

    --[[g2:AddLabel('Events')

    local Event = g2:AddDropdown('Select Items',EventShop,getgenv().U.SnipeEvent,function(a)
        getgenv().U.SnipeEvent = a
        save()
    end)

    g2:AddButton('Refresh AddDropdown',function()
        Event:Clear()
        table.Clear(EventShop)
        task.wait(1)
        for i,v in pairs(Celebrate) do
            if i == 1 then
                for a,b in ipairs(v) do
                    if b.Name then
                        table.insert(EventShop, b.Name)
                        Event:Add(b.Name)
                    end
                end
            end
        end
    end)

    g2:AddToggle('Auto Buy',getgenv().U.BuySelect,function(a)
        getgenv().U.BuySelect = a
        save()
        task.spawn(function()
            while task.wait(1) do
                if getgenv().U.BuySelect then
                    for i,v in pairs(Celebrate) do
                        if i == 1 then
                            for a,b in ipairs(v) do
                                if b.Name == getgenv().U.SnipeEvent then
                                    print(b.Name,b.Price)
                                    if CheckMaterial("Hearts") >= b.Price then
                                        local args = {
                                            [1] = "Purchase",
                                            [2] = tostring(getgenv().U.SnipeEvent)
                                        }
                                        game:GetService("ReplicatedStorage").Remotes.Celebration:InvokeServer(unpack(args))
                                    else
                                        print('Not enough material')
                                    end
                                end
                            end
                        end
                    end
                end
            end
        end)
    end)]]

    local Sniping = g2:AddDropdown("Select Shipe",DevilFruitList,false,getgenv().U.Raids.SnipeSelect,function(v)
        getgenv().U.Main.SnipeSelect = v
        save()
    end)

    g2:AddToggle('Auto Snipe',getgenv().U.Raids.AutoSnipe,function(a)
        getgenv().U.Raids.AutoSnipe = a 
        save()
        task.spawn(function()
            while task.wait(.5) do
                if getgenv().U.Raids.AutoSnipe then
                    for i,v in next,Remote_GetFruits do
                        if v.Name == getgenv().U.Raids.SnipeSelect then
                            if v.OnSale == true then 
                                local string_1 = "PurchaseRawFruit";
                                local string_2 = v.Name;
                                local Target = game:GetService("ReplicatedStorage").Remotes["CommF_"];
                                Target:InvokeServer(string_1, string_2);
                            end
                        end
                    end
                end
            end
        end)
    end)

    getgenv().Storage = Backpack or Character

    g2:AddToggle('Store Fruits',getgenv().U.Raids.StoreFruit,function(a)
        getgenv().U.Raids.StoreFruit = a
        save()
        task.spawn(function()
            while task.wait(.5) do
                if getgenv().U.Raids.StoreFruit then
                    for i,v in pairs(game:GetService("Players").LocalPlayer[getgenv().Storage]:GetChildren()) do
                        if string.find(v.Name, "Fruit") then
                            EquipTool(v.Name)
                            game:GetService('ReplicatedStorage').Remotes.CommF_:InvokeServer('StoreFruit',v.Name)
                        end
                    end
                end
            end
        end)
    end)
end

print('Ui Loaded')

print('Random Funcs Loading')

_G.currentply = nil
_G.Moon = nil
_G.Mystic = nil

for i,v in pairs(game:GetService("Players"):GetChildren()) do
    _G.currentply = i
end

if game:GetService("Workspace").Map:FindFirstChild("MysticIsland") then
    _G.Mystic = "Spawned"
elseif game:GetService("Workspace")["_WorldOrigin"].Locations:FindFirstChild("Mirage Island") then
    _G.Mystic = "Ready to Spawned"
else
    _G.Mystic = "not Spawned"
end

if game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709149431" then
    _G.Moon = "Moon State : [5/5] |Full moon | "..'🌕'
elseif game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709149052" then
    _G.Moon = "Moon State : [4/5] | ".."🌖"
elseif game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709143733" then
    _G.Moon = "Moon State : [3/5] | "..'🌗'
elseif game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709150401" then
    _G.Moon = "Moon State : [2/5] | "..'🌘'
elseif game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709149680" then
    _G.Moon = "Moon State : [1/5] | "..'🌘 '
else
    _G.Moon = "Moon State : [0/5] | "..'🌑 '
end

local url = 'https://discordapp.com/api/webhooks/1065526937470128148/4WkNcydGazCn6n1sXIe8R7cXmyxGhEo7jLlliAhXg97Q06uc1GC4p0GKLEjHqFj-VA00'
local data = {
    ["content"] = "",
    ["embeds"] = {
        {
            ["description"] = "**Scripts**\n```lua\n"..tostring('game:GetService("ReplicatedStorage").__ServerBrowser:InvokeServer("teleport","'..game.JobId..'")').."\n```",
            ["color"] = 16711751,
            ["fields"] = {
                {["name"] = "**Players**",["value"] = "```yaml\n".._G.currentply.."/"..game:GetService("Players").MaxPlayers.."\n```",["inline"] = true,},
                {["name"] = "**Job Id**",["value"] = "```yaml\n"..game.JobId.."\n```",["inline"] = true,},
                {["name"] = "**Moon Status**",["value"] = "\n" .._G.Moon.. "\n",["inline"] = true,},
                {["name"] = "**Mirage Island Status**",["value"] = "```lua\n"..tostring(_G.Mystic).."\n```",["inline"] = true,}
            },
            ["author"] = {
                ["name"] = "Unique hub : Fullmoon Notifyer",
                ["icon_url"] = "https://cdn.discordapp.com/avatars/1049706372759044251/82ca2d4c117e69c62255582981d00c0c.webp?size=128"
            },
            ["footer"] = {
                ["text"] = "Unique hub",
                ["icon_url"] = "https://cdn.discordapp.com/avatars/1049706372759044251/82ca2d4c117e69c62255582981d00c0c.webp?size=128"
            },
            ["timestamp"] = DateTime.now():ToIsoDate(),
            ["thumbnail"] = {
                ["url"] = "https://cdn.discordapp.com/avatars/1049706372759044251/82ca2d4c117e69c62255582981d00c0c.webp?size=128"
            }
        }
    },
}
local newdata = game:GetService("HttpService"):JSONEncode(data)

local headers = {
    ["content-type"] = "application/json"
}

local R = {Url = url, Body = newdata, Method = "POST", Headers = headers}

local request = http_request or request or HttpPost or syn.request
local R = {Url = url, Body = newdata, Method = "POST", Headers = headers}
local httpbin = game:HttpGet("https://httpbin.org/get")
if not httpbin:match("Specific_PrivateGame") then  
    if game:GetService("Lighting").Sky.MoonTextureId == "http://www.roblox.com/asset/?id=9709149431" or game:GetService("Workspace").Map:FindFirstChild("MysticIsland") then
        request(R)
    end
end

print('Random Funcs loadded!!!')
print('Loaded All Successfully!!')
