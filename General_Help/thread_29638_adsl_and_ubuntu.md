---
title: "adsl and ubuntu"
date: 2005-04-25
forum: General Help
---

### Post by Hrenojed on 2005-04-25
Hi, I'm not from english speaking country, so I'm sorry for my bad english.

I was wondering, how to make an ADSL connection. I was searching, but I didn't find anything. :(

Thanks...

---

### Post by Knome_fan on 2005-04-25
First off, hi.  :smile: 

Open a root terminal and type pppoeconf.

Have fun!

---

### Post by Hrenojed on 2005-04-25
Hi,

I tried, but it doesn't working! It says, that it's connected, but when I type [www.google.com](www.google.com) in Firefox, it searching some time and it doesn't fint the page!

---

### Post by Knome_fan on 2005-04-25
Hm, sounds like you have a problem with your nameserver.
Did you tell pppoeconf to always get them from your ISP? (If not, try this option)
Or try to set 62.111.62.111 as your nameserver, works for me here.

---

### Post by Hrenojed on 2005-04-25
How can I open something with root?  ;-) 

Does Konqueror exist in Gnome?

 O:)

---

### Post by Turin Turambar on 2005-04-25
[QUOTE=Hrenojed]How can I open something with root?  ;-) 

Does Konqueror exist in Gnome?

 O:)[/QUOTE]

You can open the things as a root with "sudo" command added as a prefix. Konqueror does not exist in Gnome, but in KDE. Gnome has its own - Nautilus.

You can open the file manager as a root with:

gnome-sudo nautilus

---

