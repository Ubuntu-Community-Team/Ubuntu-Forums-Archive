---
title: "DVD burning not working - considering Windows"
date: 2006-12-03
forum: General Help
---

### Post by Angellis_ater on 2006-12-03
I've seriously given up. When I first "converted" to Ubuntu there was the prerequisite time of confusion and stuff not working. But since the day I installed Ubuntu my ability to burn flawless DVDs has been ****** up.

Then I upgraded to Edgy Eft, hoping that the new stuff might contain a solution. Imagine my surprise when my computer no longer even DETECTS empty DVDs. If I start the computer with an empty DVD in the burner, it is detected, but any burning only gets to 2% and then it ejects it with an error.

And I've tried them all - GnomeBaker, Brasero, K3B, DVD Decrypter via Wine. Nothing works. And before all of this started, the DVDs were corrupt 4 out of 5 times.

Since I'm a movie buff, I NEED to be able to burn DVDs. Can someone PLEASE HELP?

---

### Post by Angellis_ater on 2006-12-03
This is what my Brasero error log says when it fails:

```
imager (BraseroLocalImage) set_output
job (BraseroLocalImage) set_task
imager (BraseroLocalImage) get_track
job (BraseroLocalImage) set_task
Session starting:
	flags			= 16727 
	media type	= 0
	speed		= 8
	track type		= 8
	track format	= 2
	output		= none
job (BraseroGrowisofs) set_rate
recorder (BraseroGrowisofs) set_drive
recorder (BraseroGrowisofs) set_flags
job (BraseroGrowisofs) set_source
job (BraseroGrowisofs) set_task
recorder (BraseroGrowisofs) record
process (BraseroGrowisofs) getting varg
growisofs (BraseroGrowisofs) set_action
process (BraseroGrowisofs) got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-speed=8
	-dvd-compat
	-use-the-force-luke=tty
	-Z
	/dev/scd1=/home/angellisater/Desktop/fiss3-wttl.dvdr.iso
process (BraseroGrowisofs) launching command
process (BraseroGrowisofs) stdout: Executing 'builtin_dd if=/home/angellisater/Desktop/fiss3-wttl.dvdr.iso of=/dev/scd1 obs=32k seek=0'
process (BraseroGrowisofs) stderr: /dev/scd1: "Current Write Speed" is 8.2x1385KBps.
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stdout:          0/4618084352 ( 0.0%) @0x, remaining ??:?? RBU 100.0%
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=0h failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting

```

---

### Post by xopher on 2006-12-03
Have you tried running any of the apps with root privileges? Just to make sure it isn't a permissions issue.

Check out how it's recognized by hdparm

Make sure it's not a hardware failure.

---

### Post by Angellis_ater on 2006-12-04
Ok, colour me a moron. How do I recognise if it's a permission issue with hdparm? I am 99% sure it ain't hardware failure since the drive worked perfectly in Windows before the transfer to Ubuntu and immediately started acting up after that.

---

### Post by _mrv on 2006-12-04
> **Angellis_ater said:**
> I am 99% sure it ain't hardware failure since the drive worked perfectly in Windows before the transfer to Ubuntu and immediately started acting up after that.

I had a similar issue with my DVD burner. I thought I had somehow broken my Ubuntu installation, but then I dual-booted into my old Windows installation where the DVD burner previously worked and noticed that the burner was broken.

I bought a new one and never had a single problem with burning ever since.

---

### Post by Angellis_ater on 2006-12-04
I guess I'll just have to re-install Windows or rip the burner out of the machine and take it over to a friends house.

The thing is it started acting up the very day I changed to Ubuntu...

---

### Post by Angellis_ater on 2006-12-04
And for those who are interested, I can't even MOUNT an empty DVD anymore. K3B can "forceburn" but then errors out with an input/output error.

When I try to mount it via the terminal it fails with the following message:
```
angellisater@Omega1:~$ sudo mount -t iso9660 /dev/scd1 /media/cdrom
mount: blockenhet /dev/scd1 är skrivskyddad, monterar som endast läsbar
mount: fel filsystemstyp, felaktig flagga, felaktigt superblock
       på /dev/scd1, codepage saknas, eller annat fel
       I en del fall kan användbar information hittas i syslog
       - prova dmesg | tail eller något liknande

```

Which essentially means about everything is wrong.

When I use dmesg | tail I get this:

```
angellisater@Omega1:~$ dmesg | tail
[17185071.972000] attempt to access beyond end of device
[17185071.972000] sr1: rw=0, want=68, limit=4
[17185071.972000] isofs_fill_super: bread failed, dev=sr1, iso_blknum=16, block=16
[17185214.260000] attempt to access beyond end of device
[17185214.260000] sr1: rw=0, want=68, limit=4
[17185214.260000] isofs_fill_super: bread failed, dev=sr1, iso_blknum=16, block=16
[17185360.528000] attempt to access beyond end of device
[17185360.528000] sr1: rw=0, want=68, limit=4
[17185360.528000] isofs_fill_super: bread failed, dev=sr1, iso_blknum=16, block=16
[17185362.588000] cdrom: This disc doesn't have any tracks I recognize!

```

Anyone?

---

### Post by alextud on 2006-12-05
Same problem for me, i can't burn a blank dvd, but I can erase my DVD-RW and burn an ISO image, also i burn an dvd on windows and make it appendable( on other computer), so I come back to my dvd-burner and finished succesfully. I do not think that my burner is broken;

---

### Post by timcredible on 2006-12-05
try a different livecd distro to see if it's the distro.  i would recommend pclinuxos or mepis.  boot with the new distro, mount your ubuntu drive, and try burning the .iso you've created with k3b.  i haven't tried burning dvds with ubuntu, but i've burned well over 200 dvds (home movies of the grandkids, photo slideshows, backups of data, liveDVD distros, etc) with several other distros on several different PCs and different dvd burners, and i've never had a problem.  i always use k3b.  i've never tried copying a movie dvd though.

---

### Post by Angellis_ater on 2006-12-06
The irony here is that I'll have to find someone else who can burn a LiveCD for me, since I can no longer do it myself.

So, can someone please guide me to where I can find LiveCDs with the above distro's? I'll try to find them myself via Google, but just to make sure.

Thanks for the tip!

---

### Post by Artemis3 on 2006-12-06
I'll tell you my experience.
First and foremost **enable dma for your burner**, ubuntu doesn't and you need to change a config file so it always does it at boot.
Edit /etc/hdparm.conf ```
sudo gedit /etc/hdparm.conf
```

you need to add at the end something like:

```
/dev/[color=blue]hdd[/color] {
        dma = on
}
```

[color=blue]hdd[/color] needs to be your burning drive, which can be different in your system. You have to find that out, try the command: ```
dmesg | grep ROM
```

**Nautilus** works but the **lack of options** and information set me on a quest to find the best non k3b gui burning app.
The current **brasero** package in Edgy Eft is **broken**. The previous version worked for me. Now it simply locks the drive and drags the system with it.
**Graveman** works, but the burning is **slow**. It seems to do things "on the fly". Be sure to never use burning simulation, it will destroy your disc.
**GnomeBaker** works, BUT it uses cdrecord, cdrecord unpatched **doesn't work with multisession** dvds BIG PROBLEM to me.

Sadly i think its either Nautilus or command line growisofs for me.

If your image is already made (.iso) its no big deal to use the command line, its something like ```
growisofs -Z /dev/[color=blue]hdd[/color]=image.iso
```

This comes from the growisofs manual, i think i'll be burning things like this from now on.

```
To master and burn an ISO9660 volume with Joliet and Rock-Ridge  exten&#8208;
       sions on a DVD:

            growisofs -Z /dev/dvd -R -J /some/files

       To append more data to same DVD:

            growisofs -M /dev/dvd -R -J /more/files

       Make  sure  to  use  the same options for both initial burning and when
       appending data.

       To finalize the multi-session DVD maintaining maximum compatibility:

            growisofs -M /dev/dvd=/dev/zero

       To use growisofs to write a pre-mastered ISO-image to a DVD:

            growisofs -dvd-compat -Z /dev/dvd=image.iso
```

---

### Post by pg99 on 2006-12-06
> **Angellis_ater said:**
> The irony here is that I'll have to find someone else who can burn a LiveCD for me, since I can no longer do it myself.

So, can someone please guide me to where I can find LiveCDs with the above distro's? I'll try to find them myself via Google, but just to make sure.

Thanks for the tip!
There are some liveCD distros which can be booted from an iso on the hard drive so you wont need to burn a CD at all.  Example for Kanotix here [http://kanotix.com/FAQ-id_cat-63.html#q298](http://kanotix.com/FAQ-id_cat-63.html#q298)

---

### Post by Angellis_ater on 2006-12-10
Ok, I've tried to get my head around PCLinuxOS and failed - feel like a moron. Anyone else have a suggestion?

I will try out Kanotix as soon as possible.

---

### Post by Shay Stephens on 2006-12-10
Not that this has anything to do with the current problem, but I worked as a pc tech for years.  Aside from the power supply, and cpu fan, optical drives are the most unreliable part of the computer.  Don't be surprised one can fail in the weirdest ways at any time.

---

### Post by Angellis_ater on 2006-12-17
I trust you about that, I've had DVD's and CD's fail for strange reasons but this one seems to work well enough on a Windows XP system - which seems to be my only solution. A dual boot just to be able to burn DVD's... but at this pace it seems like I have to re-format my entire computer since I read that Ubuntu's file system isn't the same as Windows...

JOY!

---

### Post by Angellis_ater on 2006-12-17
After the latest kernel update, it has begun to find empty DVDs completely at random. Sometimes it finds them, sometimes it doesn't. Thought that might shed SOME light on this issue?

---

### Post by Angellis_ater on 2006-12-21
Does anyone have any ideas or suggestions?

---

### Post by Toadmund on 2007-03-16
Hmmm,:-k methinks your burner is toast, I had a defective one once, it failed to record, sometimes failed to even show up as an icon in XP.
Maybe burning all those .iso's was the final straw, it broke it's back?

---

### Post by Toadmund on 2007-03-16
Actually mine doesn't either:( 
A bug that's got to be fixed, is edgy not reading my burner?
(LG super multi)

---

