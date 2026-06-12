---
title: "Removing Vista from dual boot"
date: 2008-05-06
forum: General Help
---

### Post by icedogchi on 2008-05-06
I bought a PC that came preloaded with Vista.

I used Vista to shrink the C: partition and make space for Ubuntu.

Installed Ubuntu fine.

Now, I've kicked the tires on both OS's and I've decided to keep Ubuntu 8.04 and remove Vista.

What is the best way to go about this?  I've read that Vista does not like to be removed and will leave your computer un-bootable.  Is this true?  Can't I just use GParted to wipe Vista off and Grub will still load and allow me into Ubuntu?

---

### Post by RATM_Owns on 2008-05-06
I'd say you should boot into the Live CD, use the GParted in there, wipe the Windows partition and grow the Ubuntu partition to fill the space.

At least that's what I did.

---

### Post by herteljt on 2008-05-06
I agree.  Use the live cd.  

Have you setup a separate partition for you /home directory?  It makes for an easy reinstall.  I did this the last time I "reworked" my pc and I've found it to be quite useful.

Here is a link with discussion:  [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by lfaraone on 2008-05-06
Windows Vista won't fight you to remove it, you just can't do it from within its interface (with good reason, actually)

You don't even need to burn a CD now. Get [UNetbootin]("http://unetbootin.sourceforge.net/") , run it as root, and select "Parted Magic" as your distro. []("http://unetbootin.sourceforge.net/")

---

### Post by icedogchi on 2008-05-26
Sorry for the late response.  GParted worked great off of the LiveCD.  Vista free and doing fine.

---

