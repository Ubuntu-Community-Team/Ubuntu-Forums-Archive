---
title: "azureus... crash or slow ?"
date: 2007-06-05
forum: General Help
---

### Post by enfantterrible on 2007-06-05
hello all...

i have been trying to download some torrents and

a) when using the standard java, azureus would be very slow (finds roufirewallter problems, even though same settings in win xp and bitlord work fine) and then die

b) after a hint, i downloaded the SUN java and downloads went up very fast, but i experience crashes...

is there a way to have azureus run nice and smooth on ubuntu?

thanks for all the help!

---

### Post by Gausian on 2007-06-06
have you installed java runtime v6 from the repos?  AZ is working fine with jre6 for me.

---

### Post by Azakus on 2007-06-06
Azureus in the ubuntu repos is crash prone. Download it from azureus.sourceforge.net and it will crash less.

---

### Post by Crafty Kisses on 2007-06-06
> **enfantterrible said:**
> hello all...

i have been trying to download some torrents and

a) when using the standard java, azureus would be very slow (finds roufirewallter problems, even though same settings in win xp and bitlord work fine) and then die

b) after a hint, i downloaded the SUN java and downloads went up very fast, but i experience crashes...

is there a way to have azureus run nice and smooth on ubuntu?

thanks for all the help!

You can see if something is eating resources by typing the following in the terminal:
```
top
```
From there you'll see the exact numbers, or you have the option to download Conky.

---

### Post by enfantterrible on 2007-06-06
ok... i will try to download (how to install from compressed file?) the new azureus but... how do i tell him which java to use? so far i have been trying installing/uninstalling the ones i want to use/dont use, but i am sure there's a smarter way!

---

### Post by LaLLi on 2007-06-08
You can have multiple Java versions installed simultaneously. To choose what JRE is used just run this command.
```
sudo update-alternatives --config java
```

You don't need to intall the Azureus you download from the web. Just copy azureus2.jre file from the package over your existing repo installed azureus2.jre. Sry but I don't remember where it is located, but you'll find it.

---

