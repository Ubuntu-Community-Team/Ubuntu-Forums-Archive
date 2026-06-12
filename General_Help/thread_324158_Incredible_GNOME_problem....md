---
title: "Incredible GNOME problem..."
date: 2006-12-23
forum: General Help
---

### Post by limaunion on 2006-12-23
This is really unbelievable, I've been using GNOME without problems for the last couple of years till now. 

For some reason I had to kill my gnome/xorg session with CTRL+ALT+BACKSPACE, after that when I logged in I just got my desktop background and mouse cursor, no panels, no right click, or anything else. So I renamed some of the hidden gnome files from my profile (.gconf, .gnome, etc) in order to test if it was related to some corrupt file, but got the same results. Next I tried renaming my entire home folder (/home/my_username) making a new one, ie: mv /home/my_username my_username.backup && mkdir /home/my_username && chown -R my_username /home/my_username, same results, just the default Ubuntu desktop background and mouse cursor. 

Then I created a new user in my system in order to try gnome and it's working okay, default Ubuntu/GNOME environment (from were I'm writing this thread). The most strange thing is that I renamed this new user's home folder to my default user name (the one that's having problems) and the problem still happens... ie: mv /home/testuser /home/my_username && chown -R my_username /home/my_username, then logged in to gnome with the same results.

GNOME is refusing to work with my default user name... so, does gnome keep personal settings in some other place apart from /home/my_username ?
Any ideas or suggestions on how can I switch back to my default user name ?
Thanks in advance.
JC

---

### Post by pay on 2006-12-23
I think that your home folder needs 644 permissions (off the top of my head). Try ```
sudo chown -R my_username:my_username /home/my_username
sudo chmod 644 /home/my_username
```

---

### Post by bettlebrox on 2006-12-23
**Don't** 644 your home! The permissions for ~ should be 700 or 711 or 755.

With 644 on your home directory you won't even be able to create files in your own home directory!

700 is the most restrictive setting for your home, no-one else will be able to browse it. 

711 will allow things like Apache to access your ~/public_html

755 will allow other users to view files in your home.

Try logging out of Gnome, login to the command-line, see if there are processes owned by you that are still running. (ps -ef |grep $USER). Gconf leaves a daemon process running after you logout that probably retains your old settings.

---

### Post by pay on 2006-12-23
Opps. I knew it was either 644 or 755. Sorry for misleading you.

---

### Post by iamhugeinjapan on 2006-12-23
There's been other posts in the last few days about GNOME suddenly having nothing on login. It's a bit alarming.

Maybe there is a faulty update that affects some configs.

---

### Post by limaunion on 2006-12-23
> **iamhugeinjapan said:**
> There's been other posts in the last few days about GNOME suddenly having nothing on login. It's a bit alarming.

Maybe there is a faulty update that affects some configs.

I don't know if I've made some mistake but now GNOME is working again with the default Ubuntu theme. Thanks for all the answer, this thread should be closed.
JC

---

### Post by sgbeamer on 2006-12-27
I had similar problems.  I had to start the GNOME failsafe session after upgrading to Edgy and I would get a message that said Gnome could not locate the message bus.  After poring through the posts and trying many of the network, file permission solutions, etc (none of which worked for me), I went to synaptic and re-installed the gnome-settings-daemon package and now everything works great again.  This fix took about 30 seconds to implement from start to finish.

---

### Post by ovidescu on 2006-12-27
I have had about the same problem, after I installed recommended updates from Update Manager. I have Ubuntu Edgy Eft, installed about a month ago. This is my first time on Linux, so you can imagine the frustration when I had no right click, no panels, no menus, no terminal to kill my session, I had no idea about keyboard shortcuts.... luckily I had FF open and Alt+Tab worked fine. SO I started googling for ways to restart my computer, WITHOUT hard reset from the button, because I knew some updates might screw up my Ubuntu if I did that. And so I came across Ctrl+Alt+Backspace, which fortunately worked like a charm, restarted my computer and all is well now.
I hope this helps in some way.

Ovidiu

---

### Post by ovidescu on 2006-12-27
I think Gnome problems in Ubuntu Edgy should become official now. I just experienced a crash, again, in just 2 days. My panels stopped responding, alt+tab was working ok, so was ctrl+alt+backspace. (I was running XMMS listening to online radio, GAIM, a couple of file browsers, FF2.0.0.1 with 4 open tabs and an idle terminal window) I logged out, and when I logged back in I received and error message "a panel still running will now exit" (if I recall correctly). This time I could only see my desktop wallpaper and desktop icons, no panels whatsoever. Ctrl+Alt+Backspace again, hit the restart option, at which point I got a pinkish-yellowish vertical stripes screen, with one thin green line across, right in the middle. I waited for about one minute and then it rebooted, thank god.
Now I'm back in, writing this reply, hoping that someone from the staff is watching this thread. 
I have heard for many years that linux was tougher than windows, not crash as often and so on, but my latest experiences really tend to try my confidence in Ubuntu. However, I will not give up, hoping that this issue will be solved somehow.

O.

---

