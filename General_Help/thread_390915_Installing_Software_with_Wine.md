---
title: "Installing Software with Wine"
date: 2007-03-22
forum: General Help
---

### Post by gavinjb on 2007-03-22
Hi,

I am trying to get equivalent software to any windows apps I use, to enable me to remove Windows and install Ubuntu on my Laptop, I am currently having problems finding s/w to replace VideoReDo, so I am having a go at installing it under wine, this is where my problems occur.

I managed to install the app with no problem but when I run it I get the error below

```
Cannot find import; DLL may be missing, corrupt, or wrong version File "MFC42.DLL", error 126
```

I did some googling and found the following article [http://forums.sagetv.com/forums/showthread.php?t=22404](http://forums.sagetv.com/forums/showthread.php?t=22404) from reading this it looks like VideoReDo needs Gecko Engine and DirectX, does anyone know where I can get these from, I know I can get DirectX from MS, but not sure where to look for Gecko Engine.

The Files I am editing are .tc streams, but I have found tools to convert to MPEG format in Linux, but have yet to find anything which can do some basic editing (mainly cutting bits out of the files), I have tried mainly AvideMux, but after cutting clips out of the files the sound is no longer in Sync and I cant figger this out.

If anyone else knows how to resolve this or can come up with an alternative to trying to get VideoReDo working I would appreciate that as I want to remove the need to run any Windows Apps if possible.

Thanks,


Gavin,

---

### Post by zvacet on 2007-03-22
Find missing dll here
[http://www.dll-files.com/]("http://www.dll-files.com/")

---

### Post by gavinjb on 2007-03-22
Thanks, any idea what to do with them, in windows I would copy them to c:\windows\system32 and it that didn't work try running regsrv32 file.dll but as far as I know you cant do this and I have tried copying to both c:\windows\system32 and the application folder, but no luck.

---

