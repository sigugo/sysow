# Setting up a usable CLI environment on Windows 

## Windows Terminal
Open CMD as Adminstrator
``` cmd
winget install Microsoft.WindowsTerminal

```

Pin to taskbar, in the terminal CTRL+Click new window now opens admin prompts

## Oh-my-Posh

### Install
```
winget install JanDeDobbeleer.OhMyPosh -s winget
```
To get the nerd fonts start an elevated powershell
```
oh-my-posh font install
```
Change the Windows Terminal configuration to use one of the Nerd Fonts

### Configure for Powershell

Start powershell, then use the follwing commands to generate and edit a profile configuration.
``` ps1
New-Item -Path $PROFILE -Type File -Force
notepad $PROFILE
```

Write the following contents into this file.
``` ps1
$ENV:PATH="$ENV:PATH;C:\msys64\usr\bin;$HOME/.cargo/bin"
oh-my-posh init pwsh | Invoke-Expression
Set-Alias vim nvim
```
Restart Windows Terminal / Powershell for this to take effect.

## Neovim

### Install Dependencies and Program
Open the shell as a regular user
```
winget install Git.Git
winget install OpenJS.NodeJS
winget install MSYS2.MSYS2
winget install nvim-nightly --forced
```

Start Msys2 and install gcc
`pacman -S gcc`


### Set up a kickstart nvim configuration
Restart powershell.
Edit the main nvim config file `nvim $HOME/AppData/Local/nvim/init.lua`
Paste the contents from `https://raw.githubusercontent.com/nvim-lua/kickstart.nvim/master/init.lua`, writequit and restart nvim.

## Install Modern Cli utilities

### Dependencies
``` 
winget install Microsoft.VisualStudio.2022.BuildTools
winget install Rustlang.Rustup
```

### Tools
```
cargo install ripgrep
`
