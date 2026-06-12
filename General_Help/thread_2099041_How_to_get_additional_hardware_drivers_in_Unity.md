---
title: "How to get additional hardware drivers in Unity?"
date: 2012-12-28
forum: General Help
---

### Post by oxf on 2012-12-28
Hi,

I've just installed Oneric on my laptop.

It has the infamous BC43xx series wireless card that isn't automatically enabled. However, on previous installs such as Maverick the Hardware Drivers window automatically suggested the driver  and it was simply a matter of hardwiring into my router, downloading the driver and with a simple reboot WiFi was in business.

Now using Oneric/Unity it's not listing the driver. How do I locate it or get my system to detect it? It should be fairly simple I guess. Software Sources>Drivers doesent show anything.

Thanks

---

### Post by grahammechanical on 2012-12-28
On any version before 12.10 we should be looking for the Additonal Drivers utility. With Unity it may appear as an icon representing an add-in adapter in the top panel to the right. This usually appears soon after we have rebooted after the initial installation of Ubuntu.

Otherwise we can look for it in the Dash. Click on the Ubuntu icon at the top of the Launcher. When the Dash opens search for Addtional Drivers and an icon for this utility should appear in the Dash. We can also click on the second from the left icon at the bottom of the Dash = applications and then click Installed see xx more results and scroll through the icons for all installed applications.

Regards.

---

### Post by Frogs Hair on 2012-12-28
I n 12.10 additional drivers wont appear in dash because it has been made part of software sources. Search for software sources > additional drivers.

---

### Post by audiomick on 2012-12-28
> **grahammechanical said:**
> On any version before 12.10 we should be looking for the Additonal Drivers utility....

> **Frogs Hair said:**
> ....Search for software sources > additional drivers.


*cough* ummm
> **oxf said:**
> ... Software Sources>Drivers doesent show anything.


Which b43 is it exactly?

do
```
sudo lshw -c network
```
and post the output here. Use the code tags. That is the # button.

---

### Post by oxf on 2012-12-28
> **audiomick said:**
> *cough* ummm



Which b43 is it exactly?

do
```
sudo lshw -c network
```and post the output here. Use the code tags. That is the # button.

It's the Broadcom bc4318 
The problem is though nothing is listing under Software Sources>Additional Drivers.

This was automatic under previous releases!

---

### Post by audiomick on 2012-12-28
> **oxf said:**
> It's the Broadcom bc4318 
The problem is though nothing is listing under Software Sources>Additional Drivers.

This was automatic under previous releases!

Yes, I know. It seems to mess up sometimes...

What I have been seeing a lot is the advice in this post

[http://ubuntuforums.org/showpost.php?p=11826283&postcount=4]("http://ubuntuforums.org/showpost.php?p=11826283&postcount=4")

As far as I understand it, that wont make things any worse even it it doesn't help. It sends apt-get off to get the appropriate drives, and the last one, I think, is to make sure the wireless isn't turned off.

---

### Post by oxf on 2012-12-28
> **audiomick said:**
> Yes, I know. It seems to mess up sometimes...

What I have been seeing a lot is the advice in this post

[http://ubuntuforums.org/showpost.php?p=11826283&postcount=4](http://ubuntuforums.org/showpost.php?p=11826283&postcount=4)

As far as I understand it, that wont make things any worse even it it doesn't help. It sends apt-get off to get the appropriate drives, and the last one, I think, is to make sure the wireless isn't turned off.

Thanks. I'll try that. I also have a (different) Compaq Presario. 

Caitlin

---

### Post by oxf on 2012-12-28
Hmm? what does this mean? Nothings simple is it!

```
mbdb@M2000:~$ sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
[sudo] password for mbdb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
E: Unable to locate package firmware-b43-installer

```

I'm also wondering if this little problem is a result of Unity per see or the release 12:10?
Since I will later install Gnome because I dislike Unity I wonder if that would change anything?

Caitlin

---

### Post by Luigi2012SM64DS on 2012-12-28
> **oxf said:**
> Hmm? what does this mean? Nothings simple is it!

```
mbdb@M2000:~$ sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
[sudo] password for mbdb: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package b43-fwcutter
E: Unable to locate package firmware-b43-installer

```
When you use apt-get for the first time you type "sudo apt-get update"
After that is finished install those packages.

---

### Post by oxf on 2012-12-28
> **Luigi2012SM64DS said:**
> When you use apt-get for the first time you type "sudo apt-get update"
After that is finished install those packages.

Thanks.
I ran update but it's still not finding the packages!

---

### Post by oxf on 2012-12-28
Actually its not finding a lot!

```
mbdb@M2000:~$ mbdb@M2000:~$ sudo apt-get install --reinstall b43-fwcutter firmware-b43-installer
mbdb@M2000:~$: command not found
mbdb@M2000:~$ [sudo] password for mbdb: 
[sudo]: command not found
mbdb@M2000:~$ Reading package lists... Done
Reading: command not found
mbdb@M2000:~$ Building dependency tree       
Building: command not found
mbdb@M2000:~$ Reading state information... Done
Reading: command not found
mbdb@M2000:~$ E: Unable to locate package b43-fwcutter
E:: command not found
mbdb@M2000:~$ E: Unable to locate package firmware-b43-installer
E:: command not found

```

---

### Post by Luigi2012SM64DS on 2012-12-28
> **oxf said:**
> Thanks.
I ran update but it's still not finding the packages!
Strange.
Download the package from here:
[http://www.ubuntuupdates.org/package/core/oneiric/multiverse/base/firmware-b43-installer](http://www.ubuntuupdates.org/package/core/oneiric/multiverse/base/firmware-b43-installer)
(Under the download part select All arch deb package)
(Also don't worry it will automatically install the b43-fwcutter as well)
Double click it and install though the ubuntu software center.

---

### Post by oxf on 2012-12-28
Forget my last comment, my typing error! It seems to be installing now!

---

### Post by Luigi2012SM64DS on 2012-12-28
> **oxf said:**
> Forget my last comment, my typing error! It seems to be installing now!
Yay!
After install you have to reboot.

---

### Post by oxf on 2012-12-28
> **Luigi2012SM64DS said:**
> Yay!
After install you have to reboot.

Yes that last problem was just my mistake in copying into the Terminal. All is now installed and after reboot and WiFi  worked fine!

 Many thanks for the help! 
and thanks to "audiomick" also

Caitlin

---

### Post by audiomick on 2012-12-28
Hey, great. Really pleased to hear it worked. :)

---

