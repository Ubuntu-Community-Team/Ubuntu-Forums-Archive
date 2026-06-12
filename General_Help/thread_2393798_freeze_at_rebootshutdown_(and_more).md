---
title: "freeze at reboot/shutdown (and more)"
date: 2018-06-08
forum: General Help
---

### Post by ablia on 2018-06-08
Hello everybody!

I'm having a weird issue since three days now, i've tried many things to get rid of it but it doesn't work....
So every times (or nearly every time) i try to reboot or shutdown my computer, it freeze. But like, i can't do nothing: no mouse, no terminal, nothing. Moreover, when i put the computer to sleep, then open it again it would "wake up" but just give me a black screen. Freeze happens too when i try CTRL+Alt+F1, or when i try to open "ubuntu web browser", and i also had a "little" freeze when i tried to open the system parameters (still had the mouse on this one, maybe it's not related, i did not try it another time. I'm a bit tired on forcing shutdown and reboot....)

This issue appear only on Ubuntu (i got 3 partitions, one for windonws 10, one for Ubuntu 16.04 and one for my data), and only since 3 days (i did made an update before this issue appear, it may comes from this). Oh, and my computer is an HP, with Nvidia Geforce gtx graphic card. dunno if it's important ^^

So, i've tried a lot of things, and first booting on recovery mode, verify packages and files, everything seemed ok here. Then when i shutdown from recovery mode, after the line "Stopped Thermal Daemon Service" i got this: 

"A stop job is running for Make remote CUPS printers available locally"
It has a waiting time of 1min30 and freeze within 15-20sec

With some research, i've found that it's possible to completely "delete" the waiting time; but with this down, the freeze then appear immediatly after shutdown (just like in "normal mode"). So instead i set the waiting time on 30sec (instead of 1min30), and for some reason it worked. 

Still, that's on recover mode; normal mode still freeze. Moreover, sometimes its work without reason. For example, yesterday morning i tried to shut down again before trying others way to repair it, and it worked. I was so surprised that i did maybe 3-4 shutdown or reboot, and everyone worked. Then, some hours laters, when i tried to shutdown it freezed. 
This morning i tried it again; it freezed the first time. So i've search others solutions and tried this ones: 
[https://help.ubuntu.com/community/Grub2#Fixing_reboot.2Fshutdown_freezes](https://help.ubuntu.com/community/Grub2#Fixing_reboot.2Fshutdown_freezes)
[http://mylinuxexplore.blogspot.com/2011/11/solved-ubuntu-doesnt-shutdown-properly.html](http://mylinuxexplore.blogspot.com/2011/11/solved-ubuntu-doesnt-shutdown-properly.html)
[https://askubuntu.com/questions/764568/ubuntu-16-04-hangs-on-shutdown-restart](https://askubuntu.com/questions/764568/ubuntu-16-04-hangs-on-shutdown-restart)

At first i thought it worked a bit, because for some reason, after doing it and runing recovery mode and going back on normal mode, the shutdown/reboot worked well...for some time. Then it start freezing again.
Then when i was writing this message i thought "ok, if recovery mode work well, that should comes from a graphic pilot" and i tried to open parameters...and got this other freeze, with the mouse still working. (but still not able to open the shell).

So here i am, without any other idea and with another morning of work lost. I really need to go back to work now, so i can't work on this issue anymore. As said, it appears only on Ubuntu and only in normal mode. 

Ah, i've tried something else: opening shell with CTRL+Alt+F1 and shutdown the computer from here. I got a bunch of lines who doesn't make any sense to me, and then the cursor still flicker but nothing else happens and the computer doesn't shutdown. 
the first lines are speaking about some fails (gr init fail, secboot fini failed, Xorg init failed, DRM init failed, Bug: unable to handle kernel paging request at ...) and the last line is "RIP: evo_wait+0x5a/0x130 [new] RSP ..."  (with ...being an hexa thing with 16 digits). Dunno if that could help. 

Thanks in advance for any idea!
Ablia

---

### Post by ablia on 2018-06-08
EDIT! 
i think i got it. (yeah, i know i said i won't search anymore, but would it be so hard to check my graphics drivers? eh, no. )
So here you go: there was an "additionnal driver" for Nvidia, with two possibles sources. The one selected was a weird X.Org, org server, free source. Instead i selected the Nvidia binary driver from nvidia (tested source) which just by the name seemed a lot better. 

For now, it work. I hope it wasn't just by chance, but i'm pretty confident with this one :)

---

