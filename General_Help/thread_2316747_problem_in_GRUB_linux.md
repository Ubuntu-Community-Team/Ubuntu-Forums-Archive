---
title: "problem in GRUB linux"
date: 2016-03-10
forum: General Help
---

### Post by aviram2 on 2016-03-10
[COLOR=#222426][FONT=Helvetica Neue]I have 2 hard-discs on my computer. 
on the first one install Windows 7 with linux(ubuntu)- with different partitions.
At the begin at booting i was have option to choose linux/windows.([link here]("https://en.wikipedia.org/wiki/GNU_GRUB#/media/File:GRUB_screenshot.png"))[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]But now, i have a problem with GRUB. When booting, i have [this screen]("http://www.upfile.co.il/preview/271330252/b5eb1e7975b4b0875900e448001eb0c0_PFJYKtxPOcWuCm5pftiH2g%3D%3D.html").
I managed to load linux with command-line,that load the kernel manual.[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]It seems that i have problem with the grub.cfg -( like here:[/FONT][/COLOR][http://textuploader.com/5v350](http://textuploader.com/5v350))[COLOR=#222426][FONT=Helvetica Neue].[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]What is the best way to fix grub.cfg? that when booting i will have the option to choose linux/win7 as be-four.[/FONT][/COLOR]
[COLOR=#222426][FONT=Helvetica Neue]thanks
aviram[/FONT][/COLOR]

---

### Post by oldfred on 2016-03-10
What version are you running? 12.04.4 or 13.10?
The 12.04 is still supported, but if 13.10 it is obsolete.

Best to see all details, but this will not work if 13.10. Boot from a current live installer.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by aviram2 on 2016-03-10
I am running 13.1.

 if i understand your solution is to try [COLOR=#000000]Boot-Repair?
it will work on 13.3?



[/COLOR]

---

### Post by oldfred on 2016-03-10
That versions expired July 2014. It is difficult to repair as repository has been copied to archive.

You need to use current versions, if not wanting to upgrade every 9 months better to use the LTS Long Term Support versions.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by aviram2 on 2016-03-11
ok.

If i am understaned you.
first- i need to upgrade [COLOR=#000000]version [/COLOR] (from the site you attached).
after that to fix grub using [COLOR=#000000]Boot-Repair?

or to try [/COLOR][COLOR=#000000]Boot-Repair with 13.1?


sorry about [/COLOR][COLOR=#777777][FONT=arial]annoyance on [/FONT][/COLOR]things Details- i am not so sure about  linux and i am afraid of all my date that save in my HDs.  

thaknks
aviram

---

### Post by oldfred on 2016-03-11
Boot-Repair only works with current versions of Ubuntu.
It has to be able to find the repository to down load updates, new copy of grub.
But obsolete copies will not work.

Down load live installer, see if you can get into existing system and backup anything you have not already backed up.
You really should have good backups always as drives also fail, usually the day before you planned a backup.

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop](http://www.ubuntu.com/desktop)

---

### Post by aviram2 on 2016-03-12
i try boot-repair from [COLOR=#000000]live installer.
at the and of the process it's said: 'grub-pc purge cancelled'

there is more option to fix this problem?



[/COLOR]

---

### Post by yancek on 2016-03-12
> [COLOR=#000000]there is more option to fix this problem?[/COLOR]

No, what oldfred is saying is that the boot repair will not likely work because you are using an outdated and unsupported version and that you should use a Live CD/flash drive to backup any personal data from the computer to another drive and then install a newer/supported version of Ubuntu, 14.04.

---

### Post by aviram2 on 2016-03-12
i tried boot-repair.
it found all the kernel in the HD-and fix the boot, it load automatic and show all the kernel in HD.
attach LOG from boot-repair.
[http://paste.ubuntu.com/15361730/](http://paste.ubuntu.com/15361730/)

is there any chance that i will be able to load windows?

---

### Post by oldfred on 2016-03-12
You should be able to use Boot-Repair's advanced mode and choose Windows and restore a Windows type boot loader.
Or use your Windows repair CD or flash drive to run Windows repairs, maybe just fixMBR.
If other repairs to Windows required, Boot-Repair cannot do those, you have to use your Windows repair tools.

---

