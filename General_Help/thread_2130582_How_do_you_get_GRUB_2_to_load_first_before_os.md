---
title: "How do you get GRUB 2 to load first before os?"
date: 2013-03-29
forum: General Help
---

### Post by ambiguities on 2013-03-29
[COLOR=#000000][FONT=Arial]I feel kinda silly asking this but I would like to know if it is possible to have grub2 boot before an OS loads. I'm currently running an ACER V3-571-6643 with windows 8 on it and I installed Ubuntu 12, using the grub2 boot loader to dual boot. The only issue I have is that when I start my laptop it loads Windows 8 before the grub2 menu shows creating a delay in boot time. If I want to boot Ubuntu I still have to wait for windows 8 to load to get to the grub 2 menu and then I can boot to Ubuntu which appears to restart the computer and then boot the os. Is there any way to have grub2 load and then choose an os to load? If not I'm sorry for wasting time.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]The boot order for my laptop appears to be:[/FONT][/COLOR]

ACER start up screen
v
Windows boot logo (loading the OS)
v
Grub2
v
whatever OS is chosen
[COLOR=#000000][FONT=Arial]
(when windows is chosen it goes to login instantly because it has already been loaded)[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial](when Ubuntu is chosen the computer restarts and loads Ubuntu and goes straight into login after loading the OS)[/FONT][/COLOR]

---

### Post by coldcritter64 on 2013-03-29
Is that a Wubi install, ie., Ubuntu was installed from within Windows ? 

Or did you burn a live cd, and install "side by side" with Windows using the live cd installer etc ?

---

### Post by ambiguities on 2013-03-31
It was a WUBI install. If thats the issue then how do I go about fixing it?

---

### Post by oldfred on 2013-03-31
Wubi uses the Windows boot loader to run. So with wubi you cannot directly boot with grub. 

If you want grub as your boot loader, do you not also want a full install of Ubuntu into separate LInux formatted partition?

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn&#8217;t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

