---
title: "Can Catia works on WINE?"
date: 2007-05-03
forum: General Help
---

### Post by cnr437 on 2007-05-03
I tried to run CATIA on WINE (version 0.9.36) in Ubuntu 6.10 Edgy Eft but I got two error messages about licence and OpenGL and some error outputs from WINE in terminal.

Outputs of WINE
```
caner@ubuntu:~$ wine '/home/caner/Documents/Dassault Systemes/B16/intel_a/code/bin/CNEXT.exe' 
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:advapi:EnumServicesStatusA 0x173050 type=30 state=1 0x33f2cc 168 0x33f534 0x33f538 0x33f53c
fixme:advapi:EnumServicesStatusA 0x1730a0 type=30 state=1 0x33f5d0 168 0x33f838 0x33f83c 0x33f840
fixme:advapi:EnumServicesStatusA 0x1730a0 type=30 state=1 0x33f864 168 0x33facc 0x33fad0 0x33fad4
err:ole:TLB_ReadTypeLib Loading of typelib L"Z:\\home\\caner\\Documents\\Dassault Systemes\\B16\\intel_a\\code\\bin\\CNEXT.exe" failed with error 1813
err:ole:CoGetClassObject class {cb472525-5c11-11d3-a6b5-00105ac594f0} not registered
err:ole:CoGetClassObject no class object {cb472525-5c11-11d3-a6b5-00105ac594f0} could be created for context 0x1
fixme:imm:ImmGetDefaultIMEWnd (0x10038 - (nil) 0x163b50 ): semi-stub
fixme:imm:ImmGetDefaultIMEWnd (0x10038 - 0x1007a 0x163b50 ): semi-stub
err:x11drv:X11DRV_CreateWindow invalid window height -22
```

After these, Catia run but with 2 error alert boxes as like here;
[http://img.resimupload.com/r22/resim_374915717.png]("http://img.resimupload.com/r22/resim_374915717.png")

What is mean “No certified OpenGL library”??? If I haven't certified OpenGL lib.,from where can I get it or them??? It is really important for me to solve these problem which is about that Catia runs on WINE in Ubuntu Edgy Eft distribition, I don't want to return to using windows xp. Also I heard about Dassault Systemes had developed Linux version of CATIA but they wouldn't like to distribute it. Has any body who has relative works in Dassault Systemes :)??,maybe we can stole:D.

After Accept these two Alerts I cant access Catia's Modules so I have no alternative except closing it. When closed, it is writed in terminal that;
```
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
err:ole:local_server_thread Failure during ConnectNamedPipe 317
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
err:ole:local_server_thread Failure during ConnectNamedPipe 317
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
err:ole:local_server_thread Failure during ConnectNamedPipe 317
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
err:ole:local_server_thread Failure during ConnectNamedPipe 317
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
err:ole:local_server_thread Failure during ConnectNamedPipe 317
fixme:ntdll:RtlNtStatusToDosErrorNoTeb no mapping for 8000000a
err:ole:local_server_thread Failure during ConnectNamedPipe 317
caner@ubuntu:~$ 
```

Thanks for your interested in it...

---

### Post by geogur on 2007-11-29
I want to run catia at home to learn ho to trouble shoot . I have to edit and fix catia`s output to run on haas ,fadel and parpus machines . The code is not always what I want , so I have to hack  to be able to run the code . What I want is freeware I can play with at home to learn catia`s limits and to improve my hack times . g.

---

### Post by piege on 2008-02-05
I replaced the opengl32.dll from a native from vista but still has problems...

---

