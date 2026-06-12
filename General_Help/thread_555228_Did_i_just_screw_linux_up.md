---
title: "Did i just screw linux up?"
date: 2007-09-19
forum: General Help
---

### Post by tribeca26 on 2007-09-19
ok, call me dumb, I started messing with my feisty 7.04 load after I had it perfect. :(
So here's the problem, I attempted to try and make it look fancy by installing a different splash screen. this splash screen required editing of the boot/grub/menu.lst (yes i know... :[ ) So i ended up eventually typing :
cd
cd Desktop
sudo cp usplash-theme-fingerprint.so /usr/lib/usplash
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
sudo update-alternatives --config usplash-artwork.so

and restarted my computer(as the instructions said so.)
so now when i try to boot i get :
Lots of gibberish then
[19.522043] Ramdisl: Ran out of compressed data
[19.522043] invalid compressed format [evr-1]
[19.522043] Kernel Panic-not synching:vfs:unable to mount root fs on unknow blobk (0,0)
[19.522043] 

My computer keyboard flashes and locks up and i cant do anything. I also tried "safe mode" to no avail.

So, is there any way i can return or "reset" my grub or am I out of luck? I had some important data on the linux partition, so as a last resort is there a program i can use to retrieve that data from win xp?
Thank you SO much in advance. I'm really sad, I have to go back to using windows for a bit :(

---

### Post by aidanr on 2007-09-19
You can use [www.fs-driver.org](www.fs-driver.org) to access your linux partition(s) from windows.

Or afaik you could boot the live cd, mount your ubuntu partiton, chroot to that partition and change the usplash back to the default from there.

---

### Post by tribeca26 on 2007-09-19
Alright i got onto my partition and grabbed the files i needed using fs-driver.
I will try your suggestion for the live cd and usplash edt. I appreciate your help!
If anyone else has any other idea to do it, it would also be welcome.

---

### Post by yabbadabbadont on 2007-09-19
At the boot prompt, press escape so that you get the grub menu.  Hilight your normal boot option.  Press "e" to edit the option.  Edit the kernel line and remove the word "splash".  Press "b" to boot the modified entry.  That should disable usplash for that one boot and get you into your system.

---

### Post by tribeca26 on 2007-09-19
thanks! knew there would be an easy way!

---

### Post by Vadi on 2007-09-25
Well, I didn't mess up *that* badly, but I did kill my usplash trying to get the same theme working (I just get a blank screen until ubuntu loads).

Whoops...

---

