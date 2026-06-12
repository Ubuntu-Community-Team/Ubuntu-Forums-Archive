---
title: "A problem with setting up Mutt"
date: 2013-09-29
forum: General Help
---

### Post by dshgna on 2013-09-29
Hi!

I am trying to set up a mail using esmtp and mutt. [COLOR=#000000][FONT=Arial]

When I try to send an email I get the following error :

[/FONT][/COLOR]```
Error sending message, child exited 70 (Internal error.).
```

These are my ~/.esmtprc[COLOR=#000000][FONT=Arial] file.

[/FONT][/COLOR]```
identity "xy92@gmail.com"      
hostname smtp.gmail.com:465
username "xy92@gmail.com"
password "PassWord"
starttls required

```[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR]These are my ~/.muttrc[COLOR=#000000][FONT=Arial] file.
[/FONT][/COLOR][COLOR=#000000][FONT=Arial] 
[/FONT][/COLOR]```
set sendmail="/usr/bin/esmtp"
set envelope_from=yes
set from="X Y <xy92@gmail.com>"
set use_from=yes
set edit_headers=yes

```[COLOR=#000000][FONT=Arial]

All help in finding a solution is greatly appreciated!
Thank you![/FONT][/COLOR]

---

### Post by Kirk Schnable on 2013-09-30
I did a bit of Googling, and I found this thread, which appears to be a similar problem, some discussion, and a possible solution for you: [http://comments.gmane.org/gmane.mail.mutt.user/33755](http://comments.gmane.org/gmane.mail.mutt.user/33755)

---

### Post by andrew.46 on 2013-09-30
Have a look at an Ubuntu Community page that admittedly uses msmtp:

[https://help.ubuntu.com/community/MuttAndGmail](https://help.ubuntu.com/community/MuttAndGmail)

Hopefully this will get you up and running...

---

