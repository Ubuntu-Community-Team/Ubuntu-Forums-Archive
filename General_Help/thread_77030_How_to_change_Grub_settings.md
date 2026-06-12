---
title: "How to change Grub settings"
date: 2005-10-16
forum: General Help
---

### Post by shazbot on 2005-10-16
Hello, fairly new to Linux, and new to Ubuntu and Grub

Have installed Ubuntu on my portable  with a dual boot with XP, I need XP to be the first in the boot sequence as I use it more often, but for the moment the Linux is the first line and so if I don't pay attention I will boot into linux rather than Windows

Where are the grub setting so that I can modify it, I haven' been able to find this

Thanks for any help
Trevor

---

### Post by afonic on 2005-10-16
Try editing /boot/grub/menu.lst

There is that setting:

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0
```

This is the default option (grub counts from 0, not 1). If you just have Changing this to 3 or 4 should make windows default (it depends on your configuration).

Remember to backup this file, as if you break it you will not be able to boot!

---

### Post by shazbot on 2005-10-16
That was just fine, thanks a bunch

Now How do I change th emous so that left and right buttons work ?

---

### Post by GrendelS on 2006-03-31
Hi,
how do I find out what setting (3,4,...) my boot config file needs? I have hda0 with 80GB and Win Pro installed, the next partition (all on the same hard drive) is a brandnew, shiny, uber-Ubuntu, then a 10GB /home I created manually (wowow :cool: ) and a decent-sized swap file. When I fire up my computer, Win Pro is in the last slot, I'd need it in the first. What is interesting: There's not one install of Ubuntu, but several with different "names" (or functions) as well as a memtest as boot option (very handy as well) - but I didn't install it more than once. What would I have to insert as boot option?
regards,

Grendel S.

---

### Post by ceege111 on 2006-09-28
Is there any way to make this a one time change?  I ask because i want to set up a machine that will boot into ubuntu by default but not every time - I want to be able to control it entirely over the network.  The problem is that I can't see menu.lst in winxp as it is in the linux filesystem

Thanks

C.J.

---

### Post by KazukiFlame on 2008-05-24
what about if i want grub to boot into the os i booted into last time?
like if i booted into windows, then next time when grub loads up, it defaults into windows. if i booted into linux, next time it starts up defaults into linux?

---

### Post by meierfra. on 2008-05-24
> what about if i want grub to boot into the os i booted into last time?

This can be done by editing "menu.lst". Open menu.lst via


```
gksudo gedit /boot/grub/menu.lst
```

Change "default 0"  to "default saved"

Add "savedefault" to your ubuntu and windows item:


title ubuntu.....
root .......
kernel ......
initrd ......
savedefault


title Windows....
root ....
chainloader ....
savedefault

---

### Post by KazukiFlame on 2008-05-24
ok, i did that, why is it still not saving?

---

### Post by meierfra. on 2008-05-24
> ok, i did that, why is it still not saving? 

I don't know. Post the file  "/boot/grub/menu.lst".

You might also look at the file  /boot/grub/default. The first number in that file should correspond  to  the OS you booted in last.

Also try

```
sudo grub-set-default 4
```

This should change the  first number in "/boot/grub/default" to "4"

Now if you reboot  you should boot into the  5th title  in menu.lst. Grub starts counting at 0. Also every "title" counts, for example "title Other Operating Systems"

---

### Post by meierfra. on 2008-05-24
Oops. I just noticed that I wrote  "savedefaut" instead of "savedefault". But I assume that you caught that misprints.

---

### Post by KazukiFlame on 2008-05-27
i did all that, but it still didn't save my last boot. so i just resorted to adding the boot order to savedefault.

like my windows is boot item 4, i just added savedefault 3
it worked after doing that, but i have a feeling its not the best way.

---

### Post by mister_pink on 2008-05-27
Try installing startupmanager (thats the package name). It adds a GUI settings tool to System -> Admin to do this sort of thing for you.

---

### Post by KazukiFlame on 2008-05-27
did that too, unfortunately, startupmanager did everything except save my last boot

---

