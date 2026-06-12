---
title: "Setuid command seems to not working"
date: 2014-05-15
forum: General Help
---

### Post by whiteking on 2014-05-15
[COLOR=#000000][FONT=Arial]I had windows application installed on Linux computer, for example, in Demo directory. And in Demo folder, I have files directories structure as follow

[/FONT][/COLOR]-rwxrwxrwx spuser spuser aaa.dll 
  -rwxrwxrwx spuser spuser bbb.ttf 
  -rwxrwxrwx spuser spuser ccc.ref 
  -rwsrwxrwx spuser spuser DemoApp.EXE **<= I've set setuid command on this file**
  drwxrwxrwx spuser spuser icons
  drwxrwxrwx spuser spuser secure
  drwxrwxr-- spuser spuser lang
[COLOR=#000000][FONT=Arial]If I run DemoApp.EXE with spuser privilege, it work fine, DemoApp.EXE can read files within lang directory. But when I run DemoApp.EXE with ordinary user privilege, it have error that say cannot read files within lang directory that I set it read-only for others (as above directories structure). I try to run both in Linux mint with WINE or run this program on Windows pc, it have same result.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Please advise me, and sorry for my bad english.[/FONT][/COLOR]

---

### Post by papibe on 2014-05-15
Hi whiteking. Welcome to the forums ):P

I'm afraid setuid only works for programs that run inside the Linux environment.

I'm guessing DemoApp.EXE is a Windows application and run either under Windows, or under Wine.

Under Windows proper, those permission don't even exist since NTFS does not support them. When executed in Linux through Wine, Linux does not actually execute them (via the dynamic loader: /lib64/ld-linux-x86-64.so.2), but it is read as input file to Wine, which in its effort to emulate Windows does not support Setuid.

Does that help? Let us know if you have more questions.

Come here often and have fun.
Regards.

---

