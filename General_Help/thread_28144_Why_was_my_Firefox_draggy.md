---
title: "Why was my Firefox draggy?"
date: 2005-04-19
forum: General Help
---

### Post by rykel on 2005-04-19
Hi all,

I had a very slow and draggy Firefox.

I tried solving the problem by reinstalling the program, installing the latest nightly build from mozilla.org, installing the firefox autopackage and even used mozilla suite, epiphany and opera when the drag was unbearable.

However, today I found that the REAL reason was simply that my nVidia-glx was NOT running at the optimum 1000+ fps. (run "glxgears" in a terminal to see ur own speed)

When I installed the official nvidia driver and ran "nvidia-glx-config enable", my card started churning out those frames and Firefox became responsive immediately.

In fact, everything else, including the desktop, started moving much faster.

So, that was my experience... that a draggy Firefox might not actually be a bug, but like mine, was just a problem with the graphics card.


Best Regards,

Rykel
Singapore

P/S. Interestingly, the latest Mozilla 1.8 is really FAST!! You've got to try it yourself to see what I mean.     O:)

---

### Post by noelferg on 2005-04-19
Try typing about:config into the address bar & check the line:

network.dns.disableIPv6

Value needs to be set to "true" (Double-click to change if necessary.)

---

### Post by occy8 on 2005-04-24
> noelferg  	Try typing about:config into the address bar & check the line:

network.dns.disableIPv6

Value needs to be set to "true" (Double-click to change if necessary.) 

I did that and it was still draggy oppening new tabs not loading stuff from the net

I edited my /etc/hosts file and outcommented all of these

# The following lines are desirable for IPv6 capable hosts
#::1     ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

now its allright

---

### Post by crazybill on 2005-04-24
Great post. I have a few Hoary machines where Firefox is incredibly slow. I will give these solutions a try.

---

