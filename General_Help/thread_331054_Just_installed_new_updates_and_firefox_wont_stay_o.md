---
title: "Just installed new updates and firefox wont stay open.!!"
date: 2007-01-04
forum: General Help
---

### Post by Lethal84 on 2007-01-04
Help!!!! I just updated my system and now firefox won't stay open. Firefox will open, load the home page, and then automatically close. I accessed the web by opening the terminal and clicking on the  get help online option. Is there anyway to remove updates? I really don't want to reinstall my system right now. Any help is appreciated, thank you.

---

### Post by tbroderick on 2007-01-04
Are there any error messages when you start firefox from a terminal? Did you try moving or deleting your firefox settings in your /home folder?

---

### Post by robenroute on 2007-01-04
Hi there,

Exact same problem here. Starting Firefox from the command line gives the dreaded "segmentation fault".

I'm surprised, so far only 1 other person has reported this upgrade problem; there must be thousands of people....

---

### Post by twowheeler on 2007-01-06
Yes, there are other threads about this.  Until it is fixed, downgrade your firefox to the previous version.  Open synaptic, search for firefox, click on Package --> Force Version, and pick the previous one.

---

### Post by tenjin1 on 2007-01-06
> Help!!!! I just updated my system and now firefox won't stay open.

What updates are you referring to? The firefox update or system file updates? Do you know which particuylar updates were applied before this started happening? Alot of users have reported updates to Firefox or Flash updates are causing FF to crash.

---

### Post by eleach on 2007-01-06
I have same experience here.

I reinstalled previous version using "Force version" as described in this thread and it is working again as before.

THANKS for that tip, twowheeler.

The us.archive.ubuntu.com server was very slow. Lots of people having the same problem!

---

### Post by KYhillbilly2006 on 2007-01-06
I am not having that closing problem but my problem is trying to stream using real player.  Here is a screen shot of what I am talking about.

[IMG]http://www.inspiredhandcraftedjewelry.com/img/Screenshot.png[/IMG]

If you can't read it, the box reads:  Could not find appropriate hxplay or realplay in the system path to use as an embedded player.

Realplayer plugin was working fine yesterday but this morning I seen there was a firefox update in the updater so I downloaded and now this happens.

---

### Post by jaimevz on 2007-01-06
I'm on the same boat here.  I tried the force previous version suggestion and that did not work fo me.  I'm pretty sure my problem has to do with one of the plug ins.  I can only browse the simplest of websites anything with flash will crash Firefox.  My solution for now is to use Opera and hope for a quick update.

---

### Post by nix4me on 2007-01-06
No problem with my 2 installs.  Did you try deleting your .mozilla dir?  Or search launchpad for a bug report?

Make sure there is a bug report, otherwise the developers won't know there is a problem.

nix4me

---

### Post by Gen2ly on 2007-01-07
firefox crashed repeatedly, just started happening after the 2.0.0.1 update.

Page it crashed on:

gmail
soucefourge download page
forums.macnn.com
and several others

started it in terminal this time, I'll return terminal feedback when it happens next.

---

### Post by Gen2ly on 2007-01-07
Woah, immediate crash.  I went right to gmail and got this from terminal app:

> The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by Gen2ly on 2007-01-07
got it fixed.  set my monitor to 24 bit color from 16.  read in [this forum]("http://www.ubuntuforums.org/showthread.php?t=286069") that 16 bit can cause firefox to crash.

---

### Post by JallenDragonhide on 2007-01-08
upgrading to 24 bit isn't really an option for me..

Ubuntu LTS 6.06 with fresh upgrade of firefox 1.5.dfsg+1.5.0.0-0ubuntu0.6.06

in terminal I get segmentation fault shortly after firefox stars up.

---

### Post by JallenDragonhide on 2007-01-08
> **twowheeler said:**
> Yes, there are other threads about this.  Until it is fixed, downgrade your firefox to the previous version.  Open synaptic, search for firefox, click on Package --> Force Version, and pick the previous one.

I tried that, but it asks me to uninstall ubuntu-desktop as a dep... I'm not sure I want to do that :)

---

