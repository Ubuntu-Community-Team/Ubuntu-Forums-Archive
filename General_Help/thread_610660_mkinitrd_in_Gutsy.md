---
title: "mkinitrd in Gutsy?"
date: 2007-11-12
forum: General Help
---

### Post by Erik-NA on 2007-11-12
I am trying to get Rocketraid 2320 controller working in Gutsy, and when running make install the follow error ocurrs in gutsy:

Can not find command 'mkinitrd'.

What can I do? It seems that mkinitrd has been removed in Gutsy?

---

### Post by justin_guerin on 2007-11-12
mkinitrd was part of the package initrd-tools, which has been removed from Gutsy in favor of initramfs-tools, which contains the command mkinitramfs.  If initramfs-tools is installed, you can change the script to call mkinitramfs instead, and that should work.

Justin

---

### Post by Erik-NA on 2007-11-12
Thanks for the reply.

I searched for mkinitrd in the install script in the rocket raid driver source package: osm/linux/install.sh

On row 56 I changed:
[PHP]which mkinitrd 1> /dev/null 2> /dev/null[/PHP]
To:
[PHP]which update-initramfs 1> /dev/null 2> /dev/null[/PHP]
And for the debian system on line 142
[PHP]mkinitrd -o /boot/initrd.img-${MODVER} ${MODVER}
[/PHP]
I changed it to:
[PHP]update-initramfs -u -k ${MODVER}[/PHP]

Doing a make install according to the readme.txt now works!!

---

### Post by fjgaude on 2007-11-12
Wow, good for you... can you measure how fast your array is using hdparm -tT /dev/<array>?

I've been thinking of buying Highpoint 2310 but now with the fast controllers on motherboards will likely go for a new MB.

---

### Post by raffytaffy on 2008-01-05
So lets say I compile kernel, install the deb and want to build the initrd, instead of doing 
```
sudo mkinitrd -o 2.6.23 2.6.23
```
I now have to do 
```
sudo update-initramfs -k -u 2.6.23
```
Is this correct?

---

### Post by budtske on 2008-02-25
Appoligies to bump an old thread, 

changing the lines Erik-NA mentioned worked like a charm to get my 2320 controller working on ubuntu 7.10.

would still be looking for the initrd tools if it wasent for this post, thanks :)

---

### Post by pgjensen on 2008-06-02
helped.  thanks.  i did this on the 2220 card.  i also have a 2320 but the latest drives for that i don't think had an issue as i got it to work a few months back w/o this thread.

---

### Post by okeefferd on 2008-07-17
I saw somewhere else that in order to 'fix' the problem with the driver needing help after every kernel update, we should use checkinstall instead of make install.  That way we can uninstall the driver and reinstall with the new kernels.  What do you think?  I havent really gotten that part to work.

---

