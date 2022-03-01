

local ScreenGui = Instance.new("ScreenGui")
local Main = Instance.new("Frame")
local lavel = Instance.new("TextLabel")
local Aimlock = Instance.new("TextButton")
local SilentAim = Instance.new("TextButton")
local SilentAimlock = Instance.new("TextButton")
local Fly = Instance.new("TextButton")
local AntiStomp = Instance.new("TextButton")
local ESP = Instance.new("TextButton")

--Properties:

ScreenGui.Parent = game.Workspace

Main.Name = "Main"
Main.Parent = ScreenGui
Main.BackgroundColor3 = Color3.fromRGB(200, 50, 23)
Main.BorderColor3 = Color3.fromRGB(27, 42, 53)
Main.Position = UDim2.new(0.214445278, 0, 0.255266398, 0)
Main.Size = UDim2.new(0, 660, 0, 344)
Main.Active = true
Main.Draggable = true

lavel.Name = "lavel"
lavel.Parent = Main
lavel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
lavel.Size = UDim2.new(0, 660, 0, 50)
lavel.Font = Enum.Font.SourceSans
lavel.Text = "R34PERWARE.CC"
lavel.TextColor3 = Color3.fromRGB(0, 0, 0)
lavel.TextScaled = true
lavel.TextSize = 57.000
lavel.TextWrapped = true

Aimlock.Name = "Aimlock"
Aimlock.Parent = Main
Aimlock.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Aimlock.Position = UDim2.new(0.0303030312, 0, 0.197674423, 0)
Aimlock.Size = UDim2.new(0, 247, 0, 87)
Aimlock.Font = Enum.Font.SourceSans
Aimlock.Text = "Aimlock"
Aimlock.TextColor3 = Color3.fromRGB(0, 0, 0)
Aimlock.TextSize = 36.000
Aimlock.MouseButton1Down:connect(function()
	getgenv().AimPart = "HumanoidRootPart"
	getgenv().AimlockKey = "q"
	getgenv().AimRadius = 30
	getgenv().ThirdPerson = true
	getgenv().FirstPerson = true
	getgenv().TeamCheck = false
	getgenv().PredictMovement = true
	getgenv().PredictionVelocity = 9
	local L_27_, L_28_, L_29_, L_30_ =
		game:GetService "Players",
	game:GetService "UserInputService",
	game:GetService "RunService",
	game:GetService "StarterGui"
	local L_31_, L_32_, L_33_, L_34_, L_35_, L_36_, L_37_ =
		L_27_.LocalPlayer,
	L_27_.LocalPlayer:GetMouse(),
	workspace.CurrentCamera,
	CFrame.new,
	Ray.new,
	Vector3.new,
	Vector2.new
	local L_38_, L_39_, L_40_ = true, false, false
	local L_41_
	getgenv().CiazwareUniversalAimbotLoaded = true
	getgenv().WorldToViewportPoint = function(L_42_arg0)
		return L_33_:WorldToViewportPoint(L_42_arg0)
	end
	getgenv().WorldToScreenPoint = function(L_43_arg0)
		return L_33_.WorldToScreenPoint(L_33_, L_43_arg0)
	end
	getgenv().GetObscuringObjects = function(L_44_arg0)
		if L_44_arg0 and L_44_arg0:FindFirstChild(getgenv().AimPart) and L_31_ and L_31_.Character:FindFirstChild("Head") then
			local L_45_ = workspace:FindPartOnRay(L_35_(L_44_arg0[getgenv().AimPart].Position, L_31_.Character.Head.Position))
			if L_45_ then
				return L_45_:IsDescendantOf(L_44_arg0)
			end
		end
	end
	getgenv().GetNearestTarget = function()
		local L_46_ = {}
		local L_47_ = {}
		local L_48_ = {}
		for L_50_forvar0, L_51_forvar1 in pairs(L_27_:GetPlayers()) do
			if L_51_forvar1 ~= L_31_ then
				table.insert(L_46_, L_51_forvar1)
			end
		end
		for L_52_forvar0, L_53_forvar1 in pairs(L_46_) do
			if L_53_forvar1.Character ~= nil then
				local L_54_ = L_53_forvar1.Character:FindFirstChild("Head")
				if getgenv().TeamCheck == true and L_53_forvar1.Team ~= L_31_.Team then
					local L_55_ =
						(L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
					local L_56_ =
						Ray.new(
							game.Workspace.CurrentCamera.CFrame.p,
							(L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_55_
						)
					local L_57_, L_58_ = game.Workspace:FindPartOnRay(L_56_, game.Workspace)
					local L_59_ = math.floor((L_58_ - L_54_.Position).magnitude)
					L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
					L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_55_
					L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
					L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_59_
					table.insert(L_48_, L_59_)
				elseif getgenv().TeamCheck == false and L_53_forvar1.Team == L_31_.Team then
					local L_60_ =
						(L_53_forvar1.Character:FindFirstChild("Head").Position - game.Workspace.CurrentCamera.CFrame.p).magnitude
					local L_61_ =
						Ray.new(
							game.Workspace.CurrentCamera.CFrame.p,
							(L_32_.Hit.p - game.Workspace.CurrentCamera.CFrame.p).unit * L_60_
						)
					local L_62_, L_63_ = game.Workspace:FindPartOnRay(L_61_, game.Workspace)
					local L_64_ = math.floor((L_63_ - L_54_.Position).magnitude)
					L_47_[L_53_forvar1.Name .. L_52_forvar0] = {}
					L_47_[L_53_forvar1.Name .. L_52_forvar0].dist = L_60_
					L_47_[L_53_forvar1.Name .. L_52_forvar0].plr = L_53_forvar1
					L_47_[L_53_forvar1.Name .. L_52_forvar0].diff = L_64_
					table.insert(L_48_, L_64_)
				end
			end
		end
		if unpack(L_48_) == nil then
			return nil
		end
		local L_49_ = math.floor(math.min(unpack(L_48_)))
		if L_49_ > getgenv().AimRadius then
			return nil
		end
		for L_65_forvar0, L_66_forvar1 in pairs(L_47_) do
			if L_66_forvar1.diff == L_49_ then
				return L_66_forvar1.plr
			end
		end
		return nil
	end
	L_32_.KeyDown:Connect(
		function(L_67_arg0)
			if L_67_arg0 == AimlockKey and L_41_ == nil then
				pcall(
					function()
						if L_39_ ~= true then
							L_39_ = true
						end
						local L_68_
						L_68_ = GetNearestTarget()
						if L_68_ ~= nil then
							L_41_ = L_68_
						end
					end
				)
			elseif L_67_arg0 == AimlockKey and L_41_ ~= nil then
				if L_41_ ~= nil then
					L_41_ = nil
				end
				if L_39_ ~= false then
					L_39_ = false
				end
			end
		end
	)
	L_29_.RenderStepped:Connect(
		function()
			if getgenv().ThirdPerson == true and getgenv().FirstPerson == true then
				if
					(L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 or
					(L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1
				then
					L_40_ = true
				else
					L_40_ = false
				end
			elseif getgenv().ThirdPerson == true and getgenv().FirstPerson == false then
				if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude > 1 then
					L_40_ = true
				else
					L_40_ = false
				end
			elseif getgenv().ThirdPerson == false and getgenv().FirstPerson == true then
				if (L_33_.Focus.p - L_33_.CoordinateFrame.p).Magnitude <= 1 then
					L_40_ = true
				else
					L_40_ = false
				end
			end
			if L_38_ == true and L_39_ == true then
				if L_41_ and L_41_.Character and L_41_.Character:FindFirstChild(getgenv().AimPart) then
					if getgenv().FirstPerson == true then
						if L_40_ == true then
							if getgenv().PredictMovement == true then
								L_33_.CFrame =
									L_34_(
										L_33_.CFrame.p,
										L_41_.Character[getgenv().AimPart].Position +
										L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
									)
							elseif getgenv().PredictMovement == false then
								L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
							end
						end
					elseif getgenv().ThirdPerson == true then
						if L_40_ == true then
							if getgenv().PredictMovement == true then
								L_33_.CFrame =
									L_34_(
										L_33_.CFrame.p,
										L_41_.Character[getgenv().AimPart].Position +
										L_41_.Character[getgenv().AimPart].Velocity / PredictionVelocity
									)
							elseif getgenv().PredictMovement == false then
								L_33_.CFrame = L_34_(L_33_.CFrame.p, L_41_.Character[getgenv().AimPart].Position)
							end
						end
					end
				end
			end
		end
	)
end
)
end)

SilentAim.Name = "Silent Aim"
SilentAim.Parent = Main
SilentAim.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
SilentAim.Position = UDim2.new(0.609090924, 0, 0.197674423, 0)
SilentAim.Size = UDim2.new(0, 245, 0, 87)
SilentAim.Font = Enum.Font.SourceSans
SilentAim.Text = "Silent Aim"
SilentAim.TextColor3 = Color3.fromRGB(0, 0, 0)
SilentAim.TextSize = 36.000
Silent Aim.MouseButton1Down:connect(function()
	loadstring(game:HttpGet("https://raw.githubusercontent.com/PewPewBoy/Silent-Aim-Tho/main/Silent%20Aim%20stuff", true))()
end)

SilentAimlock.Name = "Silent Aimlock"
SilentAimlock.Parent = Main
SilentAimlock.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
SilentAimlock.Position = UDim2.new(0.609090924, 0, 0.482558131, 0)
SilentAimlock.Size = UDim2.new(0, 245, 0, 78)
SilentAimlock.Font = Enum.Font.SourceSans
SilentAimlock.Text = "Silent Aimlock"
SilentAimlock.TextColor3 = Color3.fromRGB(0, 0, 0)
SilentAimlock.TextSize = 36.000
Silent Aimlock.MouseButton1Down:connect(function()
	-- thusky old lock
	local CC = game:GetService"Workspace".CurrentCamera
	local Plr
	local enabled = falseWD
	local accomidationfactor = 0.131
	local mouse = game.Players.LocalPlayer:GetMouse()
	local placemarker = Instance.new("Part", game.Workspace)

	function makemarker(Parent, Adornee, Color, Size, Size2)
		local e = Instance.new("BillboardGui", Parent)
		e.Name = "PP"
		e.Adornee = Adornee
		e.Size = UDim2.new(Size, Size2, Size, Size2)
		e.AlwaysOnTop = true
		local a = Instance.new("Frame", e)
		a.Size = UDim2.new(1, 0, 1, 0)
		a.BackgroundTransparency = 0
		a.BackgroundColor3 = Color
		local g = Instance.new("UICorner", a)
		g.CornerRadius = UDim.new(50, 50)
		return(e)
	end


	local data = game.Players:GetPlayers()
	function noob(player)
		local character
		repeat wait() until player.Character
		local handler = makemarker(guimain, player.Character:WaitForChild("HumanoidRootPart"), Color3.fromRGB(107, 184, 255), 0.3, 3)
		handler.Name = player.Name
		player.CharacterAdded:connect(function(Char) handler.Adornee = Char:WaitForChild("HumanoidRootPart") end)


		spawn(function()
			while wait() do
				if player.Character then
					TextLabel.Text = player.Name..tostring(player:WaitForChild("leaderstats").Wanted.Value).." | "..tostring(math.floor(player.Character:WaitForChild("Humanoid").Health))
				end
			end
		end)
	end

	for i = 1, #data do
		if data[i] ~= game.Players.LocalPlayer then
			noob(data[i])
		end
	end

	game.Players.PlayerAdded:connect(function(Player)
		noob(Player)
	end)

	spawn(function()
		placemarker.Anchored = true
		placemarker.CanCollide = false
		placemarker.Size = Vector3.new(8, 8, 8)
		placemarker.Transparency = 0.75
		makemarker(placemarker, placemarker, Color3.fromRGB(82, 112, 234), 0.40, 0)
	end)    

	mouse.KeyDown:Connect(function(k)
		if k ~= "b" then return end
		if enabled then
			enabled = false
			guimain[Plr.Name].Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
		else
			enabled = true 
			Plr = getClosestPlayerToCursor()
			guimain[Plr.Name].Frame.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
		end    
	end)

	function getClosestPlayerToCursor()
		local closestPlayer
		local shortestDistance = math.huge

		for i, v in pairs(game.Players:GetPlayers()) do
			if v ~= game.Players.LocalPlayer and v.Character and v.Character:FindFirstChild("Humanoid") and v.Character.Humanoid.Health ~= 0 and v.Character:FindFirstChild("HumanoidRootPart") then
				local pos = CC:WorldToViewportPoint(v.Character.PrimaryPart.Position)
				local magnitude = (Vector2.new(pos.X, pos.Y) - Vector2.new(mouse.X, mouse.Y)).magnitude
				if magnitude < shortestDistance then
					closestPlayer = v
					shortestDistance = magnitude
				end
			end
		end
		return closestPlayer
	end

	game:GetService"RunService".Stepped:connect(function()
		if enabled and Plr.Character and Plr.Character:FindFirstChild("HumanoidRootPart") then
			placemarker.CFrame = CFrame.new(Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor))
		else
			placemarker.CFrame = CFrame.new(0, 9999, 0)
		end
	end)

	local mt = getrawmetatable(game)
	local old = mt.__namecall
	setreadonly(mt, false)
	mt.__namecall = newcclosure(function(...)
		local args = {...}
		if enabled and getnamecallmethod() == "FireServer" and args[2] == "UpdateMousePos" then
			args[3] = Plr.Character.HumanoidRootPart.Position+(Plr.Character.HumanoidRootPart.Velocity*accomidationfactor)
			return old(unpack(args))
		end
		return old(...)
	end)
end)

Fly.Name = "Fly"
Fly.Parent = Main
Fly.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
Fly.Position = UDim2.new(0.0303030312, 0, 0.482558131, 0)
Fly.Size = UDim2.new(0, 247, 0, 78)
Fly.Font = Enum.Font.SourceSans
Fly.Text = "Fly"
Fly.TextColor3 = Color3.fromRGB(0, 0, 0)
Fly.TextSize = 36.000
Fly.MouseButton1Down:connect(function()
	Flyx.Parent = Main
	Flyx.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
	Flyx.Position = UDim2.new(0.0230680499, 0, 0.0778947398, 0)
	Flyx.Size = UDim2.new(0, 180, 0, 50)
	Flyx.Font = Enum.Font.Cartoon
	Flyx.Text = "Fly[x]"
	Flyx.TextColor3 = Color3.fromRGB(255, 255, 255)
	Flyx.TextSize = 36.000
	Flyx.TextWrapped = true
	Flyx.MouseButton1Down:connect(function()
		local plr = game.Players.LocalPlayer
		local mouse = plr:GetMouse()

		localplayer = plr

		if workspace:FindFirstChild("Core") then
			workspace.Core:Destroy()
		end

		local Core = Instance.new("Part")
		Core.Name = "Core"
		Core.Size = Vector3.new(0.05, 0.05, 0.05)

		spawn(function()
			Core.Parent = workspace
			local Weld = Instance.new("Weld", Core)
			Weld.Part0 = Core
			Weld.Part1 = localplayer.Character.LowerTorso
			Weld.C0 = CFrame.new(0, 0, 0)
		end)

		workspace:WaitForChild("Core")

		local torso = workspace.Core
		flying = true
		local speed=10
		local keys={a=false,d=false,w=false,s=false}
		local e1
		local e2
		local function start()
			local pos = Instance.new("BodyPosition",torso)
			local gyro = Instance.new("BodyGyro",torso)
			pos.Name="EPIXPOS"
			pos.maxForce = Vector3.new(math.huge, math.huge, math.huge)
			pos.position = torso.Position
			gyro.maxTorque = Vector3.new(9e9, 9e9, 9e9)
			gyro.cframe = torso.CFrame
			repeat
				wait()
				localplayer.Character.Humanoid.PlatformStand=true
				local new=gyro.cframe - gyro.cframe.p + pos.position
				if not keys.w and not keys.s and not keys.a and not keys.d then
					speed=5
				end
				if keys.w then
					new = new + workspace.CurrentCamera.CoordinateFrame.lookVector * speed
					speed=speed+0
				end
				if keys.s then
					new = new - workspace.CurrentCamera.CoordinateFrame.lookVector * speed
					speed=speed+0
				end
				if keys.d then
					new = new * CFrame.new(speed,0,0)
					speed=speed+0
				end
				if keys.a then
					new = new * CFrame.new(-speed,0,0)
					speed=speed+0
				end
				if speed>10 then
					speed=5
				end
				pos.position=new.p
				if keys.w then
					gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(-math.rad(speed*0),0,0)
				elseif keys.s then
					gyro.cframe = workspace.CurrentCamera.CoordinateFrame*CFrame.Angles(math.rad(speed*0),0,0)
				else
					gyro.cframe = workspace.CurrentCamera.CoordinateFrame
				end
			until flying == false
			if gyro then gyro:Destroy() end
			if pos then pos:Destroy() end
			flying=false
			localplayer.Character.Humanoid.PlatformStand=false
			speed=10
		end
		e1=mouse.KeyDown:connect(function(key)
			if not torso or not torso.Parent then flying=false e1:disconnect() e2:disconnect() return end
			if key=="w" then
				keys.w=true
			elseif key=="s" then
				keys.s=true
			elseif key=="a" then
				keys.a=true
			elseif key=="d" then
				keys.d=true
			elseif key=="x" then
				if flying==true then
					flying=false
				else
					flying=true
					start()
				end
			end
		end)
		e2=mouse.KeyUp:connect(function(key)
			if key=="w" then
				keys.w=false
			elseif key=="s" then
				keys.s=false
			elseif key=="a" then
				keys.a=false
			elseif key=="d" then
				keys.d=false
			end
		end)
		start()
	end)
end)


AntiStomp.Name = "Anti-Stomp"
AntiStomp.Parent = Main
AntiStomp.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
AntiStomp.Position = UDim2.new(0.0303030312, 0, 0.752906859, 0)
AntiStomp.Size = UDim2.new(0, 247, 0, 73)
AntiStomp.Font = Enum.Font.SourceSans
AntiStomp.Text = "Anti-Stomp"
AntiStomp.TextColor3 = Color3.fromRGB(0, 0, 0)
AntiStomp.TextSize = 36.000
Silent Aim.MouseButton1Down:connect(function()
	ANTILOSE.Parent = Main
	ANTILOSE.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
	ANTILOSE.Position = UDim2.new(0.0230680499, 0, 0.324210525, 0)
	ANTILOSE.Size = UDim2.new(0, 180, 0, 50)
	ANTILOSE.Font = Enum.Font.Cartoon
	ANTILOSE.Text = "Anti Lose Weapons[Level 6.5][Exploit]"
	ANTILOSE.TextColor3 = Color3.fromRGB(255, 255, 255)
	ANTILOSE.TextScaled = true
	ANTILOSE.TextSize = 11.000
	ANTILOSE.TextWrapped = true
	ANTILOSE.MouseButton1Down:connect(function()
		pcall(function() if tostring(game.PlaceId) == "2788229376" then local corepackages = game:GetService"CorePackages" local localplayer = game:GetService"Players".LocalPlayer local run = game:GetService"RunService" run:BindToRenderStep("rrrrrrrrrrr",2000,function() pcall(function() if localplayer.Character.Humanoid.Health <= 30 then localplayer.Character.Humanoid:UnequipTools() localplayer.Character.Humanoid:Destroy() workspace.CurrentCamera.CameraSubject = localplayer.Character wait() local prt = Instance.new("Model", corepackages); Instance.new("Part", prt).Name="Torso"; Instance.new("Part", prt).Name="Head"; Instance.new("Humanoid", prt).Name="Humanoid"; localplayer.Character=prt end end) pcall(function() if localplayer.Character.Humanoid.FloorMaterial == "Plastic" then ReplicatedStorage:FireServer("Stomp") end end) end) loadstring(game:HttpGet("https://pastebin.com/raw/MQ3wc7Zq", true))() end end)
	end)
end)

ESP.Name = "ESP"
ESP.Parent = Main
ESP.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
ESP.Position = UDim2.new(0.609090924, 0, 0.752906859, 0)
ESP.Size = UDim2.new(0, 245, 0, 73)
ESP.Font = Enum.Font.SourceSans
ESP.Text = "ESP"
ESP.TextColor3 = Color3.fromRGB(0, 0, 0)
ESP.TextSize = 36.000
Silent Aim.MouseButton1Down:connect(function()
	-- Unnamed ESP

	assert(Drawing, 'exploit not supported')

	local UserInputService = game:GetService'UserInputService';
	local HttpService = game:GetService'HttpService';
	local GUIService = game:GetService'GuiService';
	local RunService = game:GetService'RunService';
	local Players = game:GetService'Players';
	local LocalPlayer = Players.LocalPlayer;
	local Camera = workspace.CurrentCamera
	local Mouse = LocalPlayer:GetMouse();
	local Menu = {};
	local MouseHeld = false;
	local LastRefresh = 0;
	local OptionsFile = 'IC3_ESP_SETTINGS.dat';
	local Binding = false;
	local BindedKey = nil;
	local OIndex = 0;
	local LineBox = {};
	local UIButtons = {};
	local Sliders = {};
	local Dragging = false;
	local DraggingUI = false;
	local DragOffset = Vector2.new();
	local DraggingWhat = nil;
	local OldData = {};
	local IgnoreList = {};
	local Red = Color3.new(1, 0, 0);
	local Green = Color3.new(0, 1, 0);
	local MenuLoaded = false;

	shared.MenuDrawingData = shared.MenuDrawingData or { Instances = {} };
	shared.PlayerData = shared.PlayerData or {};
	shared.RSName = shared.RSName or ('UnnamedESP_by_ic3-' .. HttpService:GenerateGUID(false));

	local GetDataName = shared.RSName .. '-GetData';
	local UpdateName = shared.RSName .. '-Update';

	local Debounce = setmetatable({}, {
		__index = function(t, i)
			return rawget(t, i) or false
		end;
	});

	pcall(function() shared.InputBeganCon:disconnect() end);
	pcall(function() shared.InputEndedCon:disconnect() end);

	function GetMouseLocation()
		return UserInputService:GetMouseLocation();
	end

	function MouseHoveringOver(Values)
		local X1, Y1, X2, Y2 = Values[1], Values[2], Values[3], Values[4]
		local MLocation = GetMouseLocation();
		return (MLocation.x >= X1 and MLocation.x <= (X1 + (X2 - X1))) and (MLocation.y >= Y1 and MLocation.y <= (Y1 + (Y2 - Y1)));
	end

	function GetTableData(t) -- basically table.foreach i dont even know why i made this
		if typeof(t) ~= 'table' then return end
		return setmetatable(t, {
			__call = function(t, func)
				if typeof(func) ~= 'function' then return end;
				for i, v in pairs(t) do
					pcall(func, i, v);
				end
			end;
		});
	end
	local function Format(format, ...)
		return string.format(format, ...);
	end
	function CalculateValue(Min, Max, Percent)
		return Min + math.floor(((Max - Min) * Percent) + .5);
	end

	local Options = setmetatable({}, {
		__call = function(t, ...)
			local Arguments = {...};
			local Name = Arguments[1];
			OIndex = OIndex + 1; -- (typeof(Arguments[3]) == 'boolean' and 1 or 0);
			rawset(t, Name, setmetatable({
				Name = Arguments[1];
				Text = Arguments[2];
				Value = Arguments[3];
				DefaultValue = Arguments[3];
				AllArgs = Arguments;
				Index = OIndex;
			}, {
				__call = function(t, v)
					if typeof(t.Value) == 'function' then
						t.Value();
					elseif typeof(t.Value) == 'EnumItem' then
						local BT = Menu:GetInstance(Format('%s_BindText', t.Name));
						Binding = true;
						local Val = 0
						while Binding do
							wait();
							Val = (Val + 1) % 17;
							BT.Text = Val <= 8 and '|' or '';
						end
						t.Value = BindedKey;
						BT.Text = tostring(t.Value):match'%w+%.%w+%.(.+)';
						BT.Position = t.BasePosition + Vector2.new(t.BaseSize.X - BT.TextBounds.X - 20, -10);
					else
						local NewValue = v;
						if NewValue == nil then NewValue = not t.Value; end
						rawset(t, 'Value', NewValue);
						if Arguments[2] ~= nil then
							if typeof(Arguments[3]) == 'number' then
								local AMT = Menu:GetInstance(Format('%s_AmountText', t.Name));
								AMT.Text = tostring(t.Value);
								AMT.Position = t.BasePosition + Vector2.new(t.BaseSize.X - AMT.TextBounds.X - 10, -10);
							else
								local Inner = Menu:GetInstance(Format('%s_InnerCircle', t.Name));
								Inner.Visible = t.Value;
							end
						end
					end
				end;
			}));
		end;
	})

	function Load()
		local _, Result = pcall(readfile, OptionsFile);
		if _ then -- extremely ugly code yea i know but i dont care p.s. i hate pcall
			local _, Table = pcall(HttpService.JSONDecode, HttpService, Result);
			if _ then
				for i, v in pairs(Table) do
					if Options[i] ~= nil and Options[i].Value ~= nil and (typeof(Options[i].Value) == 'boolean' or typeof(Options[i].Value) == 'number') then
						Options[i].Value = v.Value;
						pcall(Options[i], v.Value);
					end
				end
			end
		end
	end

	Options('Enabled', 'ESP Enabled', true);
	Options('ShowTeam', 'Show Team', false);
	Options('ShowName', 'Show Names', true);
	Options('ShowDistance', 'Show Distance', true);
	Options('ShowHealth', 'Show Health', true);
	Options('ShowBoxes', 'Show Boxes', true);
	Options('ShowTracers', 'Show Tracers', true);
	Options('ShowDot', 'Show Head Dot', false);
	Options('VisCheck', 'Visibility Check', false);
	Options('Crosshair', 'Crosshair', false);
	Options('TextOutline', 'Text Outline', true);
	Options('TextSize', 'Text Size', syn and 18 or 14, 10, 24); -- cuz synapse fonts look weird???
	Options('MaxDistance', 'Max Distance', 2500, 100, 5000);
	Options('RefreshRate', 'Refresh Rate (ms)', 5, 1, 200);
	Options('MenuKey', 'Menu Key', Enum.KeyCode.F4, 1);
	Options('ResetSettings', 'Reset Settings', function()
		for i, v in pairs(Options) do
			if Options[i] ~= nil and Options[i].Value ~= nil and Options[i].Text ~= nil and (typeof(Options[i].Value) == 'boolean' or typeof(Options[i].Value) == 'number') then
				Options[i](Options[i].DefaultValue);
			end
		end
	end, 4);
	Options('LoadSettings', 'Load Settings', Load, 3);
	Options('SaveSettings', 'Save Settings', function()
		writefile(OptionsFile, HttpService:JSONEncode(Options));
	end, 2)
	-- Options.SaveSettings.Value();

	Load();

	Options('MenuOpen', nil, true);

	local function Set(t, i, v)
		t[i] = v;
	end
	local function Combine(...)
		local Output = {};
		for i, v in pairs{...} do
			if typeof(v) == 'table' then
				table.foreach(v, function(i, v)
					Output[i] = v;
				end)
			end
		end
		return Output
	end
	function IsStringEmpty(String)
		if type(String) == 'string' then
			return String:match'^%s+$' ~= nil or #String == 0 or String == '' or false;
		end
		return false
	end

	function NewDrawing(InstanceName)
		local Instance = Drawing.new(InstanceName);
		return (function(Properties)
			for i, v in pairs(Properties) do
				pcall(Set, Instance, i, v);
			end
			return Instance;
		end)
	end

	function Menu:AddMenuInstace(Name, Instance)
		if shared.MenuDrawingData.Instances[Name] ~= nil then
			shared.MenuDrawingData.Instances[Name]:Remove();
		end
		shared.MenuDrawingData.Instances[Name] = Instance;
		return Instance;
	end
	function Menu:UpdateMenuInstance(Name)
		local Instance = shared.MenuDrawingData.Instances[Name];
		if Instance ~= nil then
			return (function(Properties)
				for i, v in pairs(Properties) do
					-- print(Format('%s %s -> %s', Name, tostring(i), tostring(v)));
					pcall(Set, Instance, i, v);
				end
				return Instance;
			end)
		end
	end
	function Menu:GetInstance(Name)
		return shared.MenuDrawingData.Instances[Name];
	end

	function LineBox:Create(Properties)
		local Box = { Visible = true }; -- prevent errors not really though dont worry bout the Visible = true thing

		local Properties = Combine({
			Transparency = 1;
			Thickness = 1;
			Visible = true;
		}, Properties);

		Box['TopLeft'] = NewDrawing'Line'(Properties);
		Box['TopRight'] = NewDrawing'Line'(Properties);
		Box['BottomLeft'] = NewDrawing'Line'(Properties);
		Box['BottomRight'] = NewDrawing'Line'(Properties);

		function Box:Update(CF, Size, Color, Properties)
			if not CF or not Size then return end

			local TLPos, Visible1 = Camera:WorldToViewportPoint((CF * CFrame.new( Size.X,  Size.Y, 0)).p);
			local TRPos, Visible2 = Camera:WorldToViewportPoint((CF * CFrame.new(-Size.X,  Size.Y, 0)).p);
			local BLPos, Visible3 = Camera:WorldToViewportPoint((CF * CFrame.new( Size.X, -Size.Y, 0)).p);
			local BRPos, Visible4 = Camera:WorldToViewportPoint((CF * CFrame.new(-Size.X, -Size.Y, 0)).p);
			-- ## BEGIN UGLY CODE
			if Visible1 then
				Box['TopLeft'].Visible = true;
				Box['TopLeft'].Color = Color;
				Box['TopLeft'].From = Vector2.new(TLPos.X, TLPos.Y);
				Box['TopLeft'].To = Vector2.new(TRPos.X, TRPos.Y);
			else
				Box['TopLeft'].Visible = false;
			end
			if Visible2 then
				Box['TopRight'].Visible = true;
				Box['TopRight'].Color = Color;
				Box['TopRight'].From = Vector2.new(TRPos.X, TRPos.Y);
				Box['TopRight'].To = Vector2.new(BRPos.X, BRPos.Y);
			else
				Box['TopRight'].Visible = false;
			end
			if Visible3 then
				Box['BottomLeft'].Visible = true;
				Box['BottomLeft'].Color = Color;
				Box['BottomLeft'].From = Vector2.new(BLPos.X, BLPos.Y);
				Box['BottomLeft'].To = Vector2.new(TLPos.X, TLPos.Y);
			else
				Box['BottomLeft'].Visible = false;
			end
			if Visible4 then
				Box['BottomRight'].Visible = true;
				Box['BottomRight'].Color = Color;
				Box['BottomRight'].From = Vector2.new(BRPos.X, BRPos.Y);
				Box['BottomRight'].To = Vector2.new(BLPos.X, BLPos.Y);
			else
				Box['BottomRight'].Visible = false;
			end
			-- ## END UGLY CODE
			if Properties then
				GetTableData(Properties)(function(i, v)
					pcall(Set, Box['TopLeft'], i, v);
					pcall(Set, Box['TopRight'], i, v);
					pcall(Set, Box['BottomLeft'], i, v);
					pcall(Set, Box['BottomRight'], i, v);
				end)
			end
		end
		function Box:SetVisible(bool)
			pcall(Set, Box['TopLeft'], 'Visible', bool);
			pcall(Set, Box['TopRight'], 'Visible', bool);
			pcall(Set, Box['BottomLeft'], 'Visible', bool);
			pcall(Set, Box['BottomRight'], 'Visible', bool);
		end
		function Box:Remove()
			self:SetVisible(false);
			Box['TopLeft']:Remove();
			Box['TopRight']:Remove();
			Box['BottomLeft']:Remove();
			Box['BottomRight']:Remove();
		end

		return Box;
	end

	function CreateMenu(NewPosition) -- Create Menu
		local function FromHex(HEX)
			HEX = HEX:gsub('#', '');
			return Color3.fromRGB(tonumber('0x' .. HEX:sub(1, 2)), tonumber('0x' .. HEX:sub(3, 4)), tonumber('0x' .. HEX:sub(5, 6)));
		end

		local Colors = {
			Primary = {
				Main = FromHex'424242';
				Light = FromHex'6d6d6d';
				Dark = FromHex'1b1b1b';
			};
			Secondary = {
				Main = FromHex'e0e0e0';
				Light = FromHex'ffffff';
				Dark = FromHex'aeaeae';
			};
		};

		MenuLoaded = false;

		GetTableData(UIButtons)(function(i, v)
			v.Instance.Visible = false;
			v.Instance:Remove();
		end)
		GetTableData(Sliders)(function(i, v)
			v.Instance.Visible = false;
			v.Instance:Remove();
		end)

		UIButtons = {};
		Sliders = {};

		local BaseSize = Vector2.new(300, 580);
		local BasePosition = NewPosition or Vector2.new(Camera.ViewportSize.X / 8 - (BaseSize.X / 2), Camera.ViewportSize.Y / 2 - (BaseSize.Y / 2));

		Menu:AddMenuInstace('CrosshairX', NewDrawing'Line'{
			Visible = false;
			Color = Color3.new(0, 1, 0);
			Transparency = 1;
			Thickness = 1;
		});
		Menu:AddMenuInstace('CrosshairY', NewDrawing'Line'{
			Visible = false;
			Color = Color3.new(0, 1, 0);
			Transparency = 1;
			Thickness = 1;
		});

		delay(.025, function() -- since zindex doesnt exist
			Menu:AddMenuInstace('Main', NewDrawing'Square'{
				Size = BaseSize;
				Position = BasePosition;
				Filled = false;
				Color = Colors.Primary.Main;
				Thickness = 3;
				Visible = true;
			});
		end);
		Menu:AddMenuInstace('TopBar', NewDrawing'Square'{
			Position = BasePosition;
			Size = Vector2.new(BaseSize.X, 25);
			Color = Colors.Primary.Dark;
			Filled = true;
			Visible = true;
		});
		Menu:AddMenuInstace('TopBarTwo', NewDrawing'Square'{
			Position = BasePosition + Vector2.new(0, 25);
			Size = Vector2.new(BaseSize.X, 60);
			Color = Colors.Primary.Main;
			Filled = true;
			Visible = true;
		});
		Menu:AddMenuInstace('TopBarText', NewDrawing'Text'{
			Size = 25;
			Position = shared.MenuDrawingData.Instances.TopBarTwo.Position + Vector2.new(25, 15);
			Text = 'Unnamed ESP';
			Color = Colors.Secondary.Light;
			Visible = true;
		});
		Menu:AddMenuInstace('TopBarTextBR', NewDrawing'Text'{
			Size = 15;
			Position = shared.MenuDrawingData.Instances.TopBarTwo.Position + Vector2.new(BaseSize.X - 65, 40);
			Text = 'by ic3w0lf';
			Color = Colors.Secondary.Dark;
			Visible = true;
		});
		Menu:AddMenuInstace('Filling', NewDrawing'Square'{
			Size = BaseSize - Vector2.new(0, 85);
			Position = BasePosition + Vector2.new(0, 85);
			Filled = true;
			Color = Colors.Secondary.Main;
			Transparency= .5;
			Visible = true;
		});

		local CPos = 0;

		GetTableData(Options)(function(i, v)
			if typeof(v.Value) == 'boolean' and not IsStringEmpty(v.Text) and v.Text ~= nil then
				CPos = CPos + 25;
				local BaseSize = Vector2.new(BaseSize.X, 30);
				local BasePosition = shared.MenuDrawingData.Instances.Filling.Position + Vector2.new(30, v.Index * 25 - 10);
				UIButtons[#UIButtons + 1] = {
					Option = v;
					Instance = Menu:AddMenuInstace(Format('%s_Hitbox', v.Name), NewDrawing'Square'{
						Position = BasePosition - Vector2.new(30, 15);
						Size = BaseSize;
						Visible = false;
					});
				};
				Menu:AddMenuInstace(Format('%s_OuterCircle', v.Name), NewDrawing'Circle'{
					Radius = 10;
					Position = BasePosition;
					Color = Colors.Secondary.Light;
					Filled = true;
					Visible = true;
				});
				Menu:AddMenuInstace(Format('%s_InnerCircle', v.Name), NewDrawing'Circle'{
					Radius = 7;
					Position = BasePosition;
					Color = Colors.Secondary.Dark;
					Filled = true;
					Visible = v.Value;
				});
				Menu:AddMenuInstace(Format('%s_Text', v.Name), NewDrawing'Text'{
					Text = v.Text;
					Size = 20;
					Position = BasePosition + Vector2.new(20, -10);
					Visible = true;
					Color = Colors.Primary.Dark;
				});
			end
		end)
		GetTableData(Options)(function(i, v) -- just to make sure certain things are drawn before or after others, too lazy to actually sort table
			if typeof(v.Value) == 'number' then
				CPos = CPos + 25;

				local BaseSize = Vector2.new(BaseSize.X, 30);
				local BasePosition = shared.MenuDrawingData.Instances.Filling.Position + Vector2.new(0, CPos - 10);

				local Text = Menu:AddMenuInstace(Format('%s_Text', v.Name), NewDrawing'Text'{
					Text = v.Text;
					Size = 20;
					Position = BasePosition + Vector2.new(20, -10);
					Visible = true;
					Color = Colors.Primary.Dark;
				});
				local AMT = Menu:AddMenuInstace(Format('%s_AmountText', v.Name), NewDrawing'Text'{
					Text = tostring(v.Value);
					Size = 20;
					Position = BasePosition;
					Visible = true;
					Color = Colors.Primary.Dark;
				});
				local Line = Menu:AddMenuInstace(Format('%s_SliderLine', v.Name), NewDrawing'Line'{
					Transparency = 1;
					Color = Colors.Primary.Dark;
					Thickness = 3;
					Visible = true;
					From = BasePosition + Vector2.new(20, 20);
					To = BasePosition + Vector2.new(BaseSize.X - 10, 20);
				});
				CPos = CPos + 10;
				local Slider = Menu:AddMenuInstace(Format('%s_Slider', v.Name), NewDrawing'Circle'{
					Visible = true;
					Filled = true;
					Radius = 6;
					Color = Colors.Secondary.Dark;
					Position = BasePosition + Vector2.new(35, 20);
				})

				local CSlider = {Slider = Slider; Line = Line; Min = v.AllArgs[4]; Max = v.AllArgs[5]; Option = v};
				Sliders[#Sliders + 1] = CSlider;

				-- local Percent = (v.Value / CSlider.Max) * 100;
				-- local Size = math.abs(Line.From.X - Line.To.X);
				-- local Value = Size * (Percent / 100); -- this shit's inaccurate but fuck it i'm not even gonna bother fixing it

				Slider.Position = BasePosition + Vector2.new(40, 20);

				v.BaseSize = BaseSize;
				v.BasePosition = BasePosition;
				AMT.Position = BasePosition + Vector2.new(BaseSize.X - AMT.TextBounds.X - 10, -10)
			end
		end)
		GetTableData(Options)(function(i, v) -- just to make sure certain things are drawn before or after others, too lazy to actually sort table
			if typeof(v.Value) == 'EnumItem' then
				CPos = CPos + 30;

				local BaseSize = Vector2.new(BaseSize.X, 30);
				local BasePosition = shared.MenuDrawingData.Instances.Filling.Position + Vector2.new(0, CPos - 10);

				UIButtons[#UIButtons + 1] = {
					Option = v;
					Instance = Menu:AddMenuInstace(Format('%s_Hitbox', v.Name), NewDrawing'Square'{
						Size = Vector2.new(BaseSize.X, 20) - Vector2.new(30, 0);
						Visible = true;
						Transparency= .5;
						Position = BasePosition + Vector2.new(15, -10);
						Color = Colors.Secondary.Light;
						Filled = true;
					});
				};
				local Text = Menu:AddMenuInstace(Format('%s_Text', v.Name), NewDrawing'Text'{
					Text = v.Text;
					Size = 20;
					Position = BasePosition + Vector2.new(20, -10);
					Visible = true;
					Color = Colors.Primary.Dark;
				});
				local BindText = Menu:AddMenuInstace(Format('%s_BindText', v.Name), NewDrawing'Text'{
					Text = tostring(v.Value):match'%w+%.%w+%.(.+)';
					Size = 20;
					Position = BasePosition;
					Visible = true;
					Color = Colors.Primary.Dark;
				});

				Options[i].BaseSize = BaseSize;
				Options[i].BasePosition = BasePosition;
				BindText.Position = BasePosition + Vector2.new(BaseSize.X - BindText.TextBounds.X - 20, -10);
			end
		end)
		GetTableData(Options)(function(i, v) -- just to make sure certain things are drawn before or after others, too lazy to actually sort table
			if typeof(v.Value) == 'function' then
				local BaseSize = Vector2.new(BaseSize.X, 30);
				local BasePosition = shared.MenuDrawingData.Instances.Filling.Position + Vector2.new(0, CPos + (25 * v.AllArgs[4]) - 35);

				UIButtons[#UIButtons + 1] = {
					Option = v;
					Instance = Menu:AddMenuInstace(Format('%s_Hitbox', v.Name), NewDrawing'Square'{
						Size = Vector2.new(BaseSize.X, 20) - Vector2.new(30, 0);
						Visible = true;
						Transparency= .5;
						Position = BasePosition + Vector2.new(15, -10);
						Color = Colors.Secondary.Light;
						Filled = true;
					});
				};
				local Text = Menu:AddMenuInstace(Format('%s_Text', v.Name), NewDrawing'Text'{
					Text = v.Text;
					Size = 20;
					Position = BasePosition + Vector2.new(20, -10);
					Visible = true;
					Color = Colors.Primary.Dark;
				});

				-- BindText.Position = BasePosition + Vector2.new(BaseSize.X - BindText.TextBounds.X - 10, -10);
			end
		end)

		delay(.1, function()
			MenuLoaded = true;
		end);

		-- this has to be at the bottom cuz proto drawing api doesnt have zindex :triumph:
		Menu:AddMenuInstace('Cursor1', NewDrawing'Line'{
			Visible = false;
			Color = Color3.new(1, 0, 0);
			Transparency = 1;
			Thickness = 2;
		});
		Menu:AddMenuInstace('Cursor2', NewDrawing'Line'{
			Visible = false;
			Color = Color3.new(1, 0, 0);
			Transparency = 1;
			Thickness = 2;
		});
		Menu:AddMenuInstace('Cursor3', NewDrawing'Line'{
			Visible = false;
			Color = Color3.new(1, 0, 0);
			Transparency = 1;
			Thickness = 2;
		});
	end

	CreateMenu();

	shared.InputBeganCon = UserInputService.InputBegan:connect(function(input)
		if input.UserInputType.Name == 'MouseButton1' and Options.MenuOpen.Value then
			MouseHeld = true;
			local Bar = Menu:GetInstance'TopBar';
			local Values = {
				Bar.Position.X;
				Bar.Position.Y;
				Bar.Position.X + Bar.Size.X;
				Bar.Position.Y + Bar.Size.Y;
			}
			if MouseHoveringOver(Values) and not syn then -- disable dragging for synapse cuz idk why it breaks
				DraggingUI = false; -- also breaks for other exploits
				DragOffset = Menu:GetInstance'Main'.Position - GetMouseLocation();
			else
				for i, v in pairs(Sliders) do
					local Values = {
						v.Line.From.X - (v.Slider.Radius);
						v.Line.From.Y - (v.Slider.Radius);
						v.Line.To.X + (v.Slider.Radius);
						v.Line.To.Y + (v.Slider.Radius);
					};
					if MouseHoveringOver(Values) then
						DraggingWhat = v;
						Dragging = true;
						break
					end
				end
			end
		end
	end)
	shared.InputEndedCon = UserInputService.InputEnded:connect(function(input)
		if input.UserInputType.Name == 'MouseButton1' and Options.MenuOpen.Value then
			MouseHeld = false;
			for i, v in pairs(UIButtons) do
				local Values = {
					v.Instance.Position.X;
					v.Instance.Position.Y;
					v.Instance.Position.X + v.Instance.Size.X;
					v.Instance.Position.Y + v.Instance.Size.Y;
				};
				if MouseHoveringOver(Values) then
					v.Option();
					break -- prevent clicking 2 options
				end
			end
		elseif input.UserInputType.Name == 'Keyboard' then
			if Binding then
				BindedKey = input.KeyCode;
				Binding = false;
			elseif input.KeyCode == Options.MenuKey.Value or (input.KeyCode == Enum.KeyCode.Home and UserInputService:IsKeyDown(Enum.KeyCode.LeftControl)) then
				Options.MenuOpen();
			end
		end
	end)

	function ToggleMenu()
		if Options.MenuOpen.Value then
			GetTableData(shared.MenuDrawingData.Instances)(function(i, v)
				if OldData[v] then
					pcall(Set, v, 'Visible', true);
				end
			end)
		else
			-- GUIService:SetMenuIsOpen(false);
			GetTableData(shared.MenuDrawingData.Instances)(function(i, v)
				if v.Visible == true then
					OldData[v] = true;
					pcall(Set, v, 'Visible', false);
				end
			end)
		end
	end

	function CheckRay(Player, Distance, Position, Unit)
		local Pass = true;

		if Distance > 999 then return false; end

		local _Ray = Ray.new(Position, Unit * Distance);

		local List = {LocalPlayer.Character, Camera, Mouse.TargetFilter};

		for i,v in pairs(IgnoreList) do table.insert(List, v); end;

		local Hit = workspace:FindPartOnRayWithIgnoreList(_Ray, List);
		if Hit and not Hit:IsDescendantOf(Player.Character) then
			Pass = false;
			if Hit.Transparency >= .3 or not Hit.CanCollide and Hit.ClassName ~= Terrain then -- Detect invisible walls
				IgnoreList[#IgnoreList + 1] = Hit;
			end
		end

		return Pass;
	end

	function CheckPlayer(Player)
		if not Options.Enabled.Value then return false end

		local Pass = true;
		local Distance = 0;

		if Player ~= LocalPlayer and Player.Character then
			if not Options.ShowTeam.Value and Player.TeamColor == LocalPlayer.TeamColor then
				Pass = false;
			end

			local Head = Player.Character:FindFirstChild'Head';

			if Pass and Player.Character and Head then
				Distance = (Camera.CFrame.p - Head.Position).magnitude;
				if Options.VisCheck.Value then
					Pass = CheckRay(Player, Distance, Camera.CFrame.p, (Head.Position - Camera.CFrame.p).unit);
				end
				if Distance > Options.MaxDistance.Value then
					Pass = false;
				end
			end
		else
			Pass = false;
		end

		return Pass, Distance;
	end

	function UpdatePlayerData()
		if (tick() - LastRefresh) > (Options.RefreshRate.Value / 1000) then
			LastRefresh = tick();
			for i, v in pairs(Players:GetPlayers()) do
				local Data = shared.PlayerData[v.Name] or { Instances = {} };

				Data.Instances['Box'] = Data.Instances['Box'] or LineBox:Create{Thickness = 3};
				Data.Instances['Tracer'] = Data.Instances['Tracer'] or NewDrawing'Line'{
					Transparency = 1;
					Thickness = 2;
				}
				Data.Instances['HeadDot'] = Data.Instances['HeadDot'] or NewDrawing'Circle'{
					Filled = true;
					NumSides = 30;
				}
				Data.Instances['NameTag'] = Data.Instances['NameTag'] or NewDrawing'Text'{
					Size = Options.TextSize.Value;
					Center = true;
					Outline = Options.TextOutline.Value;
					Visible = true;
				};
				Data.Instances['DistanceHealthTag'] = Data.Instances['DistanceHealthTag'] or NewDrawing'Text'{
					Size = Options.TextSize.Value - 1;
					Center = true;
					Outline = Options.TextOutline.Value;
					Visible = true;
				};

				local NameTag = Data.Instances['NameTag'];
				local DistanceTag = Data.Instances['DistanceHealthTag'];
				local Tracer = Data.Instances['Tracer'];
				local HeadDot = Data.Instances['HeadDot'];
				local Box = Data.Instances['Box'];

				local Pass, Distance = CheckPlayer(v);

				if Pass and v.Character then
					Data.LastUpdate = tick();
					local Humanoid = v.Character:FindFirstChildOfClass'Humanoid';
					local Head = v.Character:FindFirstChild'Head';
					local HumanoidRootPart = v.Character:FindFirstChild'HumanoidRootPart';
					if v.Character ~= nil and Head then
						local ScreenPosition, Vis = Camera:WorldToViewportPoint(Head.Position);
						if Vis then
							local Color = v.TeamColor == LocalPlayer.TeamColor and Green or Red;

							local ScreenPositionUpper = Camera:WorldToViewportPoint(Head.CFrame * CFrame.new(0, Head.Size.Y, 0).p);
							local Scale = Head.Size.Y / 2;

							if Options.ShowName.Value then
								NameTag.Visible = true;
								NameTag.Text = v.Name;
								NameTag.Size = Options.TextSize.Value;
								NameTag.Outline = Options.TextOutline.Value;
								NameTag.Position = Vector2.new(ScreenPositionUpper.X, ScreenPositionUpper.Y);
								NameTag.Color = Color;
								if Drawing.Fonts then -- CURRENTLY SYNAPSE ONLY :MEGAHOLY:
									NameTag.Font = Drawing.Fonts.UI;
								end
							else
								NameTag.Visible = false;
							end
							if Options.ShowDistance.Value or Options.ShowHealth.Value then
								DistanceTag.Visible = true;
								DistanceTag.Size = Options.TextSize.Value - 1;
								DistanceTag.Outline = Options.TextOutline.Value;
								DistanceTag.Color = Color3.new(1, 1, 1);
								if Drawing.Fonts then -- CURRENTLY SYNAPSE ONLY :MEGAHOLY:
									NameTag.Font = Drawing.Fonts.UI;
								end

								local Str = '';

								if Options.ShowDistance.Value then
									Str = Str .. Format('[%d] ', Distance);
								end
								if Options.ShowHealth.Value and Humanoid then
									Str = Str .. Format('[%d/100]', Humanoid.Health / Humanoid.MaxHealth * 100);
								end

								DistanceTag.Text = Str;
								DistanceTag.Position = Vector2.new(ScreenPositionUpper.X, ScreenPositionUpper.Y) + Vector2.new(0, NameTag.Size);
							else
								DistanceTag.Visible = false;
							end
							if Options.ShowDot.Value then
								local Top = Camera:WorldToViewportPoint((Head.CFrame * CFrame.new(0, Scale, 0)).p);
								local Bottom = Camera:WorldToViewportPoint((Head.CFrame * CFrame.new(0, -Scale, 0)).p);
								local Radius = (Top - Bottom).y;

								HeadDot.Visible = true;
								HeadDot.Color = Color;
								HeadDot.Position = Vector2.new(ScreenPosition.X, ScreenPosition.Y);
								HeadDot.Radius = Radius;
							else
								HeadDot.Visible = false;
							end
							if Options.ShowTracers.Value then
								Tracer.Visible = true;
								Tracer.From = Vector2.new(Camera.ViewportSize.X / 2, Camera.ViewportSize.Y);
								Tracer.To = Vector2.new(ScreenPosition.X, ScreenPosition.Y);
								Tracer.Color = Color;
							else
								Tracer.Visible = false;
							end
							if Options.ShowBoxes.Value and HumanoidRootPart then
								Box:Update(HumanoidRootPart.CFrame, Vector3.new(2, 3, 0) * (Scale * 2), Color);
							else
								Box:SetVisible(false);
							end
						else
							NameTag.Visible = false;
							DistanceTag.Visible = false;
							Tracer.Visible = false;
							HeadDot.Visible = false;

							Box:SetVisible(false);
						end
					end
				else
					NameTag.Visible = false;
					DistanceTag.Visible = false;
					Tracer.Visible = false;
					HeadDot.Visible = false;

					Box:SetVisible(false);
				end

				shared.PlayerData[v.Name] = Data;
			end
		end
	end

	function Update()
		for i, v in pairs(shared.PlayerData) do
			if not Players:FindFirstChild(tostring(i)) then
				GetTableData(v.Instances)(function(i, obj)
					obj.Visible = false;
					obj:Remove();
					v.Instances[i] = nil;
				end)
				shared.PlayerData[i] = nil;
			end
		end

		local CX = Menu:GetInstance'CrosshairX';
		local CY = Menu:GetInstance'CrosshairY';
		if Options.Crosshair.Value then
			CX.Visible = true;
			CY.Visible = true;

			CX.To = Vector2.new((Camera.ViewportSize.X / 2) - 8, (Camera.ViewportSize.Y / 2));
			CX.From = Vector2.new((Camera.ViewportSize.X / 2) + 8, (Camera.ViewportSize.Y / 2));
			CY.To = Vector2.new((Camera.ViewportSize.X / 2), (Camera.ViewportSize.Y / 2) - 8);
			CY.From = Vector2.new((Camera.ViewportSize.X / 2), (Camera.ViewportSize.Y / 2) + 8);
		else
			CX.Visible = false;
			CY.Visible = false;
		end

		if Options.MenuOpen.Value and MenuLoaded then
			local MLocation = GetMouseLocation();
			shared.MenuDrawingData.Instances.Main.Color = Color3.fromHSV(tick() * 24 % 255/255, 1, 1);
			local MainInstance = Menu:GetInstance'Main';
			local Values = {
				MainInstance.Position.X;
				MainInstance.Position.Y;
				MainInstance.Position.X + MainInstance.Size.X;
				MainInstance.Position.Y + MainInstance.Size.Y;
			};
			if MainInstance and MouseHoveringOver(Values) then
				Debounce.CursorVis = true;
				-- GUIService:SetMenuIsOpen(true);
				Menu:UpdateMenuInstance'Cursor1'{
					Visible = true;
					From = Vector2.new(MLocation.x, MLocation.y);
					To = Vector2.new(MLocation.x + 5, MLocation.y + 6);
				}
				Menu:UpdateMenuInstance'Cursor2'{
					Visible = true;
					From = Vector2.new(MLocation.x, MLocation.y);
					To = Vector2.new(MLocation.x, MLocation.y + 8);
				}
				Menu:UpdateMenuInstance'Cursor3'{
					Visible = true;
					From = Vector2.new(MLocation.x, MLocation.y + 6);
					To = Vector2.new(MLocation.x + 5, MLocation.y + 5);
				}
			else
				if Debounce.CursorVis then
					Debounce.CursorVis = false;
					-- GUIService:SetMenuIsOpen(false);
					Menu:UpdateMenuInstance'Cursor1'{Visible = false};
					Menu:UpdateMenuInstance'Cursor2'{Visible = false};
					Menu:UpdateMenuInstance'Cursor3'{Visible = false};
				end
			end
			if MouseHeld then
				if Dragging then
					DraggingWhat.Slider.Position = Vector2.new(math.clamp(MLocation.X, DraggingWhat.Line.From.X, DraggingWhat.Line.To.X), DraggingWhat.Slider.Position.Y);
					local Percent = (DraggingWhat.Slider.Position.X - DraggingWhat.Line.From.X) / ((DraggingWhat.Line.To.X - DraggingWhat.Line.From.X));
					local Value = CalculateValue(DraggingWhat.Min, DraggingWhat.Max, Percent);
					DraggingWhat.Option(Value);
				elseif DraggingUI then
					Debounce.UIDrag = true;
					local Main = Menu:GetInstance'Main';
					local MousePos = GetMouseLocation();
					Main.Position = MousePos + DragOffset;
				end
			else
				Dragging = false;
				if DraggingUI and Debounce.UIDrag then
					Debounce.UIDrag = false;
					DraggingUI = false;
					CreateMenu(Menu:GetInstance'Main'.Position);
				end
			end
			if not Debounce.Menu then
				Debounce.Menu = true;
				ToggleMenu();
			end
		elseif Debounce.Menu and not Options.MenuOpen.Value then
			Debounce.Menu = false;
			ToggleMenu();
		end
	end

	RunService:UnbindFromRenderStep(GetDataName);
	RunService:UnbindFromRenderStep(UpdateName);

	RunService:BindToRenderStep(GetDataName, 1, UpdatePlayerData);
	RunService:BindToRenderStep(UpdateName, 1, Update);
end)
