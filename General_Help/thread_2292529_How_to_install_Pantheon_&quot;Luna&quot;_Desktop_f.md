---
title: "How to install Pantheon &quot;Luna&quot; Desktop for Ubuntu? Pakages not installing.."
date: 2015-08-28
forum: General Help
---

### Post by zuto2 on 2015-08-28
I followed the directions from this site and muiltple other sites. They all didn't work and from this site the end result was:
[http://linuxg.net/how-to-install-pantheon-desktop-environment-on-ubuntu-13-04-12-10-12-04-and-linux-mint-15-14-13/](http://linuxg.net/how-to-install-pantheon-desktop-environment-on-ubuntu-13-04-12-10-12-04-and-linux-mint-15-14-13/)

```
E: Package 'pantheon-shell' has no installation candidate
E: Unable to locate package pantheon
E: Unable to locate package lingo
E: Unable to locate package wingpanel
E: Unable to locate package pantheon-terminal
E: Unable to locate package slingshot-launcher
E: Package 'switchboard' has no installation candidate
E: Package 'snap' has no installation candidate
E: Package 'switchboard-gnome-control-center' has no installation candidate
```

Are the repos dead?

**Edit:**

I think it is working with this site.
[http://jfnlinuxproject.blogspot.com/2014/09/how-to-install-elementary-oss-pantheon.html](http://jfnlinuxproject.blogspot.com/2014/09/how-to-install-elementary-oss-pantheon.html)

Thank you,
Zuto

---

### Post by Frogs Hair on 2015-08-28
I see only packages for 12.04 on that page so if using a different Ubuntu release there would be no candidate. You check the list again but I only saw precise1 packages.                                

[https://launchpad.net/~elementary-os/+archive/ubuntu/stable](https://launchpad.net/~elementary-os/+archive/ubuntu/stable)

---

### Post by zuto2 on 2015-08-28
> **Frogs Hair said:**
> I see only packages for 12.04 on that page so if using a different Ubuntu release there would be no candidate. You check the list again but I only saw precise1 packages.                                

[https://launchpad.net/~elementary-os/+archive/ubuntu/stable](https://launchpad.net/~elementary-os/+archive/ubuntu/stable)

Luckily, I use Precise 12.04. :D

It works except....I have no exit, minimize, or maximize button even though I change it with tweaks? Know how I can fix this?
[[IMG]http://s10.postimg.org/pcm7o2zd1/Selection_002.jpg[/IMG]]("http://postimg.org/image/pcm7o2zd1/")
[B]
Edit:
[/B][http://ubuntuforums.org/showthread.php?t=2191377]("http://ubuntuforums.org/showthread.php?t=2191377Here") 

Here is the fix.

[COLOR=#141412][FONT=monospace]sudo mkdir /etc/upstream-release
[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]sudo touch /etc/upstream-release/lsb-release

[/FONT][/COLOR][COLOR=#141412][FONT=monospace]sudo gedit /etc/upstream-release/lsb-release

Now copy and paste the following in document open by gedit and save it:
[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_ID=Ubuntu[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_RELEASE=12.04[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_CODENAME=precise[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"

Now upgrade your system with following command:
[/FONT][/COLOR]
[COLOR=#141412][FONT=monospace]sudo apt-get dist-upgrade[/FONT][/COLOR]

[URL="http://postimg.org/image/pcm7o2zd1/"]

[/URL]

---

