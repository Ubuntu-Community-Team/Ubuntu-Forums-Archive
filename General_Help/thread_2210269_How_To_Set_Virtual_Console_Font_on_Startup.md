---
title: "How To Set Virtual Console Font on Startup?"
date: 2014-03-10
forum: General Help
---

### Post by dniMretsaM on 2014-03-10
I'm trying to set the TTY font on startup (on Ubuntu 12.04). I've tried [FONT=Courier New]sudo dpkg-reconfigure console-setup[/FONT], but that's not persistent over reboots. I've tried manually editing [FONT=Courier New]/usr/share/console-setup/console setup[/FONT], but that gives the same results. My most recent attempt is putting [FONT=Courier New]setfont -v Greek-Terminus16 >> /var/log/rc.local.log 2>&1[/FONT] in [FONT=Courier New]/etc/rc.local[/FONT]. Checking the logs confirm that the script is executed, but when the TTY login screen shows up, the font is unchanged. Once I'm logged in, executing the script will set the font correctly.

So how can I get the changes made by rc.local to not be overwritten? Or is there a better way to set the TTY font on startup? Any help or information will be greatly appreciated.

I also have a [FONT=Courier New]setterm[/FONT] command in rc.local to change the text color, but it has no noticable effect either. I'm guessing it's the same problem effecting both commands.

EDIT: Okay, so I finally got someone who knew what they were talking about in IRC. The reason it wasn't effecting anything is because rc.local is run in as a non-interactive user. I just threw the commands in ~/.zprofile (the ~/.profile of ZSH) and it now works just fine. I'll mark this as solved.

---

