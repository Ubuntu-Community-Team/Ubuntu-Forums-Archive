---
title: "An All Ubuntu School"
date: 2008-06-20
forum: General Help
---

### Post by thor992 on 2008-06-20
I am working to help a local school with it's computer needs and am trying to architect the best possible solution to meet those needs.

Today they have about 15 computers with about 13 of those being student computers and the rest being staff machines.  They are running a mix of XP and Vista in a workgroup and are all connected to the same, unsecured, network either by wireless or by tether.  The PCs are completely unmanaged and unsecured and there as no Internet filtering of any kind. 

My &#8220;vision&#8221; for moving them forward would be to install an Ubuntu Server to provide LDAP services, APT Repository services (for the desktops), and file and print services.  I would also like to secure the desktops to prevent software installs, terminal access, and even limit which applications they can run (kiosk like).  For Internet filtering, I could setup a different box running dansguardian.

I guess my question to the forum is two-fold.  (1) Any suggestions or tutorials on a setup like this? (2) Any feedback or suggestions on a better setup.  I want to avoid any gotchas if at all possible ;)

---

### Post by sdennie on 2008-06-20
That sounds like a reasonable setup to me.  I don't completely understand why you'd need an APT repository service but, other than that, what you are suggesting sounds like the right idea.

You can probably find more indepth tutorials but, if you run "gconf-editor" from a terminal go to Edit->Find (make sure both checkboxes are checked) and search for "lock", you can get an idea how just how many things can be locked down under gnome.  It should be fairly straightforward to customize the systems exactly how you want and then completely lock them down.

---

### Post by thor992 on 2008-06-20
The idea behind the local APT repository was to control updates to the desktops.  In other words rather than have them all go out to the internet for updates, they go to the local server and I can control what gets updated.

---

### Post by sdennie on 2008-06-20
That makes sense.  Sounds like a fun project.  :)

---

### Post by kcnnc on 2008-07-04
I am working on a similar setup although in a workplace environment. 

I have most of the desktop, apt-cacher, print, file part done. The LDAP part is where I'm stuck at the moment. Would be pleased to exchange notes if you can post your experiences or questions.

---

### Post by Riffer on 2008-07-09
deleted

---

