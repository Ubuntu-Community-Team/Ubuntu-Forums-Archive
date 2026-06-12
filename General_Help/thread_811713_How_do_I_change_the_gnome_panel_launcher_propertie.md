---
title: "How do I change the gnome panel launcher properties?"
date: 2008-05-29
forum: General Help
---

### Post by cokhavim on 2008-05-29
Hello,

I have a weird problem.  I created a launcher on my gnome panel:
Type: Application in Terminal
Name: MyCommandName
Command: mycommand

In my .bashrc file, I created an alias:
alias mycommand='long long command which includes a pipe'

This worked quite well for a long time.  Now, I've changed the alias in my .bashrc so that mycommand calls a slightly different long command.  However, the launcher still remembers the old alias.  Why is this happening?  How can I get gnome to use the new alias?

Thanks.

---

### Post by FuturePilot on 2008-05-29
Try deleting the launcher and recreate it

---

### Post by cokhavim on 2008-05-30
I did that.  Didn't work.  I even deleted the launcher, rebooted, recreated the launcher, and it STILL remembers the old alias.

---

### Post by khughitt on 2008-05-30
Have you restarted since then? The .bashrc file only gets read in when Bash is initialized, so it won't recognize the new commands right away. You could also try typing the alias directly into the console and seeing if it works then.

---

### Post by cokhavim on 2008-05-31
Yeah, I've restarted several times, but nothing works.  When I type "mycommand" directly into a console, the correct alias is called, but the gnome panel launcher still does not call the correct alias.  For some reason, the gnome panel is not reading my .bashrc and is reading an old version of my .bashrc stored who knows where.

---

### Post by khughitt on 2008-06-02
> **cokhavim said:**
> Yeah, I've restarted several times, but nothing works.  When I type "mycommand" directly into a console, the correct alias is called, but the gnome panel launcher still does not call the correct alias.  For some reason, the gnome panel is not reading my .bashrc and is reading an old version of my .bashrc stored who knows where.

That's pretty strange. Perhaps you could try storing the alias in either your .profile or .bash_login file, and see if the launcher uses either of those? Any other threads come up when you search the forums for "launcher?" I'm suprised no one else would have pointed this out before now.

---

