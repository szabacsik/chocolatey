# chocolatey
My Chocolatey package management configuration for automated and unattended installation of my development tools and stuff on windows.  

> Chocolatey is a software management solution unlike anything else you've ever experienced on Windows. Chocolatey brings the concepts of true package management to allow you to version things, manage dependencies and installation order, better inventory management, and other features.  

## Guide

Create folders and set environment variables  
```cmd
mkdir c:\code\nodejs
mkdir c:\code\perl
setx ChocolateyInstall "C:\choco"
setx /m ChocolateyInstall "C:\choco"
setx ChocolateyToolsLocation "C:\choco\tools"
setx /m ChocolateyToolsLocation "C:\choco\tools"
exit
```

Install chocolatey  
```cmd
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"
choco install packages.config --yes --prerelease --allow-empty-checksums
```
<https://chocolatey.org/install>

Install software packages  
```cmd
choco install packages.config --yes --prerelease --allow-empty-checksums
```
<https://chocolatey.org/docs/commandsinstall#packagesconfig>

### Notes

`--package-parameters=VALUE`
PackageParameters - Parameters to pass to the package. Defaults to unspecified.  

`--install-arguments=VALUE`
InstallArguments - Install Arguments to pass to the native installer in the package. Defaults to unspecified.  

<https://stackoverflow.com/questions/37803877/how-do-i-pass-parameters-to-the-installer-in-a-chocolatey-package>

```cmd
C:\Windows\System32\msiexec.exe /i "C:\Users\vagrant\AppData\Local\Temp\chocolatey\StrawberryPerl\5.30.0.1\strawberry-perl-5.30.0.1-64bit.msi" /qn /norestart TARGETDIR=C:\code\perl INSTALLDIR=C:\code\perl /L*V "c:\msiexec.log"
```
