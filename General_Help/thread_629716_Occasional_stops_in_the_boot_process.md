---
title: "Occasional stops in the boot process"
date: 2007-12-02
forum: General Help
---

### Post by loa on 2007-12-02
Hello! I'm having a problem with occasional bootup hangs. They started after I upgraded to Gutsy. I never experienced this problem with Ubuntu 7.04. Most of the times there is no problem, but maybe once out of 10 or 20 bootups the booting process stops.


What happens is this: Almost all of the booting process works fine, but after it has come to "Running local boot scripts (/etc/rc.local)", not much more happens. X is not coming up.

The first strange thing is that it says "Reloading OpenBSD Secure Shell server's configuration sshd". I have no idea why it does this. According to /var/log/boot, it does this every time I boot. After that, if I wait a minute or so, it also started reloading cupsd, and then the system log daemon. After that nothing more seems to happen with the booting. I am able to access other consoles though and Internet acess works. I was also watching top, and noticed almost no activity, except for updatedb at around 3% cpu utilisation.

These things when it comes into reloading those daemons may be due to new upstart init model, I don't know, but it could be related.

I have been digging through the logs (/var/log) to try and see if there is something particular happening with the boots when the booting freezes. I haven't found something which is only in the logs those times the boot process stops. However, I've found some things which seems a bit wrong, but which are in the logs even on those boots which works:

in kern.log:
Failure registering capabilities with primary security module.
intel_rng: FWH not detected

in daemon.log:
#Networkmanager warns several times about dhcdbd not running, lines such as
NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running!
#(However, eventually DHCP and the network connection will work)
avahi-autoipd(eth1)[5887]: fopen() failed: Permission denied
# (The network connection actually used is eth0)
#many errors about ntpd
NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))

in boot:
/etc/rcS.d/S40ifrename: 19: /sbin/ifrename: not found


When comparing boot and daemon.log, I can see that dhclient gets a DHCPACK a couple of seconds after the dhcbd is started, 8-12 secs for those boots I investigated.

Is there some pro (or some else also of course :) ) here who has got any suggestion of what to do? Specifically if you has any ideas of how to debug this problem, and what sorts of things I should  look for (in the logs and elsewhere). This must be som kind of bug in Ubuntu, but I don't know what causes the bug.

Note: in order to get /var/log/boot to work, I had to manually compile and install bootlogd. I did this in order to be able to debug these problems better. The problems existed before this, so this should not affect the booting process in any negative way.

Regards
Pär

Edit:
This is a desktop computer with a wired net connection , so those things about Networkmanager probably has nothing do to with this problem

---

