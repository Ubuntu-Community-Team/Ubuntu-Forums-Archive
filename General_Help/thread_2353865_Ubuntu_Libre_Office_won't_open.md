---
title: "Ubuntu Libre Office won't open"
date: 2017-02-25
forum: General Help
---

### Post by bthomson100 on 2017-02-25
I don't know if this is the right place to post this request for help or not. I have just tried to open an important document I am writing and got the following message:

[INDENT]The application cannot be started. 
Failed to updatefile:///home/bobt/.config/libreoffice/4/user/extensions/bundled/lastsynchronized

[/INDENT]
I've tried to open the document in Gedit but can't. I put a lot of work into this and find this extremely frustrating.

I've upgraded to Ubuntu 16.04 and Libre Office 5

Bob Thomson
Ottawa Canada

---

### Post by TheFu on 2017-02-25
Copy the file into /tmp/
Change the permissions to allow everyone to read it.
Create a new userid.
Login as that new userid.
Try to open the file in /tmp/  - does it work?

Using a different/new userid removes any old settings that could be getting in the way. If opening the file with the new userid works, it is a settings issue in your HOME.

---

### Post by bthomson100 on 2017-02-25
Thanks. Actually I was finally able to open the file and saw that it only contained the digit 1. I saved it under a different name and then deleted it. Then Libre Office opened, recovered the file(s) and went back to "normal". Hopefully it won't happen again.

How do I now mark this SOLVED?

---

### Post by wildmanne39 on 2017-02-25
Use thread tools at the to of the page to mark the thread solved.:)

---

