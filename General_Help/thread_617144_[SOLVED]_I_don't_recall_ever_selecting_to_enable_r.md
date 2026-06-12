---
title: "[SOLVED] I don't recall ever selecting to enable remote login options."
date: 2007-11-19
forum: General Help
---

### Post by Banacek on 2007-11-19
I bring up the login window preferences GUI, select the security tab and click the button for the Xserver configuration GUI. In that I select the chooser instead of the greeter for the launch. That's the only thing I changed for the Xserver. If I logout and into another account, it all seems to work just fine, at least at that time. However, on the very next reboot I get the preliminary orange screen but instead of the chooser GUI an XDHMCP window immediately pops in and tells me no networks are found. My options are for help, search and cancel. The help option isn't. The search turns up nothing, of course, because I never set up anything that I wanted to remotely log into and I never wanted to turn on XDHMCP in the first place. I just want to login to the machine I'm already using. If I cancel, then the GUI and orange screen disappear for about a half minute but there's a text only login available. Then, the orange screen comes back on and the same XDHMCP window pops back in for a repeat of the same.

Has anybody heard of this before?


On my last boot into recovery mode I managed to get a USB memory stick mounted and made copies of xorg.conf, Xsession.options, Xwrapper.config files and the entire contents of /etc/X11/Xsession.d/ in case anyone wants to see those. Anyone? I would like to know in which file on what line can I edit to change it back so that GNOME launches with the greeter and not the chooser. What other files should I copy to look at?

My mainboard is a Gigabyte GA-7VAXP with dual BIOS using an AMD Athllon T-bird 1.8 GHz CPU and a GB of DDR400 SDRAM.It has an IDE Promise 20276 RAID(0) MBFasttrakATA133 Lite controller enabled Lite and it's using an ATI RADEON 9600SE 128MB DDR video card. Gusty with GNOME is installed on the RAID(0).

---

### Post by Jussi Kukkonen on 2007-11-19
/etc/gdm/gdm.conf (fairly well commented)

---

### Post by Banacek on 2007-11-19
How did I miss that one? I was right at that directory at least once. Well, I was pretty busy checking out the /etc/X11/ directory and checking all the subdirectories. Maybe I was just too focused on that.

Okay, I have uploaded the copies of the gdm.conf and other files. Just remove the ".tar" suffix or change it to ".txt" and open with a text reader. The two files with that suffix are NOT tar files.

I see a few things of interest but of note is line 661. Apparently, Ubuntu's GDM has its chooser specifically set up for XDMCP. In Fedora the chooser is for selecting which account (on the machine you're using only) in the users list that you want to login to. I see a line or two that might disable the XDMCP but I'm not sure. Is there a way to disable the XDMCP only but have the chooser set to select account logins only of the current machine?

---

### Post by Banacek on 2007-11-20
Okay, in the /etc/gdm/gdm.conf file I commented out lines 560, 562, 652, 653, 654, and 658. I changed it from "chooser=true" to "greeter=true" on line 661. In the /etc/gdm/gdm.conf-custom file I changed line 74 the same way. That's it.

It no longer brings up the XDMCP hosts window anymore and I get a list of accounts to choose from on the login screen. I don't quite understand why but it seems to have worked. If there is anything I missed or could do better or that you could just explain to me, then tell me all about it, please.

---

### Post by Banacek on 2007-11-20
Alright, I'm going to mark this as solved because everything is working the way I'd like it to.

Thank you, Jussi Kukkonen, for your help.



However, I still don't entirely understand quite why all of it worked as well as it did. I sort of get why it turned the XDMCP off but as for keeping the login screen I wanted, that I don't get. Would, somebody, please, explain in entirety to my simple little mind why this worked out so well?

---

