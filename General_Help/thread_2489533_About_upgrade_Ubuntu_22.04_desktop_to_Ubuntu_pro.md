---
title: "About upgrade Ubuntu 22.04 desktop to Ubuntu pro"
date: 2023-08-01
forum: General Help
---

### Post by satimis on 2023-08-01
Hi all,

Each time when I update & upgrade Ubuntu 22.04 destop it reminds me to upgrade to Ubuntu Pro.  I'm aware that Ubuntu Pro is FREE for personal use.

Register for personal use
[https://ubuntu.com/pro](https://ubuntu.com/pro)

I'm prepared testing it on an Ubuntu 22.04 VM (VirtualBox)

Would following link be suitable for me to follow?
Enable Ubuntu Pro to get 5 Years More Security Updates in Ubuntu 22.04,20.04,18.04
[https://ubuntuhandbook.org/index.php/2023/05/esm-apps-updates-ubuntu/](https://ubuntuhandbook.org/index.php/2023/05/esm-apps-updates-ubuntu/)

Please advise.  Thanks

Regards

---

### Post by Dennis N on 2023-08-01
What method do you use to upgrade? Terminal? Software Updater? From Ubuntu Software? I ask because I've never noticed any message like that.

On Ubuntu Pro, I would say its premature to subscribe with 22.04. I did subscribe to it for Ubuntu 18.04, but I did that only when it was about to go end-of-life in order to prolong it's support.

The way I enrolled was to visit the Ubuntu Pro website while using the 18.04 system I wanted to enroll. Use the "Free for Personal Use" registration.

---

### Post by ian-weisser on 2023-08-01
The Ubuntu Pro free tier offers offers a specific list of benefits.

- During the first five years, some Universe security patches. No extra bugfixes. No extra technical support.
- During the second five years, all Main and some Universe security patches. No bugfixes at all. No technical support at all.

It is worthwhile for some, not for others.  The paid tier offers more, of course.

Only you can decide whether or not Pro is worthwhile for you.

I recommend Ubuntu Pro for folks who understand what it offers. It's a good service from a reliable company with no gotchas, and the business plan is honest. It's not for everybody. It's not for me (I use very little Universe software, and nothing older than 2 years), but it might indeed be for you.

---

### Post by satimis on 2023-08-02
> **Dennis N said:**
> What method do you use to upgrade? Terminal? Software Updater? From Ubuntu Software? I ask because I've never noticed any message like that.
Regularly I run following command on Terminal
$ sudo apt update ; sudo apt upgrade```

Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-plugin-qt libvlc5 libimage-magick-perl vlc-data libvlccore9 vlc vlc-bin
  vlc-l10n libavdevice58 libopenexr25 libmagick++-6.q16-8 libpostproc55
  libmagickcore-6.q16-6-extra vlc-plugin-samba libavcodec58
  libimage-magick-q16-perl libmagickwand-6.q16-6 vlc-plugin-notify libavutil56
  imagemagick-6.q16 libswscale5 libmagickcore-6.q16-6 vlc-plugin-access-extra
  vlc-plugin-skins2 vlc-plugin-video-splitter libswresample3
  imagemagick-6-common vlc-plugin-video-output libavformat58 libvlc-bin
  vlc-plugin-base vlc-plugin-visualization libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
....

```

The above warning is the frequent result.

> 
On Ubuntu Pro, I would say its premature to subscribe with 22.04. I did subscribe to it for Ubuntu 18.04, but I did that only when it was about to go end-of-life in order to prolong it's support.

The way I enrolled was to visit the Ubuntu Pro website while using the 18.04 system I wanted to enroll. Use the "Free for Personal Use" registration.
I have no urgent need upgrading all Ubuntu 22.04 PCs to Ubuntu Pro.  It is only my curiosity testing Ubuntu Pro for learning.

Regards

---

### Post by satimis on 2023-08-02
> **ian-weisser said:**
> The Ubuntu Pro free tier offers offers a specific list of benefits.

- During the first five years, some Universe security patches. No extra bugfixes. No extra technical support.
- During the second five years, all Main and some Universe security patches. No bugfixes at all. No technical support at all.

It is worthwhile for some, not for others.  The paid tier offers more, of course.

Only you can decide whether or not Pro is worthwhile for you.

I recommend Ubuntu Pro for folks who understand what it offers. It's a good service from a reliable company with no gotchas, and the business plan is honest. It's not for everybody. It's not for me (I use very little Universe software, and nothing older than 2 years), but it might indeed be for you.
Your advice noted and thanks.

It is solely my curiosity testing Ubuntu Pro, no practical use for the time being.

Regards

---

### Post by Dennis N on 2023-08-02
> **satimis said:**
> Your advice noted and thanks. It is solely my curiosity testing Ubuntu Pro, no practical use for the time being.

Give it a try. Very easy to set up. All instructions for doing so on the Ubuntu Pro website. You get a token assigned to you good for 5 Ubuntus. You apply the token with a terminal command, as I recall. All the management can be done from your terminal since many users of this are running servers with no GUI. There is a special command **pro** that is the manager.

Example: I use it here to check status:

```
dmn@Tyana:~$ pro status
SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal           yes       disabled  Common Criteria EAL2 Provisioning Packages
cis              yes       disabled  Security compliance and audit tools
esm-apps         yes       enabled   Expanded Security Maintenance for Applications
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
fips             yes       disabled  NIST-certified core packages
fips-updates     yes       disabled  NIST-certified core packages with priority security updates
livepatch        yes       enabled   Canonical Livepatch service
ros              yes       disabled  Security Updates for the Robot Operating System
ros-updates      yes       disabled  All Updates for the Robot Operating System

For a list of all Ubuntu Pro services, run 'pro status --all'
Enable services with: pro enable <service>

```

One thing you get by default is **livepatch**, which is not default in your original Ubuntu install.
You can use options "disable" or "detach" to stop or remove Ubuntu Pro.

---

### Post by satimis on 2023-08-03
> **Dennis N said:**
> Give it a try. Very easy to set up. All instructions for doing so on the Ubuntu Pro website. You get a token assigned to you good for 5 Ubuntus. You apply the token with a terminal command, as I recall. All the management can be done from your terminal since many users of this are running servers with no GUI. There is a special command **pro** that is the manager.

Example: I use it here to check status:

```
dmn@Tyana:~$ pro status
SERVICE          ENTITLED  STATUS    DESCRIPTION
cc-eal           yes       disabled  Common Criteria EAL2 Provisioning Packages
cis              yes       disabled  Security compliance and audit tools
esm-apps         yes       enabled   Expanded Security Maintenance for Applications
esm-infra        yes       enabled   Expanded Security Maintenance for Infrastructure
fips             yes       disabled  NIST-certified core packages
fips-updates     yes       disabled  NIST-certified core packages with priority security updates
livepatch        yes       enabled   Canonical Livepatch service
ros              yes       disabled  Security Updates for the Robot Operating System
ros-updates      yes       disabled  All Updates for the Robot Operating System

For a list of all Ubuntu Pro services, run 'pro status --all'
Enable services with: pro enable <service>

```

One thing you get by default is **livepatch**, which is not default in your original Ubuntu install.
You can use options "disable" or "detach" to stop or remove Ubuntu Pro.
Thanks for your advice.

I have cloned a new Ubuntu 22.04 VM for this test.

After having created it.

$ sudo apt update ; sudo apt upgrade```

....
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
.....

```

$ sudo apt list --upgradable```

Listing... Done
gnome-remote-desktop/jammy-proposed 42.9-0ubuntu0.22.04.1 amd64 [upgradable from: 42.7-0ubuntu1]

N: There are 2 additional versions. Please use the '-a' switch to see them.

```

$ sudo apt list --upgradable -a```

Listing... Done
gnome-remote-desktop/jammy-proposed 42.9-0ubuntu0.22.04.1 amd64 [upgradable from: 42.7-0ubuntu1]
gnome-remote-desktop/jammy-updates,now 42.7-0ubuntu1 amd64 [installed,upgradable to: 42.9-0ubuntu0.22.04.1]
gnome-remote-desktop/jammy 42.0-4ubuntu1 amd64

```
Which package shall I upgrade?  How?

Thanks

---

