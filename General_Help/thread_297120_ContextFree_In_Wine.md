---
title: "ContextFree In Wine"
date: 2006-11-10
forum: General Help
---

### Post by OrganicPanda on 2006-11-10
Hey I recently discovered a really cool program called [ContextFree]("http://www.contextfreeart.org/") Which is availible for Win/Mac/*Nix, the only problem is only the Win/Mac versions have a GUI which is a must have for me so I'm trying to run the Windows version under Wine and I'm getting:

```

panda@panda-desktop:~$ wine "/home/panda/.wine/c/Program Files/OzoneSoft/ContextFree/ContextFree.exe"
fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x337b0c
err:module:LdrInitializeThunk "MSVCR80.dll" failed to initialize, aborting
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\OzoneSoft\\ContextFree\\ContextFree.exe" failed, status c0000142
panda@panda-desktop:~$

```

It brings up a dialougue box saying:

```

[ Microsoft Visual C++ Runtime Library ]

Runtime Error!

Program: C:\Program Files\OzoneSoft\ContextFree\ContextFree.exe

R6034
An application has made an attempt to load the C runtime library incorrectly.
Please contact the application's support team for more information.

[ OK ]

```

Then exits, The only thing mentionable is that the DLL it is trying to use is in the same directory as the program so it's not missing or anything, I've tried different versions with no luck, Can anybody prehaps help me solve this - I don't want to have to use windows or the terminal, I've got nothing against the terminal but this is a very graphical program. anyway I'm rambling, cheers.

---

