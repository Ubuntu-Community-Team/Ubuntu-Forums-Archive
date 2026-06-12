---
title: "Deleted /etc/init.d folder..."
date: 2007-01-06
forum: General Help
---

### Post by Sha-baz on 2007-01-06
Hi...
 
Let's say "someone I know" accidentily deleted his /etc/init.d folder. Yes, entirely...
After this, Ubuntu fails to start (gee, really) and I, uhm, he is wondering how to get this folder back in place somehow.
Is there any way to do so?

---

### Post by Ramses de Norre on 2007-01-06
Search someone you know with the same version of ubuntu and try to copy his whole init.d directory over.
If that doesn't work: backup and reinstall.

I'm afraid things like this are kind of the best way to totally ruin a system, so you're pretty lucky when you get it running again.

(And how can someone accidentally remove such a directory??)

---

### Post by Sha-baz on 2007-01-06
Well, at least I found one of the best ways to ruin a system all on my own, right?
 
I had to manually remove some items from the directory using a shell. Somewhere halfway I accidentily hit the enter button while I was typing: bingo... there it went. Isn't the entire folder available from the CD?

---

### Post by taurus on 2007-01-06
I haven't tried it since never need to but what if you boot from the LiveCD, mount your harddrive where / is located, and copy /etc/init.d/* from the LiveCD to your harddrive...  

p.s.  Maybe someone NEEDS to be a little more careful with the sudo command!

---

### Post by Sha-baz on 2007-01-06
*Maybe someone NEEDS to be a little more careful with the sudo command!*
 
Gee, really? :D

---

### Post by fredster001 on 2007-01-06
just out of interest. If he copies this file from a friend, saves it to a USB, how can you then copy it to your own pc, if it wont start?

---

### Post by Ramses de Norre on 2007-01-06
Live cd ;)

---

### Post by koenn on 2007-01-06
> **taurus said:**
> Imount your harddrive where / is located, !
don't really understand this part, but, assuming the harddrive in question is mounted as /media/hda1, you'd copy from  /etc/init.d to /media/hda1/etc/init.d

---

### Post by Ramses de Norre on 2007-01-06
Indeed, make sure the files have the right permissions! (and not some kind of live user as owner)

---

### Post by Sha-baz on 2007-01-06
Great tip, thanks. The LiveCD doesn't mount on my machine however. I don't really know why, but that's the reason I'm using a Knoppix CD right now. I guess I just need to grab hold of a zipped '/etc/init.d' folder for Ubuntu 6.10 then...

---

### Post by Ramses de Norre on 2007-01-06
What do you mean "it doesn't mount"? The cd wont boot or you can't mount your harddisk?
For the first: check your bios settings;
for the latter: ```
sudo mkdir /media/hda1
sudo mount -t ext3 -o rw /dev/hda1 /media/hda1
```

---

### Post by Sha-baz on 2007-01-08
Wrong choice of words, I mean the Ubuntu LiveCD doesn't work. Many LiveCD's and installers don't work on my machine because no kernel up to 2.6.18 supports my Pioneer DVR-K15 CD/DVD burner. It's a bug that has been fixed since kernel 2.6.19. That's why I replaced all my repositories for the Feisty ones and upgraded my kernel. I'm glad to inform anyone who may read this, that this actually works.

---

### Post by Sha-baz on 2007-01-08
Oh, and I found a friend willing to boot an Ubuntu LiveCD and e-mail me the entire content of the /etc/init.d folder. So this problem has been solved too. Thanks for the support.

---

### Post by greatshape on 2007-01-08
> **Sha-baz said:**
> Oh, and I found a friend willing to boot an Ubuntu LiveCD and e-mail me the entire content of the /etc/init.d folder. So this problem has been solved too. Thanks for the support.

Did it actually fix everything just by restoring that folder and setting the right permissions? 
Just curious...

Steve

---

### Post by Sha-baz on 2007-01-08
Permissions? No, I just extracted his zipped '/etc/init.d' folder to my 'etc/init.d' folder and it worked like a charm.
How relaxed is that?
 
Not that everyone should now be less careful with the sudo command ofcourse :mrgreen:

---

