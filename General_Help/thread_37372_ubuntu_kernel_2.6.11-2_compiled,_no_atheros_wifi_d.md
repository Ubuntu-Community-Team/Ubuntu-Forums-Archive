---
title: "ubuntu kernel 2.6.11-2 compiled, no atheros wifi detection?"
date: 2005-05-27
forum: General Help
---

### Post by wbeck85 on 2005-05-27
I do not know where kernel questions go, "Other" seems to be the section that fits best...

Anyway, Today I compiled the 2.6.11 kernel from the repository. I thought I selected everything that I needed, and more so using gconfig! When it came to selecting networking drivers, I selected to compile everyone of the wireless cards as a module, as I did not see any mention of my atheros card (lspci yields "0000:00:05.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)") I did not give it anythought until I booted my laptop (Sager np4750, aka: Clevo d470k) with the new kernel. It seems to work very well, except my wireless card was missing from network-admin and I can no longer use it! When I booted back to hoary with the stock 2.6.10 kernel, the wifi card was back and I'm using it now. I am confused. Anyone else with an atheros card have trouble with the 2.6.11 kernel?
(I tried compiling a vanilla 2.6.11 and ran into the same problem)

---

### Post by wbeck85 on 2005-06-04
Man, I don't like begging for answers
But I am to assume that no one has run into this same problem? Tis a shame. I would like to know what I did wrong. Doesn't it seem bizzare that the 2.6.11 kernel would not support my wifi card, while the 2.6.10 kernel does? I downloaded the madwifi drivers (with wired ethernet, which does work well) and tried to compile it as a kernel module, using the directions on the website, I don't know if I did it properly or not, but regardless, it didn't work :( I should just be able to modprobe the module when I'm done, right?
Do you think that once I've downloaded and compiled the madwifi driver that recompiling my 2.6.11 kernel might just  work?

---

### Post by rhaces on 2005-06-07
I have the same problem.. teorically what you have to do is apply the madwifi drive to the linux-kernel-2.6.11-1-386 when you are compilling linux-kernel... havent done it, and dont know exactlly how to, cause all i do is apt-get install linux-image-2.6.11-1-386..
Cheers hope someone can help us

---

### Post by wbeck85 on 2005-06-10
Hmmmm.... Well, at least I'm not alone, thanks for keeping me company!

---

### Post by naisan on 2005-06-20
same for me - I recompiled the kernel to add thinkpad trackpoint controls using a patch on 2.6.10, then just accepted defaults for the xconfig, hoping that it would keep the same config as the previous 2.6.10. 

I think, from reading the newsgroups (me a newbie 2) that you have to recompile the same kernel in the debian way, and include the modules.

I tried to make and install the madwifi driver just now, and still nothing there, so I will have to try the kernel build tonight when I have some time. Here are some sites I found on this:
[http://madwifiwiki.thewebhost.de/wiki/Ath0OnDebian](http://madwifiwiki.thewebhost.de/wiki/Ath0OnDebian)


this site really looks promising also:
[http://www.marlow.dk/site.php/tech/madwifi](http://www.marlow.dk/site.php/tech/madwifi)

I am going to try it now!

---

### Post by naisan on 2005-06-20
just found this here also - seems that it would also work:

[http://ubuntuforums.org/showthread.php?t=36800](http://ubuntuforums.org/showthread.php?t=36800)

---

### Post by tread on 2005-06-20
Ok, I see you got a few replies, but I'm gonna weigh in anyway :)

The madwifi drivers are needed for atheros wireless, they are not part of the stock kernel. The Ubuntu developers distribute it as part of linux-restricted-modules. If you want to get your card working, you'd need to download the source and compile it against your current kernel source. Luckily, this isn't that bad, there is a good FAQ about madwifi somewhere on the net. I have used this myself to get my atheros working on Mandrake.

Edit: ah .. I'm too slow again. Today isn't my day.

---

