---
title: "[SOLVED] Scripting Question (avant-window-navigator)"
date: 2008-04-04
forum: General Help
---

### Post by Scheater5 on 2008-04-04
I'm having trouble getting avant window navigator to start on startup.  (yes, I'm on hardy, and the problem with avant may well be with hardy, but my question is not hardy-related)  I wrote a simple script consisting of merely the command "avant-window-navigator" and put it in /usr/share/gnome/autostart.  The script works, I've tested the permissions, chmod'ed, and so forth - tested it post-startup and it works fine - but it doesn't work on login.  I think the problem may be that it is trying to launch avant before compiz - so does anyone know how to write a script to wait for compiz and then launch avant?  Of course, any information on hardy and avant will be welcomed, but I know this is not the category for that - I'm posting here because I'm also interested in expanding my ability to script.

---

### Post by Scheater5 on 2008-04-05
hmmm...latest round of updates and a reboot, and "automagically" it works.  Looks pretty freaky on login to gnome, but eventually it settles and works fine.  Now the regular "Start automatically on startup" in the avant preferences works and the script created a duplicate - so I removed the script and it's all well.

---

### Post by jamesnewell on 2008-04-05
Hi,

I'm having a similar problem on Hardy. I have put avant in the sessions in order to get it to load on start up, but it never does. I have a feeling that it is starting before compiz.

Where is "Start automatically on startup" in the avant preferences?

Thanks,

James

---

### Post by jamesnewell on 2008-04-06
Ok don't worry, I updated yesterday but it just happened to work today

---

