---
title: "Hardware Dianostic Tools?"
date: 2007-04-02
forum: General Help
---

### Post by ebozzz on 2007-04-02
Can anyone suggest some cost effective resources that could be used to to troubleshoot hardware related issues? I have quite a few machines around my place now and would like to have an efficient way resolving the problems that I occasionally have. I just had had one last night on a machine that I was setting up for my sister-in-law where lots of time was invested before I hit the right answer.

The system in question had been up for about a week and appeared to be running great. While I was surfing the web I got the blue screen with an error message in Windows and kernel panic in Ubuntu. I rebooted and got the same thing after a while but with a different message in Windows. 

After the second one I proceeded to run Memtest86. The RAM checked out fine but just to be sure I changed the set of sticks that were installed to a set that I knew were good. Same issue. I then pulled the hard drive, installed a drive that I knew was good and the problem appears to be solved. It would sure be nice to have some tools that I could use to help get to the root of the problem a lot faster.

---

### Post by FluffyElmo on 2007-04-03
I find it easier to narrow down hardware issues with Linux than with Windows as *lspci*, *dmesg* and */var/log/messages* provide a lot of information that can be hard to get under Windows. For more subtle issues, *GKrellM* provides monitoring of just about anything your motherboard reports. 

Generally though, my approach is to strip it down to the bare essentials and run MemTest86. Assuming it passes I test the hard disk with the relevant vendor boot disk. If that doesn't turn up problems then under Linux *Bonnie++ * does hard disk load testing and *cpuburn* will put a load on the CPU...for both of the last tests I monitor temperature via GKrellM. 

While not really Linux based per-se the Ultimate Boot CD combines a lot of useful diagnostic programs on one disk. If nothing else it combines most of the vendors hard disk test utilities in one place. [http://ubcd.sourceforge.net/]("http://ubcd.sourceforge.net/")

Like it or not though, diagnosing old hardware can be time consuming but hopefully some of the above will be helpful...

---

### Post by ebozzz on 2007-04-03
Thanks for your reply.  I am sure that your suggestions will be very helpful. Ultimately what I would to have is some utilities that I can run to run to help with troubleshooting. With the machines that I have at home and also machines from friends & family members that are coming my way, I need to be able to get to the root of the problem as quickly as I can. I will give the resources that you provided here a thorough look over. Thanks again.

---

