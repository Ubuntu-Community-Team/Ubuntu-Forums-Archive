---
title: "Cannot boot Ubuntu 12.04 and cannot boot live cd"
date: 2013-07-30
forum: General Help
---

### Post by rodo-night on 2013-07-30
_Introduction_:
Hello! I installed Ubuntu 12.04 LTS on my Toshiba Satellite C655D-S5041 about a week ago. So far everything was perfect. I don't know what caused this problem, I can only think of one thing: I usually "suspend" the system before closing the laptop, but last night, I just closed the lid without suspending it first, aside from that I didn't do or notice anything unusual. There might have been a momentary power outage during the night, in which case my laptop wouldn't hold for more than 10 minutes cause the battery doesn't work anymore.

_Problem_:
Usually when the laptop has been suspended and closed and I open it again the screen will flash once or twice and the show me the login screen or the GRUB menu. This morning when I opened the laptop the screen wouldn't stop flashing constantly, so I turned it off manually. When I turned it on again and tried to boot ubuntu from the GRUB menu, it went into the usual purple screen but it didn't show the Ubuntu logo and the signal that it's loading, it just stayed there, frozen and I could feel the HD running like crazy. I waited for a while and since nothing more happened I turned it off manually.

Now, when I try to boot Ubuntu it goes into a black screen, runs a few lines and at the end it says "**No init found. Try passing init=bootarg**"

I tried to run ubuntu in recovery mode and it went into a black screen and gave me this:

[B]mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= bootarg[/B]
(Again that init issue).

I looked it up and it seems the common solution for both problems involves booting up from the live cd and fixing something on the terminal. I tried that, but** it won't boot up from the CD either**. It's the same cd (dvd, actually) that I used to install it in my pc and it worked fine before, but now after showing the purple screen with the two symbols on the bottom (one looks like a keyboard and the other one looks like a stickman) it goes into a different black screen and says "**Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000100**" runs a few more lines and ejects the dvd.

I ran out of resources, I can't find a case exactly like mine in any forums. There are similar cases, but usually they are solved with the live cd, and some other cases have the issue with the live cd but the installed system works fine, I haven't seen someone with both issues at once. Reinstalling wouldn't be SO terrible, but I would like to avoid it, and I would like to learn from this too.

Thanks in advance for any help!

PS: I also have Windows 7 on the PC and it's working, I don't think it's a hardware issue. Also I'm sorry if I posted this in the wrong place, it's my first post.

---

### Post by Bashing-om on 2013-07-30
rodo-night; Hi ! Welcome to the forum.

Let's see what we can do to get ya booting the liveCD as a first step.
As the livdCD is once known good, give it a proper cleaning, scratches, finger prints, and dirt do a number on the disk !

ok, boot the liveCD, make sure that in bios that the boot priority is set for the cd as 1st boot priority.

As soon as the purple splash scrren appears, depress and hold the shift key;
What results ? Looking for ubuntu's boot option screen here.
On this screen is "boot from hard drive" - selecting this option has what result ?

[INDENT][INDENT]one thing at a time, and we will get there
[/INDENT][/INDENT]

---

### Post by rodo-night on 2013-07-31
Hello, Bashing-om! Thanks for your answer!

I tried what you said. When I got to the purple splash screen I pressed and held SHIFT for a moment and the options screen appeared inmediately, I selected the last option, "Boot from first hard disk" but it didn't do much, I got exactly the same "**No init found. Try passing init=bootarg**"
Since I couldn't get past that point I went ahead and tried again with the other option, "**Try Ubuntu** **without installing**" which effectively booted the CD, then I tried to do what they say on this video:
[http://www.youtube.com/watch?v=eTH3nJ9OOBM](http://www.youtube.com/watch?v=eTH3nJ9OOBM)
No luck, this is what I get:
[COLOR=#800080][B]ubuntu@ubuntu:~$ sudo fsck -y /dev/sda1
fsck from util-linux 2.20.1
fsck: fsck.ntfs: not found
fsck: error 2 while executing fsck.ntfs for /dev/sda1
ubuntu@ubuntu:~$ 
[/B][/COLOR]Well, it seemed too simple. :icon_frown:

Any ideas from this point?

Again, thanks for your help.

---

### Post by GwL3eNC on 2013-07-31
Hello,  

is it possible that the bootloader Grub is missing some needed info. I would try
ubuntu from CD like you do. Then i would download the grub-customizer because
i cant handle his files. In that application i would proof the settings. Evtl. a

sudo update-grub

can help from terminal. Or a update-initramfs -c -k yourkernelnr-generic or also a mkinitramfs. Are all 
files there needed for booting? Hope the idea helps.

---

### Post by GwL3eNC on 2013-07-31
Hello,  

is it possible that the bootloader Grub is missing some needed info. I would try
ubuntu from CD like you do. Then i would download the grub-customizer because
i cant handle his files. In that application i would proof the settings. Evtl. a

sudo update-grub

can help from terminal, or a update-initramfs -c -k yourkernel. Also mkinitramfs i would try. Are all
files there need for booting

---

### Post by Bashing-om on 2013-07-31
rodo-night; Hi !

+1 on GwL3eNC's advise...
Most probable that (re-)installing the boot loader (grub) onto the hard drive will resolve your situation.
Is only one hard drive installed onto the system - not UEFI enabled ? -> then, install grub to "sda" MBR.
Here are guides and documentation:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

As I think it is important to understand grub, to know your system.

Noth'n to it, piece of cake. - you have come a long way, But by all means, if concerns continue, please ask back !

[INDENT][INDENT]a process of learning
[/INDENT][/INDENT]

---

### Post by rodo-night on 2013-08-02
Thanks to both!
The problem is resolved!

_Solution:_
I reinstalled the GRUB following the steps indicated in the third link provided by *Bashing-om*: [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
When I rebooted, I didn't even get to the GRUB! [COLOR=#ffffff][/COLOR]I was greeted by a command prompt saying:[B]
error: file not found[/B][B].
[/B]**grub rescue>**
I still don't know much, or why, but it seems like some GRUB directories got scrambled during the process.

I looked it up and found the solution here:
[http://askubuntu.com/questions/187862/after-update-get-error-file-not-found-followed-by-grub-rescue](http://askubuntu.com/questions/187862/after-update-get-error-file-not-found-followed-by-grub-rescue)
I installed and used that Boot Repair application and *voilà*: works like a charm.

Thanks to this I did become aware of my need to learn about GRUB and how it works; thanks for that, *Bashing-om*!

I'm sorry for the delayed update. Thank you both for your help!

---

### Post by Bashing-om on 2013-08-02
rodo-night; Outstanding ..

You did all the work, we (GwL3eNC)  just pointed ya in the right direction.

Come back often and offer to help others with the knowledge you have gained.

Please mark this thread as solved (thread tools)... aides others seeking a solution, as well as; Helps keep the forum tidy.

[INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT]

---

### Post by rodo-night on 2013-08-02
Alright, thanks!



**[Closed]**

---

