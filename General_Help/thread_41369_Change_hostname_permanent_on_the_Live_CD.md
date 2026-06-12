---
title: "Change hostname permanent on the Live CD?"
date: 2005-06-13
forum: General Help
---

### Post by kurga on 2005-06-13
Hey is it posible to change the hostname on the Live CD so that when you boot it has another hostname than ubuntu? I'm also looking for the posibility to change the default webpage in firefox. Thanks for the help.

---

### Post by Sionide on 2005-06-13
You can't change much stuff "permanently" on the LiveCD, but that's part of the point. So, I'm not about the first point - under Firefox, goto *Edit -> Prefs -> General* and it's at the top there.

By the way, this isn't the place to ask questions so find the right part of the forum next time.

---

### Post by Orunitia on 2005-06-13
Announcement:
Please do not post questions here. This is for HOWTO's and FAQs only.

 Sticky: ALL READ!!**Do not answer questions here!!!!**
		
Sticky: *read* This Is Not The Place To Ask Questions!


Hard to miss all three of those.  :-|

---

### Post by ubuntu_demon on 2005-06-13
I moved this thread.

welcome to ubuntu and welcome to the forums kurga :)

Please search a bit better where to post next time

---

### Post by kurga on 2005-06-14
Thanks for moving the post. What I look for is the posibility to change hostname on the livecd, so I can make more cd's with different hostnames. It's the same thing I'm looking for conserning the default homepage, the opportunity to change it on the cd. Any solutions?

---

### Post by ubuntu_demon on 2005-06-15
[QUOTE=kurga]Thanks for moving the post. What I look for is the posibility to change hostname on the livecd, so I can make more cd's with different hostnames. It's the same thing I'm looking for conserning the default homepage, the opportunity to change it on the cd. Any solutions?[/QUOTE]
 sionide is right .. you can't change stuff permanent on the live cd (just for this time you have booted).

did you try (I haven't tried on the live cd) :

$ sudo hostname mynewhostname

to look up the hostname simply type : 

$ hostname

also you might want to have more information about hostname .. then type this :

$ man hostname

---

### Post by kurga on 2005-06-16
I need to make some changes on the live cd so that I can choose the hostname on the pc and the default homepage. I'm going to use the live cd on some guest pc's at my work, and therefore I would like to change the default homepage to [www.mywork.com](www.mywork.com), and it wouldn't work if I have to go change every time a pc reboots:-)  So I'm looking for a way to modify the image on the cd. Sorry if I haven't got it clear from the start.

---

### Post by djalterego on 2006-02-28
I am about to try and mount the ISO image on another machine and edit the hostname before I burn the CD.  I will let you know how it goes.

---

### Post by jpv on 2006-08-11
> **kurga said:**
> Hey is it posible to change the hostname on the Live CD so that when you boot it has another hostname than ubuntu? I'm also looking for the posibility to change the default webpage in firefox. Thanks for the help.

See my feature request that would allow just want you want to be able to do: [https://launchpad.net/distros/ubuntu/+bug/40062](https://launchpad.net/distros/ubuntu/+bug/40062).

---

