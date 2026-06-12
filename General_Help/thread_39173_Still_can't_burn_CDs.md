---
title: "Still can't burn CDs"
date: 2005-06-03
forum: General Help
---

### Post by petehall on 2005-06-03
I'm unable to burn CDs in Ubuntu. I know that a lot of other people are struggling too, but I don't want to mess around aimlessly until I hit upon the solution by accident, so I hope someone can help me.

I've tried xcdroast and k3b - both of them would freeze at the splash screen when scanning for devices.

When I try burning a CD using gnomebaker or nautilus, it gets through the creation of the CD image, but then the computer freezes when it tries to do the burning. If I gksudo gnomebaker, it doesn't freeze, so this is my best bet at the moment.

So, this is the text that I get in the gnomebaker window:

```
cdrecord: No write mode specified.
cdrecord: Asuming -tao mode.
cdrecord: Future versions of cdrecord may have different drive dependent defaults.
cdrecord: Continuing in 5 seconds...
cdrecord: Warning: Running on Linux-2.6.10-5-k7
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
```

I was under the impression that the unsettled issues with Linux-2.5 and newer could be circumvented by being sudo, though please correct me if I'm wrong. This is what I get in the terminal window from which I started gnomebaker:

```
(gnomebaker:844** Message: splashdlg_set_text - Loading preferences...
** Message: creating [/tmp/GnomeBaker/root]
** Message: splashdlg_set_text - Detecting devices...
** Message: looking for device [1]
** Message: devices_add_ide_device - probing [hdc]
** Message: node [proc] mount [/proc]
** Message: node [/dev/hda2] mount [/]
** Message: node [/dev/hda5] mount [none]
** Message: node [/dev/hdc] mount [/media/cdrom0]
** Message: devices_write_device_to_gconf - Added [CW088D ATAPI CD-R/RW] [/dev/hdc] [/dev/hdc] [/media/cdrom0]
** Message: ---- key [drive name:], value [hdc]
** Message: ---- key [Can close tray:], value [1]
** Message: ---- key [Can read DVD:], value [0]
** Message: ---- key [Can change speed:], value [1]
** Message: ---- key [Can read multisession:], value [1]
** Message: ---- key [Can play audio:], value [1]
** Message: ---- key [drive speed:], value [48]
** Message: ---- key [drive # of slots:], value [1]
** Message: ---- key [Reports media changed:], value [1]
** Message: ---- key [Can read MRW:], value [0]
** Message: ---- key [Can write MRW:], value [0]
** Message: ---- key [Can write RAM:], value [1]
** Message: ---- key [Can select disk:], value [0]
** Message: ---- key [Can write CD-R:], value [1]
** Message: ---- key [Can lock tray:], value [1]
** Message: ---- key [Can read MCN:], value [1]
** Message: ---- key [Can write DVD-RAM:], value [0]
** Message: ---- key [Can open tray:], value [1]
** Message: ---- key [Can write CD-RW:], value [1]
** Message: ---- key [Can write DVD-R:], value [0]
** Message: looking for device [2]
** Message: Requested device index [2] is out of bounds.  All devices have been read.
** Message: splashdlg_set_text - Loading GUI...
** Message: toolbar style [both] [2]
** Message: toolbar style [both] [2]
** Message: selection data is /media/x/Photos/2005-02-19 Fan


** Message: received sel /media/x/Photos/2005-02-19 Fan

** Message: returning [/media/x/Photos/2005-02-19 Fan]
** Message: exec_run_cmd - umount /media/cdrom0
** Message: MessageDialog message [Error mounting /media/cdrom0

umount: /media/cdrom0: not mounted
]
mkisofs -V GnomeBaker data cd -p root -r -J -gui -joliet-long -o /tmp/GnomeBaker/root/gnomebaker_create_data_cd.iso -graft-points 2005-02-19 Fan=/media/x/Photos/2005-02-19 Fan (null)
** Message: exec_thread - parent created child with pid 8459
** Message: exec_thread - created child
** Message: exec_thread - child exited with code [0]

cdrecord dev=/dev/hdc gracetime=2 speed=12 -v -eject driveropts=burnfree -multi /tmp/GnomeBaker/root/gnomebaker_create_data_cd.iso (null)
** Message: MessageDialog message [Please insert the CD into the CD writer]
** Message: exec_thread - created child
** Message: exec_thread - parent created child with pid 8460
```

My drive is recognised as CW088D ATAPI CD-R/RW.

Please let me know what other information I can give to narrow this down.

Thanks,

Pete

---

### Post by Haegin on 2005-06-03
it seems to be throwing errors because of the kernel. 2.6 is the latest version of the kernel. Try updating gnomebaker or downgrading your kernel...

---

### Post by Joeb on 2005-06-03
I think that gksudo gnomebaker is the workaround to the problem you are having.  IIRC, it's been reported as a bug.  I can't remember what the actual problem was, though (whether kernel or one of the burning programs).  If you are wanting to use k3b, you tried gksudo k3b?  I don't know if that will work or not, but it's worth a try (I use gnomebaker for most burning).

---

### Post by petehall on 2005-06-04
Human Prototype: I'm running gnomebaker 0.3-3 (hoary) which I believe is the latest version. I would also prefer not to downgrade my kernel, though I'll certainly keep that in mind if nothing else works.

Joeb: The logs that I pasted in above were with gksudo gnomebaker - if I don't gksudo, the entire computer locks up. I tried k3b once before and it hung up on the splash screen, but I'll give it another go.

Thanks for your help.

Pete

---

### Post by Jormundgand on 2005-06-04
[QUOTE=petehall]Human Prototype: I'm running gnomebaker 0.3-3 (hoary) which I believe is the latest version. I would also prefer not to downgrade my kernel, though I'll certainly keep that in mind if nothing else works.

Joeb: The logs that I pasted in above were with gksudo gnomebaker - if I don't gksudo, the entire computer locks up. I tried k3b once before and it hung up on the splash screen, but I'll give it another go.

Thanks for your help.

Pete[/QUOTE]
 I'm in the same boat. The problem is ide-cd which is broken. ide-scsi works with CyberDrive devices, but we got sidelined when that got deprecated. There's some bug reports floating around but since the major hackers stopped work on it we've been left with no way to burn CDs. I'm contemplating buying a new supported CD-RW drive, if it's less work than the hassle of trying to get the kernel to play ball.

---

### Post by AgenT on 2005-06-04
[QUOTE=Jormundgand]I'm in the same boat. The problem is ide-cd which is broken. ide-scsi works with CyberDrive devices, but we got sidelined when that got deprecated. There's some bug reports floating around but since the major hackers stopped work on it we've been left with no way to burn CDs. I'm contemplating buying a new supported CD-RW drive, if it's less work than the hassle of trying to get the kernel to play ball.[/QUOTE]

I thought that the burning problem is a problem for all drives. Are you saying that some drives work while others do not? Why is that since they all use the same kernel "drivers"? Also, where is a good list of drive that work? They are somewhat cheap so I would be willing to replace mine as well with one that I know 100% will work with Ubuntu.

---

### Post by Jormundgand on 2005-06-04
Drives which work with ide-cd work fine, but some drives don't like ide-cd for some obscure reason (they were looking into this). CyberDrives fall into that category. Get any other drive and chances are it will work.

---

### Post by Joeb on 2005-06-04
[QUOTE=petehall]
Joeb: The logs that I pasted in above were with gksudo gnomebaker - if I don't gksudo, the entire computer locks up. I tried k3b once before and it hung up on the splash screen, but I'll give it another go.

Thanks for your help.

Pete[/QUOTE]

I'm wondering if something else is wrong.  While I do have to gksudo gnomebaker to be able to burn a CD, gnomebaker, itself doesn't hang (and I am also using 3.3-3 Hoary).

I am, however, running 2.6.10-5-386 for my kernel, whereas you are running k7.  You might try, for testing purposes, using the 386 kernel and see if that solves the problem.  If it works, then you can decide whether whatever the k7 kernel is getting you outweighs the burning problem.

Joeb

---

### Post by petehall on 2005-06-08
Ugh.

Joeb - the 386 kernel caused the computer to freeze, even when I was gksudo. Which was even worse than what I had with the k7 kernel.

Given how cheap CD drives can be these days, I think I'll get myself a new one. I'll try to find some sort of Linux CD-RW compatibility list before I make my purchase, to ensure that I don't waste my money.

I'm beginning to think that I shouldn't switch my girlfriend's computer from Windows to Ubuntu - after all, then I wouldn't have anyone to offload Linux-unfriendly hardware onto. Which would be a terrible waste.

Pete

---

### Post by petehall on 2005-07-04
Update: I purchased a [Sony CRX320E](http://www.dabs.com/uk/Search2/Product+Details.htm?quicklinx=33S3) and carefully navigated [this guide](http://linux.sgms-centre.com/howto/cdwriting/04.php) - I am pleased to say that it works and I have burned a CD (at 12x, though I expect that it can go much higher).

At some point in the future, when I'm feeling curious, I may go back and have another try with the CyberDrive to see if I can have any success. In the meantime, I can offer confirmation that the Sony CRX320E works well with kernel 2.6.10-5-k7.

Plus, the silver facia means that I don't have to hide the drive behind one of those nasty flippy doors that gets caught on the underside of the CyberDrive's tray.

---

