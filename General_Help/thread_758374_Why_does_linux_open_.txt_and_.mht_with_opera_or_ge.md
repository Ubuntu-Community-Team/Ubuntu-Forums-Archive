---
title: "Why does linux open .txt and .mht with opera or gedit?"
date: 2008-04-17
forum: General Help
---

### Post by Wage on 2008-04-17
For some reason, ubuntu opens .txt and .mht with either Opera or gedit. I can change its "open with" settings but this changes it for both filetypes.
It lists both filetypes as "Plain Text Document." How do I fix this?

(.mht if you don't know is a file format used by Opera and IE to save all a webpage with its images in a single file.)

---

### Post by AlphaWu on 2008-04-18
/etc/gnome/defaults.list  is global setting
~/.local/share/applications/defaults.list  is your personal setting

the priority is: personal> global

---

### Post by Wage on 2008-04-21
The personal one just has some settings for VLC. I think the problem is the MIME type for .mht files is wrong, set as text/plain when it should be application/mime I think?  I added a line to the personal settings "application/mime=opera.desktop" and when i right click the file it says "Open with Opera" but double clicking it gives me an error saying the file type indicates its type is "HTML file with images" but the contents of the file indicate its a "Plain Text Document" and it might present a security risk so it won't let me open it.

---

### Post by Wage on 2008-04-28
Still broken with 8.04 upgrade :(

---

