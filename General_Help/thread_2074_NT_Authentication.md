---
title: "NT Authentication"
date: 2004-10-25
forum: General Help
---

### Post by vizvayu on 2004-10-25
Hi!
Anybody knows if there's any way ("out-of-the-box") to authenticate users using a NT Domain in Ubuntu? 

Or should I configure PAM and winbind manually?
If so, maybe including winbind in the default installation could be a good idea, so I won't need and internet connection to update the packet-list and download the program... any thoughts about this?

Thanks!

---

### Post by jdong on 2004-10-25
Yeah, winbind support seems like a nice feature for Hoary.

---

### Post by water on 2004-10-25
a very simple nt-domain auth is a real kickstart to get people to try out this great distro in a typical nt based lan... it would really make sense to have in ubuntu.
  
  :water

---

### Post by vizvayu on 2004-10-27
Yes, especially when I'm planning to deploy Ubuntu in a domain with 100+ workstations without direct access to the Internet :)
But i'm preparing an additional disk to copy all the extra packets that we need, like winbind, OpenOffice internationalization files, midnight commander, and so on.

Some way to script an unnattended installation would be nice too...

---

### Post by jdong on 2004-10-27
In that case, I'd recommend installing and configuring one ubuntu system, then using **cpio** or **tar** to create an "image" of the system, then unpacking it onto the other systems.

even if the systems are different, hotplug is perfectly capable of autodetecting hardware.

---

### Post by vizvayu on 2004-11-18
[QUOTE=vizvayu]Hi!
Anybody knows if there's any way ("out-of-the-box") to authenticate users using a NT Domain in Ubuntu? 

Or should I configure PAM and winbind manually?
If so, maybe including winbind in the default installation could be a good idea, so I won't need and internet connection to update the packet-list and download the program... any thoughts about this?

Thanks![/QUOTE]
 I've made a HOWTO for this. You can see it in the FAQs and HOWTO forum.

BTW: jdong, it seems hotplug is not enough, when you switch an hdd from un PC to another, most of the time it's necessary to change at least the XF86Config-4 file, because of the video driver.
But I made a deb package with all the configuration files changed, and I'm planning to make a script to install all needed packages at once. It'll be cleaner that way.

---

