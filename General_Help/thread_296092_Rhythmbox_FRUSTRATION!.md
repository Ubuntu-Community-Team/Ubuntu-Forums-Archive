---
title: "Rhythmbox FRUSTRATION!"
date: 2006-11-09
forum: General Help
---

### Post by MrFSL on 2006-11-09
Greetings all,

I am having a problem burning audio cd's using Rhythmbox. I can burn cd's using both Serpentine and Banshee as well as Gnomebaker.

I checked my permisions for cdrecord and they are set SUID as root. I checked my groups and I am part of the cdrom group.

When started from the command line, the only suspicious thing that I see is that Rhythmbox (or cdrecord) turns off burnfree even though it is supported. When I do a **sudo cdrecord -scanbus** i get the following:

```
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
cdrecord: No such file or directory. Cannot open '/dev/pg*'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord:
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

```

Truly I wish to use Rhythmbox and not Banshee due to stability and design. Does anyone have any insight they might lend?

Thank you once again for this useful forum.

---

### Post by Sef on 2006-11-09
> cdrecord: Warning: Running on Linux-2.6.15-27-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.

The above seems to be the cause.

> cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

The above is a way to check out what is wrong.

Applications > Accessories > Terminal

sudo aptitude update

sudo aptitude install cdrtools-doc

then try this to get the readme docs:

sudo gedit /usr/share/doc/cdrecord/README.ATAPI.setup

---

### Post by MrFSL on 2006-11-10
@Sef
Thank you. Often not reading IS a leading cause of frustration with Linux I agree. - However - if you read the suggested document you see that it offers no help, and encourages you to do a *cdrecord -scanbus* and also to setup a group to use cdrecord with proper permissions... both of which I outlined that i had done already. ;) 

I ran Rhythmbox once again from terminal and *ctrl + c* before it failed. (This left the already converted wav files in my temp directory. i then scrolled up the terminal until I found the line initiating cdrecord:
```
cdrecord fs=16m speed=4 dev=/dev/hdc -dao -v -copy -audio -pad /tmp/rb-burn-tmp-2hEjuG/rb-burn-tmp.IHZTK1.wav -copy -audio -pad /tmp/rb-burn-tmp-2hEjuG/rb-burn-tmp.RP9eBu.wav -copy -audio -pad /tmp/rb-burn-tmp-2hEjuG/rb-burn-tmp.EFlUkG.wav -copy -audio -pad /tmp/rb-burn-tmp-2hEjuG/rb-burn-tmp.5Dd2uc.wav -copy -audio -pad /tmp/rb-burn-tmp-2hEjuG/rb-burn-tmp.eFMw1R.wav -copy -audio -pad /tmp/rb-burn-tmp-2hEjuG/rb-burn-tmp.lPEsQC.wav -copy -audio -pad /tmp/rb-burn-tmp-2hEjuG/rb-burn-tmp.pMuvWr.wav
```

I exited out of everything imaginable (even the GUI) and tried this command with a new blank CD-R. It failed as before. Then I ran it with _***-driveropts=burnfree***_ and it created the disk without a problem. The question is, how can I get Rhythmbox to not turn off burnfree? Or, rather, how do I get Rhythmbox to turn on Burnfree? Or, how can I configure cdrecord to always use Burnfree by default?

Take your pick! Anyone have some insight?

Thank you again.

MrFSL

---

### Post by doclivingston on 2006-11-10
> **MrFSL said:**
> Then I ran it with _***-driveropts=burnfree***_ and it created the disk without a problem. The question is, how can I get Rhythmbox to not turn off burnfree? Or, rather, how do I get Rhythmbox to turn on Burnfree? Or, how can I configure cdrecord to always use Burnfree by default?

It sounds odd that it won't burn with BurnFree turned off. Rhythmbox turn off BurnFree because if it kicks in it will corrupt the CD, BurnFree is great for data CDs but completely buggers up audio ones.

I think that making it not turn it off would require editing the source code to libnautilusburn (what it uses to burn CDs) and recompiling it.

---

### Post by MrFSL on 2006-11-10
@doclivingston

Whats up doc?... Ha!

Anyways... yeah well I found it odd as well but its the only way I can get it to burn usnig cdrecord from the command line. The resulting disk worked with now issues. And no, I'm not in any mood to recompile any more libraries. ;) 

Do you know about Serpentine? - Because Serpentine would burn an audio disk without issue. Gnomebacker is the same way. Banshee burned an audio disk but they have a checkbox for Burnfree and I had it checked (aka the reason why I turned it on in the first place). It happens, you know, in linux, about every 2-3 months... you come across an oddity issue like this and you just can't get around it. Since switching to Ubuntu this is the first time I have ever turned to the Linux "Community" for support. In the past I would just beat my head against it until I found a resolution or I would give up and move on to another app so I really appreciate the feedback.

Any more feedback? Anyone else?

Thank you.

MrFSL

---

