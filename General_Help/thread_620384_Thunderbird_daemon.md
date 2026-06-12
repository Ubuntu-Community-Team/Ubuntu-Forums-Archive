---
title: "Thunderbird daemon"
date: 2007-11-22
forum: General Help
---

### Post by Joakim Stokland on 2007-11-22
Hi!
Is there any way to enable some sort of "Thunderbird daemon"? I'm talking about a little icon to lay in the notification area, and look for new e-mail frequently.
I have to start Thunderbird to check for new e-mails, but I want it to run at startup, and frequently check for e-mails without the main window being open. Now I have to keep Thunderbird open (minimized) if I want it to check for new e-mails automatically. As soon as I close it, I get no notification about new e-mails.

Does anyone know?
Thanks!
Joakim

---

### Post by Forlong on 2007-11-22
You can do that with [AllTray](http://alltray.sourceforge.net) - it's in the repos:
```
sudo apt-get install alltray
```

---

### Post by Joakim Stokland on 2007-11-22
Great, I'll try that! Thanks :)
Joakim

---

### Post by Joakim Stokland on 2007-11-22
So, I installed alltray, but when I run it, and click the window I want to dock like the dialogue box says, nothing happens... Am I missing something?

Edit: I figured it out now. I simply added "alltray thunderbird" to the list of programs to load during bootup under System - Preferences - Sessions.

---

### Post by frafu on 2007-11-25
Hello, 

I am pleased to see that you found a solution. :)

As the Accessibility Forum is intended to talk about software related to disabilities, I am moving this thread to the General Help forum. 

Have a nice day. 

Francesco

---

