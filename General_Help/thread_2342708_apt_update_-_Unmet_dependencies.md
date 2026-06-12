---
title: "apt update - Unmet dependencies"
date: 2016-11-09
forum: General Help
---

### Post by bobwdn on 2016-11-09
Apt update is complaining ```
myuser@dt02:/# apt update && apt upgrade && apt autoremove && apt autoclean
Hit:1 http://us.archive.ubuntu.com/ubuntu yakkety InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu yakkety-updates InRelease     
Hit:3 http://us.archive.ubuntu.com/ubuntu yakkety-backports InRelease   
Hit:4 http://security.ubuntu.com/ubuntu yakkety-security InRelease      
Reading package lists... Done                     
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 r8168-dkms : Depends: dkms (>= 2.1.0.0) but it is not installed
E: Unmet dependencies. Try using -f.
```

What happened, for me to have gotten point was this. I wanted to upgrade my motherboard and had replaced the MB with the new one. The new MB had a different onboard ethernet that I had not anticipated the driver need. This left me with no internet access and no way to "apt install" the needed driver. Suddenly the computer restarts and begins a cycle of run for three to four minutes and restart. Over and over again. 

At this point I determine something is wrong with my mother board. Insert live cd, same thing 3-4 minutes and unexpected reboot happens. All this while I am trying to move needed *.deb file into machine via usb drive, which I had accomplished. So, something is wrong with this new MB.

Put the old MB back in and restart machine (sending bad MB back to vendor for replacement.)

Now, apt is still trying to install the (now unneeded) lan driver.

How do I stop this from installing, now that I do not need this driver anymore?

---

### Post by howefield on 2016-11-09
Did you try the suggested..

```
apt-get -f install
```

---

### Post by bobwdn on 2016-11-09
But, because I have returned to the original MB (due to failure of new MB) I do NOT want to install, as suggested . . . I guess I could go ahead and install and then un-install it.

It is the new MB that was requiring the installation of the different lan driver and again, while in the process of installing the driver the MB began rebooting every three to four minutes. This MB failure left behind this partial install.

Is it wise to go ahead and finish the install or is there some way for me to . . . abort the install (for lack of a better term.)

This "go ahead and install, then un-install" plan, is this the wisest course of action in this situation?

---

### Post by Bashing-om on 2016-11-09
bobwdn; Hey !

Allow me to throw my hat in here .

The advisory:
> 
Depends: dkms (>= 2.1.0.0) but it is not installed


leaves you with several options to resolve the situation.
1) If r8168 driver is not needed, you can remove it ;
2) take the package manager's advise and run - as howefield indicated too - :
```

sudo apt -f install

```
where the -f switch is " fix broken" ;
3) Install what the package manager wants :
```

sudo apt install dkms

```

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]several paths to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

