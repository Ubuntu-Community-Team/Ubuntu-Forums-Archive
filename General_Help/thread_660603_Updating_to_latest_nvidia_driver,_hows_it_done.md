---
title: "Updating to latest nvidia driver, hows it done?"
date: 2008-01-06
forum: General Help
---

### Post by phillips321 on 2008-01-06
Hi guys,

As per topic title, how do i upgrade to the latest nvidia driver (256MB 7900GS).

nvidia-settings shows im running driver version 100.14.19

Can i update it to the latest via apt-get?

Any one got any up-to-date guides?

Cheers

---

### Post by chewearn on 2008-01-07
> **phillips321 said:**
> Hi guys,

As per topic title, how do i upgrade to the latest nvidia driver (256MB 7900GS).

nvidia-settings shows im running driver version 100.14.19

Can i update it to the latest via apt-get?

Any one got any up-to-date guides?

Cheers

To get version later than 100.14.19, you need to manually install from nvidia website, or use [Envy]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by PeterJS on 2008-01-07
Is there a specific patch or update you need? Adding things out side of the package manager is generally ill advised. Just because there is a newer version doesn't mean it's better. The versions in the repositories are known to work and are easier to install and support.

Avoid envy like your system stability depends on it, because it does. Envy's track record is spotty at best.

---

### Post by chewearn on 2008-01-07
> **PeterJS said:**
> Avoid envy like your system stability depends on it, because it does. Envy's track record is spotty at best.

And the proof to this statement is... where?

---

### Post by Shazaam on 2008-01-07
Envy problems aside, there are a few ways to do it. 
1. Use synaptic.
2. Go to nvidia's site and download the closed source driver.
3. If you are using Feisty/Gutsy run the 'Restricted Drivers Manager" to install the open-source nvidia-glx-new (or -legacy depending on your card) driver.

If you go the closed source driver route make sure you read the README front to back.

[http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/index.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.07/README/index.html)

another link...

[http://www.nvnews.net/vbulletin/showthread.php?t=72490](http://www.nvnews.net/vbulletin/showthread.php?t=72490)

---

### Post by chewearn on 2008-01-07
> **Shazaam said:**
> Envy problems aside, there are a few ways to do it. 
1. Use synaptic.
2. Go to nvidia's site and download the closed source driver.
3. If you are using Feisty/Gutsy run the 'Restricted Drivers Manager" to install the open-source nvidia-glx-new (or -legacy depending on your card) driver.


Maybe I'm being a pita here; but I have to make one correction to your post: the nvidia-glx-new or nvidia-glx-legacy packages in the repositories are not open-source.  They are the same binary drivers you find in nvidia website (proprietary, close-source).

Of course, newer versions are occasionally released in nvidia website, while the one in repositories usual stayed at the same version, until the next distribution-upgrade.

---

### Post by phillips321 on 2008-01-07
im currently using the *nvidia-glx-new* driver (*nvidia-glx* is not installed).

To install the new drivers do i have to uninstall the old ones first? hows that done?

reason for new drivers is that compiz has some crazy memory leak, believed to be linked with nvidia drivers....?

cheers guys

---

### Post by nowshining on 2008-01-07
u should of told us whether u have a 32bit or 64bit computer.

i'm going to assume 32-bit or 64-bit almost i have a 32bit computer soo I think it's the same steps.

first download the driver

IA32 for 32 bit, it's a .run file
IA64 for a 64 bit computer
[B]Linux AMD64/EM64T - for the AMD64 bit computer and the EM64T 64 bit computer..

All are run files,

FIRST, open a terminal and type  

sudo gedit /etc/default/linux-restricted-modules-common

and between the  " and " input nv, save and then exit.

then u'll need to get into CLI mode - I know how, but getting there I forgot how :D without shutting off the GDM service and i use CLI to sign in on startup and removed GDM...

anyway

place it onto ur desktop or wherever

in CLI mode, (assuming u downloaded it to ur desktop)

cd urusername Desktop and hit the enter key

suso sh NV

hit the tab key to  auto-complete

enter ur pw, for security purposes ur pw will not be shown as u type it, this is normal,

follow the instructions, I don't think there is NO need for it modify ur xorg.conf file, as for uninstalling it will ask u if u'd like to go ahead- it will uninstall the oldver version for u.
[/B]

---

