---
title: "Make ubuntu take control of grub"
date: 2007-11-01
forum: General Help
---

### Post by Matticus on 2007-11-01
I installed ubuntu on my harddrive, then afterwards formatted the old windows partition into 2, one for storage and one for another linux.
I install kubuntu today, but obviously its taken over my grub loader, its set it up correctly, with ubuntu under other operating systems, and kubuntu as the default.

But I want Ubuntu to be default. Not only that I want to use ubuntu to deal with my "grubbings".

So how do I make so it ubuntu is in charge.

My disk layout is

hda1 = storage
hda2= Kubuntu
hda3=Ubuntu
hda4=swap (for both kubuntu and ubuntu)

---

### Post by chunderbunny on 2007-11-01
To make Ubuntu the default edit /boot/grub/menu.lst and change the line that says "default 0" to "default 1" (or vice-versa). You can do this from within Kubuntu or Ubuntu, it really doesn't matter.

---

### Post by Matticus on 2007-11-01
Yeah I have done that already, thanks though.

The reason I want to make ubuntu default, is that I use ubuntu much more than I will be using kubuntu.
I want to be able to mess up kubuntu beyound recovery while im still getting used to it and learning kde better, and still have ubuntu nicely set up.

Also this is for future reference, as if I install other linux's I want ubuntu to be able to take over grub control.

This may be a retarded unknowledgable notion, but I dont care :mrgreen: I just want to learn new stuff.

EDIT: and I cant actually edit it from ubuntu, no matter what i change on ubuntu it has no effect, because its reading from what kubuntu is writing to the mbr

---

### Post by meierfra on 2007-11-01
This will put the ubuntu menu.lst  in action:

sudo grub

and then  at the grub prompt:

root (hd0,2)

setup (hd0)

quit

---

### Post by Matticus on 2007-11-02
Thats exactly what I was after, thanks a bunch.

---

### Post by Matticus on 2007-11-02
Ok I got back into ubuntu and tried that, but I keep getting

Error 23: Error while parsing number

Any ideas?

---

### Post by louieb on 2007-11-02
more info please. which statement gives the error.

---

### Post by meierfra on 2007-11-02
Are you getting the error  after rebooting or  while executing the command?

---

### Post by Matticus on 2007-11-02
oh yeah sorry it was 

well I have it sorted, it was my fault for spelling it wrong. it did look like this

sudo grub

grub> root (hda0,2)

Error 23: Error while parsing number

grub> setup (hda0)

Error 23: Error while parsing number


but I realised I was typing hdA but it was just hd

but now I have this

grub> setup (hd0)

Error 12: Invalid device requested

---

### Post by meierfra on 2007-11-02
it needs to be  (hd0,2) and not (hda0,2); and as you already realized: (hd0) not (hda0).

---

### Post by louieb on 2007-11-02
Please post your partition table. ```
sudo fdisk -l
``` lowercase L   

And post your **/boot/grub/device.map** file.

---

### Post by Matticus on 2007-11-02
Well thanks for the help guys but my strong desire to work things out, my lack of knowledge, and lack of fear of mucking things up, as caused me to royally stuff it up.

So to cut a long story short after I couldnt get grub to work, I tried lilo, and that didnt seem to install proper, and grub was still loading from the kubuntu, but it wouldnt boot, then it wouldnt even load grub after I tried to fix it.

So I have formatted, changed my annoying partition layout and reinstalled ubuntu fresh, I think it had got to the point that mucked about so much needlessly to get to know things that everything was going wrong. So Ive had my fun, now I will get on with some real linuxing :mrgreen:

Dunno whether to mark this as solved or not though, maybe I will leave it open for others with similar issues to hijack.

Cheers again for the help guys.

---

