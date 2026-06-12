---
title: "How do I use an old app?"
date: 2007-07-08
forum: General Help
---

### Post by oomingmak on 2007-07-08
Is there any way that I can use the old **Disks Manager** applet that used to be in Dapper / 6.06? I really liked it and found it very useful for quickly checking Disk stats and getting an overview of all the connected storage devices. However, there's no such utility included in Ubuntu anymore. I looked in Syanptic, but it's not listed in there either.

So, in a fit of optimism, I copied the file over from 6.06 to my 7.04 install, but needless to say it didn't work.

>  disks-admin: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directoryIs there a way that I can fix this? (step by step please .... I'm a noob).

Thanks.

---

### Post by kerry_s on 2007-07-08
check synaptic, see if you have gnome-system-tools, if you do than it's probably just not listed in your menus, meaning they dumbed it down. try launching the gnome control center, usually everything is listed there. you can use the menu editor to turn hidden options back on.

---

### Post by oomingmak on 2007-07-08
> **kerry_s said:**
> check synaptic, see if you have gnome-system-tools, if you do than it's probably just not listed in your menus, meaning they dumbed it down. try launching the gnome control center, usually everything is listed there. you can use the menu editor to turn hidden options back on.
Thank you for your reply.

I do have gnome-system-tools installed (seeing as it comes as standard) but there is no disks-admin executable anywhere on my system (which is why I had to copy it from a Dapper CD).

Now that I have the disks-admin file on my system, the problem is getting the required libraries in order to run it (as I don't understand how to fix the error quoted above).

---

### Post by kerry_s on 2007-07-08
okay, what you can try is go into /usr/lib and see what version you have and link to it.
i'm using debian so mine is libdbus-1.so.3, so it would look like this.

cd /usr/lib
sudo ln -s libdbus-1.so.3 libdbus-1.so.2

---

