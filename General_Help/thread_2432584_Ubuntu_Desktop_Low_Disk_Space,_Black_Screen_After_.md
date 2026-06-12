---
title: "Ubuntu Desktop Low Disk Space, Black Screen After Login"
date: 2019-12-04
forum: General Help
---

### Post by yunjilee on 2019-12-04
Hi all, I'm new to Ubuntu and I recently installed & hardened Ubuntu OS on VirtualBox (followed this guide: [https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3](https://gist.github.com/lokhman/cc716d2e2d373dd696b2d9264c0287a3)). 

After hardening, I ran into an error that said "Low disk space on “Filesystem root” 0 bytes disk remaining". Before I was able to look into this my computer shut down & I had to reboot the VM. However, every time I get to the user login page, when I click 'submit' it leads to a black screen, and when I wave my cursor around I can see parts of the frozen screen:

[IMG]https://i.imgur.com/czORqrum.png[/IMG]

Does anyone know if the low disk space error and the black screen are related & how to fix this? Please let me know if you need more details

---

### Post by TheFu on 2019-12-05
Is this a trick question?
Free up some storage where it is needed?  Probably need to use a "Try Ubuntu" flash boot to get into the machine.

Unix OSes don't like it when file systems run out of room.  If the file systems are being used for important temporary files, it is really bad and will crash the OS.

Any extra security measures really should only be performed by Linux experts.  When someone is new to Linux, it is highly likely an outdated suggestion will cause bad side-effects.  If it were a good idea, then the distro maker would have set it up as the default.

For example, the idea that adding a swap file is a good idea.  That gist shows what to do, but doesn't help with "why" or "why not".  If the system already has a swap file or swap partition, it isn't needed.  On a VM which has very little extra storage, like commonly happens with pre-built VMs, taking 4G for another swap will likely completely fill the available storage.  I suspect this is what happened to you.

The hostname stuff in the gist isn't the whole truth.  Unix systems use DNS to find other machines, not the hostname set by some remote admin.  The hostname might be used on a desktop running avahi, but other machines would use zeus.local to access, and only if those other machines also are running avahi on the same LAN.  Outside a LAN, it just isn't used.

Fork bombs have been prevented by the Linux kernel for over a decade.

I have NEVER seen host.conf used in over 25 yrs as an admin.  nsswitch.conf replaced it in the early 1990s.

In short, be very careful following "guides" from questionable sources. Looked over a few of the "articles" from the source provided in the gist.  Not impressed.  As for ubuntu security, there are sticky threads in the Security forum here with useful information and links.

Being secure as possible is a great thing, but how to accomplish it is always a moving target.  Learn the "why" so the what can be validated.  [https://blog.jdpfu.com/2016/10/04/lamp-server-security](https://blog.jdpfu.com/2016/10/04/lamp-server-security) is my overview of the "why" questions.

Be worried about advice from people on the internet.  Sometimes they have 1 more day of experience than you do, got something working, but really don't understand why it works, then write a blog/gist article.  Beware of experts in 1 field writing in other fields.  Software development is not System Administration, for example.  I've been paid to do both. They are very different vocations.

---

