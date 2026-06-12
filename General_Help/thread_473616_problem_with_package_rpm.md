---
title: "problem with package rpm"
date: 2007-06-14
forum: General Help
---

### Post by technomaniac on 2007-06-14
I have a strange problem. I have just installed ubuntu 7.04 and wish to download software from the online repos.I have a DSL connection(BSNL,India) and the linux drivers for the modem are available in the CD accompanying the modem.Now the problem is the linux drivers are in a .rpm file and ubuntu CD has no rpm package.You have to download the rpm package from the net and I cant get online without configuring my modem. Has anyone got a solution?  I am really looking forward to some cool solutions.

---

### Post by 9a3eedi on 2007-06-14
There's alien, which is a program that converts rpm packages to deb packages. 

to install alien, 

```
sudo apt-get install alien
```

But I wouldn't recommend using it to essential stuff like drivers.. 

well.. if it's a fresh install.. try it :P You can always reformat in the worst case scenario.

---

### Post by HereInOz on 2007-06-14
Does the modem connect using Ethernet, or is it just a USB modem?  If it will connect using Ethernet, set it up for that and you should be able to connect via the ethernet port on your computer, as long as you have an ethernet port.

if it is just USB only, then the only other thing I can think of is to set up a temporary dial up connection with a serial dial up modem, install Gnome-PPP as a dialer (it should be on the CD) and then install a program called Alien, (in the repositories).  Alien will allow you to convert the RPM to a DEB file, and then you can install it.

---

### Post by technomaniac on 2007-06-14
the modem connects using ethernet. but how do i configure it without the rpm package. ubuntu is even detecting a network connection through the modem but i dont know how to set up a internet connection without using that package. Is there any way to do it without installing that rpm?

---

### Post by technomaniac on 2007-06-17
Well it seems I have to download GNOME PPP dialer from the net too. Its frustating. Come on.What were the people at ubuntu thinking. I dont know how people in US connect to the net but in most developing countries we still have dialup(DSL etc). So guys I hope you dont repeat  it next time.Trying to bundle everything on a CD you have left important things out.Please use a bit of common sense.I really wanted to shift over to ubuntu but I think I will wait until I check out Ubuntu ultimate. Right now, I am happy with opensuse. And one more thing, while most people in US of A might have very fast internet connections, most and India and other developing countries have to do with less that 56 kbps.Not at all good for downloading software from your repositories. We get our Linux distros from the DVDs accompanying various computer magazines. So please think about us. I am downloading ubuntu ultimate using bittorrent and it would take another 2 days to download at the least. I will give it a try. Hope it fits my bill. If I dont find it sufficient I am not going to recommend it to anybody. Opensuse is still the best for me.

---

### Post by technomaniac on 2007-06-17
Wow...Just great..Now that I have downloaded Roaring Penguin Client, while installing it in ubuntu, it gives an error saying "GCC cant compile" or something similar. Really, I have had enough. What OS have you made? Yeah I can go to a cyber cafe and download all the software I want from your repository. But why should I take so much pain to just get my internet connection working. Any other Linux distro is better. Even Windows is better. Really, [COLOR="Red"]**[SIZE="7"]Ubuntu SUCKS[/SIZE]**[/COLOR]

---

### Post by dineshs on 2007-11-18
Driver is required only if you are connecting via USB.otherwise configure your ethernet card
IP  192.168.1.200 and gateway 192.168.1.1
Now you can access modem via browser typing 192.168.1.1
config ur modem

---

### Post by dineshs on 2007-11-18
Also dont use rp-pppoe but use gpppon

---

### Post by bluknight on 2007-11-18
> **technomaniac said:**
> Wow...Just great..Now that I have downloaded Roaring Penguin Client, while installing it in ubuntu, it gives an error saying "GCC cant compile" or something similar. Really, I have had enough. What OS have you made? Yeah I can go to a cyber cafe and download all the software I want from your repository. But why should I take so much pain to just get my internet connection working. Any other Linux distro is better. Even Windows is better.

technomaniac,

You get free software and of course tried yr best. Linux doesnt deserve this because its not just free but devs also tried their best to make it so.

Maybe Windows will take yr rantings after u've paid for it and they dont deliver.
Nobody owes the 3rd world a living. Help yourself and become 1st world.
Gutsy worked v well for me after some adjustments of my own, even if it did not complete the installation its looking v. good.
Someone may even say to take your rantings elsewhere!

---

### Post by zvacet on 2007-11-18
system>administration>software sources>chek CD rom box>close.Put your Cd in drive and type 

```
sudo aptitude install build-essential
```

After that you will be able to compile.Don´t just give up!it can be frustrating in the begining,but you will see result later.Most of the people on this forum were noobs once,so they know how you feel and they are willing to help you if you want.

---

