---
title: "hp printer configuration error"
date: 2017-02-02
forum: General Help
---

### Post by cjdubats-i on 2017-02-02
Printer has been used successfully with ubuntu and windows for years.  Still working fine when booted to win10.  Was working fine with 16.04 LTS until installation of an app (KiCad).  Printer must be connected via USB, ethernet port is dead.  Error info is attached.  My specific request is if I should try to delete this printer in printer settings dialog and then re-add it.

---

### Post by wildmanne39 on 2017-02-02
*Thread moved to **General Help for better support**.*

---

### Post by gsahli on 2017-02-03
Error says the driver isn't found.
If you think you've already installed hpcups 3.16.3+repack0 , use terminal commands to find the location of that file:
sudo updatedb
sudo locate "hpcups*"

do you find it? I'm asking you to do this because cups has changed file locations in the last 3 yrs or so.

---

### Post by cjdubats-i on 2017-02-03
It was my intent to post in general help.  Which sub forum did it wind up in?

---

### Post by howefield on 2017-02-03
> **cjdubats-i said:**
> It was my intent to post in general help.  Which sub forum did it wind up in?

General Help..

Look at the top of the page for the path to the thread.

Forum > The Ubuntu Forum Community > Ubuntu Official Flavours Support > General Help > [ubuntu] hp printer configuration error

It had been originally posted to the "*[Installation & Upgrades]*" forum.

---

### Post by cjdubats-i on 2017-02-03
gsahli: Thanks for helping.  I had not consciously installed anything and had just let Ubuntu installation and updates handle everything (until this upset).  Response to the first command suggested was a quick return to command prompt.  Same  for the locate command, which I assume means nothing found.  I found etc/hp/hplip.conf, which I renamed as hplip.txt to expedite attachment.

---

### Post by dragonfly41 on 2017-02-04
I compared your file with mine and it is comparable (I'm on Ubuntu 14.04 with HP laserjet drivers seen in Cups).

I also tried .. sudo locate hpcups* and the wildcard character * did not work.

The reason.  Reading output from "man locate" you need the --regex option when using wildcard character *

Running command "sudo locate hpcups" (no wildcard character)  brings up a stream of hits.

Also "sudo locate --regex hpcups* " works.

....

Now to return to setting up / testing your printer try going to CUPS GUI at 

[http://localhost:631/printers/](http://localhost:631/printers/)

to see if your printer is installed or hung up anywhere.

[Later edit]

Reading your first post attachment I see this ...

Printer State: 
Idle - File "/usr/lib/cups/filter/hpcups" not available: No such file or 
directory

So logically run command ..

sudo ls /usr/lib/cups/filter/

and look for hpcups in the list (it is "not found" in your first report)

You might find it easier to use a utility such as Nautilus or Thunar to look through your filesystem.

---

### Post by cjdubats-i on 2017-02-04
Thanks to all for the help on this topic.  I mostly try to use gui apps and avoid the command line, regular expressions, etc.  My installation of Ubuntu has begun to issue quite a few error messages, even on boot.  I think I will try to get all my content to dropbox and do a fresh installation.  Then, if I can't find some sort of installation script or whatever for hp officejet, I'll just give it to my sister and buy a new one with a working lan port.  I never did like her that much anyway.

---

### Post by gsahli on 2017-02-04
Sorry about the wrong wildcard "hpcups*" above.
You still haven't mentioned whether you installed the hpcups driver from the repository. I use synaptic - it was easy to find and install.

---

### Post by cjdubats-i on 2017-02-05
Had previously installed the hpcups driver etc and everything had been working fine.  Just suddenly broke.  Downloaded a new installer from a site recommended by hp support and ran it per instructions at hplipopensource.com/hplip-web/install/install/index.html.  What I was missing is that the hp-officejet_4500_g510g-m.ppd.gz that is needed doesn't wind up in the usr/share/ppd/HP dir tree and I had to select it from the directory the installer really put it in (in my case under my Downloads directory).  Everything works now after the changes and all the updates that the installer did.  I think that most of the warts are due to repository settings, python setup, etc.  Thanks for your help.

---

