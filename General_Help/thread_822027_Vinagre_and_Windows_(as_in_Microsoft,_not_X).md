---
title: "Vinagre and Windows (as in Microsoft, not X)"
date: 2008-06-07
forum: General Help
---

### Post by ShinHadoken on 2008-06-07
I like the new Vinagre remote access client that comes with Hardy, but how do I set this up to work on my Windows XP system? I don't want to access anything ***from*** this machine, I want ***access to it***.

Thanks, 

SH

---

### Post by ShinHadoken on 2008-06-07
bump

---

### Post by ShinHadoken on 2008-06-09
bump

---

### Post by ShinHadoken on 2008-06-14
bump again please

---

### Post by cariboo on 2008-06-14
Have you tried vncserver for windows, it looks like vinagre is partially based on vnc.

Jim

---

### Post by ShinHadoken on 2008-06-14
No, I haven't. Look at this [photo from the GNOME website]("http://www.gnome.org/projects/vinagre/vinagre1g.png"), though. It looks like their might be more installed.

---

### Post by ShinHadoken on 2008-06-14
bUmP?

---

### Post by cariboo on 2008-06-15
I see from the graphic they have Ultravnc viewer + server installed. That is basically vncserver+vncviewer with a fancier gui. Looks interesting I might have to give it a try.

Jim

---

### Post by ShinHadoken on 2008-06-15
Ok, cool. Let me know what you come up with.
 
Thanks for your help,
 
SH

---

### Post by aichee on 2009-03-17
This might not the right fix for you.  You can use the VNCViewer in MS Windows to connect to Ubuntu.  At the ubuntu's Remote Desktop Preferences, select the 'Advanced' tab, clear the 'Require encryption'.  Just remember on your VNCViewer, you want to set Encryption to be "always off".

---

### Post by mocoloco on 2009-03-17
If it's XP Pro and you've got it set up for RDP (they just call it "Remote Desktop") you can use gnome-rdp.  It's indispensable for me for work.
Also, the new Vinagre in Jaunty will have RDP support as well as VNC.

---

### Post by Wolfpup on 2009-04-23
> **aichee said:**
> This might not the right fix for you. You can use the VNCViewer in MS Windows to connect to Ubuntu. At the ubuntu's Remote Desktop Preferences, select the 'Advanced' tab, clear the 'Require encryption'. Just remember on your VNCViewer, you want to set Encryption to be "always off".
 
 
I have tried this. as im trying to set up to where i can use a remote managed ubuntu system as a file server and for running ktorrent which could be remotely accesed and opereated form my winxp systems as the file server will not be readily acessable and have a 'dumy' vid cable pluged into it for fooling the system bord into thinking there is a monitor pluged in.

---

