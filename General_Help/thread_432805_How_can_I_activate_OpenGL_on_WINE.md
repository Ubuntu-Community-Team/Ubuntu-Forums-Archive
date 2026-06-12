---
title: "How can I activate OpenGL on WINE??"
date: 2007-05-04
forum: General Help
---

### Post by cnr437 on 2007-05-04
How can I activate OpenGL on Wine in Ubuntu 6.10 Edgy Eft??? I need to run Catia on Wine but It errors that "No certified OpenGL library has been found.Check your system installation." and screen shot is below;

[http://img.resimupload.com/r19/resim_927915940.png]("http://img.resimupload.com/r19/resim_927915940.png")


And WINE outputs these;
```
caner@ubuntu:~$ wine '/home/caner/.wine/drive_c/Program Files/Dassault Systemes/B16/intel_a/code/bin/CNEXT.exe'
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:advapi:EnumServicesStatusA 0x173100 type=30 state=1 0x33f2cc 168 0x33f534 0x33f538 0x33f53c
fixme:advapi:EnumServicesStatusA 0x173100 type=30 state=1 0x33f5d0 168 0x33f838 0x33f83c 0x33f840
fixme:advapi:EnumServicesStatusA 0x173100 type=30 state=1 0x33f864 168 0x33facc 0x33fad0 0x33fad4
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\Program Files\\Dassault Systemes\\B16\\intel_a\\code\\bin\\CNEXT.exe" failed with error 1813
err:ole:CoGetClassObject class {cb472525-5c11-11d3-a6b5-00105ac594f0} not registered
err:ole:CoGetClassObject no class object {cb472525-5c11-11d3-a6b5-00105ac594f0} could be created for context 0x1
fixme:imm:ImmGetDefaultIMEWnd (0x1003a - (nil) 0x1638c0 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x1003a - 0x100a0 0x1638c0 ): semi-stub
wine: Unhandled exception 0x80000003 at address 0x7b83cb93 (thread 0009), starting debugger...
caner@ubuntu:~$ 

```

After that it immediately closes Catia's window and OpenGL error message.

Please pay attention to help me about this topic :confused: :(

---

### Post by cnr437 on 2007-05-04
someone??

---

### Post by angryfirelord on 2007-05-04
Simply add the **--enable-opengl** tag at the end of your command.

It would look like this:
```
caner@ubuntu:~$ wine "/home/caner/.wine/drive_c/Program Files/Dassault Systemes/B16/intel_a/code/bin/CNEXT.exe" --enable-opengl
```

---

### Post by cnr437 on 2007-05-04
It doesn't work...there is the same warning message :(. I tried to add;
"engine 1" or "engine 2" end of code but it does not work too...

My Wine version is 0.9.36...but I didnt compile WineX and I dont think to buy Cedega for only easy OpenGL supporting, There should be a way to enable opengl on wine...:confused:

---

### Post by RobinOfSweden on 2007-05-05
Indeed, though i have the same problem i think my lies in some error during my install on my feisty 64. I receive the same error message as you and i can only use D3D.

I also tried the above tips but it ends as soon as it boots so no luck there.
i have read some issues is in FrameRate and that could be the reason but they never said anything about how they fixed it! such a shame! Will try to continue to search for a possible solution. (i am usualy reporting in at the thread "WoW + Opengl + Nvidia 7600GT doesn't work" it is for 32 bit however since the error seems to be the same i think its not 32-64 issues but framerate settings on the game or xorg.conf)

---

