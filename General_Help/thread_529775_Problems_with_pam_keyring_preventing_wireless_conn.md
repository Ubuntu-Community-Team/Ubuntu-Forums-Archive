---
title: "Problems with pam keyring preventing wireless connection"
date: 2007-08-19
forum: General Help
---

### Post by Majorix on 2007-08-19
I am - or was using Gutsy.

Now the problem is, after I install pam keyring, edit /etc/pam.d/gdm (I may be wrong about the file location because I am not on an Ubuntu box right now) and restart the computer; all I get would be repeated questions after my keyring password. I tried this numerous times, with two different installations but nothing worked.

It worked quite fine with my Feisty installation, for your information.

I had to fall back to Windows but after months of its absence I can't quite feel home. Please help me.

If this must be moved to Gutsy development forums, then may a kind mod please do so. I read "ANY" Ubuntu release at the top of this category, thats why I posted here.

Any help is greatly appreciated.

---

### Post by Majorix on 2007-08-20
*Bump*

---

### Post by Majorix on 2007-08-21
Please someone help. I am back to Gutsy btw, got rid of Windows again. Man I am too much addicted to Ubuntu :D

Please help me I have to enter this damn pass before it would connect me to the net after every boot :(

---

### Post by Majorix on 2007-08-25
Now it is even more weird.

In order to connect to the wireless, after every boot I have to:
1. Enter the key for the wireless.
2. Enter keyring password when it asks.
3. Confirm the keyring pass for a second time like I was doing it for the first time. It won't register the entries the boot before.

Anyone?

---

### Post by Foaming Draught on 2007-08-28
Sorry no-one's responded sooner, Majorix.   It is a pain, isn't it.  This tip is for Feisty, but I'm using it for Gutsy nae bother.  Just make sure that both passwords (gdm and keyring) are the same.

You can't have automatic log-on to a user (you) on gdm at the same time as using pam-keyring.  The former is less hassle than the latter.

[http://ubuntuforums.org/showpost.php?p=2776815&postcount=1](http://ubuntuforums.org/showpost.php?p=2776815&postcount=1)

---

### Post by Majorix on 2007-08-29
The login pass and the keyring pass are the same by me. But it still doesn't work :(

---

### Post by mike_g on 2008-07-23
Out of curiosity did this problem ever get solved? I'm using Gutsy, I did what it said on the wiki for the pam-keyring here but I'm simply getting double spammed now :(

---

