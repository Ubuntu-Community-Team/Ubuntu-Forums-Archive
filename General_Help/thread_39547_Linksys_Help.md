---
title: "Linksys Help"
date: 2005-06-05
forum: General Help
---

### Post by pschweiss on 2005-06-05
Hey,
I am trying to install a Linksys WPC11 v2.5

and it is asking me for the  Linux source directory 

and this is the suggestion it gives me for the location,[/usr/src/linux] but that is not  correct for ubuntu anyone know what the actaul locatoin is.

Here is what the readme says about the command.

   - Linux source directory [/usr/src/linux]: 
        The config script will attempt to automagically find your kernel
        source directory.  If found, the kernel source source directory
        will be presented as the default selection.  If the default
        selection is wrong, you may correct it here.

I would appreciate the help,

Thanks in advance,

you can reply in the thread or email me

[email]pschweiss@gmail.com[/email]

thanks,

Peter

---

### Post by K2712 on 2005-06-07
apt-get install build-essential fakeroot linux-headers-$(uname -r)

Then try again.

---

