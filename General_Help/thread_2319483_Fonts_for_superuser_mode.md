---
title: "Fonts for superuser mode"
date: 2016-04-04
forum: General Help
---

### Post by pwabrahams on 2016-04-04
When I start Firefox or Dolphin in superuser mode, I don't get the fonts that I normally use.   The preferences I've set don't seem to apply.  How can I configure those fonts?

---

### Post by Bucky Ball on 2016-04-04
You are starting Firefox from a terminal with 'gksudo firefox'? May I ask why? You shouldn't be running these programs as root, which is what you're doing.

Anyhow, that's the reason: you're running Firefox as root. The font and other settings belong to your regular user profile.

---

### Post by pwabrahams on 2016-04-04
I got a little confused -- the problem showed up in dolphin and kate, not Firefox.  It's often useful to run those programs in superuser mode -- in fact, I have desktop icons for "root dolphin" and "root kate".  I've also encountered this behavior in other programs.   What I'd like to do is extend my settings to programs that I run as root.

---

### Post by Impavidus on 2016-04-05
Using a file manager or text editor as root makes some sense. To change the fonts, you'd have to run the tool to change your settings as root. Or you can simply copy your config files from /home/your_user_name to /root, which is root's home directory. I expect them to be hidden somewhere in ~/.config.

---

### Post by pwabrahams on 2016-10-25
This is a bit old, I know, but I did solve the problem by **sudo cp -a /home/pwa/.config /root**.  It turns out that initially, /root is totally empty.  That surprised me.

---

### Post by Impavidus on 2016-10-25
Great. Could you now mark this thread as solved? Thread tools (near top of page) -> maek as solved.

---

