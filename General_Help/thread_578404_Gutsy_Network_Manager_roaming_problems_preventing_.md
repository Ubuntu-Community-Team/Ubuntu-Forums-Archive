---
title: "Gutsy Network Manager roaming problems preventing NIS from binding"
date: 2007-10-17
forum: General Help
---

### Post by garymansell on 2007-10-17
Hi,

I have a dell D630 with an Intel 3945 ABG wireless card it has a fully updated Gutsy Beta OS installed.

I have run into problems with NIS not being able to bind to the NIS server which I think are ultimately due to Network Manager.

As the machine boots it hangs for ages at the ypbind stage which ultimately times out and fails. The machine continues to boot and only local user accounts can login.

If I login as a local user and restart NIS with sudo /etc/init.d/nis restart then I find that I can logout and then login successfully using a NIS user account.

I have done some research on the net and I have a suspicion that this may be something to do with problem in Network Manager - I was finding that I had to disable roaming mode to get a DHCP address lease for the wired network connection sometimes.

Any Ideas/Suggestions gladly received

Rgds

Gary

---

### Post by negated on 2007-10-17
You could try replacing network manager with [WICD]("http://wicd.sourceforge.net/"). They have Unbuntu repositories on the download page.

I did last night and can't believe I didn't know about this sooner! Now I have no problems connecting to my school WPA2 network, home, etc. Everything works the way you would imagine it would.

-S

---

### Post by garymansell on 2007-10-18
I am still having troubles with this even if I swap out Network Manager for WICD.

When I boot the machine it still hangs as it trys to bind to the NIS domain and when this timeout's and the machine comes up, I can login (very slow) and see that neither eth0 (wired) or eth1 (wireless) are configured.

If I try running sudo ifup eth0 I get the response: 

unknown interface eth0=eth0

If I add the following lines to the file /etc/network/interfaces:

auto eth0
iface eth0 inet dhcp

Then the machine boots up fine with the wired network interface (eth0) coming up OK and hence NIS binds OK.

I can then use WICD to turn on and off both the wired and wireless interfaces OK and everything seems to be OK but this cannot be the expected way of working as this effectively turns off roaming mode for networking !!

Surely someone must have come across this before.

Help much appreciated as this is the only thing stopping me being able to migrate to gutsy.

Rgds

Gary

---

### Post by kvtb on 2007-10-20
I can confirm, I have the same problem with NIS and NetworkManager

some log files such as daemon.log can become very large due to NetworkManager .


Oct 20 12:20:31 s-abrt NetworkManager: <info>  Will activate connection 'eth0'.
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Device eth0 activation scheduled...
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) started...
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Oct 20 12:20:31 s-abrt NetworkManager: <WARN>  nm_dhcp_manager_begin_transaction(): dhcdbd not running!
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) failure scheduled...
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Activation (eth0) failed.
Oct 20 12:20:31 s-abrt NetworkManager: <info>  Deactivating device eth0.
Oct 20 12:20:31 s-abrt NetworkManager: <info>  SWITCH: no current connection, found better connection 'eth0'.
Oct 20 12:20:31 s-abrt NetworkManager: <WARN>  nm_dhcp_manager_get_state_for_device(): dhcdbd not running!

And above lines keep repeating for a large number of times.


It is very annoying.

---

### Post by doyston on 2007-11-15
Has anyone fixed this yet?  Just tried 7.10 64-bit and the whole thing fell over with the NetworkManager problem as soon as I rebooted after NIS setup.

Seems fairly fundamental failure (especially as I'm trying to persuade my colleagues to switch from RHEL to Ubuntu).

---

### Post by Tempest261 on 2007-11-21
I'm having the same *EXACT* issue here, only with Fedora 8 (at work). We have a bunch of Fedora Core 3 boxes, and a couple Fedora 7 boxes, but I decided to dip my toe into Fedora 8. We (our NIS admin and I) spent all day yesterday trying to troubleshoot the issue- modifying every configuration file and script under the sun. We, too, were able to get it to work if we manually logged in as root (we have no local users on these boxes) and started it by hand and then logged back in as a NIS user, but never were able to get NIS to bind on a fresh boot. 

So, taking all of that into account, it seems that whatever changed between Feisty->Gutsy and F7->F8 in context with NIS and/or networking in general broke NIS, at least for some network setups. 

Anyone have any other ideas?

---

### Post by xargon on 2007-12-01
Did anyone find a solution to this? I am having the same problem. The machine is taking ages to boot as it hangs at the ypbind stage...times out and than I cannot login anymore...

Any help would be really useful.

Thanks,
xarg

---

### Post by anoir on 2007-12-15
The same issue here, too.

After installing nis, autofs, and nfs-common onto Gutsy, I edited various configuration files under /etc:

auto.master
defaultdomain
nsswitch.conf
passwd
group
host.conf 

Restarting nix and ypbind services gives me nis directory, but I cannot log into the nis user. The boot process takes like forever. I also tried command line without success.

I guess the following bugs in Launchpad are related to this problem:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/152794](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/152794)
[https://bugs.launchpad.net/ubuntu/+source/nis/+bug/26717](https://bugs.launchpad.net/ubuntu/+source/nis/+bug/26717)

--

I translated this post from Japanese LoCo Forum on behalf of a member.

---

### Post by dinoc on 2008-06-20
I have the same problem with NIS , after upgrading to Hardy .
Another problem is that , with a NIS user I'm not able to do a "xhost +" on a terminal/console, as I'm able to do this with any local user.

---

### Post by doyston on 2008-07-04
This bug still seems unresolved.  Fiddling with startup orders, or adding a nis restart line to /etc/rc.local as recommended in

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/152794/comments/13](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/152794/comments/13)

hasn't worked.  Those with better understanding of these things have suggested changing YPBINDARGS in the nis default setup:

[https://bugs.launchpad.net/ubuntu/+source/nis/+bug/224828/comments/6](https://bugs.launchpad.net/ubuntu/+source/nis/+bug/224828/comments/6)

but solution failed to work for our network.  Unfortunate, as users are unprepared to upgrade or change OS whilst this bug is outstanding.

---

