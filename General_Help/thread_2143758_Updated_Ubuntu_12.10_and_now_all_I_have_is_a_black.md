---
title: "Updated Ubuntu 12.10 and now all I have is a black screen"
date: 2013-05-10
forum: General Help
---

### Post by SUPERFITTER on 2013-05-10
I updated Ubuntu 12.10 and now all I have is a black screen after repeated reboots. Does anyone else have this problem?  If so how did you fix this problem?

---

### Post by papibe on 2013-05-10
Hi SUPERFITTER.

Do yo have any proprietary graphic driver installed?

Regards.

---

### Post by SUPERFITTER on 2013-05-10
I have a duel boot with windows 7 and have a Radeon HD7770 Card with driver.  Everything was working perfectly until I updated.

---

### Post by papibe on 2013-05-10
Are you able to see the grub menu?

If so, I assume you are getting a black screen after selecting Ubuntu?

Regards.

---

### Post by SUPERFITTER on 2013-05-10
> **papibe said:**
> Are you able to see the grub menu?

If so, I assume you are getting a black screen after selecting Ubuntu?

Regards.

Yes to both. Thank you for the help

---

### Post by QIII on 2013-05-10
Hi --

Just a quick question before I leave you again in papibe's capable hands...

Did you update or install fresh?

If you updated without first disabling the driver for your graphics adapter, that could be part of the problem.

Best wishes!

---

### Post by SUPERFITTER on 2013-05-10
This was a fresh install that I did a couple of months ago.  Now I just updated like I have done in the past.  How do you disable the driver for your graphics adapter?

---

### Post by papibe on 2013-05-10
Thanks. That looks like good news.

Once you get to the black screen, wait a minute or so, and press Ctrl+Alt+F1 to get to a text-mode console. There you can login as you.

Once you get to a terminal, run these commands:
```
sudo service lightdm stop

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo service lightdm start
```
If everything goes well, you will get to the graphic desktop.

Let us know how it goes.
Regards.

---

### Post by SUPERFITTER on 2013-05-10
> **papibe said:**
> Thanks. That looks like good news.

Once you get to the black screen, wait a minute or so, and press Ctrl+Alt+F1 to get to a text-mode console. There you can login as you.

Once you get to a terminal, run these commands:
```
sudo service lightdm stop

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old

sudo service lightdm start
```
If everything goes well, you will get to the graphic desktop.

Let us know how it goes.
Regards.

When I booted into Ubuntu I got the desktop picture and that changed from the black screen. I then got a terminal and followed your code. As soon as I got to sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old  it said that there is no file by that name. I did it twice and got the same results?  I will have to continue tomorrow, time to bed for me.  Thanks again for the help

---

### Post by papibe on 2013-05-10
I see.

Let's try again. You don't need to reboot as long as you are able to go back to the console using Ctrl+Alt+F1.

I'm still assuming it is a graphic driver problem, so let's remove the proprietary driver (you can reinstall it later).
```
sudo apt-get remove --purge  fglrx  fglrx-amdcccle  fglrx-updates  fglrx-amdcccle-updates

sudo reboot
```
Let us know how it goes.
Regards.

---

### Post by SUPERFITTER on 2013-05-10
> **papibe said:**
> I see.

Let's try again. You don't need to reboot as long as you are able to go back to the console using Ctrl+Alt+F1.

I'm still assuming it is a graphic driver problem, so let's remove the proprietary driver (you can reinstall it later).
```
sudo apt-get remove --purge  fglrx  fglrx-amdcccle  fglrx-updates  fglrx-amdcccle-updates

sudo reboot
```
Let us know how it goes.
Regards.

I had some questions:  1. How does this affect my windows 7 duel boot?  2. Is the driver for my graphics card the same for windows and Ubuntu? 3. How do I get the driver back and installed?  4. How come I never had to do this before, I have used Ubuntu for about 2 years and this is the first time this has happened in all the computers that I have installed a duel boot?  Thank You

---

### Post by papibe on 2013-05-11
> **SUPERFITTER said:**
> 1. How does this affect my windows 7 duel boot?
Those commands uninstall the AMD/ATI only on the Ubuntu side.
> **SUPERFITTER said:**
> 2. Is the driver for my graphics card the same for windows and Ubuntu?
No. Each OS needs its own driver. 
> **SUPERFITTER said:**
> 3. How do I get the driver back and installed?
Either running 'Additional Drivers' or, running the same commands but replacing 'remove -purge' with 'install'.
> **SUPERFITTER said:**
> 4. How come I never had to do this before, I have used Ubuntu for about 2 years and this is the first time this has happened in all the computers that I have installed a duel boot?
I can't say for sure, sorry. If removing the driver helps, it means it was a problem with either the graphic driver, or its compatibility with the kernel itself.

Regards.

---

### Post by SUPERFITTER on 2013-05-11
> **papibe said:**
> I see.

Let's try again. You don't need to reboot as long as you are able to go back to the console using Ctrl+Alt+F1.

I'm still assuming it is a graphic driver problem, so let's remove the proprietary driver (you can reinstall it later).
```
sudo apt-get remove --purge  fglrx  fglrx-amdcccle  fglrx-updates  fglrx-amdcccle-updates

sudo reboot
```
Let us know how it goes.
Regards.

I ran the code and it said: each is not installed, so not removed

---

### Post by SUPERFITTER on 2013-05-11
I will run: sudo apt-get install fglrx  fglrx-amdcccle  fglrx-updates  fglrx-amdcccle-updates

sudo reboot

---

### Post by SUPERFITTER on 2013-05-11
That did not work.  All have fglrx: conflicts with fglrx, drivers, updates, NVidia updates etc.  It also said I have broken packages.

---

### Post by SUPERFITTER on 2013-05-11
Could this be a Kernel problem?  My last update where the problem started had an update for the kernel.

---

### Post by papibe on 2013-05-12
Could you confirm that you have an AMD/ATI card?

Could you post the result of this command?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by SUPERFITTER on 2013-05-13
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Cape Verde [Radeon HD 7770 Series][1002:683d]       Subsystem: Giga-byte Technology Device [1458: 2556]      Kernel driver in use: radeon

---

### Post by SUPERFITTER on 2013-05-14
Papibe  What should I do now?

---

### Post by papibe on 2013-05-15
Hi again.

Let's try to install the AMD driver then:
```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get install linux-headers-generic

sudo apt-get install fglrx fglrx-amdcccle

sudo amdconfig --initial

reboot
```
Let us know how it goes.
Regards.

---

### Post by SUPERFITTER on 2013-05-15
I just get a desktop picture with no panel, just as before.

---

### Post by papibe on 2013-05-15
I see.

Let's try to reset Unity:
[LIST]
[*]Clean your compiz pre-recorded settings:
```
rm  -rf  ~/compiz  ~/.config/compiz-1
```
[*]Go into text mode again, and install this:
```
sudo apt-get install compizconfig-settings-manager
```
[*]Then run it like this:
```
DISPLAY=:0  ccsm
```
[*]Go back to the GUI by pressing Ctrl+Alt+F7 (or Ctrl+Alt+F8 if that don't work).
[*]Go to the open program there: CompizConfig Settings Manager.
[*]Search for Unity plugin, and make sure it is enabled.
[*]Open a terminal in the GUI by pressing Ctrl+Alt+t, and run this:
```
unity --reset-icons & disown
```
[Let it run for a couple of minutes.
[*]If you don't get your desktop back, reboot:
```
sudo reboot
```
[/LIST]
Let us know how it goes.
Regards.

---

### Post by SUPERFITTER on 2013-05-16
[SIZE=2]Hi Papibe
[/SIZE]
[SIZE=2]Thank you very much.  [/SIZE]
[SIZE=2]
After a lot of nail biting and hair pulling I was able to restore my Ubuntu. I updated the software first. I then did three cold starts and it seems like everything is working correctly.  I will run Ubuntu for a few days and if all goes well I will post solved.  [/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]I did have a few questions that I think others would also like to know.[/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]1. Did I miss something when I installed Ubuntu?[/SIZE]
[SIZE=2]
[/SIZE][SIZE=2]2. Is there anything that I can do to keep this problem from recurring?
[/SIZE]
[SIZE=2]3. Is this a common problem with the panel or unity disappearing?[/SIZE]

---

### Post by papibe on 2013-05-16
> **SUPERFITTER said:**
> After a lot of nail biting and hair pulling I was able to restore my Ubuntu.
Glad it's working OK now :)
> **SUPERFITTER said:**
> 1. Did I miss something when I installed Ubuntu?
Very unlikely. This looks like a botched update. My guess is that either a graphic driver update or a kernel update were not fully compatible with each other.
> **SUPERFITTER said:**
> 2. Is there anything that I can do to keep this problem from recurring?
There are several recommendations that I can give you, but all of them are in general to have a more stable system:
[LIST]
[*]Avoid installing software outside the Ubuntu repositories.
[*]In particular the graphic driver. Let the driver on AMD site as a last resort. Follow small upgrade steps in case it does not work. For instance, if the driver proposed by Ubuntu doesn't work, use the recommended swat ppa, and then the edgers ppa.
[*]Regarding ppas: try to add as little as possible to your repositories. When you add too many you create unstability.
[*]Finally, my assessment is that this kind of problems seldom occur on LTS versions, so if this happens again, I'd recommend reverting to 12.04.
[/LIST]
> **SUPERFITTER said:**
> 3. Is this a common problem with the panel or unity disappearing?
Not at all. Although I've seen it  a few time when upgrading Ubuntu versions (like from 12.10 to 13,04).

Regards.

---

