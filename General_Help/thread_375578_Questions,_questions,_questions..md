---
title: "Questions, questions, questions."
date: 2007-03-03
forum: General Help
---

### Post by Entity` on 2007-03-03
When answering one of my questions, I request that you insert the number representing the question you are answering in front of your answer.

     1.  I have libntfs8 and all relevant items installed, but cannot access my NTFS drives still.  What must I do?  Note: I can now see them as volumes with removable storage.

     2.  How do I use Automatix to install Friefox 2.0?

     3.  I am distraught at the sight of VLC media player being removed from the applications list in the Multimedia section of Add Applications.  It was removed after I upgraded to 6.06 LTS and I want my favorite media player back.  How do get it back.  I prefer it because it supports every media format under the sun (except Shockwave; and for good reason) and its user iterface is highly manageable (e.g. very simple, no confusing menus, bare theme (you can add themes though)).

     4.  My soundcard currently is a Creative Labs Sound Blaster Live! (just Live!, not Live! Platinum or anyting else).  I am searching for proper drivers for it so I can make full use of its nice 24bit proc (everything sounds tinny and lifeless now).  Its model number is CT4840.

     5.  I have an old TV Tuner card made by the now extinct STB Systems.  It was made in 1998, has these features:  Coaxial IN (TV Tuner), VGA out, S-video out, and composite out.  Interesting little device, isnt it?  The 2 strings of numbers that identifies it are as follows:  1X0-0484-301 and 201-0253-00X.  Im wondering if I can use it with Zapping TV Viewer or some other program.  Drivers are something I have given up hope on.

     6.  This question is about Grub.  The number of Ubuntu versions that I choose from is rediculous.  5 options plus recovery modes, and one of the choices is broken anyway!  How do I delete the extra entries (assuming that your first choice is ALWAYS the latest and NON-broken versoin.  I only use Grub to Dual Boot Windows XP (Thats About to change if I get SAMBA up and running and when I get to use NTFS partitions upon bootup of Linux.

Thats All for questions now. Thanks in advance for all who can contribute.

---

### Post by tgalati4 on 2007-03-03
6.) sudo nano -B /boot/grub/menu.lst

set "howmany=7" to limit the number of distros to be added and shown.

5)  Find the video chipset on the Tuner card and do a forum search and google search.  It may be similar to a more common TV card.

4)  lsmod to see if CT48XX drivers are loaded.

3)  Try Automatix2 at [www.getautomatix.com](www.getautomatix.com)

2)  See 3 above.

1) Did you try mounting the drive?
sudo mount /dev/mycheesywindowsNTFSdrive /media/adirectorythatIcreatedbeforehandtomountmycheesydrive

---

### Post by Entity` on 2007-03-03
I thank you for you assistance,  All your advice is most helpful, although I am not familliar with Ismod at all.

---

### Post by NewOldTimer on 2007-03-03
#3 - VLC is in add & remove in edgy{never used dapper}
#4 - Sb Live drivers should already be installed, don't know the code but you can look thru device manager /soundcard driver #EMU10k1,   probably a wrong setting in Sb/sound preferences causing your problems

---

### Post by tgalati4 on 2007-03-03
In a terminal:  lsmod

lsmod will list what modules are loaded.  Your sound card will have a driver that looks like snd_CT48XX or similar.  Lack of such drivers means that more work is involved in setting up your sound.  Sound Blaster cards are common and have good support under Linux.

---

### Post by Entity` on 2007-03-04
Thank you for describing lsmod.
Nope cant see snd_CT488XX anywhere nor do I see any related items.  What must I do now?

Question 3 is vioded cause I fixed it myself; however, VLC was nowhere to be seen in Add Applications.  Probobly because Im using Dapper.

---

### Post by NewOldTimer on 2007-03-04
try this 

sudo modprobe -l emu

should show driver  which if I'm not wrong is EMU10k1 and should already be installed

---

### Post by Entity` on 2007-03-04
> **NewOldTimer said:**
> sudo modprobe -l emu

It gives nothing at all, even when waiting.

---

### Post by NewOldTimer on 2007-03-04
#4   I'm at a loss maybe this will help   [http://ubuntuforums.org/showthread.php?t=161817](http://ubuntuforums.org/showthread.php?t=161817)

---

### Post by Entity` on 2007-03-04
thanks, the only thing i had to do is mess with the ac97 setting while playing a test track.  Dropping the ac97 setting all the way to 00 restored life to my audio.  Increasing the 'wave' setting reduced the distance I had to turn the speaker knob to get to the desired volume level.

---

### Post by tgalati4 on 2007-03-04
It is helpful to remember that most computer sound hardware is built like a small audio mixer.  The AC97 is an analog-to-digital conversion chipset.  It takes a WAV file (digital) and turns it into sound (analog voltage to drive speakers).  The "0" is probably 0-Level, which in sound parlance means maximum level or "0" decibels.  The larger numbers is decibels below maximum.  For instance 40 is really -40 decibals below maximum volume level.  That would explain the backwards response you are getting.

It looks like sound is working, you just have to turn up the levels of the appropriate channels, including the master level to get sound.

---

### Post by Entity` on 2007-03-04
#5):  While I did not take time to crack open my steel cube (no really it is a steel cube) to check for a chipset; I ran this in the console:

lspci

and got:

0000:02:06.0 VGA compatible controller: Brooktree Corporation BtV 2164 (rev 09)
0000:02:06.1 Multimedia controller: Brooktree Corporation BtV 2165 (rev 09)

---

### Post by tgalati4 on 2007-03-05
Never heard of Brooktree.  Familiar chipsets are Intel, Via, and Sis.  It's possible that Linux will have problems with a chipset that is not standard or common.  Perhaps others have tried Ubuntu or other flavor of Linux on this chipset.  Try a google search for Linux and Brooktree and see what comes up.

Good luck.

---

### Post by Entity` on 2007-03-13
I just want to know if i can use it with zapping tv viewer cause i never tried it before.

---

### Post by Entity` on 2007-03-31
After a long withdrawl from the cold paradise of Antarctica where all linux users thrive, I have returned and am still yet confused evermore yet wont give up.

1):  The more I try to mount my NTFS drives, the more confusing it gets:

```
server@Server-01:~$ sudo mount NTFS /dev/hdf /media/F:
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

```

(cant remember the number):  How do I tie my STB/Booktree video card to zapping TV veiwer?
The same goes for Kpilot, how do I tie my (usb) handspring visor to Kpilot?

And adding on;
7): never mind, i figured it out myself :P

---

