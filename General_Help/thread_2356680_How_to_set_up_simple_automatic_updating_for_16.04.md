---
title: "How to set up simple automatic updating for 16.04"
date: 2017-03-25
forum: General Help
---

### Post by AbleTassie on 2017-03-25
I just recently did a clean install of Lubuntu 16.04. I now have to do my updates manually by going to the Software Updater in Systems Tools. In the past, I got security and other updates automatically. A dialogue box asked me if I wanted to update my software. I would like to set up some kind of automatic updates again. But, I don&#8217;t want to make it too complicated.
 
 [B]
 Does anybody have any suggestions as to how to do this?[/B]

 
 In trying to investigate this myself (See [https://www.howtoinstall.co/en/ubuntu/xenial/unattended-upgrades](https://www.howtoinstall.co/en/ubuntu/xenial/unattended-upgrades) ) , it appears that it is just a simple matter of running these two terminal commands:

 
 sudo apt-get update
sudo apt-get install unattended-upgrades

 
 On the other hand, this webpage ( [https://help.ubuntu.com/lts/serverguide/automatic-updates.html](https://help.ubuntu.com/lts/serverguide/automatic-updates.html) ) has more complicated instructions. These complicated instructions allow *&#8220;t**he unattended-upgrades package can be used to automatically install updated packages, and can be configured to update all packages or just install security updates.&#8221;*  
 
Similarly, *&#8220;**Certain packages can also be blacklisted and therefore will not be automatically updated.**&#8221;*
 
And the updating can be configured so the [I]&#8220;configuration updates the package list, downloads, and installs available upgrades every day. The local download archive is cleaned every week.&#8221; 
[/I]
But, as I said above, I don't want to get into anything too  complicated. [B]

Any comments will be welcomed.[/B]

Thanks,

A.

---

### Post by ian-weisser on 2017-03-25
Easy: Install unattended-upgrades. Turn it on.

---

### Post by AbleTassie on 2017-03-25
> **ian-weisser said:**
> Easy: Install unattended-upgrades. Turn it on.

Thanks Ian, 

I assume that installation is accomplished by the two terminal commands in my first post. But is there another command to "turn it on?" Or is this just an expression of speech?

A.

---

### Post by Dennis N on 2017-03-25
> In the past, I got security and other updates automatically. A dialogue box asked me if I wanted to update my software.

Sounds like you had automatic notification of available updates (without you starting and checking with Software Updater). This is different from unattended upgrades, which downloads and install certain updates **without** notification. 

Set these options in "Software and Updates" > Updates Tab.

The "Download and Install automatically" option does unattended upgrades. Options to "Display" either immediately or weekly give you notification first.

The package unattended-upgrades in 16.04 is installed by default (at least it is in Xubuntu 16.04).

---

### Post by AbleTassie on 2017-03-25
> **Dennis N said:**
> Sounds like you had automatic notification of available updates (without you starting and checking with Software Updater). This is different from unattended upgrades, which downloads and install certain updates **without** notification. 

Set these options in "Software and Updates" > Updates Tab.

The "Download and Install automatically" option does unattended upgrades. Options to "Display" either immediately or weekly give you notification first.

The package unattended-upgrades in 16.04 is installed by default (at least it is in Xubuntu 16.04).

Thanks Dennis,

I found the utility you are talking about under Preferences. Do you have any comments as to the best settings? I have tentatively set "when there are security updates" to be downloaded and installed immediately. This required me to enter my password. It appears that the "when there are security updates" drop down menu is not "grayed out" for some reason and it cannot be changed back easily.

Any comments from you or others will be appreciated.

A.

---

### Post by Dennis N on 2017-03-25
> **AbleTassie said:**
> Thanks Dennis,

I found the utility you are talking about under Preferences. Do you have any comments as to the best settings? I have tentatively set "when there are security updates" to be downloaded and installed immediately. This required me to enter my password. It appears that the "when there are security updates" drop down menu is not "grayed out" for some reason and it cannot be changed back easily.

Any comments from you or others will be appreciated.

A.
Each user has to decide what settings are best for them. 

Looking at mine, "Security Updates" has 3 options: 1) display immediately, 2) download automatically, and 3) download and install automatically. I use option #1 simply because I want to see the list of things being updated before it is done. I have "automatically check for updates" set to "Daily", and "when there are other opdates" set to "display weekly". 

The password requirement is normal, since you are changing the way your system is going to operate.

---

### Post by AbleTassie on 2017-03-26
Thanks Dennis,

The dropdown menu for "When there are security updates" under the Updates tab in Software & Updates is now grayed out and cannot be changed for some reason, even after rebooting.
 I am now wondering if I harmed my system because I ran the 4 "remove unattended upgrades" terminal commands below described at 
[https://www.howtoinstall.co/en/ubuntu/xenial/unattended-upgrades?action=remove](https://www.howtoinstall.co/en/ubuntu/xenial/unattended-upgrades?action=remove) : 

sudo apt-get remove unattended-upgrades

sudo apt-get remove --auto-remove unattended-upgrades

sudo apt-get purge unattended-upgrades

sudo apt-get purge --auto-remove unattended-upgrades

I ran the above 4 commands because I tried unsuccessfully to run the "add unattended upgrades" commands at 
[https://help.ubuntu.com/lts/servergu...c-updates.html]("https://help.ubuntu.com/lts/serverguide/automatic-updates.html") and I thought I needed to reverse those commands.

Do you (or others) think I harmed my system? 

Thanks,

A.

---

### Post by Dennis N on 2017-03-26
Not having that package installed could be a reason why your selector is misbehaving.
You can check if it's removed with the command:

```
apt-cache policy unattended-upgrades
```

If the first line of output says "Installed: (none)" then it has been removed. I suggest you reinstall it, and the options should again be available in the selector. I don't think you did any damage.

```
sudo apt-get install unattended-upgrades
```

---

### Post by AbleTassie on 2017-03-26
> **Dennis N said:**
> Not having that package installed could be a reason why your selector is misbehaving.
You can check if it's removed with the command:

```
apt-cache policy unattended-upgrades
```

If the first line of output says "Installed: (none)" then it has been removed. I suggest you reinstall it, and the options should again be available in the selector. I don't think you did any damage.

```
sudo apt-get install unattended-upgrades
```

Thanks Dennis,

That worked. The output was "Installed: (none)." So I reinstalled using the terminal command and now the drop down menu works and is no longer grayed out.

I will mark this thread solved.

A.

---

