---
title: "ndiswrapper problems"
date: 2005-10-15
forum: General Help
---

### Post by bottledwater on 2005-10-15
I'm having difficulties getting my wireless internet access setup. I can get it to work perfectly fine in Hoary, so it's a problem in Breezy.

When I type:

```
sudo modprobe ndiswrapper
```

I get the following error message:

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
```

I need to modprobe it so I can see the wireless card in the networking dialog.

Any help would be great, thanks! :o

---

### Post by bottledwater on 2005-10-15
any help?

---

### Post by majikstreet on 2005-10-15
Mmm... Are you 100% sure you are doing "sudo modprobe ndiswrapper"?

Try re-installing ndiswrapper. (I'm really not sure how you are installing it. At least in a hoary cd it's in pool/main/n/ndiswrapper-utilsXXXXXX.deb probably in a similar form on a Breezy CD. I may have gotten pool and main mixed up though. I don't have a breezy cd on hand...


majikstreet

---

### Post by bottledwater on 2005-10-15
I'm installing ndiswrapper using synaptic (ndiswrapper-utils). In hoary I installed my card by the following:

sudo ndiswrapper -i /path/to/inf
sudo modprobe ndiswrapper
sudo ndiswrapper -m

It's only the 2nd command that doesn't work

---

### Post by bottledwater on 2005-10-15
I really need to get this working :(

---

### Post by lithorus on 2005-10-15
What does dmesg say? Btw. why are you using the generic 386 kernel? Under all circumstances I would suggest using one of the more specific kernels like k7(for athlon and above) and 686(for P4 and the likes)

---

### Post by bottledwater on 2005-10-15
what's the dmesg command and i'll give it a try

---

### Post by Eleka on 2005-10-15
Have you installed the packge frm apt-get or have you downloaded and compiled it?

I recommend you the second option, in Ubuntulinux.org you can find a very well wiki that helps me a lot, and I have running ndiswrapper in my laptop's breezy :).

The process I follow, very very resumed, was apt-get various packages necessaries tu compile, upgrade kernel, download the latest stable release of ndiswrapper, compile it with deb flag, to obtain 2 deb packages, and installed it with dpkg ... but, for more details, see the wiki of ubuntulinux.org

Good luck!

---

### Post by az on 2005-10-15
[QUOTE=bottledwater]I'm having difficulties getting my wireless internet access setup. I can get it to work perfectly fine in Hoary, so it's a problem in Breezy.

When I type:

```
sudo modprobe ndiswrapper
```

I get the following error message:

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
```

I need to modprobe it so I can see the wireless card in the networking dialog.

Any help would be great, thanks! :o[/QUOTE]

You can get that error if you have the wrong .inf file installed.

---

### Post by lithorus on 2005-10-15
[QUOTE=bottledwater]what's the dmesg command and i'll give it a try[/QUOTE]
Well, it's 'dmesg' :)

Have you tried using the System -> Administration > Windows Wireless Drivers? It's a part of the ndisgtk package which is new for Breezy AFAIK.

---

### Post by Zachs23 on 2005-10-15
I had the same problem, and I just got lazy, backed up my files, and wiped the hd and installed breezy fresh from the cd. Then I synaptic-ed ndiswrapper-utils (ndiswrapper itself is included in the kernel), and it worked as intended. This probably isnt the answer you are looking for, but that is what worked for me.

---

### Post by müller on 2005-11-29
I had the same problem; error at modprobe. I checked out the messages at making the .deb file and there were the real errors: mising gcc 3.4

I solved it by installing the gcc 3.4 package

---

### Post by Jay-Kill on 2005-12-04
Hey Guys
I'm sorry but I'm a newbie with Ubuntu. I can't compile the ndiswrapper (and I think it is because I don't have an Internet Connection to load some required modules via apt-get). Could you please load me the 2 required *.deb files up?
I'm using Ubuntu 5.10 (since 12 hours). 

Thx a lot for answers. Sorry for my small Linux Knowledge if I did a mistake but I've just been converted from Win**** to Linux. :) 


Greets Jay-Kill :rolleyes:

---

