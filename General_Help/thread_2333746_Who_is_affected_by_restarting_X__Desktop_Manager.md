---
title: "Who is affected by restarting X / Desktop Manager?"
date: 2016-08-12
forum: General Help
---

### Post by fbird3 on 2016-08-12
Hello, there!
As the title suggests, I am looking for clarification about whether restarting X / the desktop manager of a particular user also affects [all?] other users logged in, instead of only restarting X for the interested user.
I am convinced [correctly...?] that rebooting the system will affect all users, in that all open applications will be terminated.
But, what happens when instead of rebooting, the [super] user only wishes to restart a crashed X server of a particular user...?
Many thanks in advance.

---

### Post by #&amp;thj^% on 2016-08-12
What gets affected by restarting X / Desktop Manager on ubuntu

on systems with systemd (Ubuntu 15.04 and newer)

    Default Ubuntu (with LightDM)

   ```
 sudo systemctl restart lightdm.service

```
    KDE (with SDDM)

  ```
  sudo systemctl restart sddm.service
```

This restarts only the Xorg server, so that other programs,_** which do not require a graphical interface**_, for instance a web server, can continue to work. As well as all mounter file systems (like encrypted ones), all connections to remote hosts etc. do persists in the case of this... instead of the reboot.
So anything requiring a GUI will be closed for that session.

---

### Post by fbird3 on 2016-08-12
Thank you, unknown16, but what I really need to know [and in _**plain english**_] is whether it is possible to **_only_** _**restart X on one user**_ [and _**not**_ globally, for all logged in users].
I do not mind that the user has their graphical interfaces closed, as long as _**that does not happen to all other users**_ _**as well**_.
Good try, though.

---

### Post by #&amp;thj^% on 2016-08-12
I don't know how to put it any plainer.... but restarting X will close all the applications and documents immediately without saving.(For All or Globally)
Except for the running services I already described.
Thought I would give you that much anyway even if you want to get snarky.
Cheers

---

### Post by fbird3 on 2016-08-13
This is my solution. It fits my needs like a glove. I hope future users can also benefit from this post, as I benefited from others' posts over the internet.
It is meant to be of service to common users such as I; savvy users can skip most of it and still learn something new.

Basically, it involves the use of the command 'kill -15 -1' from a terminal session of the user to be affected ['virtual console' or 'tty', is what I mean; not the terminal emulator available on GUI's]; also: **do not use root with this command**! For the experienced user, that's enough information.

I have tested it with a VBox machine and with my 'real' system.
Two user accounts were used [one of them being a member of sudoers group / had access to administrative privileges {but those were **not** used / required}].
The idea was to check whether user1 was affected when the 'solution' was applied to user2 [i.e.: user1 also had their graphical session restarted].
Whilst using a Lubuntu virtual machine worked flawlessly, on the real system I had to 'nudge' it a bit to achieve the desired result [the logging screen did not reappear, but I could get to it via user1]; but it did the job, and that is what matters to me. I will keep on using it as it is.
The procedure was the same, whether on the VBox or not.
1 - log in user1 [normal graphical session], then switch to user2 [now, both users have a graphical session -- do not log out user1...!]
2 - access a terminal [see above; not a terminal emulator on the GUI!] via ctrl + alt + fx [where 'x' ranges from 1 to 6]; to return to the GUI, press ctrl + alt + f7 [or f8, initially]
3 - on the first terminal log in user1; on another terminal log in user2 [now, both users have a graphical session and a terminal session each]
4 - in each terminal type 'who' to get a list of logged users [you will get  4 entries: 2 for each user; each user has a terminal and a GUI session]; both terminals will show the same result
5 - on user2 terminal type 'kill -15 -1' [without the quotes]; there is no need for root access [in fact, **do not use this command with root access**!]
6 - the effect is to return user2 to the initial graphical login screen [their graphical session was terminated], **but user1 graphical session remains unaffected**! To check user1 graphical session even before logging back into user2, press ctrl + alt + f7 [probably]; it should be as you left it before entering 'kill -15 -1' for user2; to return to user2 logging screen press ctrl + alt + f8 [probably]
7 - log in user2 again and check their terminal [which is still running]
8 - repeat the command 'who' on both terminals; now user2 has a **newer** graphical session than user1 [previously, their creation time was almost identical]
9 - return to user1 graphical session with ctrl + alt + f7 [user2 should have their graphical session back with ctrl + alt + f8]
10 = the end.

---

