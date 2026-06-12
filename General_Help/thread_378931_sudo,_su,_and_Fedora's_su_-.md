---
title: "sudo, su, and Fedora's su -"
date: 2007-03-07
forum: General Help
---

### Post by CocoAUS on 2007-03-07
I've been searching on the forums for an explanation, but what I've read seems somewhat incomplete and confuses me.  What exactly is the function of sudo?  What is the function of su?  Is this su different from Fedora's su - command?

To help things along:
Does sudo perform the action as root, or does it perform the action as the user with super user privileges?  What about su?

What are the time limits?  For instance, if I use su, does this make me root for the entire duration of the terminal session?  Does it simply function on a per-use basis?

Which one is better?

If sudo only requires the user password, how is this secure?  Wouldn't any user be able to look at other users' files and make system-wide changes?

From a thoroughly confused sudoer,
Thanks ahead of time

---

### Post by etank on 2007-03-07
sudo means "super user do". Only users that are in the admin group listed in /etc/group have the ability to use sudo to do root activities by default.  sudo performs the actions as root.

su means "switch user". You can use it so switch to any user.

I think that the time limit for sudo is 10 minutes of inactivity before it will ask for **your** password again.

You can do ```
sudo -i
```to log in as root if you really want to (not advised). This would make you root until you typed exit in the terminal.

Here is a good read about this that can explain it better than I can [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I hope that helps to clear it up some.

---

### Post by CocoAUS on 2007-03-07
That does help some, but I'm still unclear on some things.  For instance, you say that su changes the user.  However, when I do a "sudo gnome-open ___", it opens nautilus with root's settings.  It does the same thing when I do "sudo gedit ___".  If sudo doesn't change users, why does it use root's properties?  How is this different from simply switching to the root user by using "su"?

---

