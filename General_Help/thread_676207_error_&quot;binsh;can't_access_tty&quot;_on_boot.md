---
title: "error &quot;/bin/sh;can't access tty&quot; on boot"
date: 2008-01-23
forum: General Help
---

### Post by alfiesty on 2008-01-23
I am a total Linux newbie who has been wanting to dump Vista, which is the operating system for my Acer 5100-3949 laptop. Wubi looked to me as an easy way to get Linux loaded with a minumum of hassles. I loaded the default KUBUNTU installation with Wubi. First time it ran fine. but the second time I booted it, it stopped at about 5-10 % on the progress bar below the word KUBUNTU. After about 10 minutes it came up with this message:

/bin/sh;can't access tty; job control turned off
(initramfs)

it said to type "help" for commands but all that comes up is a block of gooblegook that means nothing to me. Then it returns to the (initramfs) prompt.As I live in a small town with no gurus around, I am pretty much on my own. I have some computer experience but have not dealt with a command line since Windows 3.3.

 KUBUNTU looked really good when it came up but it didn't seen to find the wireless adapter. Is this going to be a complex problem? At least with Wubi uninstallation is easy.

Jim
[email]jim@alfiesty.com[/email]

---

### Post by ago on 2008-01-23
Did you hard reboot (shut down holding down the PC power button)?
In case run chkdsk /r from windows

---

### Post by alfiesty on 2008-01-26
Yes, I tried that several times.

Jim

---

### Post by superunknownnot on 2008-01-27
Dear all

This is my first post, also - I am new to Linux. Ive heard all good things about Ubuntu and when I saw the Wubi installed I thought to give it a try. I am familiar with OS/2 and WindBlows.

Me as the thread starter, recived the error "/bin/sh;can't access tty" on the "first" reboot.

I installed the Wubi, ran it. It downloaded the iso file and asked me to reboot, as I did.
Upon reboot the non gfx gui appeared and continued with the installation.
Then second reboot and the gfx Ubunto logo appeard, it froze before the first tick on the progress bar and went to shell, with the thread subject error.

My system is a intel 3GHz x2 CPU.
2 SATA disk configured as raid 0, these are again split into C: and D: in Windows.

I tried installing ubuntu first at D:, failed. Then C: failed again - both with same tty error.

// ------------------------------------------------------------
Stopped the boot with ESC and choose to boot from "memtest86+" option, this gave
Booting 'Ubuntu, memtest86+'

(hd0,0)
Filesystem type is ntfs, partition type 0x7
kernel   /boot/memtest86+.bin

Error 17: File not found
Press any key...


When I open a shell, there is no /boot directory to be found while ls command
// ------------------------------------------------------------
Booted with the recovery option

...
[  10.423402] XFS: SB validate failed
Done.
Begin: Waiting for root file system... ...
    Check root= bootarg cat /proc/cmdline
    or missing modules, devices: cat /proc/modules ls /dev
ALERT! /media/host/wubi/install/install.virtual.disk does not exists. Dropping to
 a shell

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu-3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(inittramfs) _



any help? thanks.

---

### Post by ago on 2008-01-28
Press esc, choose verbose mode.
Look at the logs in /*log and /tmp/*log and /var/log/*log
Look for errors

grep -i err /*log /tmp/*log /var/log/*log

---

### Post by alfiesty on 2008-01-29
I posted the following. 
I am a total Linux newbie who has been wanting to dump Vista, which is the operating system for my Acer 5100-3949 laptop. Wubi looked to me as an easy way to get Linux loaded with a minumum of hassles. I loaded the default KUBUNTU installation with Wubi. First time it ran fine. but the second time I booted it, it stopped at about 5-10 % on the progress bar below the word KUBUNTU. After about 10 minutes it came up with this message:

/bin/sh;can't access tty; job control turned off
(initramfs)

I received in reply

In case run chkdsk /r from windows

First I'd like to comment on this reply. Although correct, it ignored that this command cannot be easily run from Vista. It immediately excludes most Windows users who do not easily negotiate the command line. The way I found to do this was:

At the grub? Screen press F8
Choose the "command line option" and press enter
When you get to the command prompt type chkdsk /r - enter
type ctl-alt-del
On the screen that comes up click the red “Shut down” button
At the grub? Screen choose "windows Vista" and press enter
Chkdsk will run, and then reboot
At the grub? Screen choose "windows Vista" and press enter
Vista runs a check and reboots
Now at the grub? Screen choose "WUBI UBUNTU" and enter and if you are lucky UBUNTU will run

For me it did not, instead after getting to 10% on the progress bar it sat there for about 5 minutes then I got a blank screes with an underline in the top left corner. I repeated this three times. Same each time! I'm just dumping the whole works at this point.

More comments. If you are to believe the hype Linux is theNEW BEST THING. This is not true if it won't install on basic hardware without many complex steps. If you don't have a Linux guru handy (I live in a small town, and don't) to explain or do these steps for you, you're lost. I think you should look at what percentage of help requests are installation problems. Then there is this myth that help is as near as the Internet. This “help” is fine for the sophisticated user but any newbie is unable to understand this so called “help”. Most windows users probably wouldn't have gotten as far as I did! I'll bet 99.9% of all windows users have never heard of chkdsk or would know what it did. I'll bet more windows users trying Linux give up than those succeeding.

---

### Post by ago on 2008-01-30
> **alfiesty said:**
> 
For me it did not, instead after getting to 10% on the progress bar it sat there for about 5 minutes then I got a blank screes with an underline in the top left corner. I repeated this three times. Same each time! I'm just dumping the whole works at this point.

That is a video driver issue. Press ctrl+alt+f2, then at the command line type:

sudo dpkg-reconfigure xserver-xorg

Select vesa driver, leave the other options to their default value.

---

### Post by alfiesty on 2008-01-30
Thanks for sticking with me, ago! If you would like to take this private to save forum bandwidth that's OK with me.

 You didn't say where to hit ctrl-alt-f2 so I assumed it was at the blank screen with the underline at the top left. Nada! Then I tried at the grub screen. Nada! On boot there are only two options, Vista or UBUNTU, so I'm unsure where else to try it. Hitting f8 gives only windows options. I've decided to give this the old college try and not give up until I know I'm licked. Is there any way to load KUBUNTU in the command line mode instead of in X?

Jim

---

### Post by ago on 2008-01-31
You can have a more verbose boot by hitting esc at the initial countdown, then  press "e" on the first option, select theh kernel line and press "e" again to edit, then delete "quiet splash". Then hit enter and then "b"

8.04 is coming out these days you might want to try that too

---

### Post by superunknownnot on 2008-01-31
> **ago said:**
> Press esc, choose verbose mode.
Look at the logs in /*log and /tmp/*log and /var/log/*log
Look for errors

grep -i err /*log /tmp/*log /var/log/*log

Thanks

Found only errors in /tmp/zenigata.log
grep: /*log: No such file or directory
grep: /var/log/*log: No such file or directory

the begning of the /tmp/zenigata.log contains some constants (I think)
ERR_MNT_ROOT=1
...
ERR_WRONG_FILESYSTEM=20
Failed to load $MFT: Input/output error
Failed to startup volume: Input/output error
Failed to mount '/dev/sda1': Input/output error
Failed to load $MFT: Input/output error
Failed to startup volume: Input/output error
Failed to mount '/dev/sda1': Input/output error
Failed to load $MFT: Input/output error
Failed to startup volume: Input/output error
Failed to mount '/dev/sda1': Input/output error
Failed to load $MFT: Input/output error
Failed to startup volume: Input/output error
Failed to mount '/dev/sda1': Input/output error

---

### Post by alfiesty on 2008-01-31
ago said:

You can have a more verbose boot by hitting esc at the initial countdown, then press "e" on the first option, select theh kernel line and press "e" again to edit, then delete "quiet splash". Then hit enter and then "b"

I'm not sure where an initial countdown is so I tried
After starting - nothing
At grub - reboots computer
At KUBUNTU splash - nothing
After progress bar stops - nothing
At blank screen - nothing

I'm getting closer to waiting for a stable release of 8.0.? and trying again. sheesh! What a pain, my connection is so slow the iso takes 24 hours to dl. I still think you are on the right track, a painless way to try Linux.

Jim

---

### Post by the.ant on 2008-01-31
It's at grub. Omit the ESC, just edit the boot entry. 
'e' got to the right line 'e' delete quiet and splash 'return' 
'b'

voila, verbose output. 


BTW, Ubuntu is stable, Wubi is Beta. If you have such troubles starting it I would rather opt for the Ubuntu live-cd...

---

### Post by alfiesty on 2008-02-01
Just realized I not even getting to grub. I had just assumed it was grub cause I'd never seen that screen before. The banner at top says "Windows Boot Manager".
 I just found a book in our only bookstore called "Beginning Ubuntu Linux" with a disk, I'll try that. Part of my problem is that I live 100 miles (and 3000 feet higher) from the nearest town over 20,000 people. I've got no local guru to consult with. I was just hoping to use Wubi for it's minimum impact  / ease of removal. If I liked it, i'd then do a normal installation of KUBUNTU.

Jim

---

### Post by the.ant on 2008-02-01
wow, sounds like a pretty nice place to live! 

Good luck wih the install!
You seriously don't need to be or know a guru, just stick to everything default until you have your system up and running, I would therefore also recommend ubuntu instead of kubuntu. Personally, I like kubuntu better most guides and howtos are written for ubuntu.

---

### Post by superunknownnot on 2008-02-07
Any idea on this
[http://ubuntuforums.org/showpost.php?p=4243203&postcount=10](http://ubuntuforums.org/showpost.php?p=4243203&postcount=10)
Thanks again. I did follow all defaults

---

