---
title: "how do i get owner access???"
date: 2005-06-16
forum: General Help
---

### Post by js88888888 on 2005-06-16
im tryn to disable tapping but i need owner access to do it.  ](*,)

---

### Post by defkewl on 2005-06-16
Could you please be more specific about your issue? If you need owner access you could either use su or chgrp it to the same group.

---

### Post by js88888888 on 2005-06-16
i have have an hp pavilion xt412 laptop and i wanted to disable mouse tapping, but the file  (xorg.conf) is only a read only file, i cant edit it w/o being the owner. i tried the su but it denies me access. i did set the password and add my name to the list of su.

Posts: 433
Send a message via Yahoo to defkewl
	
Default Re: how do i get owner access???
Could you please be more specific about your issue? If you need owner access you could either use su or chgrp it to the same group.
__________________
Visit my blog
Report Bad Post   	Reply With Quote Quick reply to this message
defkewl
View Public Profile
Send a private message to defkewl
Visit defkewl's homepage!
Find More Posts by defkewl
Add defkewl to Your Buddy List
Visit defkewl's Journal
Reply

« Previous Thread | Next Thread »

Quick Reply
Message:
Bold
	
Italic
	
Underline
		
Wrap [QUOTE] tags around selected text

---

### Post by angkor on 2005-06-16
sudo gedit /etc/X11/xorg.conf should give you permission to write the file. 

Don't forget to make a backup

---

### Post by XDevHald on 2005-06-16
[off topic] - ***js88888888***
If you could please delete your signature in your User CP to something shorter. It also seems that you copy/paste from the site or it could be a bug that needs attention.
[/off topic]

---

### Post by js88888888 on 2005-06-16
sry 'bout length it was an accident

---

