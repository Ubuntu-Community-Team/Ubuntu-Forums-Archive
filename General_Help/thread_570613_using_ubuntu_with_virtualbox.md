---
title: "using ubuntu with virtualbox"
date: 2007-10-08
forum: General Help
---

### Post by hilfer on 2007-10-08
Hi all:

I managed to install ubuntu on virtualBox.
Now I need some help:

1-What to do to  hear music inside ubuntu ?? I have to install my sound card ??
2-How can I print any document from inside ubuntu ???
3- can I share documents between ubuntu and windows ???

tks hilfer.

---

### Post by bodhi.zazen on 2007-10-08
> **hilfer said:**
> Hi all:

I managed to install ubuntu on virtualBox.
Now I need some help:

1-What to do to  hear music inside ubuntu ?? I have to install my sound card ??

It depends on what music you are trying to play and is somewhat complicated by VMWaer as vmware provides it's own sound card ...

I am not sure if it helps, but take a look here : 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

> 2-How can I print any document from inside ubuntu ???

You can share a printer with samba

> 3- can I share documents between ubuntu and windows ???

tks hilfer.

Easiest would be samba

[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

You do not need to set up a samba server, just a samba client (on Ubuntu).

With VirtualBox you can share hard drives (partitions) and usb/flash drives as well :

[http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

---

### Post by hilfer on 2007-10-08
Thanks for yr replies.

I downloaded samba, but now...Oh my god I dont know how to make an instalation on UBUNTU !!!

I know this is the ABC... but I've been working with windows....Which is the file to install ???
In windows normally it's an EXE file what's in  UBUNTU the corresponding to an exe file ?????

---

### Post by bodhi.zazen on 2007-10-08
You do not need to install samba, I don't think

I think the samba client is already installed.

Anyways installing software in Ubuntu is different, but easy.

You do not need to directly download anything, use "Add/Remove programs" or synaptic

[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by hilfer on 2007-10-09
Ok I think I managed to install "SAMBA" using the synaptic package manager.

Everytime I try to print a document I get an " error on printing"

Any ideas ??

---

