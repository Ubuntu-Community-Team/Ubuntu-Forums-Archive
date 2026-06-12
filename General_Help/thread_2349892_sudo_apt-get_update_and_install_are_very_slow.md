---
title: "sudo apt-get update and install are very slow"
date: 2017-01-19
forum: General Help
---

### Post by parminides on 2017-01-19
Updating (sudo apt-get update) has been very slow lately. It seems to stall at various points. It takes over 12 minutes to update. This was tested on 2 machines running Ubuntu 16.04, one of which was a fresh installation (only a few hours old).

Installation of individual packages (sudo apt-get install) has also slowed down greatly.

Surprisingly, updates proceed at blazing speed in my virtual machines. I recently installed a virtual machine running Linux Mint, and it zips through the update in 5 seconds. It's about 150x faster! I have a virtual machine running Ubuntu 16.04, and it updates even quicker (about 4 seconds).

I know that Ubuntu updates weren't so slow in the past. And why should they be so much faster in virtual machines. Does anyone know what's going on?

---

### Post by bearlake on 2017-01-19
> **parminides said:**
> Updating (sudo apt-get update) has been very slow lately. It seems to stall at various points. It takes over 12 minutes to update. This was tested on 2 machines running Ubuntu 16.04, one of which was a fresh installation (only a few hours old).

Installation of individual packages (sudo apt-get install) has also slowed down greatly.

Surprisingly, updates proceed at blazing speed in my virtual machines. I recently installed a virtual machine running Linux Mint, and it zips through the update in 5 seconds. It's about 150x faster! I have a virtual machine running Ubuntu 16.04, and it updates even quicker (about 4 seconds).

I know that Ubuntu updates weren't so slow in the past. And why should they be so much faster in virtual machines. Does anyone know what's going on?

Try a different mirror.

---

### Post by parminides on 2017-01-19
I don't think the mirror is the problem. All three Ubuntu machines (2 physical and 1 virtual) use us.archive.ubuntu.com and security.ubuntu.com. For some reason the virtual machine doesn't hang and stall. The 2 physical machines took about 12 minutes to run the update.

As another check, I did a "sudo apt-get update" after booting to live usb. Again, it took around 12 minutes. At least one of the mirrors used was different: archive.ubuntu.com. (I think it used security.ubuntu.com, but I forgot to write it down.)

All the previous update tests were done at home. I'm at a cafe now with one of the physical machines (a laptop). I did an update test and it finished almost instantaneously. (Perhaps this is because there's nothing to update.)

In the cafe I booted to live usb, which I believe is not persistent. It updated in 20 seconds. Both virtual machines also boot quickly at the cafe (around 5 seconds).

In summary,

1. The physical machines (1 laptop and 1 desktop) update very slowly at home (even with a usb boot, which uses a different mirror).
2. The virtual machines update very quickly at home and at the cafe.
3. The laptop updates very quickly at the cafe.

What would make the laptop (either native or live usb) boot slowly at home but quickly at the cafe? Presumably, the other physical computer would behave similarly.

---

### Post by ian-weisser on 2017-01-19
Try a different mirror, really.
The most common reasons for updates-are-slow are server load and network congestion.
Eliminate the most common causes before assuming your system is somehow at fault.

Many of us likely have the same setup you do, and few of us are slow.

That the VM does not run slowly does not eliminate server load nor network congestion as possible causes. Sometimes a connection gets lucky and runs fast, sometimes not.

---

### Post by parminides on 2017-01-19
> **ian-weisser said:**
> Try a different mirror, really.

When I get home I will. There's no point in doing it at the cafe when all updates are proceeding very quickly without changing mirrors. If I can't duplicate the problem here, nothing I do can justify any conclusions about causes/solutions.

BTW, I didn't go to a cafe to study this issue. I had to drop someone off at work and stopped by at a cafe afterward. When I get home, I'll see if updates are still slow. If they are, I'll change mirrors and see what happens.

---

### Post by lisati on 2017-01-19
> **bearlake said:**
> Try a different mirror.

+1

There's a bunch of stuff that can confound connection speed, and if you're at a cafe there's possibly something running behind the scenes that works a bit differently to what happens when you're at home.

---

### Post by gupperino on 2017-01-19
It's most likely, as everyone is saying, a network issue. Try a different mirror (wow original answer) or maybe use ethernet if you weren't before. It can help you squeeze the maximum network speeds out of your internet.

---

### Post by parminides on 2017-01-19
I got home, changed the mirror to [http://www.gtlib.gatech.edu/pub/ubuntu](http://www.gtlib.gatech.edu/pub/ubuntu), and updates were still extremely slow!

Based on [https://www.bearfruit.org/2013/05/06/ubuntu-server-having-ipv6-probs-its-easy-to-disable](https://www.bearfruit.org/2013/05/06/ubuntu-server-having-ipv6-probs-its-easy-to-disable), it appears that there is a conflict or miscommunication involving IPv6 and my server/router at home. (Why it doesn't affect the virtual machines I'll leave as a reader exercise.)

The solution proposed in the body of the article was to add the following 3 lines to /etc/sysctl.conf:

```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

Then run "sudo sysctl -p".

I'm reluctant to mess around with a file that claims to have settings that "can improve the network security of the host and prevent against some network attacks including spoofing attacks and man in the middle attacks through redirection." However, as a test, I verified that the workaround does restore my update speed. After I confirmed that it works, I removed those 3 lines until further explanation or clarification.

In the comment section of the article, someone suggested to comment out the following line (and any subsequent lines) from /etc/hosts:

```

::1 ip6-localhost ip6-loopback

```

It's not clear to me if that's meant to be an additional step or an alternate workaround. Making that change (with no change in /etc/sysctl.conf) did not speed up the updates.

To reiterate, I'm reluctant to monkey around with /etc/sysctl.conf without some convincing argument that the change doesn't make my network and home computers more vulnerable to nefarious activities. (I've been on a big security kick lately.)

Maybe a moderator could move this thread to either the Networking & Wireless or Security sub-forum. Or maybe someone could explain what's going on here.

As another commentator to the article noted, "Wiping out IPV6 is a pretty big swing at the problem." (BTW, the solution offered in their comment didn't work for me.)

---

### Post by parminides on 2017-01-20
FYI: [http://www.techrepublic.com/article/how-to-fix-the-slow-apt-get-update-issue-on-linux-machines/](http://www.techrepublic.com/article/how-to-fix-the-slow-apt-get-update-issue-on-linux-machines/)

The comments at the end best summarize my attitude, especially,

>  I agree, fix the problem, not the symptom.  I have been running IPv6 on my home network for almost 7 years without problem.  Also, the world is moving to IPv6 faster than many realize.  For example, my ISP provides IPv6 and my cell phone is IPv6 only, relying on 464XLAT for IPv4.  Apple requires new apps on the App Store to support IPv6.  Telling people to disable IPv6 is a stupid step backward.  IPv6 is already here for many people around the world and coming for many, many more. 

Any ideas?

---

### Post by parminides on 2017-01-20
The comments at [http://unix.stackexchange.com/questions/9940/convince-apt-get-not-to-use-ipv6-method](http://unix.stackexchange.com/questions/9940/convince-apt-get-not-to-use-ipv6-method) show ways to tailor preferences for particular repositories. That's better than disabling IPv6 completely, but it's mostly gobblety-gook to me.

I'm satisifed with one workaround that disables IPv6 for apt-get commands only, e.g.,

```
sudo apt-get -o Acquire::ForceIPv4=true update
```

I can live with that, as it doesn't disable IPv6 completely. I'm marking this thread as solved.

(I knew it wasn't the mirror!)

---

### Post by parminides on 2017-01-20
I discovered a couple of things that might help someone else:

An online test for IPv6 capability: [http://test-ipv6.com/](http://test-ipv6.com/)
Software that aims to fix problem: [https://www.remlab.net/miredo/](https://www.remlab.net/miredo/)

I've attached an image of the results of the test. As you can see, my home connection is very IPv6 challenged. 

I could not get the program (miredo) to work, but I'm happy with the workaround applied to apt-get only.

From what I've read, the crux of the problem might be an old router from my ISP.

---

### Post by trshyd on 2017-06-20
> **parminides said:**
> 
An online test for IPv6 capability: [http://test-ipv6.com/](http://test-ipv6.com/)
Software that aims to fix problem: [https://www.remlab.net/miredo/](https://www.remlab.net/miredo/)


Thanks for sharing the test-ipv6 site. Informative.

I agree with parminides that globally disabling ipv6 for all uses is overkill for this solution.

I have not solved this problem concerning ipv6 and apt, but I can provide yet another workaround, temporary fix:


Use "Network Connections" and "edit" your connection (whether wired or WiFi), and under Ipv6 Settings select "ignore"



There are also options in your router concerning ipv6 that probably will solve the problem as well, but we all have different routers.

Something changed in a recent update to cause this APT ipv6 problem. I only started experiencing this about a week ago or so, I'd have to go back in the logs to see which update did it.
It did not occur with the 17.04 update, but with a package that was updated much more recently.

---

### Post by stconeten on 2017-09-03
I may be late (because I just got back onto linux) but this thread has an awesome configuration: [https://unix.stackexchange.com/a/100887](https://unix.stackexchange.com/a/100887)

---

### Post by willem-tee on 2017-09-28
That made the trick in a freshly installed 16.04.3 amd64 - Desktop

Cheers



> **parminides said:**
> I got home, changed the mirror to [http://www.gtlib.gatech.edu/pub/ubuntu](http://www.gtlib.gatech.edu/pub/ubuntu), and updates were still extremely slow!

Based on [https://www.bearfruit.org/2013/05/06/ubuntu-server-having-ipv6-probs-its-easy-to-disable](https://www.bearfruit.org/2013/05/06/ubuntu-server-having-ipv6-probs-its-easy-to-disable), it appears that there is a conflict or miscommunication involving IPv6 and my server/router at home. (Why it doesn't affect the virtual machines I'll leave as a reader exercise.)

The solution proposed in the body of the article was to add the following 3 lines to /etc/sysctl.conf:

```

net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

Then run "sudo sysctl -p".

I'm reluctant to mess around with a file that claims to have settings that "can improve the network security of the host and prevent against some network attacks including spoofing attacks and man in the middle attacks through redirection." However, as a test, I verified that the workaround does restore my update speed. After I confirmed that it works, I removed those 3 lines until further explanation or clarification.

In the comment section of the article, someone suggested to comment out the following line (and any subsequent lines) from /etc/hosts:

```

::1 ip6-localhost ip6-loopback

```

It's not clear to me if that's meant to be an additional step or an alternate workaround. Making that change (with no change in /etc/sysctl.conf) did not speed up the updates.

To reiterate, I'm reluctant to monkey around with /etc/sysctl.conf without some convincing argument that the change doesn't make my network and home computers more vulnerable to nefarious activities. (I've been on a big security kick lately.)

Maybe a moderator could move this thread to either the Networking & Wireless or Security sub-forum. Or maybe someone could explain what's going on here.

As another commentator to the article noted, "Wiping out IPV6 is a pretty big swing at the problem." (BTW, the solution offered in their comment didn't work for me.)

---

