---
title: "Wine and Gnome desktop files issues"
date: 2008-06-18
forum: General Help
---

### Post by adster101 on 2008-06-18
Hi,

I am running Ubuntu 8.04 on my Compaq laptop. It is an upgrade from 7.10 rather than a fresh install.

The installation is fairly standard i.e. i'm not breaking new ground with my linux install!

Two issues that I am having.

1. When I run IE6 under Wine the CPU usage goes to 100% and wineserver takes up 200+MB of RAM. The cpu fan starts whirring and eventually the whole desktop slows down.

Can anyone tell me is this is an issue with my laptop not being powerful enough (Compaq Evo N600, 760Mb Ram, 1.6GHz CPU) or to do with my set up?

2. A couple of time recently all my files on the Desktop disappear. I can still see the files via Places > Desktop but they disappear from the actual 'desktop'. All the files return if I ctrl-alt-backspace and log back in.

If anyone can help on these two issues then that would be great.

Update: I ran sudo apt-get install wine and got the following:

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
wine: Depends: libldap2 (>= 2.1.17-1) but it is not installable
E: Broken packages


Thanks in advance,

Adam

---

### Post by adster101 on 2008-06-18
bump

---

### Post by secular on 2008-06-18
adster101, I can't help, but I can confirm that I've had similar problems with Internet Explorer using 100% of one of my CPU cores. 

Fortunately, I don't need it but once every couple of weeks or so. I use the System Monitor (System, Administration, System Monitor) to turn off Wine and IE when I'm finished using IE, and that frees up my CPUs.

I've also tried to update Wine the past couple of days, and, after refreshing everything in Synaptic, get the same message as you: "wine: Depends: libldap2 (>=2.1.17-1) but it is not installable."

If anyone has a fix, I'd appreciate the help, too.

---

### Post by MysteriousMystery on 2008-06-18
The solution lies in this file, [http://packages.ubuntu.com/gutsy/libldap2](http://packages.ubuntu.com/gutsy/libldap2) Install it for your architecture. It solved the problem on my end.

---

### Post by vexorian on 2008-06-18
If you are running IE6 for testing web pages intentions, then I must say a virtual machine (like virtual box) is more desirable.

I think it is better to use a virtual machine to test your developments.

---

