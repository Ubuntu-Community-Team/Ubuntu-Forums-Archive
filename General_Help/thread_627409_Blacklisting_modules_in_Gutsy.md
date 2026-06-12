---
title: "Blacklisting modules in Gutsy"
date: 2007-11-30
forum: General Help
---

### Post by mandyfester on 2007-11-30
Hello

I am running into problems trying to blacklist the default ralink modules supplied with Gutsy.

I have added the following modules into the file
/etc/modprobe.d/blacklist

blacklist rt2x00pci
blacklist rt2x00lib

But everytime I restart Gutsy issuing the following command gives me the following result.

sudo lsmod | grep rt2

rt2x00pci 13184 1 rt61pci
rt2x00lib 21760 2 rt61pci,rt2x00pci
rfkill 9616 1 rt2x00lib
mac80211 196104 4 rc80211_simple,rt61pci,rt2x00pci,rt2x00lib
input_polldev 6672 1 rt2x00lib
crc_itu_t 3456 1 rt2x00lib

My question is how can I remove a module from loading with Gutsy on each boot?

Thanks

Andy

---

### Post by schmolch on 2007-12-24
Same here.

Every wiki and whatnot says to do it this way but it does not work and nobody admits or cares that its broken.

---

### Post by fixture on 2007-12-29
same here, tried to blacklist a bunch of modules in /etc/modprobe.d/blacklist, doesn't work

---

### Post by metallicatony on 2008-01-02
As you said, blacklisting of modules is not working in Gutsy. Its broken!
But you can always add the following in /etc/rc.local to achieve the same. Please replace <modulename> with the name of the module which you dont want to load.

#Blacklist or remove the unneeded module
modprobe -r <modulename>

---

### Post by RostokMcSpoons on 2008-01-06
Hi, I've just stumbled across this thread as I've had the same problem.  I'm an utter noob at this, so please forgive me...

I've added the lines...

modprobe -r rt73usb
modprobe -r rt2500usb
modprobe -r rt2x00usb
modprobe -r rt2x00lib

because if I do those from the Terminal I get down to just rt73, and my connection works.

However, it still doesn't seem to happen.   The script itself mentions changing the 'execution bit' ...
after a quick google I've tried this:

cd ../../etc
sudo chmod +x rc.local

but it still doesn't seem to work (I can't even tell if it 'took').  Can you help a noob? ;)

---

### Post by woZa on 2008-02-17
Blacklisting not working here on 7.10 either. Hope this gets fixed soon...

---

