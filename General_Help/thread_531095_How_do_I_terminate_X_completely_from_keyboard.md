---
title: "How do I terminate X completely from keyboard"
date: 2007-08-21
forum: General Help
---

### Post by maestrobwh1 on 2007-08-21
I am having issues getting my display back from suspend (I use Kubuntu so I guess that complicates things a bit).  I have tried all of the things in this post [http://ubuntuforums.org/showthread.php?t=495826]("http://ubuntuforums.org/showthread.php?t=495826")

So now, rather than hope to have it resume properly and fight that same battle (ever since dapper came out and now gutsy still won't wake properly), I hope at least be able to terminate x completely, get some sort of terminal I can see, where I can restart x and not have to completely reboot.

The computer itself seems to resume, just not the display... 

Waking even causes screen to flicker.  No way to get anything "usable" and the only way to avoid an improper shutdown is:

First: ctrl+alt+F1 (screen just goes black)

Second: ctrl+alt+del (lots of hard drive activity, then the computer reboots - assuming the OS is running shutdown scripts because there is no warning on reboot that any filesystems were unmounted uncleanly)

I can't get to a point at being able to see what I am typing, and was hoping there might be a keyboard shortcut to kill x completley and get me to a terminal, then I could just restart it.

I found this in a post "**You can kill X by opening a terminal, using `su` to switch to root, and then typing `killall X`"** but that means I would have to type in my user/psswd then all of that without seeing.  God Bless Helen Keller, but I am not that talented.

---

### Post by l33t_3lv3n_g33k on 2007-08-21
Ctrl+Alt+Backspace should restart the X-server and bring  you back to a login screen.

---

### Post by maestrobwh1 on 2007-08-25
Excellent!  Thanks.  I thought I remember someone noting that there was a shortcut, but could not find it anywhere when I did a search.

---

