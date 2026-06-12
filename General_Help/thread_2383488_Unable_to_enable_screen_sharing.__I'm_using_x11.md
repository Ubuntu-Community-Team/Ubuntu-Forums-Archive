---
title: "Unable to enable screen sharing.  I'm using x11"
date: 2018-01-25
forum: General Help
---

### Post by hondaman on 2018-01-25
Ubuntu 17.10 server.  Logged in using Ubuntu xorg.  Verified using x11 with "echo $XDG_SESSION_TYPE".  When I go to Settings -> Sharing -> Screen Sharing, the toggle in the upper left corner is "off" and it wont turn "on"  Can someone please help me figure out how to enable screen sharing?  Thank you.

---

### Post by #&amp;thj^% on 2018-01-25
What dose this show then:
```
vino-preferences
```

---

### Post by hondaman on 2018-01-25
That was all turned off there.  I enabled it in vino-preferences with my password, went back to Settings -> Sharing -> Screen Sharing and it's turned off still and won't allow me to turn it "on", however "allow connections to control the screen" is now ticked and my password is entered.

Edited, sorry, should have replied with quote :D

---

### Post by #&amp;thj^% on 2018-01-25
Yes we have seen a few reporting that " Settings -> Sharing -> Screen Sharing and it's turned off still and won't allow me to turn it "on","
But was solved with enabling it through "vino-preferences"
Let us know how it goes.

---

### Post by hondaman on 2018-01-25
I have a feeling it's not going to let me turn on screen sharing because, as it says in the Screen Sharing dialogue "No networks selected for sharing", as seen in this image [https://www.linux.com/sites/lcom/files/styles/rendered_file/public/sharing_1.jpg?itok=NEPGTCs9]("https://www.linux.com/sites/lcom/files/styles/rendered_file/public/sharing_1.jpg?itok=NEPGTCs9")  I believe this is a function of Network Manager?

---

