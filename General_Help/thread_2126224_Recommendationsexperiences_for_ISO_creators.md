---
title: "Recommendations/experiences for ISO creators"
date: 2013-03-16
forum: General Help
---

### Post by zembelaa on 2013-03-16
[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]We are thinking for our software office to use Ubuntu 12.04 32 bit which has long term support. We have more than 15 machines. First we want to make a new ISO which will include the updates and some extra packages.[/COLOR]

[COLOR=#000000]The ISO should be stable. If it can not be done, please tell it.[/COLOR]

[COLOR=#000000]Which application do you recommend for making this ISO?[/COLOR]

[COLOR=#000000]-Remastersys project has stopped about 3 months ago.. Now it started again, but it does not update itself and the support is too bad.[/COLOR]

[COLOR=#000000]-Re-linux didn't published any stable version yet.[/COLOR]

[COLOR=#000000]-UCK's latest stable version gives me "dependency is not satisfiable libfribidi-bin" on Ubuntu 12.04. I don't think that is normal. UCK is already designed just for Ubuntu. It is possible to install 2.4.5 version of UCK properly, but it is published on 2011-11-30 which is before release of Ubuntu 12.04. I think they are kidding..[/COLOR]

[COLOR=#000000]I could not find time to try these:[/COLOR]

[COLOR=#000000]-Ubuntu builder seems nice app.[/COLOR]

[COLOR=#000000]-reconstructor is cloud based. I want to make my own iso on my local machines. Also they are getting money for that.[/COLOR]

[COLOR=#000000]Can you please tell me your experiences about all these applications? They are (or which are) stable do you think?[/COLOR]

[COLOR=#000000]Thanks in advance...[/COLOR]

---

### Post by deadflowr on 2013-03-16
You can try a more manual approach like those listed here:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

It's painstaking, but seems to be what you'd want.

---

### Post by zembelaa on 2013-03-16
> **deadflowr said:**
> You can try a more manual approach like those listed here:

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

It's painstaking, but seems to be what you'd want.

First thank you for your interest.

I'm not worring about painstaking but it is technically really hard for me to make this. I am sure that I will face many problems, If I will make it manually myself. That's why I want to use an application.

I had already read this link which you gave me. I understand that it is officially possible to create customized ISO from Ubuntu. That is good to know...

They all ISO creators (which I write top) does the same thing? I mean they are doing background these: [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) or they work really differently?

---

### Post by oldfred on 2013-03-16
Are all these systems identical, particularly amount of RAM and video card?

Are they new enough to boot from Flash?  If not they may have too little RAM (or video) to run full Ubuntu and need either Xubuntu or Lubuntu?
But I run 64 bit Ubuntu in fallback not Unity on my 5 year old laptop with only 1.5GB of RAM. That is generally considered too little RAM for 64 bit but it works. Only occasionally does it use swap, and it seems better than my previous 10.10 install on the laptop. 

I have not tried any of these suggestions and some are getting old, so may not work.
 OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

   Kickstart - Unattended Ubuntu installations made easy
[http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/](http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/)

   Setting up your own APT repository with upload support - 2005
[http://www.debian-administration.org/articles/286](http://www.debian-administration.org/articles/286)
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[URL="https://help.ubuntu.com/community/LocalAptGetRepository"]https://help.ubuntu.com/community/LocalAptGetRepository

[/URL] Offline Updates:
[https://launchpad.net/keryx/+download](https://launchpad.net/keryx/+download)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
apt-cache search foo
[https://help.ubuntu.com/community/Apt-Cacher-Server](https://help.ubuntu.com/community/Apt-Cacher-Server)
Download once for many machines
How To Install Apt-Cacher-NG in Ubuntu Linux
[http://ubuntuforums.org/showthread.php?t=981085](http://ubuntuforums.org/showthread.php?t=981085)
Location of downloaded debs
/var/cache/apt/archives/
sudo apt-get install --no-download <package name>

[URL="https://help.ubuntu.com/community/LocalAptGetRepository"]
[/URL]

---

