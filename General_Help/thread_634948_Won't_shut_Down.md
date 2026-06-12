---
title: "Won't shut Down"
date: 2007-12-08
forum: General Help
---

### Post by tuxnewbestfriend on 2007-12-08
When I shutdown my computer it gets stuck on this screen every time. Does anyone have any ideas? Please help.

NetworkManager: <WARN> nm_signal_handler (): Caught Signal 15, shutting down normally

NetworkManager: <info> Caught terminal signal

NetworkManager: <debug> [1197127585.356623] nm_print_open_sock (): Open Sockets
Lists:

NetworkManager: <debug> [1197127585.356710] nm_print_open_sock (): Open Sockets
Lists Done:

NetworkManager: <info> Deactivating device eth0

NetworkManager: <info> Deactivating device eth1

---

### Post by wormser on 2007-12-20
Wow, you have been waiting a while for a post.  What type of wireless card do you have?  I am getting the same error when I enable my Broadcom BCM4309.  The latest kernel broke it for me.  It was working fine in Gusty.

---

### Post by wormser on 2007-12-22
It seems the shutdown problem has stopped for me.  Here is what I did:

1.  Uninstalled the firmware
2.  Reboot (still had shutdown issue)
3.  Reboot (no problems)
4.  Installed firmware again.
5.  Reboot (no problems)

After a couple of shutdowns the problem occurred again.  I went threw the same steps and it has been a while since I have had the   No idea why this helped but it did.

---

### Post by tuxnewbestfriend on 2007-12-22
I tried it and it still is still giving me the same screen at shutdown. Did the screen you were getting include eth0 and eth1? On mine I have eth0 - network interface card eth1 - Wi-Fi, I tried disabling roaming mode on my Wi-Fi and it still comes up on shutdown. 

I am pretty new to linux. I believe the screen I get means that when the computer is shutting down it isn't allowing it to deactivate my NIC or wi-fi and complete the shutdown. Is that right? 

Thanks for the help.

---

### Post by wormser on 2008-02-26
This solution did not work on the latest kernel upgrade. :(  Does anybody have a good solution to this issue?

---

### Post by MasonicMaster on 2008-04-30
I am having the precise same problem in hardy are there any ides to the cause? any solutions?

I must elaborate on a few facts,this ONLY occures when I shut down if I do a restart I do not get the error.

---

### Post by wormser on 2008-04-30
> **MasonicMaster said:**
> I am having the precise same problem in hardy are there any ides to the cause? any solutions?

I must elaborate on a few facts,this ONLY occures when I shut down if I do a restart I do not get the error.

I never did find a solution with this issue in Gusty.  It has not happened in Hardy.  Try uninstalling it, reboot and install.  That worked for a while.  Search for a bug report and if you cannot find one then [file it]("http://ubuntuforums.org/showthread.php?t=734460").

---

