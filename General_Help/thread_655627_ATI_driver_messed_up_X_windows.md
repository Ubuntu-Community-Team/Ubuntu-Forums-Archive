---
title: "ATI driver messed up X windows"
date: 2008-01-01
forum: General Help
---

### Post by milan2008 on 2008-01-01
Hi everyone!
Happy New Year!

I have a problem with ATI Proprietary Drivers & X Window manager.

System:
-----------------------------------------------------
CPU: Pentium D 805
MB: Asus P5PL2 
VGA: ATI Radeon X550 ASUS
OS: Ubuntu Feisty Fawn x86 (7.04) + Beryl
------------------------------------------------------

I installed ATI Proprietary Drivers to get better game support.I restarted Ubuntu,it said Restricted Drivers found.I enabled them and it said that I need to restart the PC.I restarted the PC and when it was time for the X Window to show up,nothing happened.

How can I revert to original drivers?
Also,can you help me to set up ATI Proprietary Drivers properly?

Thanks in advance.

---

### Post by luisromangz on 2008-01-01
How exactly did you install the drivers? From the repositories? or were they the binary package from ATI's web page?

What kind of error sputs the X server?

To revert to the opensource ATI drivers you just have to change the driver name in /etc/X11/xorg.conf. You'll need root privileges for that.

---

### Post by peitschie on 2008-01-01
Hmm... I hate problems like that.  I think your easiest way in fact is to try and fix this all in one fell swoop.  Rather than using the Restricted Drivers (stable, but often a little out dated), I would recommend you use a script called "Envy" ([http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")).  This downloads the latest ATI drivers from the ati website, and compiles them specifically for your system.  The package is updated with every new release from ATi, so usually is updated once every month or two.

To get this from your current install, do the following (see the Envy Ubuntu FAQ for more details: [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)):
[LIST=1]
[*]Start Ubuntu
[*](Assuming you are given a console to log in at) log in with your normal username
[*]Download the Envy Ubuntu package: ```
wget [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.9-0ubuntu4_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.9-0ubuntu4_all.deb)
```
[*]install Envy (note: see the Envy FAQ for more details on this step: [http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu)): ```
sudo dpkg -i envy*.deb
``` 
[*]Use Envy to install the latest ati drivers: ```
sudo envy -t
```
[/LIST]

I am not sure I would recommend the opensource ATI drivers though, as game and 3d performance is lacking very badly in these drivers unfortunately.

---

### Post by tgilber1 on 2008-01-01
To use the proprietary drivers, you need to change a couple of things, /etc/default/linux-restricted-modules-common and /etc/X11/xorg.conf

1.  Edit the /etc/default/linux-restricted-modules-common file by preventing Ubuntu from loading its own fglrx module 

DISABLED_MODULES="nv fglrx"

2.  Generate a new xorg.conf file

sudo aticonfig --initial -f # will backup original file - pay attention to name if you want to revert back

3.  Make sure that driver name in device section is "fglrx"

4.  sudo /etc/init.d/gdm restart


_If you want to revert back to the original_

1.  cd /usr/share/ati/

2.  sudo ./fglrx_uninstall  # will restore original configuration, i.e. xorg.conf file

3.  Edit etc/default/linux-restricted-modules-common by removing flgrx from DISABLED_MODULES line

4.  sudo /etc/init.d/gdm rsetart #May have to reboot to boot up to the xorg fglrx driver rather than the proprietary

---

### Post by milan2008 on 2008-01-02
Thanks a lot!
It works.
I reverted back to the original & installed Envy.Works fine now.:)

---

### Post by milan2008 on 2008-01-02
But now games are messed up,they either start with ruined graphics(I can't even exit from a game)or they don't start at all.
Help please!

---

### Post by milan2008 on 2008-01-02
I reinstalled ATI Proprietary drivers with some additional settings everything works now.

---

### Post by kellemes on 2008-01-02
> **milan2008 said:**
> I reinstalled ATI Proprietary drivers with some additional settings everything works now.


Next time you could explain what settings you changed, so other can actually learn something from this thread.

---

### Post by milan2008 on 2008-01-02
I added this to the end of /etc/X11/xorg.conf

Section "Extensions"
    Option "Composite" "0"
EndSection

I think that solved the problem.

---

