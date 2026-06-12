---
title: "Trying to Install vmware server on ubuntu 7.04"
date: 2007-07-12
forum: General Help
---

### Post by celloyd on 2007-07-12
I'm using instructions from here:

[http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

I get hung up where is wants me to edit sources.list by adding the specified line.

I did this command: sudo vi /etc/apt/sources.list

I could not figure out how to add the line.  I don't know what program that opened up.  It appeared to be a terminal window but I could not make any changes to it.  So I closed out of it and started over and then I got this:


[COLOR="Navy"]E325: ATTENTION
Found a swap file by the name "/etc/apt/.sources.list.swp"
          owned by: root   dated: Thu Jul 12 11:14:48 2007
         file name: /etc/apt/sources.list
          modified: YES
         user name: root   host name: chad-desktop
        process ID: 6884
While opening file "/etc/apt/sources.list"
             dated: Sun Jun 10 22:39:44 2007

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/apt/sources.list"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/apt/.sources.list.swp"
    to avoid this message.
"/etc/apt/sources.list" 36 lines, 1892 characters
Press ENTER or type command to continue[/COLOR]

So- I can't modify the sources.list file and I can't delete the swap file.  It's greyed out and does not give me the option to delete it in the file manager....?

I'm stuck.

---

### Post by TheExplorer on 2007-07-12
Dunno about vmware and its peculiarities but try [COLOR="YellowGreen"]**[this]("http://virtualbox.org/")**[/COLOR].

No bugs for me at all in Ubuntu Feisty Gnome Environment.

---

