---
title: "How do i uninstall Extreme Download Manager on ubuntu 12.04?"
date: 2014-02-15
forum: General Help
---

### Post by deaton25 on 2014-02-15
hi 

how do i uninstall Extreme Download Manager on Ubuntu 12.04? That means also getting rid of the icon that appears in the Application area of Dash as well as all the Java related stuff that was downloaded with it
i tried using 'sudo apt-get purge xdman' but i am not certain that that did the job:(please tell me that i didn't make things worse, PLEASE!). I was told that xdman was uninstalled but
all the Java related stuff is still in the History section of the ubuntu software center and the extreme download manager icon is still in the app section of Dash. And i want to get rid of that also. I have heard that Java is dangerous because its loaded with spyware etc!

thanks

---

### Post by ian-weisser on 2014-02-15
The 'xdman' package does not seem to be in the Ubuntu Repositories (nor Debian archives).
That means two things.

1) You got it from somewhere else (where?)
2) It's not supported by this forum. It's supported by whomever you got it from.

But we can try to help a bit.

- Java-related stuff in 'History' is...well, history. Uninstalling does not alter the past. Paste it here if you want our opinion.
- Where did you get xdman from? How did you install it? How you installed it determines how you uninstall it.
- Look in /var/log/apt for the terminal log of package management sessions. Find the session where you uninstalled xdman. Paste that entire session here.
- Please don't spread FUD. Java is *not* "loaded with spyware." Some malware is written in Java, but some malware is written in lots of languages.

---

### Post by deaton25 on 2014-02-15
I do know that usually when something is uninstalled , the removal shows up there.This time the only thing that showed up when i used 'sudo apt-get purge xdman' was
the removal of 'lbnspr-O4 (4.9.5 OubuntuO 12.0.4.2)' I have no idea what that is....
2) I got xdman from SourceForge and downloaded it from there
3) being new to Ubuntu, i do not know how to use the /var/log/apt directory and thus do not know how to find the session where i think i uninstalled xdman

---

### Post by bc.haynes on 2014-02-15
To check the log: Enter in Terminal:
```
cd /var/log/apt
```
To change to the apt directory.

You want to look at history.log, so:
```
cat history.log | less
```
You can scroll through the log OR press the <Spacebar> to move down a page at a time.
When you find what you are looking for, copy and paste the results in your thread.
Change back to your home directory after finishing:
```
cd ~/
```
Hope this helps.

---

### Post by deaton25 on 2014-02-15
Start-Date: 2014-02-15  04:40:40
Commandline: apt-get purge xdman
Purge: xdman:amd64 (3.0.1)
End-Date: 2014-02-15  04:40:51
(END)

AND THAT' S IT. Does this mean that  'xdman' has been uninstalled? if not, how do i uninstall it? thanks

---

### Post by deaton25 on 2014-02-15
Start-Date: 2014-02-15  04:40:40
Commandline: apt-get purge xdman
Purge: xdman:amd64 (3.0.1)
End-Date: 2014-02-15  04:40:51
(END)

does this mean that xdman has been uninstalled? if not how do i uninstall it?

---

### Post by Frogs Hair on 2014-02-15
If  this is the same application there is Mint .deb package if you have removed the package  the following command should remove additional packages. ```
sudo apt-get autoremove
```  [http://sourceforge.net/projects/xdman/files/](http://sourceforge.net/projects/xdman/files/)

---

