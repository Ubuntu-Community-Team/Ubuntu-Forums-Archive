---
title: "Ubuntu 18.04 and system error at every login"
date: 2019-08-22
forum: General Help
---

### Post by jpp. on 2019-08-22
Hello  At every login on my Lenovo T470 laptop, running 18.04, something is crashing and I am asked if I want to send an error report. All seems to work fine though, but the popup annoys me. Please find attached the system log file.  

Any suggestions as to where I might look for solving this issue? I've permanently disabled the bluetooth radio as I dont use it and no reason to have it enabled then.  Please let me know if you need any other information.

---

### Post by uRock on 2019-08-22
I see there is a bug report for that error here, [https://bugs.launchpad.net/ubuntu/+source/spice-vdagent/+bug/1800196](https://bugs.launchpad.net/ubuntu/+source/spice-vdagent/+bug/1800196)

For others looking at this thread, the info from the above log message file is,```
19:27:45 kernel: xhci_hcd 0000:3d:00.0: xHCI host controller not responding, assume dead
19:26:02 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
19:26:01 pulseaudio: [pulseaudio] backend-ofono.c: Failed to register as a handsfree audio agent with ofono: org.freedesktop.DBus.Error.ServiceUnknown: The name org.ofono was not provided by any .service files
19:25:56 kernel: xhci_hcd 0000:3d:00.0: HC died; cleaning up
19:25:34 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
19:25:26 wpa_supplicant: dbus: Failed to construct signal
```

---

### Post by fragglebliss on 2019-08-23
Surely this must be one the longest running bugs in Linux history. I've had it for years. I have got so used to it I've come to just expect it and would actually be concerned if it didn't pop-up! :D

---

### Post by deadflowr on 2019-08-23
Clear out the /var/crash directory.
Crash reports generated are saved here.

Sometimes you might have had a crash a while back but when you reboot it sees that old crash report and 
thinks it's new, so it tells you there is another system problem. I think t relates to whether or not you reported it yet.
(I think if you haven't reported it yet it will keep asking until you do, or until you delete the crash report.)

Clearing it out should stop that.
(Well until there is another crash)

You can see what the crash(es) are by opening the Files program and navigating to the var > crash directory (click on Other Locations > Computer to get the system directories include var)
and opening the crash report with the crash report program. (simply double click on any file in the /var/crash directory will auto open the crash report utility program.)
It'll tell you what actually crashed, plus some non-sense information useless to any normal user/person.

You can also turn off the crash reporting altogether
see: [https://askubuntu.com/a/93467]("https://askubuntu.com/a/93467")

---

### Post by jpp. on 2019-08-23
Thanks deadflowr, I'll be sure to check at next boot. The dir is empty right now, made a habit of submitting the report. :-) Its a real shame if one should be forced to disable crash reporting all together due to a stupid old bug.

---

### Post by TheFu on 2019-08-23
Well, spice and virtio are related to using KVM+libvirt, so if you aren't, the install seems to think you are.
Big into virtualization? Yes?

If not, you don't need those subsystems. They are safe to remove.

---

### Post by uRock on 2019-08-23
Yup, it is not installed by default in Debian and I have virtual machines in VirtualBox.

---

### Post by jpp. on 2019-08-24
Hello TheFu

I've installed Virtualbox recently, but the error was there before that.

So youre saying I should be OK to remove spice and virtio packages right?

---

### Post by dora5 on 2019-08-25
This is a nuisance error message that usually doesn't mean a thing, and I ignore it.  I once saw an explanation of it.   I've gotten it since I first installed Ubuntu, and that is normal.  Actually I see far less of it lately, and it's also far more random.   What it doesn't mean is there is a system error.    

I think there is actually a way to configure Ubuntu so you don't get that system error message but I've forgotten where I saw that.   Probably one of those web sites and videos on how many things to do after you install Ubuntu.

---

### Post by TheFu on 2019-08-25
> **jpp. said:**
> Hello TheFu

I've installed Virtualbox recently, but the error was there before that.

So youre saying I should be OK to remove spice and virtio packages right?

Those packages are for use by KVM virtual machines and spice (replacement for RDP/VNC/NX) is only possible under KVM to my knowledge.  virtualbox doesn't use either.  I have no idea how they would be installed unless you installed KVM related stuff.  The spice client would be a separate package.
```
$ dpkg -l |grep spice
```
I have 8 client-side packages and 1 server-side one.

Having multiple hypervisors installed on the same physical system isn't a good idea, BTW.

---

