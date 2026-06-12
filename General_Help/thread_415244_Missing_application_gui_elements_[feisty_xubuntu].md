---
title: "Missing application gui elements [feisty xubuntu]"
date: 2007-04-20
forum: General Help
---

### Post by tactus on 2007-04-20
I have used feisty Xubuntu since the beta, recently I did a fresh install (but kept my home partition of course) from the final feisty Ubuntu alternate cd and did a aptitude install xubuntu-desktop to get back on track. It went ok, but now there is issues with some theme elements. Buttons in some XFCE/gtk application seems missing, and the logout dialog window have no button icons at all. I've tried to change icon theme to no avail, also creating a new user didn't help. Any suggestions? Worth reporting to launchpad.net, or am I alone with this issue, or is there just an easy fix? Thanks.

[[img]http://bildr.no/thumb/57758.jpeg[/img]](http://bildr.no/view/57758)

[[img]http://bildr.no/thumb/57761.jpeg[/img]](http://bildr.no/view/57761)

[[img]http://bildr.no/thumb/57762.jpeg[/img]](http://bildr.no/view/57762)

---

### Post by tactus on 2007-04-20
Okey, I think I've solved it. I logged out, switched to a virtual console, and did something like this:

*sudo aptitude purge xubuntu-desktop && sudo aptitude clean && sudo aptitude update && sudo aptitude install xubuntu-desktop && sudo /etc/init.d/gdm restart*

Of course it only worked because I installed xubuntu-desktop with aptitude to begin with. Cheers. \\:D/

---

