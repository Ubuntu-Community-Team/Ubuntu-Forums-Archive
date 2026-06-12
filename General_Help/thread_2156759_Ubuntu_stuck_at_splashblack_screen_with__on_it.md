---
title: "Ubuntu stuck at splash/black screen with_ on it"
date: 2013-06-23
forum: General Help
---

### Post by Retrias on 2013-06-23
I decided to boot ubuntu again since i need to do something on it,  windowsill it to the boot screen,  and it just stuck there for like an hour or so,  restarted it and passed the boot screen and changed into a black screen where there is a_ where i cant do anything,  and it just stuck there. 

I think the last thing i do was updating it,  i am dualbooting with windows,  any idea what can i do to fix it?

---

### Post by dino99 on 2013-06-23
boot without "quiet splash" on the boot line to get the verbose mode and know where/why it hangs (edit /etc/default/grub for permanent change, then run: sudo update-grub)
or boot in recovery mode (2d grub menu line choice (ctrl+h to unhide the menu on single OS system))
or use the boot option : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Retrias on 2013-06-23
I can boot in recovery mode , however if I click on any option it forces a check disk, and if I do  check disk it doesn't do anything at all 

I am going to try again later, kinda confused why its doing this

---

### Post by steveneddy on 2013-06-23
I had the same issue this morning - updated yesterday afternoon - the update did not require a restart - shut down last night and when I restarted this morning - 

Text logon - in tty screen F1

Looked at screens F2 - F6 - looks normal

F7 is supposed to be the GUI screen - nothing - broken pipe I think it said.

login and type "startx"

GUI starts but it's the Unity interface - I loathe Unity and had installed the older Gnome GUI - 

So using the advice given above I thought I would simply look at the grub menu by typing in terminal

```
[COLOR=#000000]edit /etc/default/grub[/COLOR]
```

and we get this

```
steve@linux:~$ sudo edit /etc/default/grub
[sudo] password for steve: 
Warning: unknown mime-type for "/etc/default/grub" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

```

*groan

I just want my GUI of choice back - and I'm too old to hack it again - and I just don't want to.

Any help appreciated. Using 12.04 LTS

<rant>I cannot believe that this failure occurred after this much time using an LTS release.

And Shuttleworth wants to port Ubuntu to a phone? Not if this continues. </rant>

---

### Post by steveneddy on 2013-06-23
NVM

I restarted and all is well - the world is round again.

Whew!

*why didn't I try that the first time?*

Thanks for looking - sorry for the hijacked thread.

Peace!

---

