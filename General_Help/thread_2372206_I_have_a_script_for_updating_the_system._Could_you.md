---
title: "I have a script for updating the system. Could you please tell me if it's correct?"
date: 2017-09-22
forum: General Help
---

### Post by brunces on 2017-09-22
Hey, guys.

I've been using Linux for not so long and come across some commands that I have found very useful in different situations. That said, I've created a script to update the system with those commands.

Normally, one would just type "sudo apt update && sudo apt upgrade" in Terminal to get their system updated, but I usually run this script instead:

```
#!/bin/sh

echo ""
echo ""
echo "   Cleaning stuff..."
echo ""
echo ""

sudo apt install -f
sudo apt autoclean
sudo apt clean
sudo apt autoremove

echo ""
echo ""
echo "   Unlocking stuff..."
echo ""
echo ""

sudo fuser -vki /var/lib/dpkg/lock
sudo dpkg --configure -a
sudo fuser -v /var/cache/debconf/config.dat
sudo rm /var/lib/apt/lists/* -vf

echo ""
echo ""
echo "   Updating and upgrading..."
echo ""
echo ""

sudo apt update
sudo apt upgrade
sudo apt dist-upgrade

echo ""
echo ""
echo "   Cleaning stuff again..."
echo ""
echo ""

sudo apt install -f
sudo apt autoclean
sudo apt clean
sudo apt autoremove

echo ""
echo ""
echo "   System successfully updated."
echo ""
echo ""
```

Now, what I want to know is, instead of using just "sudo apt update && sudo apt upgrade":

1) Should I keep on using this script? I mean, is it safe to be used the way it is?
2) Is there any command(s) I should not be using every time? If so, which one(s)?
3) Considering the safe and correct commands, is their order correct or should I run one before another and etc.?
4) Is there any command(s) I should use that is not there? If so, which one(s)?

Just for the record, I've been running this script in all Ubuntu based distros I've ever used. Today, I'm using KDE Neon. So far, I haven't had any problems, I mean, not that I've known of. If this has caused any troubles, it's probably something under the hood that, so far, I haven't noticed. But, you know, it's good to listen to an expert's opinion, so here I am.

Thank you very much for your attention.

brunces

---

### Post by karl96 on 2017-09-22
I don't understand the point, simply running update, upgrade and dist-upgrade should be sufficient (I think it does all of those things automatically anyway)

---

### Post by ian-weisser on 2017-09-22
The script seems to duplicate what unattended-upgrades already does, including autoremoval.

Running both 'apt clean' and 'apt autoclean' is a waste of resources. Pick one.

Running 'apt autoremove' *after* clean/autoclean also seems non-optimal. Why keep the package after uninstalling?

Why do you need to run 'dpkg configure -a'  at all?

This kind of catch-all package maintenance script pops up every few months. Most apt tools already try to do the right thing and clean up any messes they find before they even tell you there's a problem. As the human in the system, your job is to use package management properly and diagnose those few corner-cases that apt cannot handle. Beyond that, simply let apt do it's job.

Is there some package-related problem that you need to handle frequently?

---

### Post by oldos2er on 2017-09-22
```
sudo apt upgrade
sudo apt dist-upgrade
``` This is incorrect, not to mention a waste of resources. It should be ```
sudo apt full-upgrade
``` dist-upgrade is for the older apt-get command. *sudo apt full-upgrade* does everything *sudo apt upgrade* does, so it's pointless to run both.

If you have to repeatedly run ```
sudo dpkg --configure -a
sudo fuser -v /var/cache/debconf/config.dat
sudo rm /var/lib/apt/lists/* -vf
``` something is wrong somewhere, as ian-weisser implied.

---

### Post by deadflowr on 2017-09-22
apt clean and apt autoclean are not needed when running apt.
apt (versus apt-get) will automatically remove (clean) the archived packages upon successful installation.
(That's the default setting, you can manually change it to preserve archives, though, through apt's configuration files ; I forget where and how)

I would think running anything than update upgrade and the occasional autoremove would be extraneous.

And I would never run any of the fixit commands unattended.
(fixit being the install -f, dpkg --configure -a and what goes with those)
People seem to run those commands all the time and have them not do what they are supposedly suppose to do and still have issues.
Having them in a script will more likely cause you to lose the important reasons why said command isn't working.
If that convolutingly makes sense.

---

### Post by VMC on 2017-09-22
> **oldos2er said:**
> ```
sudo apt upgrade
sudo apt dist-upgrade
``` This is incorrect, not to mention a waste of resources. It should be ```
sudo apt full-upgrade
``` dist-upgrade is for the older apt-get command. ***sudo apt full-upgrade*** does everything *sudo apt upgrade* does, so it's pointless to run both.

If you have to repeatedly run ```
sudo dpkg --configure -a
sudo fuser -v /var/cache/debconf/config.dat
sudo rm /var/lib/apt/lists/* -vf
``` something is wrong somewhere, as ian-weisser implied.

```
**$** **sudo apt full-upgrade**

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

**$ sudo apt-get update && sudo apt-get dist-upgrade**
...
  The following NEW packages will be installed:  linux-headers-4.4.0-97 linux-headers-4.4.0-97-generic
  linux-image-4.4.0-97-generic linux-image-extra-4.4.0-97-generic
The following packages will be upgraded:
  google-chrome-stable libpam-systemd libsmbclient libsystemd0 libudev1
  libwbclient0 linux-generic linux-headers-generic linux-image-generic
  linux-libc-dev samba-libs systemd systemd-sysv udev unattended-upgrades
15 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 145 MB of archives.
After this operation, 298 MB of additional disk space will be used.
```

---

### Post by oldos2er on 2017-09-22
@VMC, perhaps you should've run sudo apt update prior to sudo apt full-upgrade?

---

### Post by VMC on 2017-09-23
> **oldos2er said:**
> @VMC, perhaps you should've run sudo apt update prior to sudo apt full-upgrade?

I did , its just not listed.

edit: thinking about it, I'm unsure. I use old-school apt-get.

---

### Post by oldos2er on 2017-09-23
I'm on 17.10 too, and I've only run apt full-upgrade rather than the older apt-get dist-upgrade. I can't see any functional difference between the two.

---

### Post by brunces on 2017-09-23
First of all, thank you all for taking the time to help me. I really appreciate it.
 
I will try to explain why I&#8217;ve been using these commands so you can maybe understand my reasons.
 
Once in a while &#8211; not often &#8211; I stumble upon a situation in which &#8220;apt upgrade&#8221; just won&#8217;t work. Then I&#8217;m asked to run a command such as &#8220;apt install -f&#8221; or &#8220;dpkg --configure -a&#8221; to &#8220;fix&#8221; something, and then &#8220;apt upgrade&#8221; works again.
 
Same goes with the &#8220;unlocking procedure&#8221;. Once in a while &#8211; not often &#8211; I stumble upon a situation in which &#8220;apt upgrade&#8221; just won&#8217;t work. Then I&#8217;m asked to run a command such as &#8220;fuser -vki /var/lib/dpkg/lock&#8221; or &#8220;fuser -v /var/cache/debconf/config.dat&#8221; or &#8220;rm /var/lib/apt/lists/* -vf&#8221; to &#8220;fix&#8221; something, and then &#8220;apt upgrade&#8221; works again.
 
So I thought maybe I could write a script that would always run those commands before &#8220;apt upgrade&#8221;. Whenever they were needed, they would already be there. I always thought that, if there&#8217;s something to be fixed, those commands would do it; if not, they would not do anything at all, I mean, I understand they would be useless, a waste of time and resources, but that&#8217;s OK; I just never thought they could be harmful when not needed.
 
Now... Often &#8211; not once in a while &#8211; after running &#8220;apt upgrade&#8221;, I get a message that says something like &#8220;The following packages are no longer needed and can be removed.&#8221; So, unlike it was said above that &#8220;apt&#8221; does the cleaning itself, it seems it doesn&#8217;t. At least, not completely. Otherwise, I wouldn&#8217;t get that message. So, I assume &#8220;apt autoremove&#8221; is still useful, isn&#8217;t it?
 
Well, that&#8217;s it. After reading everything you posted, I think I&#8217;ll quit using this script and keep on running only the necessary commands to get my system updated. By the way, thanks for the &#8220;apt full-upgrade&#8221; tip. I didn&#8217;t know about that. And, whenever needed, I&#8217;ll run the other commands.
 
Thanks for your time, guys. Cheers. :)

---

### Post by oldos2er on 2017-09-23
We would need more information about what exactly is causing apt to ask you to run either "apt install -f," "fuser -vki /var/lib/dpkg/lock," etc. If one of these situations occurs again, could you post your sources.list, any outside repos (any files listed in /etc/apt/sources.list.d/), and the commands you ran that led up to it? If you're interested in pursuing it, that is.

---

### Post by brunces on 2017-09-23
oldos2er, if it ever happens again, I'll post it here so you can help me. Thank you very much. :)

---

