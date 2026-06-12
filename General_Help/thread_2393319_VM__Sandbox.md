---
title: "VM?  Sandbox?"
date: 2018-06-01
forum: General Help
---

### Post by mlnease on 2018-06-01
Hello,

I have legitimate access to an ebook provided I first install an Adobe application on my system.

No offense to anyone, but I don't trust Adobe.  I don't use any of their products and generally prefer to avoid non-FOSS applications.

So my question is, is there a relatively simple way (I'm no rocket scientist) to install some kind of virtual system within my xubuntu system that will allow me to download and install this software and use it (to read an epub) without compromising my xubuntu system?

Thanks in advance.

[edit]  The application is Digital Editions; I looked for a 'snap' for it but to no avail.  I'll keep trying your other solutions.

[edit]  As it turns out, this was all a fantasy.  The epub content can't be separated from Adobe Digital Editions and read on a different application--at least not by the likes of me.

p.s.  ***18.04***?  I think I may have missed something...

[edit]  
**Upgrading from Ubuntu 16.04 LTS**

 **Upgrades from 16.04 LTS will not be enabled until a few days after 18.04.1's release expected in [late July]("https://wiki.ubuntu.com/BionicBeaver/ReleaseSchedule").**

---

### Post by TheFu on 2018-06-01
I am a rocket scientist, but that doesn't matter here. ;)
I agree about your concerns.
There isn't any 100% certain method to do what you want, but few things in life are 100% certain.  We just play the odds in most things and try to mitigate those risks.

2G of RAM will make most of the possible solutions difficult.  With 4G, it wouldn't be an issue.  Ok ... so a few options for you to research.
* virtual machines using a full hypervisor. These are probably the most secure solution, but the most RAM and CPU will be used.
* Linux containers - like LXD.  You'll have to do some research on this. My experience is highly limited.
* Linux chroot.  This is probably too complex for people new to Linux to setup for a GUI program and a chroot doesn't constrain a program nearly as much as the others.  chroot is mostly being replaced by the cgroup tools.
* Linux "sandbox" tools, like firejail.  Firejail runs a program inside a constrained environment, but the install for the program is still on the main system.  If there isn't a firejail profile already for the application, then you'll want to create one that provides access only to what is required.
* "Snaps" - these are relatively new. Many programs haven't been converted to snaps, since doing that would also constrain where the app can see on the OS.  Snaps are being used much more in 18.04.

Containers, snaps, and sandbox tools all make use of cgroups, which is a way to constrain access to different kernel resources.  They are fairly lite, especially when compared to the full VM technique.

The full VM method has the longest history, so the most trust from a security standpoint.  They emulate the hardware for the OS, so all that emulated hardware requires RAM and CPU overhead. All of these solutions are complex and bugs which can be used by "bad actors" exist in all of them.

To learn more about these things, just google "ubuntu snaps" or "ubuntu lxd" or ... you get the idea.  I'd start by looking for a snap for the specific adobe tool, but you didn't name it.  If you had 4G of RAM, the answer is easy - use a virtual machine. On a 2G system, you have to make trade-offs, unfortunately.

Anywho - hope this is helpful.

---

### Post by mlnease on 2018-06-01
Thanks for the speedy response, TheFu.  And a pleasure to meet a rocket scientist to add to the lengthy list of my correspondents a lot smarter than me.

Your reply is full of good food for thought.  I'll sort it out and respond here with whatever results I'm able to achieve.

Cheers,

mn

> **TheFu said:**
> I am a rocket scientist, but that doesn't matter here. ;)
I agree about your concerns.
There isn't any 100% certain method to do what you want, but few things in life are 100% certain.  We just play the odds in most things and try to mitigate those risks.

2G of RAM will make most of the possible solutions difficult.  With 4G, it wouldn't be an issue.  Ok ... so a few options for you to research.
* virtual machines using a full hypervisor. These are probably the most secure solution, but the most RAM and CPU will be used.
* Linux containers - like LXD.  You'll have to do some research on this. My experience is highly limited.
* Linux chroot.  This is probably too complex for people new to Linux to setup for a GUI program and a chroot doesn't constrain a program nearly as much as the others.  chroot is mostly being replaced by the cgroup tools.
* Linux "sandbox" tools, like firejail.  Firejail runs a program inside a constrained environment, but the install for the program is still on the main system.  If there isn't a firejail profile already for the application, then you'll want to create one that provides access only to what is required.
* "Snaps" - these are relatively new. Many programs haven't been converted to snaps, since doing that would also constrain where the app can see on the OS.  Snaps are being used much more in 18.04.

Containers, snaps, and sandbox tools all make use of cgroups, which is a way to constrain access to different kernel resources.  They are fairly lite, especially when compared to the full VM technique.

The full VM method has the longest history, so the most trust from a security standpoint.  They emulate the hardware for the OS, so all that emulated hardware requires RAM and CPU overhead. All of these solutions are complex and bugs which can be used by "bad actors" exist in all of them.

To learn more about these things, just google "ubuntu snaps" or "ubuntu lxd" or ... you get the idea.  I'd start by looking for a snap for the specific adobe tool, but you didn't name it.  If you had 4G of RAM, the answer is easy - use a virtual machine. On a 2G system, you have to make trade-offs, unfortunately.

Anywho - hope this is helpful.

---

### Post by TheFu on 2018-06-01
There's always someone smarter than me around. Always.

---

### Post by mlnease on 2018-06-01
A sound axiom.  Applies to 'tougher' too, according to my old kung-fu teacher (a great man).

Thanks again for your advice--working on it.  Found a compatible ram stick on Ebay and downloaded 18.04.

---

### Post by mohicann on 2018-06-03
Hi,

I would personally go for a VM as well with something light, lubuntu for instance. If you know that you are going to use unsafe material, you still can copy your VM and erase your first one to restart from a safe point. In the past, I would also have used Grsecurity but it is no longer freely downloadable and its unofficial forks stopped when came up meltdown, spectre and PTI.

---

### Post by mlnease on 2018-06-29
> **mohicann said:**
> Hi,  I would personally go for a VM as well with something light, lubuntu for instance. If you know that you are going to use unsafe material, you still can copy your VM and erase your first one to restart from a safe point. In the past, I would also have used Grsecurity but it is no longer freely downloadable and its unofficial forks stopped when came up meltdown, spectre and PTI.  All righty then--I've double my RAM to 4G.  I've--with reservations--installed VirtualBox (honestly don't trust Oracle either but VB seems highly recommended in *buntu forums).  I have one day left to download this epub,  dependent--as above--on installing Adobe, in this case in lubuntu/wine in the VM if I can figure it out in time.   Thanks, All.  mn

---

### Post by TheFu on 2018-06-30
If you don't want to use virtualbox, don't use virtualbox. There are other options.  I've been using KVM+libvirt+virt-manager for about 8 yrs. In that time, it started as a solid server-on-server solution, but now it is a well-regarded desktop-on-desktop solution.  

KVM is built into the Linux kernel. It is a type-1 hypervisor, if you are into labels. That means it is fast. Probably the fastest hypervisor providing full hardware abstraction.

libvirt is a cross-hypervisor compatibility layer (you don't use it directly as an end-user)

virt-manager is a GUI similar to the one provided by virtualbox to create, manage, run virtual machines with different virtualization technologies.  Last time I checked it supported KVM, Xen, QEMU, virtualbox, containers and Docker.  I think KVM is the default, so that is the easiest choice in the GUI.  There are lots of how-to guides for setting up KVM + virt-manager (also called VMM sometimes).  Check out some youtube videos, if you learn that way.  It isn't much more than apt install .... but there are a few manual steps dependent on your needs - mainly networking and ssh and ensuring you have QXL video drivers installed for any guests to get the high performance desktop video stuff.

BTW, looks like you need to update your signature - 4G now, right? ;)

---

### Post by mlnease on 2018-06-30
> **TheFu said:**
> If you don't want to use virtualbox, don't use virtualbox. There are other options.  I've been using KVM+libvirt+virt-manager for about 8 yrs. In that time, it started as a solid server-on-server solution, but now it is a well-regarded desktop-on-desktop solution.    KVM is built into the Linux kernel. It is a type-1 hypervisor, if you are into labels. That means it is fast. Probably the fastest hypervisor providing full hardware abstraction.  libvirt is a cross-hypervisor compatibility layer (you don't use it directly as an end-user)  virt-manager is a GUI similar to the one provided by virtualbox to create, manage, run virtual machines with different virtualization technologies.  Last time I checked it supported KVM, Xen, QEMU, virtualbox, containers and Docker.  I think KVM is the default, so that is the easiest choice in the GUI.  There are lots of how-to guides for setting up KVM + virt-manager (also called VMM sometimes).  Check out some youtube videos, if you learn that way.  It isn't much more than apt install .... but there are a few manual steps dependent on your needs - mainly networking and ssh and ensuring you have QXL video drivers installed for any guests to get the high performance desktop video stuff.  Thanks for all this--I've got rid of virtualbox and installed QEMU/KVM, virt-manager, libvirt-bin etc. etc.  Still working on getting it configured and up and running.  At the moment, attempting to start Virtual Machine Manager yields 

```
Unable to connect to libvirt.

Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started
 - You are member of the 'libvirtd' group

Libvirt URI is: qemu:///system

Traceback (most recent call last):
  File "/usr/share/virt-manager/virtManager/connection.py", line 903, in _do_open
    self._backend.open(self._do_creds_password)
  File "/usr/share/virt-manager/virtinst/connection.py", line 148, in open
    open_flags)
  File "/usr/lib/python2.7/dist-packages/libvirt.py", line 105, in openAuth
    if ret is None:raise libvirtError('virConnectOpenAuth() failed')
libvirtError: Failed to connect socket to '/var/run/libvirt/libvirt-sock': Permission denied
``` 

I've verified as much as I can of the above--I don't think libvirtd-daemon is starting.

 I'll keep working on it and report my results here.  > **TheFu said:**
> BTW, looks like you need to update your signature - 4G now, right? ;)

Right you are, thanks for the reminder and for all your help.

---

### Post by TheFu on 2018-06-30
Did you remove all the virtualbox stuff first?  1 hypervisor per physical install.

---

### Post by mlnease on 2018-06-30
Yes--at least I think so.  Any way I can check to be sure?  I used Synaptic 'Mark for Complete Removal (including configuration files)'--I am pretty much a GUI guy though I do use CLI as much as I can.

---

### Post by mlnease on 2018-06-30
By the way, my window of opportunity--to download and read this very obscure epub from University of Chicago Press--has pretty much run out.  If you're interested in *really *outside literature and can run it with Adobe in a virtual machine (my goal, of course), I suggest you take advantage of the link I've been unable to--before midnight CDT:

[http://www.bibliovault.org/cgi-bin/DeliverADE.epl?transid=a12DJmR7pSzvhzS5](http://www.bibliovault.org/cgi-bin/DeliverADE.epl?transid=a12DJmR7pSzvhzS5)

Thanks again for all your help.

---

### Post by TheFu on 2018-07-01
The requirement to "create and Adobe ID" stops me cold.  

For me, there is already way too many great opportunities for reading material that doesn't have those limits.

---

### Post by TheFu on 2018-07-01
> **mlnease said:**
> Yes--at least I think so.  Any way I can check to be sure?  I used Synaptic 'Mark for Complete Removal (including configuration files)'--I am pretty much a GUI guy though I do use CLI as much as I can.

I've never seen that issue.
Did you verify those 3 things in the error?

```
Verify that:
 - The 'libvirt-bin' package is installed
 - The 'libvirtd' daemon has been started
 - You are member of the 'libvirtd' group

```
Did you setup ssh first?

---

### Post by mlnease on 2018-07-01
I agree about Adobe.  And I have reservations about DRM in general at least in its present form.  I was in bookselling for many years and and my greatest reservation is the absence of a used ebook market.  DRM as it exists makes that impossible which means that ebooks are a luxury that most Americans (and others I suppose) really can't afford.

My intention was to install Adobe Digital Editions in a virtual machine (because the publisher requires it to download the drm-free epub); then to save the drm-free epub and delete the corporate spyware.  This is quite a fine publisher and they give away a free as in free beer *and* drm-free epub every month (as I understand it).**[CORRECTION:  The copy is *not* drm-free and *cannot* be separated from Adobe Digital Editions]**.  The idea of installing the malware on a virtual machine was that I'm not sophisticated enough to be confident that I could remove all the malware after having infected my OS directly.  In that way I hoped (and still do hope) to be able to acquire a new, free, drm-free book from this publisher each month to do with as I please--just as if I'd acquired a second-hand book.  That's the idea, anyway.

---

### Post by mlnease on 2018-07-01
I did verify that 'libvirt-bin' is installed and that I'm a member of that group.  I don't think 'libvirtd' daemon had been started but not sure.  I had *not* set up ssh--I just installed it and will get back to you.  Thanks again.

---

### Post by TheFu on 2018-07-01
> **mlnease said:**
> I agree about Adobe.  And I have reservations about DRM in general at least in its present form.  I was in bookselling for many years and and my greatest reservation is the absence of a used ebook market.  DRM as it exists makes that impossible which means that ebooks are a luxury that most Americans (and others I suppose) really can't afford.

DRM provides a license, not ownership.  That means the days of discovery an old book that your grandma read in her 20s is going to be lost to future generations.  I won't purchase books that have DRM and cannot be gifted to my kids and grandkids.

PDF v1.6 or earlier is well supported on most platforms. Newer PDF versions only work on currently supported commercial OSes which all include tracking.   PDF is useful in publishing where total control over page layouts, but for all other uses, it should be avoided.  I worked in publishing about 5 yrs - both paper and electronic. Most of the time people use PDF, they really should be using simplified HTML.

IMHO.

As for getting vmm and KVM working, let me know if you are still having issues and we can start by checking everything necessary to run it.  I've made common assumptions about your system which might not be true for older systems.
```

$ kvm-ok
$ systemctl status libvirtd
``` to start.

---

### Post by mlnease on 2018-07-01
> **TheFu said:**
> DRM provides a license, not ownership.  That means the days of discovery an old book that your grandma read in her 20s is going to be lost to future generations.  I won't purchase books that have DRM and cannot be gifted to my kids and grandkids.

PDF v1.6 or earlier is well supported on most platforms. Newer PDF versions only work on currently supported commercial OSes which all include tracking.   PDF is useful in publishing where total control over page layouts, but for all other uses, it should be avoided.  I worked in publishing about 5 yrs - both paper and electronic. Most of the time people use PDF, they really should be using simplified HTML.

IMHO.

As for getting vmm and KVM working, let me know if you are still having issues and we can start by checking everything necessary to run it.  I've made common assumptions about your system which might not be true for older systems.
```

$ kvm-ok
$ systemctl status libvirtd
``` to start.

```
mn@mn-OptiPlex-745:~$ kvm-ok
INFO: /dev/kvm does not exist
HINT:   sudo modprobe kvm_intel
INFO: For more detailed results, you should run this as root
HINT:   sudo /usr/sbin/kvm-ok
mn@mn-OptiPlex-745:~$ systemctl status libvirtd
&#9679; libvirt-bin.service - Virtualization daemon
   Loaded: loaded (/lib/systemd/system/libvirt-bin.service; enabled; vendor pres
   Active: active (running) since Sat 2018-06-30 11:20:45 PDT; 21h ago
     Docs: man:libvirtd(8)
           http://libvirt.org
 Main PID: 505 (libvirtd)
   CGroup: /system.slice/libvirt-bin.service
           &#9500;&#9472; 505 /usr/sbin/libvirtd
           &#9500;&#9472;8026 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default
           &#9492;&#9472;8027 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default

Jun 30 11:20:59 mn-OptiPlex-745 libvirtd[505]: Failed to probe capabilities for 
                                               failed to initialize KVM: No such
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: started, version 2.75 cachesize 1
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: compile time options: IPv6 GNU-ge
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq-dhcp[8026]: DHCP, IP range 192.168.122.2
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq-dhcp[8026]: DHCP, sockets bound exclusiv
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: reading /etc/resolv.conf
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: using nameserver 127.0.1.1#53
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: read /etc/hosts - 7 addresses
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: read /var/lib/libvirt/dnsmasq/def
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq-dhcp[8026]: read /var/lib/libvirt/dnsmas
lines 1-22/22 (END)...skipping...
&#9679; libvirt-bin.service - Virtualization daemon
   Loaded: loaded (/lib/systemd/system/libvirt-bin.service; enabled; vendor preset: enabled)
   Active: active (running) since Sat 2018-06-30 11:20:45 PDT; 21h ago
     Docs: man:libvirtd(8)
           http://libvirt.org
 Main PID: 505 (libvirtd)
   CGroup: /system.slice/libvirt-bin.service
           &#9500;&#9472; 505 /usr/sbin/libvirtd
           &#9500;&#9472;8026 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper
           &#9492;&#9472;8027 /usr/sbin/dnsmasq --conf-file=/var/lib/libvirt/dnsmasq/default.conf --leasefile-ro --dhcp-script=/usr/lib/libvirt/libvirt_leaseshelper

Jun 30 11:20:59 mn-OptiPlex-745 libvirtd[505]: Failed to probe capabilities for /usr/bin/kvm: internal error: QEMU / QMP failed: Could not access KVM kernel module: No such file or
                                               failed to initialize KVM: No such file or directory
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: started, version 2.75 cachesize 150
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect inotify
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq-dhcp[8026]: DHCP, IP range 192.168.122.2 -- 192.168.122.254, lease time 1h
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq-dhcp[8026]: DHCP, sockets bound exclusively to interface virbr0
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: reading /etc/resolv.conf
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: using nameserver 127.0.1.1#53
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: read /etc/hosts - 7 addresses
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq[8026]: read /var/lib/libvirt/dnsmasq/default.addnhosts - 0 addresses
Jun 30 11:21:16 mn-OptiPlex-745 dnsmasq-dhcp[8026]: read /var/lib/libvirt/dnsmasq/default.hostsfile
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
lines 1-22/22 (END)
```

Sorry to be taking so much of your time--thanks again for all the help.

Huh:

```
mn@mn-OptiPlex-745:~$ sudo /usr/sbin/kvm-ok
[sudo] password for mn: 
INFO: /dev/kvm does not exist
HINT:   sudo modprobe kvm_intel
INFO: Your CPU supports KVM extensions
INFO: KVM (vmx) is disabled by your BIOS
HINT: Enter your BIOS setup and enable Virtualization Technology (VT),
      and then hard poweroff/poweron your system
KVM acceleration can NOT be used
mn@mn-OptiPlex-745:~$ 
```

I'll try editing my BIOS, restart and get back.

Well!  I enabled VT in BIOS setup--now 16.04 won't start at all.  Hmph.  Guess I'll try troubleshooting it but may be looking at a reinstall.  If so I'll reproduce everything I've tried so far and let you know the results.

Thanks very much again for all your time and attention.

[edit]  It was an Xorg crash--seems ok now.

Enabling VT in BIOS seems to have done the trick--VMM (QEMU/KVM) is running.  I noticed as I was restarting that there are now several KVM options in GRUB, too.  So next step is to install lubuntu in VMM?

---

### Post by mlnease on 2018-07-01
> **TheFu said:**
> DRM provides a license, not ownership. You're right, of course.    If corporate contract lawyers have their way, we won't own anything anymore--we'll just lease (strictly curtailed) rights to their products temporarily.  It's a tendency I'd like to see reversed.> **TheFu said:**
> That means the days of discovery an old book that your grandma read in her 20s is going to be lost to future generations.  I won't purchase books that have DRM and cannot be gifted to my kids and grandkids.

PDF v1.6 or earlier is well supported on most platforms. Newer PDF versions only work on currently supported commercial OSes which all include tracking.   PDF is useful in publishing where total control over page layouts, but for all other uses, it should be avoided.  Agreed--> **TheFu said:**
> I worked in publishing about 5 yrs - both paper and electronic. Most of the time people use PDF, they really should be using simplified HTML.

IMHO.

As for getting vmm and KVM working, let me know if you are still having issues and we can start by checking everything necessary to run it.  I've made common assumptions about your system which might not be true for older systems.
```

$ kvm-ok
$ systemctl status libvirtd
``` to start.

---

### Post by TheFu on 2018-07-01
> **mlnease said:**
>  
Enabling VT in BIOS seems to have done the trick--VMM (QEMU/KVM) is running.  I noticed as I was restarting that there are now several KVM options in GRUB, too.  So next step is to install lubuntu in VMM?

You need to setup the virtual hardware for the VM, then install from a normal ISO into the VM.  There should be a wizard to help.  Use virtio for the HDDs and networking devices. They are fastest and light.  Use QXL for the display/video stuff and it will be fast too.

If you get stuck, there are 1,000s of youtube videos on virt-manager.

A key thing that may not be clear is that you can manage, create, run VMs all from a remote client using an SSH connection.  ssh-keys will be honored.  But ...QXL doesn't work through the SSH (last time I checked), so it won't work over the internet.   On the LAN, it is pretty good for simple, non-GPU heavy desktops like mate, ldxe, xfce ... basically anything except KDE or Unity or Gnome3. Avoid those of you want to run over the network.

Also, don't over allocate RAM or CPU to the VM.  Leave 1G of RAM for the hostOS and 1 vCPU for the hostOS. Also, don't forget that the amount of RAM you allocate doesn't include the overhead of the HW being simulated, so assume about 250MB extra for that and video-RAM.

If you run full screen, it should feel nearly native on performance.

---

### Post by mlnease on 2018-07-01
Up and running and connected to the internet.  Thanks a million for all the help--never could've done it without you.

---

### Post by mlnease on 2018-07-01
Well.  Unsolved after all.  I can't make this work.  Good luck to you and sorry if this thread has led you on.  I'm *done*.

In short, if you haven't the skills of a programmer, system adminstrator or rocket scientist, [I]

Don't.  

Bother.[/I]

---

### Post by larry2311 on 2018-07-01
Also, check that your username/login is a member of the '***libvirtd***' group, as mentioned in your previous post.
Use the [FONT=courier new]id[/FONT] or [FONT=courier new]groups[/FONT] commands to check if the '[FONT=courier new]*libvirtd*[/FONT]' group is listed.

If not use:
```
sudo usermod -a -G libvirtd yourusername
```

Your username/login must be a member of the group.

Also, check out this reference: [URL="https://askubuntu.com/questions/930491/group-libvirtd-does-not-exist-while-installing-qemu-kvm"]https://askubuntu.com/questions/930491/group-libvirtd-does-not-exist-while-installing-qemu-kvm
[/URL]
and the usual Ubuntu doco: [URL="https://help.ubuntu.com/community/KVM/Installation"]https://help.ubuntu.com/community/KVM/Installation
[/URL]

---

### Post by mlnease on 2018-07-02
Thanks for the response--yes, libvirtd group is there and I am a member.  That wasn't a problem.  The most recent problem is that on reopening I started receiving error messages saying I was out of memory (after running > sudo apt update && sudo apt upgrade).

The long and short of it is that, despite all the excellent and generous help I got here I just don't have the skills to configure it--to many questions within questions.  So I'm marking the thread 'solved' even though, for me, it isn't and won't be.  Thanks for the advice just the same.

---

### Post by mlnease on 2018-07-02
lubuntu space

---

### Post by deadflowr on 2018-07-02
How much storage did you allocate and how much can you allocate?

---

### Post by mlnease on 2018-07-02
Thanks for your interest, I do appreciate it--I really don't know the answer to either question.  Basically I just allowed the wizard defaults and have no idea how to change the memory allocation.

I take it back--my memory allocation was 2626.

I really do appreciate all the help but can't help thinking I'm wasting everyone's time.

Thanks, all, just the same.

---

### Post by deadflowr on 2018-07-02
it's not the memory (which we usually relate to RAM), it's the hard drive storage space that is the issue (at least the issue in the dpkg error output.)
virt manager's storage settings can be daunting at first.
(Here's a basic storage settings example/help guide:
[https://www.tecmint.com/manage-kvm-storage-volumes-and-pools/]("https://www.tecmint.com/manage-kvm-storage-volumes-and-pools/")
I'm not sure but I thought the defaults was somewhere around 20GB, but it might shrink below that based on how much space the host system can give.
(Like if the host only has 10GB free then that would be all it can give, or at least I think it's like that.)

Not that that helps anything

> I really do appreciate all the help but can't help thinking I'm wasting everyone's time.
It'll only be a waste if you give up and erase what's been advised from your memory.

---

### Post by mlnease on 2018-07-02
> **deadflowr said:**
> it's not the memory (which we usually relate to RAM), it's the hard drive storage space that is the issue (at least the issue in the dpkg error output.)
virt manager's storage settings can be daunting at first.
(Here's a basic storage settings example/help guide:
[https://www.tecmint.com/manage-kvm-storage-volumes-and-pools/](https://www.tecmint.com/manage-kvm-storage-volumes-and-pools/)
I'm not sure but I thought the defaults was somewhere around 20GB, but it might shrink below that based on how much space the host system can give.
(Like if the host only has 10GB free then that would be all it can give, or at least I think it's like that.)

Not that that helps anything


It'll only be a waste if you give up and erase what's been advised from your memory.

Thanks again.  I've opened the link and am trying to make sense of it.  I'll post any results here.  From the link:

> **3.** There is no restriction where the storage pool will be created, but it is very recommended to create ‘**SPool1**‘ directory on separate partition. One important thing also is to give the right permissions and ownership for this directory.

 I will use **/dev/sda3** as my partition, you may have a different one. Make sure you have mounted it properly.

I've determined to use /dev/sda6/ for my partition, but don't understand how to create 
```
ext4 /dev/sda6 /mnt/personal-data/
``` there.

Thanks again for your time and attention.

---

### Post by mlnease on 2018-07-02
> **deadflowr said:**
> it's not the memory (which we usually relate to RAM), it's the hard drive storage space that is the issue (at least the issue in the dpkg error output.)
virt manager's storage settings can be daunting at first.
(Here's a basic storage settings example/help guide:
[https://www.tecmint.com/manage-kvm-storage-volumes-and-pools/](https://www.tecmint.com/manage-kvm-storage-volumes-and-pools/)
I'm not sure but I thought the defaults was somewhere around 20GB, but it might shrink below that based on how much space the host system can give.
(Like if the host only has 10GB free then that would be all it can give, or at least I think it's like that.)

Not that that helps anything

It'll only be a waste if you give up and erase what's been advised from your memory.

I added this as an edit to my last post, but maybe I should've posted it as a new reply.  Sorry for the redundancy.

From the link:

> **3.** There is no restriction where the storage pool will be created, but it is very recommended to create ‘**SPool1**‘ directory on separate partition. One important thing also is to give the right permissions and ownership for this directory.

 I will use **/dev/sda3** as my partition, you may have a different one. Make sure you have mounted it properly.                      

I've determined to use /dev/sda6/ for my partition, but don't understand how to create 
```
ext4 /dev/sda6 /mnt/personal-data/
``` 
 there.

Thanks again for your time and attention.

---

