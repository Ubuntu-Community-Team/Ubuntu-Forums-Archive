---
title: "problems with hardy"
date: 2008-04-28
forum: General Help
---

### Post by harecanada on 2008-04-28
Help!!
I just hit Version upgrade in  adept and figured I would go ahead and upgrade from gutsy to hardy. Now I can get to my konsole but not my desktop. It's like I don't have my nvidia driver. I get to darrell@home:~$ but then don't know what to do. Can someone help me out?
Please e-mail me at [email]dbh@eastlink.ca[/email]
Darrell Hare

---

### Post by anjilslaire on 2008-04-28
at the konsole, try

```

sudo -dpkg-reconfigure xserver-xorg

```

This should let you configure xorg to get your GUI back up at a minimum.

---

### Post by harecanada on 2008-05-01
> **anjilslaire said:**
> at the konsole, try

```

sudo -dpkg-reconfigure xserver-xorg

```

This should let you configure xorg to get your GUI back up at a minimum.
Hi. Thanks for the help but it wasn't the x server. I put in the followingline
sudo aptitude install kubuntu-desktop
and after about 45mins I got the black screen and prompt again then I rebooted and got Ubuntu Hardy. Works great but I wanted Kubuntu. I'm trying to figure that out now and get back to Kubuntu. Do you know how to go from Ubuntu to Kubuntu?
harecanada

---

