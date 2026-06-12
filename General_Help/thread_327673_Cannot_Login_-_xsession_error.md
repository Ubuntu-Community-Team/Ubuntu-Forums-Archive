---
title: "Cannot Login - xsession error"
date: 2006-12-29
forum: General Help
---

### Post by WiseSalesman on 2006-12-29
Sorry to bother everyone with this. I've searched all over google and this site and, while I've found many xsession errors, I've never encountered the particular one with which I'm dealing. I'm pretty new to Linux, and really don't know what to do.

As far as I know, my computer was working fine last week. I went out of town for a week, and when I came back and tried to boot into Dapper, I received a message about my session lasting less than 10 seconds, and was directed to look at ~/.xsession-errors for help. Because I've been gone for a week, I have no idea what, if anything, I've changed to cause this error. I am able to login with the GNOME failsafe session, which is how I am able to check the file and post this.

The content of the .xsession-errors file:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "justin"
/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: line 73: ls: command not found
/etc/gdm/Xsession: Executing default failed, will try to run x-terminal-emulator
/etc/gdm/Xsession: line 224: exec: x-terminal-emulator: not found
```

I've tried reinstalling a couple of packages, but it's really just needle-in-a-haystack for me, since I don't even know in what package the error is occurring. The file means very little to me. Ubuntu is currently my only OS, so this has my PC fairly crippled. Can anyone help me? Thanks in advance.

---

### Post by WiseSalesman on 2006-12-29
Update: 

- tried reinstalling both gdm and xsession via terminal from someone's advice. Did not fix the problem.

- despite it saying "ls: command not found" I can easily type ls in a terminal. ls is in my /bin and /bin is in my PATH.

Still feel no closer to solving this problem, and have continued to search with no success. Can't anyone help me?

---

### Post by WiseSalesman on 2006-12-30
Last bump here and then I'll assume no one knows the answer, stop bothering you folks, and just reinstall Windows.

---

### Post by GrumpyBob on 2006-12-30
In my experience the "session lasted 10 seconds" error is usually due to a problem with the file .ICEauthority - rename it to something else in recovery mode, and try logging in again.  (The file has a leading dot in the filename, marking it as hidden).

Robert

---

### Post by WiseSalesman on 2006-12-31
Thanks for responding!

Unfortunately, this didn't work. In a GNOME failsafe session, I backed up my.ICEauthority file onto my desktop, then renamed the original copy. Rebooted, but got the same error upon trying to log into the default session. Logged into the GNOME failsafe session, and realized that the file had recreated itself.

Came online to post the results, and then noticed you had mentioned recovery mode specifically. Booted into recovery mode, navigated to home folder, executed an rm to just get rid of the file altogether, rebooted. Same results as above. 

Damn, this is really getting frustrating. Nothing seems to get me any close to solving this. I really appreciate you taking time to look at this and offer your advice. Do you have any other ideas?

---

### Post by bhupeshdogra@gmail.com on 2007-01-05
i am also having the same problem
ls not found
didnt figure out how to solve 
plz help me out
its irritating

---

### Post by rioghal on 2007-01-05
Just out of curiousity, run the following commands from the failsafe terminal:

ls -l ~/.ICEauthority
ls -l ~/.Xauthority

Does root own either of those files or have the permissions of either file changed? If so, you may be the victim of a problem that is caused by running a GUI app with sudo instead of running it with gksu or gksudo.

More about this problem here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by WiseSalesman on 2007-01-06
I know that my user account owns ~/.ICEauthority , because someone over at Linux forums had me check that when I mentioned this problem. I'm in Windows right now so I can't check the ~/.Xauthority file, but I'll give it a look when I'm back in Dapper.

---

### Post by WiseSalesman on 2007-01-06
Okay, checked it. My user account is justin.

ls -l .Xauthority 

from inside /home/justin returns 

-rw------- 1 justin justin 125 2007-01-06 14:33 .Xauthority

ls -l .ICEauthority

from inside /home/justin returns

-rw------- 1 justin justin 525 2007-01-06 14:33 .ICEauthority

So it seems my user account has permissions for both. :-?  Another lead down the hatch.

---

