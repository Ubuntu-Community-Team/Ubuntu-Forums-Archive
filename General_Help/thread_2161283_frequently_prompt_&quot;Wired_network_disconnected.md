---
title: "frequently prompt &quot;Wired network disconnected you are now offline&quot;"
date: 2013-07-10
forum: General Help
---

### Post by chenzero on 2013-07-10
Hello,
after upgrade to the latest version yesterday(Ubuntu 12.04.2 LTS), 

$ uname -a
Linux delta3 3.2.0-49-generic-pae #75-Ubuntu SMP Tue Jun 18 18:00:21 UTC 2013 i686 i686 i386 GNU/Linux

a problem is, the "Indicator Applet Complete", that is on the right corner of Desktop, frequently prompts (about every 5 minutes) "Wired network Disconnected - you are now offline".
but actually, the wired network is on. I have a ADSL network and using "pon dsl" command to dial. I can surf internet.

Any ideas to fix this ? 

Thanks!

---

### Post by dino99 on 2013-07-10
is it a fresh 12.04 install, then been upgraded to 12.04.2 ? or an oldish dist-upgrade installation ?
lot of changes have been made about the network packages and their config files; so its important to clean the system (at least) or doing a fresh install.

use: clean/autoclean/autoremove/gtkorphan/bleachbit  to clean the system, then be sure your /etc/apt/sources.list is also clean (not using oldish entries and/or untrusted sources); then:

sudo apt-get -f install
sudo dpkg-reconfigure -phigh -a
(be patient, it can take a while to end up itself)

---

### Post by sanderj on 2013-07-10
> **chenzero said:**
> 
a problem is, the "Indicator Applet Complete", that is on the right corner of Desktop, frequently prompts (about every 5 minutes) "Wired network Disconnected - you are now offline".
but actually, the wired network is on. I have a ADSL network and using "pon dsl" command to dial. I can surf internet.


What does dmesg say? Also disconnects/connects?

---

### Post by chenzero on 2013-07-10
@Dino99, 
I tried those commands, the system seems in good shape, then reboot computer. but the problem is still there.
things are a little complex because my system is upgraded from a PPA kernel 3.3.6 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)  
the previous kernel was often freezed on my computer, so, I installed 3.3.6, then installed the 3.2.0-49-generic-pae in yesterday.
in 3.3.6, the prompt HZ is more frequent (about every minute), in 3.2.0-49, at least it's about every 5 minutes.

@sanderj
in the last lines of dmesg, there are lots of Ipv6 log:

[  136.856292] eth0: no IPv6 routers present
[  183.978103] eth0: no IPv6 routers present
[  528.696633] eth0: no IPv6 routers present
[  576.369620] eth0: no IPv6 routers present
[  624.697636] eth0: no IPv6 routers present
[  672.490446] eth0: no IPv6 routers present
[ 1017.336789] eth0: no IPv6 routers present
[ 1065.337289] eth0: no IPv6 routers present
[ 1112.818564] eth0: no IPv6 routers present
[ 1161.242436] eth0: no IPv6 routers present

However, I have disabled the IPv6. (in the "IPv6 settings" tab, the Method is set to "Ignore")
looks when every prompt, it adds a line in the dmesg log.

is a problem in my network configuration ?


Thanks!

---

### Post by chenzero on 2013-07-10
at last, a workaround for this is to disable notification from network manager
[http://askubuntu.com/questions/67500/how-to-disable-notification-from-network-manager](http://askubuntu.com/questions/67500/how-to-disable-notification-from-network-manager)
the imperfect is, I still can notice that the network manager periodically configures something from its icon status(a broadcasting weave)

---

