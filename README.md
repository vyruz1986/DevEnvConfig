# DevEnvConfig

A repository for hosting various config files, installer-commands, etc for setting up my development environment

## Windows config

Make sure you have Windows 11 22H2 or higher installed.

## Installers

Install all the tools:

```powershell
winget install --id=Microsoft.VisualStudioCode -e  ; winget install --id=Git.Git -e  ; winget install --id=GitExtensionsTeam.GitExtensions -e  ; winget install --id=alexx2000.DoubleCommander -e  ; winget install --id=Microsoft.dotnet -e  ; winget install --id=Perforce.P4Merge -e  ; winget install --id=WinMerge.WinMerge -e  ; winget install --id=Docker.DockerDesktop -e  ; winget install --id=7zip.7zip -e  ; winget install --id=Canonical.Ubuntu.2204 -e
```

This will install:

- Git
- Visual Studio Code
- GitExtensions
- Double Commander
- .NET Core SDK
- P4Merge (Perforce visual merge tool)
- Docker Desktop
- 7Zip
- Ubuntu 22.04 LTS
  
Install CaskaydiaCove Nerd Font font:

Download CaskaydiaCove Nerd Font from https://www.nerdfonts.com/font-downloads

## Settings

### Windows services

Make sure the ssh-agent service always starts automatically by running the following command in an **admin** command prompt

```powershell
Get-Service ssh-agent | Set-Service -StartupType Automatic
Get-Service ssh-agent | Start-Service
```

### Generate SSH key and add it to ssh-agent

```powershell
ssh-keygen
ssh-add .\.ssh\id_rsa
```

### Windows terminal

Open the settings and paste the following in the `defaults` section:

```json
{
  "acrylicOpacity": 0.5,
  "backgroundImage": "https://media.giphy.com/media/l2QE862DCBR8tAh9u/giphy.gif",
  "backgroundImageOpacity": 0.7,
  "backgroundImageStretchMode": "fill",
  "closeOnExit": true,
  "colorScheme": "Dracula",
  "cursorColor": "#FFFFFF",
  "cursorShape": "bar",
  "fontFace": "Cascadia Code PL",
  "fontSize": 14,
  "historySize": 9001,
  "padding": "12, 12, 0, 0",
  "snapOnInput": true,
  "startingDirectory": "%USERPROFILE%",
  "useAcrylic": true
}
```

And the following in the `themes` section:

```json
[
  {
    "name": "Dracula",
    "background": "#272935",
    "black": "#21222C",
    "blue": "#BD93F9",
    "cyan": "#8BE9FD",
    "foreground": "#F8F8F2",
    "green": "#50FA7B",
    "purple": "#FF79C6",
    "red": "#FF5555",
    "white": "#F8F8F2",
    "yellow": "#FFB86C",
    "brightBlack": "#6272A4",
    "brightBlue": "#D6ACFF",
    "brightCyan": "#A4FFFF",
    "brightGreen": "#69FF94",
    "brightPurple": "#FF92DF",
    "brightRed": "#FF6E6E",
    "brightWhite": "#F8F8F2",
    "brightYellow": "#FFFFA5"
  }
]
```

And the following in the `keyBindings` section:

```json
[
  { "command": "closeTab", "keys": "ctrl+w" },
  { "command": "newTab", "keys": "ctrl+t" },
  { "command": "openNewTabDropdown", "keys": "ctrl+r" }
]
```

### Git

Run the following commands to configure git accordingly:

```PowerShell
git config --global user.name "Alex Goris"
git config --global user.email "alex.goris@fastlikehell.com"
git config --global merge.tool p4merge
git config --global diff.tool p4merge
git config --global difftool.p4merge.cmd '\"C:/Program Files/Perforce/p4merge.exe\" \"$LOCAL\" \"$REMOTE\"'
git config --global mergetool.p4merge.cmd '\"C:/Program Files/Perforce/p4merge.exe\" \"$BASE\" \"$LOCAL\" \"$REMOTE\" \"$MERGED\"'
```

### Visual Studio Code

Install extensions by running the commands below in PowerShell (non-admin) prompt:

```powersehll
code --install-extension ban.spellright
code --install-extension DavidAnson.vscode-markdownlint
code --install-extension dracula-theme.theme-dracula
code --install-extension eamodio.gitlens
code --install-extension esbenp.prettier-vscode
code --install-extension heaths.vscode-guid
code --install-extension KnisterPeter.vscode-commitizen
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-dotnettools.csharp
code --install-extension ms-vscode-remote.remote-wsl
code --install-extension ms-vscode.cpptools
code --install-extension ms-vscode.powershell
code --install-extension ms-vscode.vscode-typescript-tslint-plugin
code --install-extension msjsdiag.debugger-for-chrome
code --install-extension platformio.platformio-ide
code --install-extension esbenp.prettier-vscode
```

Disable the following extensions globally, they only need to be enabled in their corresponding workspaces:

- PlatformIO IDE

Press F1, and select `Preferences: Open Settings (JSON)`. Paste the following into the settings file:

```json
{
  "editor.tabSize": 3,
  "git.autofetch": true,
  "editor.detectIndentation": false,
  "git.confirmSync": false,
  "breadcrumbs.enabled": true,
  "spellright.language": ["en"],
  "spellright.documentTypes": ["markdown", "latex"],
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "editor.formatOnPaste": true,
  "editor.formatOnSave": true,
  "editor.fontFamily": "Cascadia Code PL, Consolas, 'Courier New', monospace",
  "editor.fontLigatures": true,
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "editor.fontSize": 14,
  "terminal.integrated.shell.windows": "C:\\Program Files\\PowerShell\\7\\pwsh.exe",
  "workbench.startupEditor": "newUntitledFile",
  "omnisharp.enableEditorConfigSupport": true,
  "workbench.colorTheme": "Dracula"
}
```
