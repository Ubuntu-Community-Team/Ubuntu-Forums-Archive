---
title: "Add new user - has no sound"
date: 2008-02-28
forum: General Help
---

### Post by zorlab on 2008-02-28
After install I made a shell account,( I guess you would call it.) "adduser"
But there is no sound for this user. 
This seems strange, how do I config the sound?

---

### Post by deepclutch on 2008-02-28
why?if sound is working for others,then for this user also.u can may be enable esd(enlightened Sound Daemon).try playing with mpg123 or ogg123 playing some mp3 or ogg files.

---

### Post by jschaab on 2008-02-28
I'd guess the new user hasn't been added to the "audio" group. Try adding them to that group.

---

### Post by zorlab on 2008-02-28
This, in fact, is the user I will login as, instead of root, through  the initial setup.
I'll try to find the audio group; I am fairly new to ubuntu.

---

### Post by jschaab on 2008-02-28
try this:

```
sudo usermod -a -G audio username
```

---

### Post by zorlab on 2008-02-28
ok ....I was able to change privileges in users, works now, thanks. 

I see there, that there is a root user... is this the same as the administrator user that I set up during Ubuntu install? 
If so.... why have, in essence, 2 root users?

If not what is the difference?

---

### Post by jschaab on 2008-02-28
by default I don't believe root login is enabled. the Administrator is basically a normal user who happens to be in the admin group and therefore has access to the sudo command to execute commands  with root privileges.

---

### Post by zorlab on 2008-02-28
does that mean that it is for security, that there is no enabled root?

Are there time when you need root enabled?

---

