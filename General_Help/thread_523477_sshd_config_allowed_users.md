---
title: "sshd_config allowed users"
date: 2007-08-11
forum: General Help
---

### Post by dasnipa on 2007-08-11
greetings, I'm creating a fairly specialized setup for my sshd_config. My intentions are I want to be able to connect in externally, but limited to one (restricted) user account only. From within my home network (192.168.2.*), I don't want any of these restrictions to apply. I'm currently setup with the first goal (allowing connections to only one user) via the AllowUsers <account> tag. I was hoping it would be as easy as something like another tag like AllowUsers * from IP

---

### Post by dasnipa on 2007-08-12
since I figured it out, I figured I would reply to my own post with my answer, so that hopefully someone looking for info will stumble upon this and find it of use.
All I had to do was add a second instance of AllowUsers so the lines in my sshd_config are:
AllowUsers <user>
AllowUsers *@192.168.2.*

tada, only <user> is accessible from outside my network. while any user is accessible internally.

---

