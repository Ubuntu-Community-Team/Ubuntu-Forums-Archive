---
title: "wine"
date: 2006-12-28
forum: General Help
---

### Post by manutdfan2850 on 2006-12-28
hi i installed WINE using Automatix 

but where can i find it? and how do i use it?

I want to run a program from my NTFS partition which i mounted for read/write access.

thanks.

---

### Post by tzulberti on 2006-12-28
> **manutdfan2850 said:**
> hi i installed WINE using Automatix 

but where can i find it? and how do i use it?


Fist, you should configure it: winecfg...

> **manutdfan2850 said:**
> 
I want to run a program from my NTFS partition which i mounted for read/write access.

thanks.

Yes. First, you should tell wine to directly use de Windows (the official one) libraries which are in the partition ZZZ. Then to run a program, you should do: wine NameOfExe.exe

---

### Post by Olav on 2006-12-28
> **manutdfan2850 said:**
> hi i installed WINE using Automatix 

but where can i find it? and how do i use it?

I want to run a program from my NTFS partition which i mounted for read/write access.

thanks.
You can use wine from a command shell (terminal) window: 

$ wine program.exe

... that should run program.exe.

But I would actually advice against using it to run programs on your NTFS. I assume you have dual boot, and you will want to be able to run the same program in Windows too. Depending on what kind of program it is, you may get into trouble. It is better to INSTALL your program using its packaged installer (setup.exe?) into the Wine environment and run it from there. If it works at all, which cannot be guaranteed with Wine. It's not Wine's fault either, some Windows programs just use rather arcane programming techniques which rely too much on specific bugs in the Windows operating system.

Of course, there is always the fine manual: [http://www.winehq.com/site/docs/wineusr-guide/index](http://www.winehq.com/site/docs/wineusr-guide/index)

You can skip the parts about installing and most of the chapter about configuring. But please do have a look, at the very least. You should also check out the application database on the Wine website, to see if your specific program is already mentioned. If it is, you may benefit from the experiences of other users with that software.

---

### Post by manutdfan2850 on 2006-12-28
ok so i am trying to install counterstrike. so i have the exe installer file on my ubuntu desktop. i did winecfg and added it. but when i try to open it using wine i get this error:

> laptop:~$ wine counterstrike.exe
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
wine: could not load L"c:\\windows\\system32\\counterstrike.exe": Module not found

what could be the problem.

i tried it with another app but same result. 

thanks in advance for ur help.

---

### Post by Death4Life on 2006-12-28
Make sure you are in the right folder when you execute wine counterstrike.exe
because else wine returns errors

over here i installed Steam, from Valve and that work's perfectly fine.
I can run CS1.6 fine ( haven't tryed source yet )
here is the guide i followed.
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Steam&back=HOWTO+INDEX+Wine+Games)

---

### Post by hadiriazi on 2006-12-28
I imagine you are giving the path to the exe as c:\.....? this is completely wrong since linux file management and partition system isn't like windows it uses /media/... for the path.

Make sure you give the correct path to the .exe application. In your case if counterstrike is in "c:\windows\system32\counterstrike.exe" you need to find the mount point of c: in ubuntu, regularly sda1 under the media folder. So the equivalent path would be "/media/sda1/windows/system32"

```
laptop: /media/sda1/windows/system32/$: wine counterstrike.exe
```

this should work. unless you have counterstrike installed in some other partition or directory, then you need to change the path above to that location.

Hope this will help

---

### Post by manutdfan2850 on 2006-12-28
oh that makes sense now. ill try it and let you know if it works

thanks

---

### Post by majoridiot on 2006-12-28
if the install file is sitting on your desktop, as you say it is:

```
 wine ~/Desktop/counterstrike.exe
```

---

