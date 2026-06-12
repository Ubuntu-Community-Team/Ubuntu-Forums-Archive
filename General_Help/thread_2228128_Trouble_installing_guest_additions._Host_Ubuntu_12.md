---
title: "Trouble installing guest additions. Host Ubuntu 12.10, guest Debian stable"
date: 2014-06-05
forum: General Help
---

### Post by gtzanakis on 2014-06-05
Hi all,

In the labs of our uni we have virtualbox (version: 4.1.18_Ubuntu r78361) installed on our computers running Ubuntu 12.10 with the 3.5.0-48-generic kernel. 
Mind that I do not have root privilleges. I have created a virtual machince with guest Debian with the 3.2.0-4-amd64 kernel. I have been googling around but 
I'm failing to install the guest addons in debian. In most of the forums I've seen, people are suggesting to upgrade virtualbox to the latest version, but this
is not an option for me. 

So, for instance, the last thing that I tried was the following:

[LIST]
[*]In the guest, I do:```
apt-get install virtualbox-guest-* build-essential linux-headers-$(uname -r) dkms 
``` Not sure if I need all those, but just in case. 
[/LIST]

[LIST]
[*]From the VB menu, I go* Devices-> Install guest additions*. This downloads *VBoxGuestAdditions_4.1.18.iso*. Then I mount it to */media/cdrom* 
[*]Then I get this message: 
[*][[IMG]http://s2.postimg.org/r14bg0aeh/Screenshot_from_2014_06_05_20_23_31.png[/IMG]]("http://postimage.org/") 
[*]I choose to continue, and I get those messages:
[[IMG]http://s27.postimg.org/940v0cz2r/Screenshot_from_2014_06_05_20_29_21.png[/IMG]]("http://postimage.org/") 
[/LIST]
Then I reboot, both guest and host, but no full screen or any other guest addition. So this didn't work.

Anybody has any ideas, please?

---

