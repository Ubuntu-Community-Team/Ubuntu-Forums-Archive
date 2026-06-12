---
title: "&quot;A disk read error occurred&quot; error for Win 7 boot after changing boot order in grub"
date: 2013-10-29
forum: General Help
---

### Post by macakcira on 2013-10-29
I have installed Win7 first, then installed Ubuntu and that made Ubuntu the 1st choice on the boot order, but since I am natively a Windows user I tried to put Windows on 1st  place via grub customizer, but after I pulled it on the 1st place, when I choose windows 7 on boot meny  it gives me an error "A disk read error occurred. Press Ctrl+Alt+Del to restart".

I did exactly like in this tutorial: [http://itsfoss.com/windows-default-os-dual-boot-ubuntu-1304-easy/](http://itsfoss.com/windows-default-os-dual-boot-ubuntu-1304-easy/)

Help :S

EDIT: After I have changed the boot order in grub, there is "on /dev/sda1" next to the "Windows 7" text in the boot menu. Before I changed boot order I am 99% sure there was only "Windows 7", without "on /dev/sda1". My guess is that the disk names in windows and linux are different so Windows can't find the path grub has writen for it where to boot from. But I am a total noob for linux and I don't know how to fix this!

---

### Post by tomearp on 2013-10-29
There is a tool referenced in the Community Ubuntu Documentation that can help to repair GRUB. I have not used it myself but it may be worth a shot to restore the ability to boot to both operating systems.
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

There is a YouTube video demonstrating its use to restore the ability to boot Ubuntu following the scenario whereby installing Windows after installing Ubuntu has resulted in GRUB being replaced. This may help you get an idea of how it works.
[http://m.youtube.com/watch?v=bClcHGAmRSc&desktop_uri=%2Fwatch%3Fv%3DbClcHGAmRSc]("http://m.youtube.com/watch?v=bClcHGAmRSc&desktop_uri=%2Fwatch%3Fv%3DbClcHGAmRSc")

If you're at all unsure I would suggest waiting for some more replies as someone with experience of your particular scenario may pass by soon.

If you are successful in restoring GRUB then I would consider following the instructions detailed in this post on askubuntu for changing the boot order via the command line, which rather than rearranging the boot menu simply instructs GRUB to use an entry other than the top one as the default option.
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order]("http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order")

---

### Post by macakcira on 2013-10-31
Hi, I have solved the problem by following this tutorial: [http://www.coolinformation4all.com/2012/01/remove-grub-restore-windows.html](http://www.coolinformation4all.com/2012/01/remove-grub-restore-windows.html)

Bye

---

