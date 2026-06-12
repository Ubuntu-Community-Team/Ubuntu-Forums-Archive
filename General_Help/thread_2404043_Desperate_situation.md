---
title: "Desperate situation"
date: 2018-10-19
forum: General Help
---

### Post by Joentokyo on 2018-10-19
I have been using Ubuntu 18.04 for quite a while. Today when I booted up my machine the downloads folder and music folder had disappeared. After spending much too long looking for a solution I decided to reinstall. Much to my surprise my internal dvd drive is no longer mounted and cannot be accessed for booting from my Ubuntu 18.04 DVD. I tried hooking up a usb cd/dvd, but even though I select it in BIOS the machine will not boot from it. The machine will only boot from the hard disk, so I am stuck with a broken version of Ubuntu 18.04. Anybody have any idea how I can put this back together?

---

### Post by dino99 on 2018-10-19
First check the 'global settings' menu to see if the hardware is found and well identified. lshw can list them all too.
Then checking 'journalctl - b' or 'journalctl -b -1' will show you the main warnings (highlighted lines) and errors (red lines).
Is your installation encrypted ? Also check that blkid and fstab are matching.

---

### Post by HermanAB on 2018-10-19
Hmm, don't change anything until you know what is broken.  Using a broken machine to try and fix itself, can make things worse, since it can make computational and read/write errors.

I would first try to boot off a USB widget.  If that doesn't work, I would put the HDD into a USB caddy and examine it with another machine and make a backup.

---

### Post by cmcanulty on 2018-10-19
Have you tried Boot repair?

[https://linuxconfig.org/ubuntu-boot-repair]("https://linuxconfig.org/ubuntu-boot-repair")

---

### Post by Joentokyo on 2018-10-19
> **dino99 said:**
> First check the 'global settings' menu to see if the hardware is found and well identified. lshw can list them all too.
Then checking 'journalctl - b' or 'journalctl -b -1' will show you the main warnings (highlighted lines) and errors (red lines).
Is your installation encrypted ? Also check that blkid and fstab are matching.

lshw showed the dvd drive is there, but it does not show up in the places menu or in home. Also, if I select it in BIOS to boot the computer, it is ignored.

I ran bleachbit the other day, but I cannot see why that would delete folders and settings.

---

### Post by Joentokyo on 2018-10-19
> **cmcanulty said:**
> Have you tried Boot repair?

[https://linuxconfig.org/ubuntu-boot-repair](https://linuxconfig.org/ubuntu-boot-repair)

Yes, but the problem is not booting the computer will boot as long as I choose the hard disk for it to boot from, but it will not boot from a dvd, which is what I need to do to reinstall the system. Also, the report given me by boot repair is way above my level of understanding of OS and computers.

---

### Post by dragonfly41 on 2018-10-19
> [COLOR=#000000][INDENT]Also, the report given me by boot repair is way above my level of understanding of OS and computers.[/INDENT]
[/COLOR]


Boot-repair provides a url during its run, which allows the report to be previewed by others here in this forum. Try again and post the url here.

---

### Post by cmcanulty on 2018-10-19
Also you can just try the recommended option on boot repair, usually fixes things

---

### Post by HermanAB on 2018-10-19
"I ran bleachbit the other day" - Bingo.

---

### Post by #&amp;thj^% on 2018-10-19
> **HermanAB said:**
> "I ran bleachbit the other day" - Bingo.

+1 I noticed that also.
Bleachbit is a great tool with expericnce and without expericnce it can be your worst enemy. :(
I use it regulary but with a learned wisdom. ;)

---

### Post by Joentokyo on 2018-10-19
> **dragonfly41 said:**
> Boot-repair provides a url during its run, which allows the report to be previewed by others here in this forum. Try again and post the url here.

Here is the url boot repair provided: 
  
[http://paste.ubuntu.com/p/tJhmdVVYWm/](http://paste.ubuntu.com/p/tJhmdVVYWm/)

---

### Post by dragonfly41 on 2018-10-20
I see this note right at the end of the boot-repair report:

> [COLOR=#000000]Boot successfully repaired.[/COLOR]
You can now reboot your computer.
Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sda [COLOR=#666666]([/COLOR]ATA ST3500418AS[COLOR=#666666])[/COLOR] disk!

The boot files of [COLOR=#666666][[/COLOR]The OS now in use - Ubuntu 18.04.1 LTS[COLOR=#666666]][/COLOR] are far from the start of the disk. 
Your BIOS may not detect them. You may want to retry after creating a /boot partition 
[COLOR=#666666]([/COLOR]EXT4, >200MB, start of the disk[COLOR=#666666])[/COLOR]. 
This can be performed via tools such as gParted. 
Then [COLOR=#AA22FF]**select **[/COLOR]this partition via the [COLOR=#666666][[/COLOR]Separate /boot partition:[COLOR=#666666]][/COLOR] option of [COLOR=#666666][[/COLOR]Boot Repair[COLOR=#666666]][/COLOR]. 
[COLOR=#666666]([/COLOR]https://help.ubuntu.com/community/BootPartition[COLOR=#666666])[/COLOR]

---

### Post by Joentokyo on 2018-10-21
Thank you all for your advice. Especially the mention of Boot Repair. Of course with my usual flair for screwing up I forgot to set the BIOS to boot from the correct disk which caused another error. I thought that was all she wrote, but perusing Ubuntu Questions I found a way to get into the settings and changed the boot settings to boot from a disk that could boot. I am now reinstalling the OS.

Once again thanks to all for the  help.:P

---

