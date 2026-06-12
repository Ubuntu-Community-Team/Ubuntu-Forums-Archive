---
title: "Problem with Wine"
date: 2007-05-19
forum: General Help
---

### Post by Spectre31337 on 2007-05-19
Having recently converted over to Ubuntu Full time (though I have been using it for over a year) I have realized that I do need windows for an obscure reason. I race RC cars and in order to tune the car I need a program I have been using Wine with success for some time however when I try to install the software this is the issue I get

spectre31337@spec:~$ wine Desktop/CastleLinkInstall_225_2.exe 
fixme:process:IsWow64Process (0xffffffff 0x33fce8) stub!
Usage:
  Install a product:
    msiexec {package|productcode} [property]
    msiexec /i {package|productcode} [property]
    msiexec /a package [property]
  Repair an installation:
    msiexec /f[p|o|e|d|c|a|u|m|s|v] {package|productcode}
  Uninstall a product:
    msiexec /x {package|productcode} [property]
  Advertise a product:
    msiexec /j[u|m] package [/t transform] [/g languageid]
    msiexec {u|m} package [/t transform] [/g languageid]
  Apply a patch:
    msiexec /p patchpackage [property]
    msiexec /p patchpackage /a package [property]
  Modifiers for above operations:
    msiexec /l[*][i|w|e|a|r|u|c|m|o|p|v|][+|!] logfile
    msiexec /q{|n|b|r|f|n+|b+|b-}
  Register a module:
    msiexec /y module
  Unregister a module:
    msiexec /z module
  Display usage and copyright:
    msiexec {/h|/?}
NOTE: Product code on commandline unimplemented as of yet


THanks for your help //Spec

---

