---
title: "HELP PLEASE!!!!! first dance with linux"
date: 2007-08-01
forum: General Help
---

### Post by rdbaron02 on 2007-08-01
Alright, I have a dell vostro 1400 laptop that is just purchased.  It has windows vista home on it, and i am trying to run a dual-boot with linux.  I have the partitions all set up, made sure the ubuntu cd i made was the correct file.  I chose the 32bit desktop 7.04 ubuntu version.  When i edit my boot order to boot from the ubuntu disc, it comes up like it should, but once it starts loading i get this message
[B]

"BusyBox v1.1.3 (Debian 1:1.1.3-3 ubuntu3)  Built-in shell (ash)
enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)[/B]

Any ideas, is it vista?, is it my ubuntu disc, im trying really hard to figure this out. PLEASE HELP!!!!!

---

### Post by dpar on 2007-08-01
Check the md5sum on the disk you downloaded. Could be a bad burn.

---

### Post by Seisen on 2007-08-01
Most likely it is your cd that you burned. What speed did you burn the CD at?

---

### Post by rdbaron02 on 2007-08-01
I checked the hash on it, just like the website said. But.... I did burn at max speed, so ill slow it down and increase the buffer. its a fresh vista installation, so i dont think its that, and i have a clean and formatted partition. anyone know what that code means.....besides failed OS load?

---

### Post by rdbaron02 on 2007-08-01
I slowed it from 24x to 8x, so we'll see if its another wasted cd. here goes. Also, i have a core 2 duo processor, i dont want the amd64 ubuntu, right?

---

### Post by rdbaron02 on 2007-08-01
i slowed it down, burned it again. and exact same thing happened. any ideas?

---

### Post by Naci Sey on 2007-08-01
Same problem here. Downloaded the file for 7.04 desktop using uTorrent, checked the resulting CD with md5sum, burned the image to a CD-RW, then tried options on two separate boot efforts to check the CD and start the Live CD. Got the same message each time as rdbaron reports.

Had no trouble with 6.06 LTS CD, so why with this one?

---

### Post by merlinus on 2007-08-01
You might try this, from a compilation of threads (no guarantees, however!):

SOLUTION TO /bin/sh: can't access tty; job control turned off
UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

-merlin

---

### Post by Naci Sey on 2007-08-01
Merlin, what is a SATA hard drive? The HD I want (eventually) to install Feisty on is a Fujitsu MPF3204AT.

---

### Post by merlinus on 2007-08-01
sata = serial ata
pata = parallel ata
ide = good old days hard drive controller

-merlin

---

### Post by Naci Sey on 2007-08-01
OK, well I don't know how to find out if my HD is serial or parallel. I checked System Information and saw IDE in several places (e.g., primary and secondary channels); nothing about SATA or PATA.

At any rate, was able to following your instructions to this point:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting

What you say next - "Ubuntu will start booting, but kick you out to a command prompt" - didn't happen. What I got instead was the original message:

[b]BusyBox v1.1.3 (Debian 1:1.1.3-3 ubuntu3) Built-in shell (ash)
enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)[/b]

---

### Post by merlinus on 2007-08-01
OK.  As I said, no guarantees.

Post your system specs, if possible.

Another problem may be with Dell's usual hidden restore partition.

Also, exactly how did you partition your hard drive?

-merlin

---

### Post by Naci Sey on 2007-08-01
My computer isn't a Dell. It was custom built in 2000 and upgraded with the second hard disk and a CD burner in 2003. 

It has two hard disks.
* WinXP is installed on the C drive (28 GB, hda0) 
* ubuntu 6.06 LTS is on the D Drive (19 GB, hda1) 

When installing Dapper, I chose to wipe hda1 and let the automatic process do the partitioning. 

RAM is 378 MB.

I'm still puzzled re why there's a problem at all with this new CD which has 7.04 on it, yet there was    no problem with the 6.06 LTS CD.

---

### Post by merlinus on 2007-08-01
There is a good chance that the problem lies with your video card.  What is it?

Feisty has problems with several different ones, since the drivers are proprietary.

Selecting "vesa" will normally get it up-and-running, and then the correct drivers can be installed.

But it seems that you cannot even get to a CLI.

-merlin

---

### Post by Naci Sey on 2007-08-01
Checking the Device Manager... 

Is this it?

**NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]**

---

### Post by rdbaron02 on 2007-08-01
i typed that command on the options line, and it booted vista, any ideas?

---

### Post by merlinus on 2007-08-01
Not sure, but it looks like an older NVidia card, which will definitely create installation problems.

You might try the text-based Alternate Install cd:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by rdbaron02 on 2007-08-01
i have an Nvidia 9600 GS, the 128mb one.

---

### Post by rdbaron02 on 2007-08-01
i got that same message when i typed in that command prompt too

---

### Post by rdbaron02 on 2007-08-01
i started downloading the text base version, will burn it to c-d once its done, and hopefully she fires

---

### Post by merlinus on 2007-08-01
Did you try Safe Video Mode at the startup screen?

-merlin

---

### Post by Naci Sey on 2007-08-01
Yes, I did. That was the first option I chose.

---

### Post by merlinus on 2007-08-01
Someone else may have a better answer, but as I wrote a bit earlier, you might try the text-based Alternate Install cd.

-merlin

---

### Post by Naci Sey on 2007-08-01
Thanks for trying, Merlin. Perhaps rdbaron will be back to report on success with the text-based CD. I'm reluctant to try that b/c of my inexperience, but if he tries it and it works, then...:p

---

### Post by rdbaron02 on 2007-08-02
i actually got the load to start, but i made an error somewhere while installing it, because it said something about X server error.  Ill clean out the installation and start again.

---

### Post by tashmooclam on 2007-08-02
I have the same problem with a brand new vostro dell laptop! It just came today.
I see the EXACT same error message.
I thought it was my fault.
It is probably NOT the CDs you have, because I installed the SAME ubuntu DVD onto this laptop I am typing on.
I tried to install the same ubuntu 7.04 dvd as this one has. Then, I tried the 64 bit dvd. Then, just for laughs, I tried the Linux Mint CD I had to show someone else.
NONE of them will install.
I think it has something to do with Dell? 
Could it be the partition I asked them to do?
I like the machine, it's really nice. But if I can't put linux on it, I'll send it back. 
:confused:

---

### Post by splintercellguy on 2007-08-02
Oh, please please next time create a new thread. It helps give us proper attention to your issue. Have you tried sudo dpkg-reconfigure xserver-xorg? Ditto for the OP.

---

### Post by Naci Sey on 2007-08-02
tashmooclam, my computer isn't a Dell, which suggests this isn't an issue specific to one manufacturer.

That said, I'm testing ubuntu on this machine b/c I've ordered a Dell Inspiron 1520. Need to familiarize myself with ubuntu in order to make the decision whether to add it to the new baby once it gets here (in another week - can't wait!)

---

### Post by tashmooclam on 2007-08-02
I did create another thread. I was seaching the forum and saw the same exact error message, and a vostro dell laptop. 
It has a SATA hard drive.
I'll complain to Dell and maybe their ubuntu dept. has a fix.

---

### Post by tashmooclam on 2007-08-02
I have the same message as RedBaron:


"BusyBox v1.1.3 (Debian 1:1.1.3-3 ubuntu3) Built-in shell (ash)
enter 'help' for a list of built-in commands.
/bin/sh: can't access tty; job control turned off
(initramfs)

---

### Post by chadteck on 2007-08-03
Check [this link]("http://forums.slickdeals.net/showpost.php?p=7479562&postcount=983") for my experience.  There is another post a few after it that has info regarding getting the sound working.

---

### Post by rdbaron02 on 2007-08-08
My ubuntu installation got pretty far, but it eventually failed. and in doing so, i lost vista also. So now im waiting on a new laptop from dell, they are sending a new one for free.

---

### Post by Naci Sey on 2007-08-09
That's really nice of Dell, rdbaron02, but I don't think the problem is with them. As mentioned in a previous post, my computer isn't a Dell and I've encountered the same problem, same message.

---

