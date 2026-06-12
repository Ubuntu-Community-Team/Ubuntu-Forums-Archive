---
title: "Missing linux-restricted-modules"
date: 2006-10-07
forum: General Help
---

### Post by GaryH on 2006-10-07
All,

I recently upgraded my kernel to 2.6.17. The upgrade went smoothly and everything appeared to work just fine afterwards. Later on I found that my winmodem no longer worked. Using the lsmod command I observed that ltmodem and ltserial were missing from the module list. The modules were, however, in the file system in both the 2.6.15-26-386 and 2.6.15-27-386 directories but there was no 2.6.17-13-386 directory. I think my winmodem quit working because there are no linux-restricted-modules, especially ltmodem & ltserial, associated with the upgraded kernel. 

How do I generate a linux-restricted-modules directory and all associated modules for my new 2.6.17 kernel?

Best

---

### Post by sunny_nwho on 2006-10-09
neither could i could anyone give a solution

---

### Post by GaryH on 2006-10-09
What are restricted modules? How do they differ from modules. If I knew what they were, maybe I figure out how to generate them.

Thanks,
GaryH

---

### Post by vidak on 2006-11-01
there is a package named linux-restricted-modules-2.6.17-10-386, but I don't know if it is included in the standard repo list, since I edited mine a lot... Try apt-cache search restricted
restricted modules are " Non-free Linux 2.6.17 modules" which couldn't be included in the standard kernel, because they are non-free.
What about sudo modprobe ltmodem?

---

### Post by GaryH on 2006-11-01
Thanks for enlightening me vidak.
GaryH

---

### Post by vidak on 2006-11-01
did this solve your problem?

---

### Post by GaryH on 2006-11-02
No. I'm still struggling but at least I know what restricted modules are. I'm currently battling Edgy. I did an upgrade two days ago and have yet to recover. Neither my wg811t wireless nor my modem work due to lack of restricted modules in Edgy. I will let you know when I solve the restricted module situation now that, at least, I know what restricted modules are.

---

### Post by vidak on 2006-11-06
you could check out the kernel modules package which are made for the edgy default kernel if it's on the list...

---

### Post by tommcd on 2006-11-06
In terminal do 'uname -r'. This will tell you what kernel you are on. Then just search synaptic for linux-restricted-modules that match the kernel you got from 'uname -r'. 
Or just "sudo apt-get install linux-restricted-modules `uname -r`". Note: that is a ` key (below tilde) nad not a ' (single quote).
This, of course, assumes you have a working internet connection without the modem.
If not, search through here:
[http://packages.ubuntu.com/edgy/base/](http://packages.ubuntu.com/edgy/base/)
and download the .deb modules on another computer and copy them to CD to install on your edgy box.
Hope this helps.
EDIT: the Dapper modules are here:
[http://packages.ubuntu.com/dapper/base/](http://packages.ubuntu.com/dapper/base/)

---

### Post by GaryH on 2006-11-06
Thank you for the response to my thread tommcd. I couldn't find restricted modules for Edgy in Synaptic. At least last week I couldn't find them. Thanks for the tip on searching [http://packages.ubuntu.com/edgy/base/](http://packages.ubuntu.com/edgy/base/). I'm not sure how to install modules from a CD, but that isn't a problem yet.

Thanks again tommcd,
GaryH

---

### Post by Gustav on 2006-11-06
Do you have the restricted repository enabled?

---

### Post by GaryH on 2006-11-13
Thanks for the reply Gustav. Yes I do have the restricted modules respositories enabled. As of right now I don't think they have been built for Edgy.
GaryH

---

### Post by tommcd on 2006-11-14
Gary H,
There are linux-restricted-modules for edgy. They are in the restricted repo in synaptic. In edgy there are only 'generic' and '386' kernels (and corresponding linux-restricted-modules) available. The 686 and k7 kernels have been replaced with generic. If you open synaptic, then click on settings>repositories, check all the options (you can omit the 'source code' option if you want). Then click the reload button (or do sudo apt-get update), then search for 'linux' in synaptic. Scroll all the way down to linux restricted-modules. That is how I found them anyway. 
After you install them, do 'sudo apt-get install linux-generic' (or 386 if you are on 386 kernel). This should ensure that you get your restricted-modules updated whenever there is a kernel update.
Here are the linux-restricted-modules for egdy 386 for 2.6.17.10 kernel.
[http://packages.ubuntu.com/edgy/base/linux-restricted-modules-386](http://packages.ubuntu.com/edgy/base/linux-restricted-modules-386)
and for generic kernel:
[http://packages.ubuntu.com/edgy/base/linux-restricted-modules-generic](http://packages.ubuntu.com/edgy/base/linux-restricted-modules-generic)
To install them from CD just copy them to your home folder and right-click on them and choose 'open with G-debi package installer'. 
Hope this helps. I am far from an expert on this, but this is how I would go about it anyway. You can always easily remove any .deb via synaptic or apt-get if it causes problems.

---

### Post by GaryH on 2006-11-16
Hi tommcd,
Thanks for replying to my last. I think you helped me once before. Thanks again for that too. I have been able to install the restricted modules as you suggested without any problem. The problem comes when I try to use either my modem or wireless. They don't work. A little detective showed that the appropriate modules are not even installed as they don't appear in the list which I observe using lsmod. The modules displayed just fine before the upgrade. I thought the problem was due to not having the latest and greatest restricted modules installed. I thought I needed -13 based on what uname -a told me. See following log:

highbeg@highbeg:/lib/linux-restricted-modules/2.6.17-10-386$ uname -a
Linux highbeg 2.6.17.13 #1 Mon Sep 25 12:31:20 EDT 2006 i686 GNU/Linux

I also thought I needed -13 because modprobe wouldn't couldn't find the modules either. See following log:

highbeg@highbeg:/lib/linux-restricted-modules/2.6.17-10-386$ ls
ath_hal  fcdsl2   fcdslslusb  fcdslusb2  fcpci  fglrx  ltmodem   nvidia
fcdsl    fcdslsl  fcdslusb    fcdslusba  fcusb  fxusb  ltserial  nvidia_legacy
highbeg@highbeg:/lib/linux-restricted-modules/2.6.17-10-386$ modprobe ltmodem
FATAL: Module ltmodem not found.
highbeg@highbeg:/lib/linux-restricted-modules/2.6.17-10-386$ 

Maybe the problem is I don't know how to use modprobe. It is also interesting that before the Edgy upgrade the modules loaded just fine on powerup right out of the "Dapper" box so to speak.

Any help you can give me will be much appreciated.

GaryH

---

### Post by ahbart on 2008-01-20
Hi GaryH, 
I have the same problem and I'm not able to solve it either. I use the 2.6.22-14-generic kernel on Gutsy.
I found out that the generic restricted modules package do not contain the ltmodem module because it has been shown to not behave on SMP kernels, causing kernels to panic (closes: launchpad.net/46685). The 386 kernel en restricted modules do not have this problem. 
Source: [http://changelogs.ubuntu.com/changelogs/pool/restricted/l/linux-restricted-modules-2.6.22/linux-restricted-modules-2.6.22_2.6.22.4-14.9/changelog](http://changelogs.ubuntu.com/changelogs/pool/restricted/l/linux-restricted-modules-2.6.22/linux-restricted-modules-2.6.22_2.6.22.4-14.9/changelog)
I do not know if installing the 386 kernel is a solution? Anyone else?
Bart

---

### Post by GaryH on 2008-01-22
Hope this helps ahbart,

Thanks to the MarvS and Jacques at linmodems.org my modem is now working with the custom kernel and life is beautiful.

I decided to use the newer modem driver package, martian. If anybody is interested in details please see my post on linmodems.org.

What I learned:

   1. Restricted modules quit working after the module is customized.
   2. Ubuntu doesn't support restricted-modules
   3. Agere DSP modems are supported at linmodems.org
   4. Wireless devices using the Atheos chip set are supported at madwifi.org
   5. It takes a long time to find everything necessary to rebuild and reinstall restricted-modules


Peace,
GaryH

---

