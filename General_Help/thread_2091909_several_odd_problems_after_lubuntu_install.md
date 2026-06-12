---
title: "several odd problems after lubuntu install"
date: 2012-12-06
forum: General Help
---

### Post by DrScum on 2012-12-06
I am using ubuntu for several years now for work and leisure on both desktops and laptops. Recently I installed lubuntu on an older laptop (Dell inspiron 1501 with a single core AMD Sempron 3600+ processor and 2GB memory). I am facing problems with network connections, file sharing and DVD playback.

Network: I couldn't figure out how to configure the wired network connection. I can configure the wired connection using the network connections gui, but I can't get the adapter to connect while the wireless adapter is working (that one works well).

file sharing: I couldn't figure out how to get file sharing to work. I installed and uninstalled samba and samba4 several times, following various instructions on the internet, but I can't get it to work. Currently I have samba installed (as far as I can tell from the installed packages visible in the synaptic package manager).

DVD Playback: several DVD's won't playback correctly and will freeze the whole system to the point where I have to pull the power plug. First I thought this is a hardware problem but the drive works fine when unsing puppy linux from a pendrive.

What I could need is some help diagnosing and hopefully solving these problems (one at a time of course). Top priority being the file sharing problem.

Thanks in advance.

---

### Post by Cheesehead on 2012-12-06
> **DrScum said:**
> I can configure the wired connection using the network connections gui, but I can't get the adapter to connect while the wireless adapter is working (that one works well).

Can you get the wired connection to work if the wireless is disabled?
What kind of 'configuration' does it need to work?
Is there any circimstance where wired works well?
Is it a static IP or DHCP network?


> **DrScum said:**
> file sharing: I couldn't figure out how to get file sharing to work.

Are you trying to share files?
Or are you trying to access files the have been shared by a different machine on the network?


> **DrScum said:**
> DVD Playback: several DVD's won't playback correctly and will freeze the whole system to the point where I have to pull the power plug.

Playing DVDs (DVD video) is different from reading data from a DVD. It's not clear which function (playing video, reading data) fails, and if the failure is consistent. 
Do all non-data DVDs fail to play? Do some work?
Do some data-only DVDs fail to work?

---

### Post by DrScum on 2012-12-06
Thanks  for the response.

LAN connection:
The wired connection works, if the wireless connection is disabled. The configuration is easy, there is a DHCP server on the network.


file sharing:
I am trying to do both, sharing files on the lubuntu machine and accessing files on the network. The network consists of Ubuntu and Windows machines, it's home network. The files on the network can be accessed from various ubuntu machines and windows machines on the network.


DVD:
Non DVD-disks work perfectly and also some DVD's did work and some DVD's worked for a while and stopped in the middle of a movie. I am using only original DVD's no ripping or copying involved.

---

### Post by DrScum on 2012-12-06
Here are some more data regarding the DVD problem I just gathered a minute ago:

In order to make sure that this is not a lubuntu specific problem I created a bootable ubuntu 12.04 usb-stick and tried a video that didn't work before: Inception.

The dvd becomes visible in the file manager, when trying to run it with movie player I get the message: can't read from source. 

At this point the DVD can't be ejected anymore neither through the file manager nor by pushing the eject button. When I shutdown the system, the display becomes white for a second and darkens. When I try to reboot, the DVD can be ejected by pushing the power button but the display doesn't work anymore. I mean you don't even see the boot screen, there is no display at all. In order to fix this I have to completely cut the power (line and battery for at least 30s). 

WEIRD, isn't it?

---

