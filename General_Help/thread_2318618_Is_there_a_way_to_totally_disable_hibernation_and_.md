---
title: "Is there a way to totally disable hibernation and sleep modes in ubunu?"
date: 2016-03-27
forum: General Help
---

### Post by Chris1965 on 2016-03-27
I have a minimal ubuntu 14.04 with xfce DE installed presently on a Dell M4600 laptop and I know it will not resume without a hard shutdown after closing the lid. I even found one other thread off site that said to upgrade the kernel and it still didn't seem to fix the problem due to the kernel was way older then the one installed. I found one other waiting for a reply here and it said something about gconf-editor which is not installed. Closest thing I find in Synaptic that is power related  is something called upower.

What I really want is to totally disable hibernation and sleep as to me it's only something to use up system resources that I do not use just as I did in MS Windows.

Any help would be amazingly nice at this point.

---

### Post by Chris1965 on 2016-04-02
This one has really got me stumped. I did finally find out the key combination to wake the computer back up again by hitting the power button once and then the "enter" key. When it wakes nothing is running. This to me is really annoying.

 Here are the settings from the settings editor:

xfce4-power-manager Empty
brightness-on-battery   Integer 9
dpms-on-ac-off           Integer 5
dpms-on-ac-sleep        Integer 0
dpms-on-battery-off     Integer 5
dpms-on-battery-sleep  Integer 0
lid-action-on-ac           Integer 0
lid-action-on-battery     Integer 0
power-button-action      Integer 3

Again any help would be greatly appreciated

---

### Post by sammiev on 2016-04-02
Just go into power manager and change the settings.

To wake up from Suspend, I need to tap the power button once and then move the mouse.

---

### Post by Bucky Ball on 2016-04-02
Varies on different machines. My laptop, a Toshiba, and my desktop, my hybrid, space key wakes them up from suspend. My wife's machine: power button then space bar (probably mouse also), login.

Are you wanting to not need to login when you wake the machine? You say 'when it wakes nothing is running'. What exactly are you looking at when it wakes. A black screen?

---

### Post by Chris1965 on 2016-04-02
At night I would play internet radio and close my lid so the light would not shine all over the room. When I did it would play for a while then stop then I would open the lid, have to type in password in greeter ..... firefox would be open but at home page. And yes I do want to login with greeter, no auto login.

I did just fix this however. I gedited a file named logind.conf under /ect/systemd/ and changed it to:

[Login]
#NAutoVTs=6
#ReserveVT=6
#KillUserProcesses=no
#KillOnlyUsers=
#KillExcludeUsers=root
Controllers=blkio cpu cpuacct cpuset devices freezer hugetlb memory perf_event net_cls net_prio
ResetControllers=
#InhibitDelayMaxSec=5
[B]HandlePowerKey=poweroff
HandleSuspendKey=ignore
HandleHibernateKey=ignore
HandleLidSwitch=ignore[/B]
#PowerKeyIgnoreInhibited=no
#SuspendKeyIgnoreInhibited=no
#HibernateKeyIgnoreInhibited=no
#LidSwitchIgnoreInhibited=yes
#IdleAction=ignore
#IdleActionSec=30min

I don't know enough about linux yet to say if it is a true fix however it is working as now when I close the lid and reopen there is no login and firefox is still playing uninterrupted.

I just wish there was a way like in windows to easily disable hibernation and suspend as there are allot of problems with it that I've read about. Perhaps not putting swap space on my drive helped enabling this issue but I refuse to use swap with 16 gig of memory installed.

So even though this modification is presently working I would still like to find a way to totally disable them both if anyone knows of a way to do so.

---

### Post by yetimon_64 on 2016-04-02
<Removed procedure ("/usr/share/polkit-1/actions/org.freedesktop.upower.policy" policy file alteration) instructions after retesting. Apparently no longer works.>

---

### Post by Chris1965 on 2016-04-06
Another question I have somewhat related to the topic at hand is during installation I didn't create a swap space yet once the system starts shutting down I notice there's a process that says it's deactivating swap, how can this be?

---

### Post by Bucky Ball on 2016-04-06
Give us the output of 'lsblk'.

---

### Post by Chris1965 on 2016-04-06
**Yetimon_64** what is the difference between what I did in login.conf and what you said to do in upower? Does upower control the whole isystem where my first way doesn't. Just trying to understand linux better. I did notice with upower all the boxes grayed out in power manager however not in log out.

---

### Post by Chris1965 on 2016-04-06
> **Bucky Ball said:**
> Give us the output of 'lsblk'.

```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 149.1G  0 disk 
sdb      8:16   0  74.5G  0 disk 
sdc      8:32   1   7.5G  0 disk 
&#9492;&#9472;sdc1   8:33   1   7.5G  0 part /
sr0     11:0    1  1024M  0 rom  
```


sdc is the drive where ubuntu is installed

---

### Post by yetimon_64 on 2016-04-06
> **Chris1965 said:**
> **Yetimon_64** what is the difference between what I did in login.conf and what you said to do in upower? Does upower control the whole system where my first way doesn't. Just trying to understand linux better.

Chris1965, it is best you disregard my last post. I just retested the procedure here and it failed. It is a method I used to use in older versions of ubuntu, but apparently it no longer works in 14.04. On older systems doing that procedure would remove access to the system power menu items for suspend and hibernate (totally disabling their usage system wide). 

I still have the suspend option and it still works even with the policykit files altered. Sorry for the misinformation in this case. Regards, yeti.

---

### Post by Chris1965 on 2016-04-12
I don't know what happend but today none of the settings above work not to mention now there is no reboot/shutdown/hibernate/suspend options in logout on menu and now the monitor won't even black out after time. I take it the programmers are working on it or something? Now I am back to square one again, this is **extremely frustrating** since up till today all was working nicely.

---

### Post by Bucky Ball on 2016-04-12
Have you updated/upgraded lately? Open a terminal and do so:
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get dist-upgrade
```

Post any and all error messages, please.

I am running virtually the same setup (Ubuntu minimal + xfce4) on the laptop I'm using now and have no such issues, so odd. Maybe hardware? If you have Windows, is that working fine?

---

### Post by Chris1965 on 2016-04-12
> **Bucky Ball said:**
> 

Post any and all error messages, please.

I am running virtually the same setup (Ubuntu minimal + xfce4) on the laptop I'm using now and have no such issues, so odd. Maybe hardware? If you have Windows, is that working fine?

I did an update/upgrade and unfortunately there were no new available. I have my video driver for Quadro FX 2700M (Nvidia-304) and wifi driver for BCM4312 (firmware-b43-installer) installed and working. I am presently running xfce 4.10 on it's own drive without swap and without any other OS. Here is the link to my install that I followed. [https://xpressubuntu.wordpress.com/2014/02/22/how-to-install-a-minimal-ubuntu-desktop/](https://xpressubuntu.wordpress.com/2014/02/22/how-to-install-a-minimal-ubuntu-desktop/) I know it worked fine with windows 7 just before I gave ubuntu a shot. Below are some screenshots of my power manager.

 [ATTACH=CONFIG]268332[/ATTACH][ATTACH=CONFIG]268333[/ATTACH][ATTACH=CONFIG]268334[/ATTACH][ATTACH=CONFIG]268335[/ATTACH]

When I go and close my laptop lid it goes into suspend or hibernation and now nothing will wake it back up as far as I know. The power and enter key combo I pushed earlier doesn't work now.

I also noticed now in "applications menu" that the "log out" doesn't offer a suspend/hibernate/shutdown/restart boxes like it did a few days prior. Now I use the "action buttons". All's I know is I'm rubbing my head way to often especially for someone with out much to begin with.:confused:

---

### Post by Chris1965 on 2016-04-12
I also did a lspci and this is what it showed.

[ATTACH=CONFIG]268337[/ATTACH]

I am just so frustrated with it all at this point.

---

### Post by Bucky Ball on 2016-04-12
If you right click the logout then 'Properties' that should give you a list to choose which options you want available; suspend, hibernate, logout, shutdown, etc.

---

