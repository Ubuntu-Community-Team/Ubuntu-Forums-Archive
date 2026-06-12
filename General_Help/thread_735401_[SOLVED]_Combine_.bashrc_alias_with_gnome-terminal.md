---
title: "[SOLVED] Combine .bashrc alias with gnome-terminal option"
date: 2008-03-25
forum: General Help
---

### Post by FakeOutdoorsman on 2008-03-25
I often ssh into various servers and manually change to a specific gnome-terminal profile per host server to prevent confusion.  I've added a few aliases in .bashrc to shorten "ssh [email]user@domain.tld[/email] -p 4921" to "sshdomain".  Is there a way to combine this alias and "gnome-terminal --window-with-profile=PROFILENAME" so I don't have to manually change the profile for each different connection?

---

### Post by FakeOutdoorsman on 2008-03-25
I figured it out:
```
gnome-terminal --window-with-profile=PROFILENAME -e 'ssh user@domain.tld -p 4029'
```

---

