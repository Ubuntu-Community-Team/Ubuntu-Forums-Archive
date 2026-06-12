---
title: "password 7.04 problem"
date: 2007-07-07
forum: General Help
---

### Post by alexga on 2007-07-07
I downloaded 7.04 home use it installed and found all hardware PERFECT when it was loaded and restarted it ask for USER Name then Pssword I entered the ubuntu 6.06 and it refuses all efforts not accepting o9ld password or 6.06 password so I cant use it HELP
[email]Alexga@pclnet.net[/email]

---

### Post by taurus on 2007-07-07
Try using **oem** as your login name and the same password that you have created.  Then, you need to run this command to create an actual account for you to use from then on.

```
sudo oem-config-prepare
```

p.s.  Not a good idea to include your e-mail here unless you want spam from others...

---

### Post by alexga on 2007-07-07
I get a screen orange screen with utunbu and a slot with username and when you put it in and hit enter it ask for a password put it in and hit enter it sets there a few seconds and comes back in red letters incorrect user or password I can not do anything else it won't let me in I put it on a new hard drive.
Thanks for any advice I can't get to where you told me to go.

alex

---

### Post by taurus on 2007-07-07
Boot into recovery mode from GRUB menu and post the output of this command here.

```
ls -la /home
```

---

