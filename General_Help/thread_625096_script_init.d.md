---
title: "script init.d"
date: 2007-11-27
forum: General Help
---

### Post by anna611 on 2007-11-27
am looking for weeks to get my script running.

Just to learn it, I made a test, want to run skype at startup.
How does it work?

I wrote a script 'example'

Code:
Code:
Code:

#!/bin/sh

/usr/bin/skype


Placed it in /etc/init.d
did chmod +x example
did update-rc.d example defaults

I thought this would be enough?
I test it by typing /etc/init.d/./example,and it works, skype runs.

But it doesn't work when I restart my computer.

Thank you in advance for helping me!

---

### Post by PeterJS on 2007-11-27
I ran in to a problem like this when setting up some init scripts on an Ubuntu server box. The default shell for the user environment is bash, so if you run a script from the terminal it will run under bash. However when init runs at start up it uses the dash shell, so you want to test your script with dash:
```

sudo dash /etc/init.d/script start

```
And see if it gives you any errors. Dash is a bit more strict than bash on what it will and won't allow.

---

### Post by anna611 on 2007-11-27
It gives me a list of what is in the file of /home/user/.Skype?

---

### Post by feizex on 2008-04-26
Hi,

I know this is an old thread but I am new to Ubuntu and was looking for an answer to this myself. I figure others would like to know. I found an alternative to a script.

In gnome choose System > Preferences > Sessions 
Then in the Startup Programs TAB click on the + ADD button.

Enter settings as follows...
Name: skype
Command: skype
Comment: skype

Click OK and Close.

Skype should now load when you login to gnome.

Regards,
Feizex.

---

### Post by Aearenda on 2008-04-26
I think feizex has it right. To fill in the details, the init.d directory is for background services that should run whether a user is logged on or not. If started from there automatically, skype would be running for the wrong user (root!), and would not be able to connect to the user interface when a real user did log on.

---

