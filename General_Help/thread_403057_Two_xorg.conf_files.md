---
title: "Two xorg.conf files"
date: 2007-04-06
forum: General Help
---

### Post by mgaskell on 2007-04-06
I'm relatively new to Ubuntu. I'm going through a reference book and decided to look at the contents of xorg.conf using vi. This is the initial output that I got:

E325: ATTENTION
Found a swap file by the name "/etc/X11/.xorg.conf.swp"
          owned by: root   dated: Sun Jan 21 19:44:56 2007
         file name: /etc/X11/xorg.conf
          modified: YES
         user name: root   host name: mike-laptop
        process ID: 3667
While opening file "/etc/X11/xorg.conf"
             dated: Thu Feb  1 22:54:10 2007
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/X11/xorg.conf"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/X11/.xorg.conf.swp"
    to avoid this message.
"/etc/X11/xorg.conf" 166 lines, 4463 characters
Press ENTER or type command to continue

Is this a problem? What should I do?

Thanks in advance.

Mike

---

### Post by jimbob on 2007-04-06
First of all if you are going to "just look" at the contents of a file use a command like 'more' or 'cat' from the command line.

It looks like you had vim end improperly or something to get that .swp file although usually it leaves a file with the same name and a ~ character appended.

Obviously the xorg.conf file that is in there now is working or you wouldn't get the X display so go ahead and and delete the .swp file and that message will go away.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

