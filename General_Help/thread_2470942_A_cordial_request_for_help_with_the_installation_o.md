---
title: "A cordial request for help with the installation of the Compatible Wine Emulator"
date: 2022-01-17
forum: General Help
---

### Post by luke1608 on 2022-01-17
A cordial request for help with the installation of the Compatible Wine Emulator for Visual Studio + NetFramework.

Hello, please send me a support. I need to install the Wine Emulator. Compatible with the entire library - the one on which I run NetFramework from version 2.0 to version 4.8. And Visual Studio from the oldest to the latest version.

Is Emulator Wine - recommended not only for running Games, but also for programming language applications - such as Net Framework and Visual Studio?

I need an emulator to run Visual Studio, all Versions, and Net Framework all Versions for me. Is there such an Emulator? 

I don't need an emulator to run Linux Ubuntu Games.

I have Linux Ubuntu on USB. Can I go further or do I need to install to an internal SSD?

---

### Post by TheFu on 2022-01-18
WINE only works for very specific needs. The best answers for any specific program will be at the WineHQ website.
I'd guess only about 20% of Windows programs work under WINE. Most won't be install-n-run. Each will need specific "winetricks" to work and those winetricks are tied to the exact version of WINE and the exact version of the program you want to run. Even then, expect 20% of the program not to work, ever.

If you are stubborn and have time, you can probably get more working than I in WINE.
If you are not stubborn and just want things to work, load up Windows inside a virtual machine and run all those programs there 
OR
setup a dual boot Windows machine to run those Windows-only programs.

I spent about a month back in 2012 to get Quicken working under WINE.  When the next release of Quicken came, it didn't work. I spent a week trying to get it working under WINE and failed.  Since then, I've used Windows in a VM for any programs that need MS-Windows.

It is all about trading time+effort for simplicity.

There is a vscode that runs on Linux.  I don't know what "NetFramework" is, but there are DotNet and Mono frameworks for native Linux if you are coding in C# or some other MSFT language.

---

