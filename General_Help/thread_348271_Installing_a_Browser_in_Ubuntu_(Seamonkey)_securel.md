---
title: "Installing a Browser in Ubuntu (Seamonkey) securely"
date: 2007-01-28
forum: General Help
---

### Post by emarkay on 2007-01-28
I realized on a casual inspection that I have been installing the browsers in my user directory, because I was getting the 'permission denied' error when trying to go to /usr/local/.

In reviewing this thread, I found, that for security, the root is the place to install: 
[http://ubuntuforums.org/showthread.php?t=186011&highlight=seamonkey](http://ubuntuforums.org/showthread.php?t=186011&highlight=seamonkey)

However, installing as shown caused a MAJORITY of the files installed in my <USERNAME> directory to have root permissions - I had to (literally) check the preferences of each file and manually change permissions back to me. 

Is that a Linux fault or a Seamonkey fault?

Also, to ask for confirmation on my install, I have the following:
In my ROOT directory there is:
.mozilla/default/xxxxxxxx.slt/ directories and files, all static as to the time the program was installed.  All permissions (file owner and file group) are "root".
In my HOME/<USERNAME> directory there is:
.mozilla/default/yyyyyyyy.slt/directories and files, all active to the current moment.  All permissions (file owner and file group) are , or have been changed to <USERNAME> .

THANK YOU!

---

### Post by aysiu on 2007-01-28
The majority of your files in your *username* directory should not be owned by root.

But the last thing you said makes sense. Everything in /root--including /root/.mozilla--should be owned by root. Likewise, everything in /home/*username*--including /home/*username*/.mozilla--should be owned by *username*.

```
sudo chown -R *username:username* /home/*username*
``` should take care of things.

---

### Post by emarkay on 2007-01-28
That's what was so strange - the files in the <USERNAME> dir WERE owned by root.  
For example, I missed one and had to go back and "make it mine" when I found that every time I exited the browser, the screen settings kept returning to default!  (filename "chrome.rdf, in the CHROME subdir, BTW.)

Anyway, it's fixed now - just wondered if anyone knew why that happened, and if I (finally) do have this thing installed in the"correct" place!

Thanks!

---

### Post by aysiu on 2007-01-28
The only way I know to get files mysteriously owned by root all of a sudden is launching graphical applications with *sudo*. More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by emarkay on 2007-01-30
My suspicions are that something in all these permission-changing caused a TOTAL Ubuntu system crash for me:
[http://ubuntuforums.org/showthread.php?t=349200](http://ubuntuforums.org/showthread.php?t=349200)

I would ask if someone can clearly explain the harm in putting your browser in your <username> directory.  (Because I think that's where it's going back to, this time...)

I know about ports, firewalls, malware, SUDO, Windows pitfalls, and most Linux "built-in" defenses regarding online and network security, and thusly, ask, if all is configured, basically by default, and a browser is NOT in the ROOT, what possible/potential harm can happen to the user's system.

A sincere thank you.

Back in a few hours....  :(

---

