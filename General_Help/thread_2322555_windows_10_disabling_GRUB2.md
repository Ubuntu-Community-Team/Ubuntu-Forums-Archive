---
title: "windows 10 disabling GRUB2"
date: 2016-04-28
forum: General Help
---

### Post by AngerIssues42 on 2016-04-28
G'Day all,

Whilst I am sure this has probably been posted, I can't find anything that matches my issue, 99% of what I can find is to do with upgrading windows to W10.

Ok, so I have just done *multiple* re-installs and mucking around trying to find the best possible way to get Ubuntu (15.10) and Windows10 to happily co-exist and have come up with a solution that kind of works but is still really not good.

So, at the moment I have Windows and all it's 50 bajillion partitions on one SSD, and Ubuntu with EFI, Swap and / on my other SSD. Boot loaders are on their OS drives and not intermixed. I can boot into GRUB2 fine and from there into Ubuntu and Windows. BUT when I boot into windows, it does its virus thing and disables GRUB2 :. making Windows always boot. It also stops me from selecting Ubuntu from my Motherboards EFI Bootmenu, Ubuntu just simply disappears from it. Unfortunately, I don't know how to boot from a file or to add Ubuntu back onto the list, or if I even can with my Mobo (ASRock 970 Extreme3 R2).

If I boot into my Live-USB I can run boot-repair fine, fixes it back to grub booting, but again, once into windows I have to run boot-repair from my Live-USB, see? unfeasible.

Now I came across something on Google saying something about setting windows boot loader to boot 0000 and first, but disabled, should trick windows into believing everything is fine, but, when I run boot-repair it basically does what windows does, removes the windows boot-loader and replaces with GRUB2. This is the point I get lost, I'm don't know how to get windows back onto this list to set it to 0000.

Secure boot is off, fast boot is off.

running windows in a VM is also not feasible as I use it for WoW (and only wow), I can't get WoW to run acceptably under wine for raid condition (again, not skilled enough)

If you can help out that would be grand. Whilst I'm not a complete newbie in terminal, I will require more then just "oh, just run xxx and set xxx to xxx, it's in your xxx folder". I'm still wrapping my head around the file structure and terminal commands even for basic stuff like installing deb and tarballs. Basically, pretend I've been on Windows for the last 25 years of my 29 years of life, or well, not pretend.

Any help would be awesome, my timezone is UTC+8 so if I don't reply quickly, I'm probably asleep or the wife has me running errands.

Kind Regards,

Chris.

---

### Post by UbuntuAddict99 on 2016-04-28
[COLOR=#000000]Hello [/COLOR][COLOR=#000000]AngerIssues42, 
 Now the issue you are describing is almost identical to the issue i had with Windows 10 and Ubuntu 14.04 LTS. So this is my answer to your question to repair GRUB through Windows 10 follow the URL link and repair GRUB. URL:[/COLOR][COLOR=#000000][http://itsfoss.com/no-grub-windows-linux/](http://itsfoss.com/no-grub-windows-linux/) 

Now this should work with minimal issues. Now i noticed you said you have Secure Boot disabled so that is not the issue, so if that does not work repairing GRUB through Windows 10. Then try booting Ubuntu with a Live DVD. Download Boot Repair and run it and then restart your PC and it SHOULD fix the issue.

So a rundown.

1) Either re-install Linux Ubuntu, or attempt to fix GRUB with a Live CD/DVD with Boot Repair.
2) Attempt to fix GRUB through Windows with the provided URL as written above.

P.S. _PLEASE NOTE! I have YET to run dual boot on two different HDD's/SSD's so this solution may and or may not work._

Or the easy option.

4) [/COLOR][COLOR=#ff0000]_**OPTIONAL!**_[/COLOR][COLOR=#000000] Run Windows 10 or Linux Ubuntu on a virtual Machine.

I hope this has helped/answered your question. I have been where you  were before with a almost identical issue. 

P.S. I am NOT a Linux Zen Grand master, so to the more experienced Ubuntuers that will respond to this thread. I am still learning as well.

Happy  Linuxing.[/COLOR]

---

### Post by AngerIssues42 on 2016-04-29
Just having a look at the link now, I have been running boot-repair, and it works, up until I load into windows, then I have to do boot-repair again.

Unfortunately, no VM's are feasible as pretty much all my games are linux native except for the blizzard games I play.

---

### Post by AngerIssues42 on 2016-04-29
Thanks mate, this worked, I ignored this the first time as I figured it would throw up all sorts of errors seeming that my loaders are on two completely different drives. It worked, I'm happy. Thanks Champ

Chris.

---

### Post by oldfred on 2016-04-29
It seems Asrock has this problem on other model motherboards also. 
And UbuntuAddict99's suggestion is the solution of adding BCD entry. Boot-Repair often suggests that also.

---

### Post by UbuntuAddict99 on 2016-04-29
You are welcome the problem is easy now that we know the solution.

Happy Linuxing.

---

