# AOAOAO
no
--// Orion Style UI (Delta Executable)

local ScreenGui = Instance.new("ScreenGui")
local Main = Instance.new("Frame")
local KeyFrame = Instance.new("Frame")
local Loading = Instance.new("Frame")

ScreenGui.Parent = game.CoreGui

--// Loading Screen
Loading.Size = UDim2.new(1,0,1,0)
Loading.BackgroundColor3 = Color3.fromRGB(20,20,20)
Loading.Parent = ScreenGui

local LoadingText = Instance.new("TextLabel")
LoadingText.Text = "Loading..."
LoadingText.Size = UDim2.new(1,0,1,0)
LoadingText.TextColor3 = Color3.new(1,1,1)
LoadingText.BackgroundTransparency = 1
LoadingText.Parent = Loading

task.wait(2)
Loading:Destroy()

--// Key System
KeyFrame.Size = UDim2.new(0,300,0,200)
KeyFrame.Position = UDim2.new(0.5,-150,0.5,-100)
KeyFrame.BackgroundColor3 = Color3.fromRGB(30,30,30)
KeyFrame.Parent = ScreenGui

local Box = Instance.new("TextBox")
Box.PlaceholderText = "Enter Key (2525)"
Box.Size = UDim2.new(0.8,0,0,40)
Box.Position = UDim2.new(0.1,0,0.3,0)
Box.Parent = KeyFrame

local Button = Instance.new("TextButton")
Button.Text = "Submit"
Button.Size = UDim2.new(0.8,0,0,40)
Button.Position = UDim2.new(0.1,0,0.6,0)
Button.Parent = KeyFrame

--// Main UI
Main.Size = UDim2.new(0,500,0,300)
Main.Position = UDim2.new(0.5,-250,0.5,-150)
Main.BackgroundColor3 = Color3.fromRGB(40,40,40)
Main.Visible = false
Main.Parent = ScreenGui

local Title = Instance.new("TextLabel")
Title.Text = "Orion UI"
Title.Size = UDim2.new(1,0,0,40)
Title.BackgroundTransparency = 1
Title.TextColor3 = Color3.new(1,1,1)
Title.Parent = Main

--// Toggle Function
local function createToggle(name, yPos)
    local Frame = Instance.new("Frame")
    Frame.Size = UDim2.new(0.8,0,0,30)
    Frame.Position = UDim2.new(0.1,0,0,yPos)
    Frame.BackgroundColor3 = Color3.fromRGB(60,60,60)
    Frame.Parent = Main

    local Label = Instance.new("TextLabel")
    Label.Text = name
    Label.Size = UDim2.new(0.7,0,1,0)
    Label.BackgroundTransparency = 1
    Label.TextColor3 = Color3.new(1,1,1)
    Label.Parent = Frame

    local Toggle = Instance.new("TextButton")
    Toggle.Size = UDim2.new(0,50,0,20)
    Toggle.Position = UDim2.new(0.75,0,0.2,0)
    Toggle.BackgroundColor3 = Color3.fromRGB(100,100,100)
    Toggle.Text = ""
    Toggle.Parent = Frame

    local state = false

    Toggle.MouseButton1Click:Connect(function()
        state = not state
        Toggle.BackgroundColor3 = state and Color3.fromRGB(0,255,0) or Color3.fromRGB(100,100,100)
        print(name .. ":", state and "ON" or "OFF")
    end)
end

--// Toggles (Blobman All)
createToggle("All Grab", 60)
createToggle("All Throw", 100)
createToggle("All Bring", 140)
createToggle("All Kick (Others)", 180)
createToggle("Destroy Server", 220)
createToggle("Force Kick (Others)", 260)

--// Key Check
Button.MouseButton1Click:Connect(function()
    if Box.Text == "2525" then
        KeyFrame:Destroy()
        Main.Visible = true
    else
        Box.Text = "Wrong Key"
    end
end)
