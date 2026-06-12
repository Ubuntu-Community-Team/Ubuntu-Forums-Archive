---
title: "[SOLVED] NTFS partition on ext HDD"
date: 2014-10-02
forum: General Help
---

### Post by chkneater on 2014-10-02
I'm running 12.04 off a ext HDD, have been for a while.  I have an NTFS paration that I store everything on so that I can use it on someones windows sys..   Just recently the NtFS partition has been yielding this even tho the other partition is working, obniously:

Error mounting: mount exited with exit code 13: $MFTMirr does not match $MFT (record 0).
Failed to mount '/dev/sda3': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.


Please help!!  All my music is on there...

Has anyone had NTFS probs on an Ext HDD?

---

### Post by oldfred on 2014-10-02
First thing to run is chkdsk from Windows. 

Ubuntu runs fsck every 40 or 60 reboots, but Windows does not seem to automatically run chkdsk. It is up to the user to run it. And if you have errors then you must run it. 

You cannot run chkdsk from Linux, and the ntfsfix in Linux does very little and just turns on the chkdsk flag so Windows will run chkdsk.

If you do not have a Windows repair CD or flash drive some third party Windows tools may work.

 [http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
      
 [URL="http://www.hirensbootcd.org/"]http://www.hirensbootcd.org/
[/URL]
 [http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

[URL="http://www.hirensbootcd.org/"]
[/URL]

---

### Post by chkneater on 2014-10-02
Has anyone encountered problems with their NTFS partitions on an EXT HDD?

yeah, personally don't run windows, just wanted the compatibility with NTFS, I use Ext3 for Ubuntu

---

### Post by Iowan on 2014-10-02
Merged.
Reminder from the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Do not cross post, or post the same thing in multiple locations.

---

### Post by chkneater on 2014-10-02
tru, that was a mistake

Are there any tools that work with linux, the ones in synaptic don't do jack?

---

### Post by Bucky Ball on 2014-10-02
And merged again and moved to*** General Help***. 

Keep it on the one thread, please, as suggested by QIII. Avoid duplicates. It dilutes community effort and reduces, rather than increases, your chances of getting support. Good luck.

---

### Post by chkneater on 2014-10-02
tru, I made the same mistake about the same tiem, won't happen again plomise :-)

These commands yielded this:

hellkiller@hellkiller-desktop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="39f43acc-6254-42a6-ba3e-45a94f2ccaa0" TYPE="ext3" 
/dev/sda2: UUID="78a12334-f2c2-4135-8d08-ff9ea464955f" TYPE="swap" 
/dev/sda3: UUID="409CCDDC6304A495" TYPE="ntfs" 

hellkiller@hellkiller-desktop:~$ cat /etc/fstab

yielded nuthin???

ellkiller@hellkiller-desktop:~$ mount
/dev/sda1 on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/hellkiller/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=hellkiller)

I've tried every tool in synaptic and found nothing that worked, the device is recognized but the size doesn't match?  I think that's the source maybe?

How to fix this?

---

### Post by coffeecat on 2014-10-03
> **chkneater said:**
> How to fix this?

Read post #3, please. The answer to your question was posted hours ago.

---

### Post by chkneater on 2014-10-03
I really need help with this, all my multimedia is stored on there and I can't access any of it cuz of this problem..

> **coffeecat said:**
> Read post #3, please. The answer to your question was posted hours ago.

Uhhhmm No. I would have checked the very first reply?!  He was helpful but none of those answers or programs worked.  I don't have windows so I can't use chkdsk.  I've tried every thing I can find in synaptic and the forums have been no help....

---

### Post by matt_symes on 2014-10-03
Hi

> He was helpful but none of those answers or programs worked.  I don't have windows so I can't use chkdsk.

From post #3. 

Download HirensBootCD. 
Burn it to a CD or create a bootable USB.
Boot into the CD/USB by changing the boot options on your PC/Laptop.
Choose the XP option and it will boot into a mini XP environment.
From there you can run chkdsk on the drive.

You don't need to have windows installed on any of your PCs. This does assume your PC/Laptop has sufficient memory.

Kind regards

---

### Post by chkneater on 2014-10-03
That just may werk... I'm gonna work on that now, thanks so much!!  I'll let you know wut happens...

---

### Post by Mark Phelps on 2014-10-03
> none of those answers or programs worked.

Those are NOT programs.  The Minitool Partition Wizard Boot CD is an ISO file you can download and burn to a CD.  Then, you boot from the CD and use the option to Check the filesystem.

Since you did not mention any of this, I'm presuming you did NOT try the links provided in post #3.

---

### Post by chkneater on 2014-10-03
Actually, Yes I Did... now STOP telling me what I am and am not doing... the fact it that answer would not have worked as I have found the fix, so stop harassing me about it.

Mat, you're solution seems to be working thus far, I have run into one prob., I can't run the /f option with chkdsk cuz the drive is write protected??  What do I do to remove write protection?

---

### Post by matt_symes on 2014-10-03
Hi

Having looked at chkdsk's flags from here...

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

... i would try

```
chkdsk C: /f /r /x
```

Change C: as appropriate. Run the above command repeatedly until there are no errors.

This was oldfred's solution so i cannot take credit for it.

BTW: I would image the hard drive first before trying any more repair attempts.

Kind regards

---

### Post by chkneater on 2014-10-03
That sounds like a solution that should work, I'll let ya know and thanx!!!

I keep getting an error about not being able to open the volume...

how do I turn off the write protection from the volume so /f will work?

---

### Post by matt_symes on 2014-10-03
Hi

> I keep getting an error about not being able to open the volume...

A question: Is the error message you are getting "Cannot open volume for direct access" ?

> how do I turn off the write protection from the volume so /f will work?

IIRC, That's the reason for the /r (recovery) flag and the /x flag forces an umount so chkdsk can actually run.

I'll see if there is another way.

**EDIT:**

Just a though but you are running chkdsk on the correct drive ?

Kind regards

---

### Post by chkneater on 2014-10-03
In which way do you mean drive, as in windows C:, or ubuntu sdawhatever
How would I switch the drive chkdsk is done on?  I thot it was done on all of them

Oh and you were correct 'cannot open volume for direct access'

---

### Post by matt_symes on 2014-10-03
Hi

> **chkneater said:**
> In which way do you mean drive, as in windows C:, or ubuntu sdawhatever

I meant as in Windows C:. I was just asking you to double check that the drive you were running chkdsk is the drive in your hard drive box and not not the LiveCD/USB drive.

> How would I switch the drive chkdsk is done on?  I thot it was done on all of them

You change the drive chkdsk runs on by changing the drive letter you pass to the chkdsk binary.

How exactly are you running chkdsk ?

Kind regards

---

### Post by matt_symes on 2014-10-03
Hi

> **chkneater said:**
> Oh and you were correct 'cannot open volume for direct access'

I am wondering if chkdsk in HirensBootCD is suffering from this bug.

[https://support2.microsoft.com/kb/823439](https://support2.microsoft.com/kb/823439)

Anyway this thread seems to be turning into a Microsoft support thread. 

Surely you must have a friend that has a windows box from which you can run chkdsk on the external hard drive ?

Kind regards

---

### Post by chkneater on 2014-10-03
I don't know if it's a Hirens bug or not but I am willing to bet it was user error, I've logged back into ubuntu for now, and tomorrow I will try that..  what command to get fschk to check sda3 (the NTFS part)?

---

### Post by oldfred on 2014-10-03
The fsck package is only for the ext2,ext3 & ext4 family of Linux formats.

See this:
 man ntfsfix

Confirm which partition is NTFS.
sudo parted -l

The you can run this, but again chkdsk is all the really works. Change example with sda3 to correct NTFS partition.
      
 sudo ntfsfix /dev/sda3

Only after you have run chkdsk, which clears most errors, should other fixes be considered as they may make it worse as then chkdsk cannot fix it.

---

### Post by matt_symes on 2014-10-04
Hi

> fschk

??? 

Is that a typo ?

See oldfred's previous post.

Kind regards

---

### Post by chkneater on 2014-10-04
I ran the command 'sudo ntfsfix /dev/sda3' and I still get the 'cannot access volume cuz it's write protected crap??  the command did see that there were inconsistencies in the size of that partition so I am sure that it is the prob here...

---

### Post by oldfred on 2014-10-04
As said the ntfsfix set the chkdsk flag so Windows will run chkdsk on next reboot if system partition. Or you run chkdsk from your Windows repair CD or Flash drive.

Once chkdsk flag is set Linux tools will not mount NTFS to prevent damage that then chkdsk cannot fix.
You may be able to force mount in read only mode, but I have not tried that.

---

### Post by chkneater on 2014-10-04
Awwwww SNAP... after running the command and then booting into mini-windows with the Hirens ISO and running chkdsk, I ran chkdsk /f, it did not like that but gave me a different error?!  Long story short I can acces the partition now from Ubuntu... the icon is not on the desktop but so what, at least I can get to my music and other files thanx so much!!!

---

### Post by Bucky Ball on 2014-10-04
Excellent work to all concerned. Getting an icon on the desktop is the easy bit!! I don't use Unity, so can't help with that, but perhaps post a new thread if you need help there. Good luck and enjoy! ;)

---

### Post by oldfred on 2014-10-05
Chkdsk does not fix everything in one pass, so often it needs to be run more than once and maybe with different parameters. It seems there are different versions and each newer version of chkdsk has new parameters. 
Not sure then what version is in Hirens.

 Always run chkdsk and run again until there are no errors, that may be all that is required
chkdsk c: /b
/b includes /r
[http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc730714%28v=ws.10%29.aspx)

The older XP version used either /f or /r as parameters.

---

### Post by chkneater on 2014-10-09
it seems anytime I ran chkdsk with the C: parameter it hated that... no command worked at all except for chkdsk itself... one weird thing and this maybe related to just having an ext HDD is that it will never boot the first pass.  

This is what I've had to do to get this thing booted since I got this HDD:  first I unplug the Ext HDD, turn on the comp, before the BIOS splash I plug in the EXT HDD quickly, and because I have the image-boot file it boots... Now since this prob with the Ext HDD reading the wrong sizes, and somewhat fixing it so far, I have to do the whole process twice!  the first tiem it won't boot, I think the error is 'file: not found'.. however after turning it off and doing the whole thing over again, it boots fine right into grub...  

I plan on running chkdsk again, maybe it will let me run some of the parameters, however I'm skeered since gparted the MST and MBR are all reading the same info and the drive is working?  Whutdya think?

---

### Post by oldfred on 2014-10-09
Not sure what it going on then. And know less about details of NTFS partitions.

I thought chkdks without parameters like /b or /f, only c: or d: was just a test mode and made no fixes.

---

### Post by chkneater on 2014-10-09
Apparently it did something... the weird thing is I ran chkdsk a number of times before I checked the file manager in the Start Menu and then checked gparted and sure enough it was finally showing the correct size and all the files were still there, which is exactly WHY I created an NTFS partition LOL...

Anyway, always had boot probs, cuz of the Ext HDD, finally found grubimage-boot or something along those lines, I think I placed it in one of the boot folders and while experimenting that is when I realized that if I unplugged the Ext. while the computer is booting running it's start tests and stuff but plugged it in before the Bios splash (short tiem frame LOL) that it would boot?!

Now after this ordeal I have to do the process twice due to 'error: file not found', but it boots at least and I have my files!

I'monna try to get the icon on the desktop now...

---

