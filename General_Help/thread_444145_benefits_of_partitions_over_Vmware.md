---
title: "benefits of partitions over Vmware?"
date: 2007-05-15
forum: General Help
---

### Post by rygar on 2007-05-15
Currently, I have separate partitions for XP, Vista, Ubuntu, and swap on my 100gb hard drive.

I'm considering deleting XP and Vista partitions and giving the space to Ubuntu, but had a few questions.
Here are a few pros/cons that I can see.  If you can add to the list, correct any misconceptions, or give me any advice on your personal experience, i'd be obliged.

keep partitions!
--if ubuntu goes bad, i can still boot into windows if they are under separate partitions.
--programs will run slower from VMware since ubuntu is still using up memory (how much slower?  i dont know)

lose the partitions!
--partitions require me to dedicate space to an OS.  the less space i give to Vista, the slower it will run, even though i don't use it much.
--no rebooting to run a windows program; i can even keep all my windows/programs open

is vmware even the best solution?  is there better VM software?
what is everyone's opinion on running VM software?

---

### Post by ikonia on 2007-05-15
it all comes down to usage and personal experience.

If for example your windows partitions are there to write the odd word document or write some small apps, or test website compatability, then vmware would be more than fine, 

if your windows partitions are there to allow you to say,play some games or do driver testing etc then vmware is not really an option.

The key thing to remember is vmware is virtualisation, so things like direct access to the hardware is dead - straight away.

Don't listen to what other peoples do "I delete my windows partitions, I do X, I do Y" consider your own personal situation and decided.

What do you use these operating systems for
How often do you access them
is rebooting to use them nativly a problem

etc.

---

### Post by rygar on 2007-05-15
off the top of my head, the most demanding software i would use would be Reason and occasionally some Adobe products like Illustrator.  will these run significantly slower in a virtual machine?  i've got 1gb of ram on a 1.86ghz pentium m laptop.  also, if ubuntu can see my hardware (say, an MPD to be used in Reason), will it almost certainly work in the VM?

---

### Post by hyperair on 2007-05-15
It would. The only apps (I think) that would not run in a VM are those 3d-rendering applications, or games, or something that requires intensive 3d-rendering. I rekcon that anything in Adobe's Creative Suite would work. As of now, VMware server as well as VirtualBox have zero support for Direct3D, though I hear that the VMWare workstation will be having 3d support. 

My configuration is one hard disk for Vista, another for Ubuntu Feisty, and in Ubuntu, a Virtualbox drive for Windows XP. One really important thing I noticed while using these virtualization products.. while applications seem to work with the same speed that they have on native hardware, memory intensive programs will slow down unless you have enough RAM. I used VMWare server back in the times when my RAM was 256+256MB DDR. Now I upgraded to 1GB +256MB DDR, and I noticed that the virtual machines run a lot smoother. But as it is, Virtualbox seems to run more efficiently compared to VMWare. I've never done any real benchmarks, my comments are based on the responsiveness of the applications. 

VMWare is more feature rich, and some may say it's bloated, but I believe it is easier to configure. VirtualBox on the other hand, is more lightweight, and it seems to run more efficiently, but slightly hard to configure. If you don't need much from the virtual machine (no direct connection to internet, but NAT-ed through your host, no direct network interface to the guest) then I'd suggest VirtualBox, as it seemingly runs quicker on the system, and is easy to configure in those aspects. If you're not really familiar with Linux but still need those advanced features then use VirtualBox. If you're familiar with Linux networking and TUN/TAP networks then VirtualBox is good for you. Otherwise, use VMWare.

---

### Post by zvacet on 2007-05-15
Do you realy need XP and Vista?If you don´t choose wich one you want to keep and delete other.That will give you more space  for Ubuntu.You can try out wich one is better for you,VMware or Virtual box.I worked with VMware only so I´&#7743; not in position to compare.Maybe this will be interesting to you

[http://ubuntuforums.org/showthread.php?t=361528]("http://ubuntuforums.org/showthread.php?t=361528")

---

### Post by rich.bradshaw on 2007-05-15
Why not just try it, it doesn't take long...

---

### Post by hyperair on 2007-05-15
You might also want to consider KVM. It's good, fast, but does not work on old CPU's like my P4 (without HT).

I wouldn't recommend Qemu, KQemu, and KVM though, unless you're willing to learn how to use those commands. From what I see, there's no GUI utility to configure those.

---

### Post by veloce on 2007-05-16
> **rygar said:**
> 
--programs will run slower from VMware since ubuntu is still using up memory (how much slower?  i dont know)


Because Ubuntu manages memory better than XP, the performance issue is not simple.  I find most things are working faster on virtual XP!

So the best idea is to try is as suggested.  Set up vmware and the windows virtual machines - see how they do your tasks.

---

### Post by hyperair on 2007-05-16
I too, found that most things work faster on Virtual XP. But that does not change the fact that I didn't install any UI enhancement on my Virtual XP. My native XP installation (while it was around) had WindowBlinds running, along with Google Desktop and a whole lot of other stuff. Result: laggy, unresponsive, the usual complaints.

---

### Post by veloce on 2007-05-16
> **hyperair said:**
> I too, found that most things work faster on Virtual XP. But that does not change the fact that I didn't install any UI enhancement on my Virtual XP. My native XP installation (while it was around) had WindowBlinds running, along with Google Desktop and a whole lot of other stuff. Result: laggy, unresponsive, the usual complaints.

That's a really good point - my virtual windows machine is bare bones, just windows and office.

---

### Post by hyperair on 2007-05-16
See, that's what I meant. There's no way that Windows' poor management of memory (I'm taking your word for it) will work any better with Virtual Memory.

---

