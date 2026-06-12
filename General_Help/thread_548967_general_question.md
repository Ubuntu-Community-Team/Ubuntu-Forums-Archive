---
title: "general question"
date: 2007-09-11
forum: General Help
---

### Post by puner on 2007-09-11
I heard the hard drive access is a little slow, and i dont blame that since it's in beta right now.

For me i want to access the music and video's that i have on my WinXp drive and play them on ubuntu after i install it with Wubi. How will that feel slow or normal?

Also when i download date of the internet, where does it save it to ?

---

### Post by tuxcantfly on 2007-09-12
> **puner said:**
> I heard the hard drive access is a little slow, and i dont blame that since it's in beta right now.

For me i want to access the music and video's that i have on my WinXp drive and play them on ubuntu after i install it with Wubi. How will that feel slow or normal?

Also when i download date of the internet, where does it save it to ?

The disk performance when accessing the Windows partition will be just as fast as normal, since that's an actual partition, not a loopmounted one. It'll be fine for watching movies and listening to music, the only task a native install would be noticeably better for would be manipulating large files, like in movie editing. Probably, the reason that some were reporting extremely slow drive access speeds were some hardware incompatibilities; chances are, unless you're using some complex raid array or some other complex drive arrangement, the performance loss won't be noticeable.

---

### Post by puner on 2007-09-12
Also, if i were to download stuff where would ubuntu save the date to? the Ubuntu partition or Windows partition? 

How big of a partition does Wubi make?

---

### Post by ago on 2007-09-12
Files created/downloaded from within Wubi are saved in the Wubi "partition", but the Wubi "partition" is just a file within the Windows partition. So we call it a virtual drive. You can choose the size of the virtual drive when you install.

---

### Post by puner on 2007-09-12
Okay, and one last question.

Are the files downloaded on Wubi virtual drive, accessible from Windows?

---

### Post by ago on 2007-09-12
> **puner said:**
> Okay, and one last question.

Are the files downloaded on Wubi virtual drive, accessible from Windows?

If you place them in the "shared" folder or in a mounted windows partition, yes

---

### Post by reckless2k2 on 2007-09-12
here's a general wubi answer......

don't use it.

---

### Post by tuxcantfly on 2007-09-12
> **puner said:**
> Also, if i were to download stuff where would ubuntu save the date to? the Ubuntu partition or Windows partition? 

How big of a partition does Wubi make?

By default, it saves to the Wubi disk image, but you can change the default save location to /media/host in the firefox preferences, which would make it download to C:\ on your Windows drive.

---

