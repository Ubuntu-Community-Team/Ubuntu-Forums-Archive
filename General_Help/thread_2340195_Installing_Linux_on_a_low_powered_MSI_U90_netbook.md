---
title: "Installing Linux on a low powered MSI U90 netbook"
date: 2016-10-16
forum: General Help
---

### Post by GeordieJedi on 2016-10-16
Hi there.

I'm, looking to install Linux on a low spec machine. It's a netbook, an MSI U90
with 1GB RAM.

My neighbours daughter has been given this machine and would like to use for school
work (She's only 7, so it doesn't have to run anything too demanding).
Just basic web browsing, word processing, and maybe some basic graphics work.
It's currently running Windows XP (which is obviously, severely out of date).

I realise that it's an old, slow machine, but I'd like her to get some use from the
netbook.

I just want something easy to use and maintain. As they aren't particularly technically
minded, and I won't always be on hand to support them.

I've been having a good look around the net, but I'm struggling to find a distro
that can run on the Atom processor.

I was considering Lubuntu or puppy Linux.

Can anyone point me in the right direction and give me some advice please.


Full specs can be found here:
[https://en.wikipedia.org/wiki/MSI_Wind_Netbook](https://en.wikipedia.org/wiki/MSI_Wind_Netbook)

Basic specs:
CPU= Intel ATOM / Intel 945GSE, ICH7-M
RAM= 1GB
HDD= 120GB

TIA for any help or advice.

---

### Post by ajgreeny on 2016-10-16
Go Lubuntu 16.04, but watch out for the possible bug of the machine booting to a totally black screen, not even a command line where you can log-in as shown at  [https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460](https://bugs.launchpad.net/ubuntu/+source/lubuntu-meta/+bug/1575460) where I mention the solution.
> I had the same problem as Camilo Gonzalez in post #5, on a netbook with Atom 270 cpu and Intel 954M graphics.
Solved by booting with nomodesdet option from the grub menu to get a low resolution GUI and then installing the xserver-xorg-video-intel package.
All works very well now.

This bug is now perhaps overcome in the 16.04.1 point version, but as I showed above it can also be overcome relatively easily even if the bug is not yet squashed.

The Atom CPU is not a problem as such, apart from its low power, so don't worry about that; my machine is similar in specs and is still running fine with a fully updated Lubuntu 16.04, though I have also tried Xubuntu 16.04 on it and the difference in speed is not that great, so you may like to see if you like that as well.

---

### Post by GeordieJedi on 2016-10-22
Hi there ajgreeny.

That worked a treat !
And thank you for the heads up on the booting issue.

As you were correct, it did fail to boot properly. However after following the advice in the thread that you posted
I got it up and running in short order.

The neighbors daughter is over the moon with her "new" laptop/netbook.

So thanks once again for your help, it's very much appreciated.

---

