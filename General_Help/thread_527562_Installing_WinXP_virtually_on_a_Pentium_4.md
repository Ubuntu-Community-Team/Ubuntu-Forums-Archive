---
title: "Installing WinXP virtually on a Pentium 4?"
date: 2007-08-16
forum: General Help
---

### Post by QwUo173Hy on 2007-08-16
I know KVM needs a Dual Core processor to let you run windows, but is there another piece of software that will let me run it on a pentium 4? I thought I had seen people with virtual windows installation before the Core Duo came out.

---

### Post by oddin85 on 2007-08-16
you could try qemu: [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo")

---

### Post by aldenhg on 2007-08-16
It'll work with Qemu and VirtualBox (I use VirtualBox - it's a little easier to work with and as kernel drivers like Qemu) or even VMWare - it just won't be all that fast. I ran XP from 7.04 on my 3ghz P4 and it was pretty damn slow. It's an older P4 (the last of the Socket 478s - whatever core they were), so a newer one with SSE3 might be a bit faster, but I make no promises.
Also, just for the record, it's the built-in processor emulation instructions that are built in to the Cores and Core 2s that make the virtualization go so much faster. I recently got a C2D laptop and I have to tell you the virtualization is freakin' amazing. Everything runs at near enough to native speed that I don't notice any slowdown what so ever. If you get the scratch to put a new system together I'd recommend doing it.

---

### Post by Chaotic Thought on 2007-08-16
I have a P4 1800mhz and am running Windows XP inside a virtual machine using VMWare Player, and I think it runs fine. As long as it lets you get your work done, but of course it is too slow to play games (for games in Linux you need Wine or Cedega) Cedega is basically Wine but with special 3d extensions.

Really you for virtual machines the things you need most is lots of RAM. For quite a while I had only 256MB of RAM so running the VM meant lots of disk swapping, but now 512MB running the VM concurrently with Linux tasks is very smooth. Of course nowadays lots of people have systems with 1~2GB of RAM.

---

### Post by QwUo173Hy on 2007-08-16
Thanks guys. Yes, it's a 2GB system I'm working with so RAM isn't a problem. I'll look into Qemu. I've heard that VMware has improved performance in it's most recent versions so I might check that out too.

Regards,
Jarlath

---

### Post by HermanAB on 2007-08-16
Qemu is the fastest and it runs XP reliably.  VMware Server is however the easiest to install and get to work and it also runs XP reliably.  

Win2003 crashes on Qemu, but runs on VMware server - for that reason I always use VMware server, since I sometimes need to test things on 2003.

Just my tuppence worth.

Herman

---

### Post by QwUo173Hy on 2007-08-16
Thanks Herman. I'm installing it for a user as opposed to a dev so I'm pretty sure XP will do here. I think I'll take the time to put Qemu on since the concensus is that it runs faster.

Thanks folks,
Jarlath

---

