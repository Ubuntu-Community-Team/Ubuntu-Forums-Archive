---
title: "New User here, Error with Package Manager. Please Help!"
date: 2008-07-02
forum: General Help
---

### Post by wokapowa84 on 2008-07-02
Hi, I'm a new Ubuntu user (Installed last night), and all of a sudden I can't add or remove any new applications.  My guess is that the last thing I tried doing didn't complete or something like that.  Anywho, this is the error message.


Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type '--21:29:09--' is not known on line 1 in source list /etc/apt/sources.list.d/winehw.list, E:The list of sources could not be read.'

I tried finding a similar problem on the forums but they seem like they are pretty user specific.  Also..I apologize if this is in the wrong section, I'm not an avid forum user as either.  Any help would be appreciated.  Thanks alot, so far Ubuntu has impressed me quite a bit!

---

### Post by boblemur on 2008-07-02
hey im prity new to ubuntu, but u could try going into "system > admin > software sorces" and enabeling them all and seeing if it will over write the file that it cannot read,

then try going into package manager and go reload, and see if i can get the package info again from the server... if ur using apt-get install try... sudo apt-get update

hope this helps... but as i said im very new to ubuntu also so sorry if it dosent work

---

### Post by iaculallad on 2008-07-02
Go on to your terminal and issue the commands below one at a time:

```
sudo cp /etc/apt/sources.list.d/winehw.list /etc/apt/sources.list.d/winehw.list.backup
```

```
sudo rm /etc/apt/sources.list.d/winehw.list
```

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by wokapowa84 on 2008-07-02
It worked! Thanks a lot iacullad.  It's pretty cool how fast someone helped out!

---

