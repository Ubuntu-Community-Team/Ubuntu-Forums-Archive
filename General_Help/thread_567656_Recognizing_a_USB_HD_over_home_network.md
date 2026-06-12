---
title: "Recognizing a USB HD over home network"
date: 2007-10-04
forum: General Help
---

### Post by friendorfaux.vox.com on 2007-10-04
I have an old Pentium 3 machine running the latest Ubuntu build. I want to use it as a media dump for the rest of my machines (both Macs). Can I plug my 160GB external USB drive into the Ubuntu box and access it from the rest of the network (for example, use it as my iTunes library from my other machines)? 

Thanks for any help.

---

### Post by T700 on 2007-10-04
Absolutely.  How you do so will depend on the operating systems on the other machines.  If they are Windows, Samba is your best bet.  If Linux, you might consider NFS.

Paul

---

### Post by friendorfaux.vox.com on 2007-10-05
Thanks for the response. I little update, though. I just cut out the middle man and installed the drive as a slave inside the box. It was recognized and mounted without a hitch. I have SMB running and my Ubuntu box shows up great on the rest of my machines (a Powerbook and a Macbook). 

I then assigned my slave HD as a shared folder. Here's where I have a problem. While it *does *show up when connecting from another machine, it won't recognize the same password as when I access any of the other shared folders on my Ubuntu machine. Weird. 

Is this a permission issue? Do I need authorize my other machines somehow?

---

