---
title: "torguard Lite application will not launch in 13.04"
date: 2013-06-09
forum: General Help
---

### Post by drascus on 2013-06-09
I am using the TorGuard application that is designed for ubuntu for the TorGuard Proxy. When I attempt to launch the application it says that I need administrative privilages. I put in my password and then nothing happens. According to the log it looks like my privilages are being denied but I have no idea why it works everywhere else. Customer support has not been able to help with this yet. I thought maybe someone here would have an idea. here is the logs. it could be that here the USER is set as = root. I am not sure how to change that though. 

Jun  9 21:03:09 drascus-Alienware-X51 sudo:  drascus : TTY=unknown ; PWD=/opt/TorGuard ; USER=root ; COMMAND=/usr/bin/java -cp ./:./bin/:./lib/gtk-linux-x86_64.jar:./lib/json_simple.jar:./lib/commons_lang.jar oast.Oast
Jun  9 21:03:09 drascus-Alienware-X51 sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Jun  9 21:03:09 drascus-Alienware-X51 sudo: pam_unix(sudo:session): session closed for user root

---

### Post by drascus on 2013-06-10
Okay I figured this out. It had to do with a program really more written with 12.04 or 12.10 in mind then 13.04. Basically they were trying to set com.canonical.Unity.Panel to all for the whitelist but ubuntu 13.04 no longer uses this in the debconf. So I installed a PPA that re-enabled it. They also had some problems with the script that they wront in general that was missidentifying my OS as 64 bit when it is 32 bit. I fixed their script and bam everything is working.

Here are the gritty details in case anyone else runs into this

1) In ubuntu 13.04 com.canonical.Unity.Panel has been disabled. The first thing the start.sh script tries to do is set the whitelist to all but it can't because it's been disabled. If I run this script directly I get the error of "Scheme not defined" using debconf I confirmed that this was indeed disabled. In order to re-enable the panel I did the following...

sudo add-apt-repository ppa:timekiller/unity-systrayfix
sudo apt-get update
sudo apt-get upgrade

Afterwards, restart Unity, press ALT+F2 (run application), then type in unity, press ENTER key.

at this point using the debconf editor I could see that the scheme had been fixed.

The next time I ran the script it again failed but for a different reason. This time it failed because of my processor type. I am running a i686 processor but with a 32bit distro. I noticed that "$procstr" = i686 for the 64.jar file. I deleted this part of the script so that it would skip over to the 32bit portion.

Once I made these edits I am able to launch the script without issue.

---

### Post by Zeros Spark on 2013-07-07
Hey there I am currently having a similar issue with torguard except that I get the xmessage "Please install gksudo/gnomesu/sdesu." I have everything installed except for the openvpn software - Virtual private network daemon which after 12.04 I have not been able to find in the ubuntu software center. So would you help me out in letting me know what you did for that part of this setup?

---

### Post by drascus on 2013-07-07
Hi Zeros, 

Yes that is a problem with the new version of ubuntu there is no gksudo. you can actuall install it if you want. this post will show you how to install it. [http://askubuntu.com/questions/290810/how-to-add-gksudo-or-what-to-use-instead-in-ubuntu-13-04]("http://askubuntu.com/questions/290810/how-to-add-gksudo-or-what-to-use-instead-in-ubuntu-13-04")

You can find the vitrual private network daemon in the software center. if you search openvpn is should be the first on the list... At least it was for me. 

I recommend that you use the method in network manager for torguard. I have found that network manager is faster, more seamless, and more stable for me than using torguard lite. The have an install doc on how to do this. Let me know if you run into any snags.

---

### Post by JimS on 2013-07-08
This year I've been distro hopping and installed TorGuard
in Ubuntu 12.10, Mint13xfce, LMDE, LM15Cinnamon, Debian7, and a couple other Ubuntu clones. 
Sometimes I had to do sudu su and sometimes not.
Only one problem, I couldn't get TG to run after login in Direct Linux last month.
It just disappeared.

---

