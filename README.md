loadstring(game:HttpGet("https://raw.githubuserc
ontent.com/thimaiz/Evomon/main/hack.lua"))()
local gui = Instance.new("ScreenGui", game.CoreGui)
local f = Instance.new("Frame", gui)
f.Size, f.Position, f.Draggable, f.BackgroundColor3 = UDim2.new(0,150,0,200), UDim2.new(0,0,0,0), true, Color3.fromRGB(30,30,30)

local function btn(txt, y, cb)
    local b = Instance.new("TextButton", f)
    b.Size, b.Position, b.Text, b.BackgroundColor3 = UDim2.new(1,0,0,35), UDim2.new(0,0,0,y), txt, Color3.fromRGB(200,0,0)
    b.TextColor3, b.Font = Color3.new(1,1,1), Enum.Font.SourceSansBold
    b.MouseButton1Click:Connect(cb)
end

btn("AUTO CATCH", 0, function()
    while wait(1.5) do
        pcall(function()
            for _,v in pairs(workspace:GetChildren()) do
                if v:FindFirstChild("Humanoid") and v.Humanoid.Health>0 and game.Players.LocalPlayer.Character then
                    game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,0,2)
                end
            end
        end)
    end
end)

btn("AUTO EVOLVE", 40, function()
    while wait(3) do
        pcall(function()
            game.ReplicatedStorage.Remotes.Evolve:FireServer("Evolve","Best")
        end)
    end
end)

btn("SPEED 120", 80, function()
    pcall(function()
        game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = 120
    end)
end)

btn("JUMP 200", 120, function()
    pcall(function()
        game.Players.LocalPlayer.Character.Humanoid.JumpPower = 200
    end)
end)

btn("CLOSE", 160, function() gui:Destroy() end)
