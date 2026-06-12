---
title: "Telnet issue after Virtualization"
date: 2022-08-12
forum: General Help
---

### Post by googleme2 on 2022-08-12
We have a custom application that runs on a very old version of Ubuntu its very custom and probably only 5 people in world that know the language.   Don't hate me for that as cost of replacement is 7 figures.   We virtualized the physical machine via VMware and have no problems booting or gaining access to the machine after.  Works just fine as a Ubuntu machine from what I see.   The issue is our application runs through telnet and telnet connects just fine but it sits at the motd message after logon and then times out.   It should show the motd then go into the program which is just a menu of commands.  I am lost for why it doesn't work as the only thing that would change is the underlying hardware.   I am not sure how the program runs once you login to telnet but maybe someone on here would have an idea.   I am a Windows guy not linux so be nice.

---

### Post by TheFu on 2022-08-12
I'd ask what is the business plan for when this program doesn't work any more?  Computers break.  Parts break.  Data becomes corrupted.

If it worked fine last week, restore a backup from last week.  If it worked last year, restore a backup from last year.  Backups aren't just a Unix thing. All businesses should have them for anything THAT important.

I've worked at a Fortune 10 company where we had "1000 X devices" helping about 20K customers. Over the years, those devices started failing and when I was there, we were searching for replacement parts on the used market.  The govt mandated that we provide the service as long as the clients wanted it and it was possible to provide. 

Sometimes I was unable to find replacement parts and we'd try to help client companies move to current, not N-10 generation old, services.  Many of these customers were small mom-n-pop businesses and didn't have any plan to migrate, so they died when the service wasn't possible anymore - because they lacked $50K to fund moving to newer, faster, better, more secure, services.  I felt bad, but there wasn't any way to do anything to help.  Old stuff dies.  It is a law of nature.  

When I left that job, there were less than 100 of those "X devices" still working and we weren't able to find any more parts.  We did cannibalize some of the failed systems to get some parts. BTW, we'd been losing money for a decade on the service.  Gotta love govt regulation - but not always.

Something worth so much to the company needs a migration plan to get on current solutions.  I'd be certain to get upper management a "Risk Acceptance" Document, so it is clear and formal, how close they are to total failure.  If it is THAT important, the BoD needs to know too.

Having a program run just by logging into any Unix system is pretty basic stuff that any admin can help with.  The company should engage someone qualified for half a day to fix this. I think it is a 10 min effort, but things are often more complex than what the client knows.  Hopefully, they will make the login ssh-based, then you can connect via localhost to the telnet, gaining much more network security. Also, they should be able to block all attempted connections from any IPs that aren't specifically allowed for ssh.  If you like, you can attempt this using tcp_wrappers. It has been built-into most daemons for 20 yrs now. Definitely ssh and telnetd have it.

---

### Post by googleme2 on 2022-08-12
Totally agree.   Business view vs IT is always different.   This is a DIBOL program so if you look at the system you see nothing outside of normal Ubuntu stuff.  No clue how the program works and the only vendor that supports it mainstream cannot do anything since we do not have the uncompiled code.   I am just perplexed on why it works on physical system but as soon as I virtualize it does not.   Nothing changed except the hardware drivers, I also do not know how the custom program interacts with telnet.   MOTD comes up and it just sits there flashing cursor then eventually times out.   Seems like a simple service or something isn't running but no clue.   I've compared production and this all around and nothing is different.   We are talking Ubuntu 10.04 also... LOL.

---

### Post by arraybolt3 on 2022-08-12
You are using the VM with bridged networking, right? Part of me thinks you shouldn't be able to get even this far if you were using user-mode networking, but it might be something to look into. Also, perhaps KVM would work better than VMware? KVM is designed to work with Linux from square one, VMware can have some serious problems.

---

### Post by TheFu on 2022-08-13
Bridged networking would be my first guess as  arraybolt3 says.

Sigh. I miss 10.04.  It was the best Ubuntu ever released, but hasn't been supported for 7 yrs, so I'm loath to help.  10.04 didn't have any surprises and worked like we expect every Linux server to work.  Disks, networking, DNS, even the GUI on the desktop versions, all worked as expected. I miss those days/release.

Drivers matter.  They typically aren't installed separately on Linux. The kernel should come with the needed drivers 98% of the time, unless there is some proprietary external hardware.

I started using KVM/QEMU when 10.04 was released. We dumped VMware ESX and ESXi, along with Xen. Best decision I've made related to VMs.  For storage and network drivers, the virtio drivers should be used. I think those are provided with all Ubuntu releases since 10.04. Faster and lower system overhead for the hostOS.

---

### Post by kinddolphin8827 on 2022-08-13
Another  reason that your customer could be hanging on to this legacy  configuration is that they fear that if they modernized a mission critical component of their daily workflow they may go broke. When in fact the would do themselves a gigantic favor by upgrading to a more modern  system of virtualization of all mission critical  components of their business. What I just can't  wrap my head around is thae fact that  it  may be the case that the piece of soft ware  the client in question is hanging on to may depend on older version of key libraries and  system wide software  such as perl or even a more archaic programming language such as fortran or maybe even COBAL.

---

