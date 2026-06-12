---
title: "Help w/bash script opening window and closing xdotool"
date: 2016-07-04
forum: General Help
---

### Post by silverspr on 2016-07-04
HI
I'm currently using Keepass, password manager which is a graphical gui only.  I'm session and startup w/two scripts, one running the application and the second using xdotool to minimize it once it opens (the application does not have a minimize parameter).  When I run each script separately, they both work, but when I try combine it into one script I can't get it to work:


#!/bin/bash
export DISPLAY=:0.0
 
/usr/bin/keepass2 "/home/user/odrive-agent-mount/Google Drive/mypassw.kdbx" -pw:"xxxxxxx"

sleep 7

/usr/bin/xdotool windowminimize $(/usr/bin/xdotool search --name "mypassw.kdbx - KeePass")


exit

any help appreciated

---

### Post by TheFu on 2016-07-04
Have you seen **WMCtl **yet? I've never used it.  Found this: [http://ubuntuforums.org/showthread.php?t=1958535](http://ubuntuforums.org/showthread.php?t=1958535) with some notes about why some xdo stuff doesn't work for all events. It is the WM that receives window events, not the application, BTW.

But having the credentials for a password database in a file just seems so very wrong. OTOH, it is your machine.

---

### Post by Keith_Helms on 2016-07-10
The problem is you're running the keepass command in the foreground, which means the script does not advance past that command until it completes, i.e. you've choosen exit from the keepass file menu.

The simple fix is to run the command in the background.  Add an amphersand after the first command.

```
/usr/bin/keepass2 "/home/user/odrive-agent-mount/Google Drive/mypassw.kdbx" -pw:"xxxxxxx" &
```

---

### Post by silverspr on 2016-07-12
...gosh darn how many hours I tinkered for not and all for an ampersand...
thank you thank you
s

---

### Post by vasa1 on 2016-07-12
> **silverspr said:**
> ...gosh darn how many hours I tinkered for not and all for an ampersand...
thank you thank you
s
If you're happy with the solution, you can marked your thread [SOLVED] like this: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Thanks!

---

### Post by TheFu on 2016-07-13
> **silverspr said:**
> ...gosh darn how many hours I tinkered for not and all for an ampersand...
thank you thank you
s

Sorry I missed that. I was fixated on what a bad idea  putting passwords into a script is and missed the need to detach the GUI program from the shell process. Sorry.

---

