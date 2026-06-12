---
title: "Internet craps out alllll the time."
date: 2005-06-06
forum: General Help
---

### Post by MicroChris on 2005-06-06
Hey everyone,

Ever since I started using Ubuntu (Warty, Hoary, and Breezy), my Internet would crap out a lot. It seemed to happen whenever I went idle and then came back. I would temporariliy fix it by reseting my router, but I would eventually have to restart.

If its any help, Im running an nForce 2 onboard NIC, with a ZyXEL 645 Series DSL Modem and Linksys Wireless (B) Router (I "host" the wireless connection from my box)

Thanks everyone.

-Chris

---

### Post by xao on 2005-06-07
[QUOTE=MicroChris]Hey everyone,

Ever since I started using Ubuntu (Warty, Hoary, and Breezy), my Internet would crap out a lot. It seemed to happen whenever I went idle and then came back. I would temporariliy fix it by reseting my router, but I would eventually have to restart.

If its any help, Im running an nForce 2 onboard NIC, with a ZyXEL 645 Series DSL Modem and Linksys Wireless (B) Router (I "host" the wireless connection from my box)

Thanks everyone.

-Chris[/QUOTE]





Is it possible that there is some kind of power management enabled for the onboard NIC that shuts it down after inactivity?

Also, are you by chance running Limewire? Cause I had similar symptoms jsut by running that....



xao

---

### Post by adwait on 2005-06-07
maybe u have enabled connect on demand for the connection...

---

### Post by MicroChris on 2005-06-07
[QUOTE=xao]Is it possible that there is some kind of power management enabled for the onboard NIC that shuts it down after inactivity?

Also, are you by chance running Limewire? Cause I had similar symptoms jsut by running that....



xao[/QUOTE]

No, I don't believe theres any power on/off while idle option. And nope, no Limewire.

> maybe u have enabled connect on demand for the connection... 

Hmm how do I check that? Heh. Thanks guys.


-Chris

---

### Post by Curlydave on 2005-06-07
> My internet craps out allllll the time.

Heh, I so know what you're talking about, and it gets on my nerves and pisses me off. In my case however it's not Ubuntu's fault. Sorry I can't help, but you're not alone in the world of intermittant internet! :)

---

### Post by xao on 2005-06-07
if i read your original post correctly, you are dual booting. do you have the same problem with windows?

---

### Post by MicroChris on 2005-06-07
No, everythings cool with Windows (dont quote me on that please, heh).

---

### Post by adwait on 2005-06-07
[QUOTE=MicroChris]No, I don't believe theres any power on/off while idle option. And nope, no Limewire.

 

Hmm how do I check that? Heh. Thanks guys.


-Chris[/QUOTE]
 Is it a DSL connection? If it is, look at /etc/ppp/peers/dsl-provider. If the word "persist" doesnt appear in it, try adding it on a new line. This is could be problem only if you have set up the connection to ask your password when logging on, and haven't stored your password. If not, it shouldn't be a problem but in case of some ISPs, connection on demand doesn't work too well so you could try turning it off.

---

### Post by MicroChris on 2005-06-08
"persist" is there. Heres the whole file:

```
# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "********@earthlink.net"
``` 

Thanks for the continued help.

---

### Post by xao on 2005-06-08
are you losing the connection entirely, or is the problem with DNS, etc. i seem to remember a similar problem i encountered some time ago, and i think that it wasn't resolving (its been a while). 

do you think the issue is with rp-pppoe, the modem, or your drivers?

btw, ive worked as a net tech for a long time, and this kind of problem is the hardest to take care of. but hang in there, we'll get it...

---

### Post by Joeb on 2005-06-08
[QUOTE=MicroChris]No, I don't believe theres any power on/off while idle option. And nope, no Limewire.

 

Hmm how do I check that? Heh. Thanks guys.


-Chris[/QUOTE]


The power on/off while idle option, would actually be in your CMOS settings of the computer.  Your computer  may be dropping into a powersaving mode and thus shutting down the NIC.  In Windows, you can turn that off in the control panel.  In linux, you do it when the kernel loads. 

If you suspect that it is the automatic power management, you could add the kernel parameter apm=off  to /boot/grub/menu.lst for the kernel you are booting (you might also want to add pci=noacpi, too and see if that helps).

---

### Post by void_false on 2005-06-08
You are not alone mate.  ;-) 
I think this problem is digged deep-deep in linux.  ;-)

---

### Post by MicroChris on 2005-06-08
[QUOTE=xao]are you losing the connection entirely, or is the problem with DNS, etc. i seem to remember a similar problem i encountered some time ago, and i think that it wasn't resolving (its been a while). 

do you think the issue is with rp-pppoe, the modem, or your drivers?

btw, ive worked as a net tech for a long time, and this kind of problem is the hardest to take care of. but hang in there, we'll get it...[/QUOTE]

Yes, I'm pretty much losing the connection entirely. Sometimes, it'll happen when I go and watch TV for 20-30 mins, and I come back and its off. 

Surprisingly, my NIC/Audio drivers (nForce2) were built right into the Ubuntu kernel, or atleast it seems so, because NIC and audio do work.

It could be rp-pppoe, I'll look into that, as well as my modem. 

I'll also check CMOS to see if the option wasn't disabled.

Thank you all very much,
Chris

---

### Post by Joeb on 2005-06-08
I'm assuming you are using Sprint DSL, since you show an earthlink address and the dsl modem you have is also the one used by Sprint (at least here).

I, too, had a similar problem with Sprint DSL and that modem, it was acting just like you described.  As it turned out, although I thought it was a DSL problem, it really was apm=on in the kernel.  When I changed that to apm=off and the other setting I posted, the problem went away.

I never really was able to determine whether it was a modem problem or networking problem, but as it was resolved, I didn't care.  (I'm still thinking the computer, not Ubuntu, was turning off the nic and it wasn't detecting the network signal to wake back up).

---

### Post by MicroChris on 2005-06-08
Yes, I do have Sprint, and thats good to here that someone had the sme problem and fixed it.. how do I turn apm off?

EDIT: Nevermind, I think I found out how to do it. I hope this is correct.

```
title		Ubuntu - 2.6.10-5-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda1 ro quiet splash apm=off
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot
``` 

Thanks again everyone for the help. I'll let you all know how this works out.

-Chris

---

### Post by Joeb on 2005-06-08
[QUOTE=MicroChris]Yes, I do have Sprint, and thats good to here that someone had the sme problem and fixed it.. how do I turn apm off?[/QUOTE]


You need to edit the /boot/grub/menu.lst file (as root or sudo) and add the text "apm=off" (without quotes) to the line with the kernel you are booting from.  You might also want to add "pci=noacpi" (again, without quotes), too.  I think I had to add both.

After adding them, you will need to reboot so the kernel is loaded with the new parameters.

---

### Post by MicroChris on 2005-06-08
Thanks for the help, Joeb.

I'm going to go idle now and see if it worked.. I'll report back.

Thanks a bunch again!
Chris

---

### Post by MicroChris on 2005-06-09
Seems to be working! Thanks again Joeb!

-Chris

---

