---
title: "Login Screen Cycles - Won't Accept Password"
date: 2012-12-13
forum: General Help
---

### Post by Steve R. on 2012-12-13
I am unable to get past the login screen. It won't accept passwords, the screen momentarily goes black, and then returns to the login screen.

I recently found out that you can use **_CTRL-ALT-F1_** to switch from the login screen to the command line. My password works in that situation and I was able to enter terminal mode. 

I typed in "*startx*" to see what would happen. I received several error messages that pointed to the "*xkeyboard-config*" file being corrupt. 

That would seem to confirm why I could not use the login screen to login, but could login from the terminal mode.

How can this file be fixed? Or, how can "*startx*" be deleted and then reinstalled?

---

### Post by BlinkinCat on 2012-12-13
Hi,

I'm not sure, but this may help -
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Steve R. on 2012-12-13
> **BlinkinCat said:**
> I'm not sure, but this may help -
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)Thanks. I had already tried that, did not work.  The passwords do work from the command line. So problem would have to be in the keyboard configuration file.

---

### Post by steeldriver on 2012-12-13
Hmm.. well if you just switch to a VT with Ctrl-Alt-Fn that leaves the whole Xserver / lightdm running in TTY7 I think - so I'd be surprised if startx worked in that scenario - usually you'd need to manually stop the lightdm service first

Have you checked your .Xauthority file didn't just get messed up? logged in to your VT, try

```
ls -l ~/.{ICE,X}authority
```and report back

---

### Post by Steve R. on 2012-12-13
I didn't see anything. .Xauthority was 0 bytes long. Still got the message "*Keyboard initialization failed.  Missing or incorrect setup for the Xkeybaord-Config*". It occurred to me that this error message itself is a misleading error message as the login screen was just pushed into the background so I was actually starting a second instance.

That's probably going to be it for tonight.

---

### Post by steeldriver on 2012-12-13
OK more important is ownership / permissions - they should be

```

-rw------- 1 user user 2258 2012-12-03 18:29 /home/user/.ICEauthority
-rw------- 1 user user   52 2012-12-03 18:29 /home/user/.Xauthority

```

i.e. owned and writable by 'user'

---

### Post by Steve R. on 2012-12-13
> **steeldriver said:**
> OK more important is ownership / permissions - they should be

```

-rw------- 1 user user 2258 2012-12-03 18:29 /home/user/.ICEauthority
-rw------- 1 user user   52 2012-12-03 18:29 /home/user/.Xauthority

```

i.e. owned and writable by 'user'

Good point, they were owned by "*root*".  I went ahead and corrected the ownership.
I experimented by toggling between "*lightdm*" and "*gdm*", still had the same problem.

---

### Post by steeldriver on 2012-12-13
OK that happens... if they're root owned just delete ('rm') them - they will get regenerated with correct ownership next time you successfully log in to your X session

---

### Post by Steve R. on 2012-12-15
I may have a match. I received the following error message in the file "*.xsession-errors*"
> openConnection: connect: No such file or directory
cannot connect to brltty at :0
mkdtemp: private socket dir: Permission denied

A writeup on this error appeared on [Judson's Notes - Ubuntu login screen loop!]("http://judsonsnotes.com/notes/index.php?option=com_content&view=article&id=699:ubuntu-login-screen-loop&catid=37:tech-notes&Itemid=59"). From what I could tell, my "*libxfce4util.so.6*" was in the correct place, though under the additional sub-directory of "*x86_64linuxgnu*"
I experimented around some, but nothing worked.

I will need to look into this post too: [login loop after 4.10 install - libxfce4util.so.6 not found]("http://forum.xfce.org/viewtopic.php?id=7342")

---

### Post by Steve R. on 2012-12-15
I have achieved **_partial success_** in that I can now login under my wife's account and I get to the Ubuntu desktop.  I did get a bunch of Ubuntu "*internal error messages*". I hope that those will clear-up through further clean-up.  Additionally, when logging into my wife's account, the screen goes nuts for a few seconds.

I still can't directly login into my account. To solve that issue, I plan save my user files under my wife's account, delete myself, and then reinstall myself as a user. For now, I need to take a break and fix some real-world issues.

Essentially, I ended up deleting the packages for the Ubuntu desktop, Lamp, [Xorg]("http://askubuntu.com/questions/143179/startx-doesnt-work"), and [brllty]("http://askubuntu.com/questions/86635/whats-brltty"). I then slowly reinstalled one by one, but that didn't resolve the login issue until I reset the ["*/tmp*"]("http://mihirknows.blogspot.com/2008/06/mkdtemp-private-socket-dir-permission.html") directory's read/writer permissions.

---

### Post by Steve R. on 2012-12-16
I will mark this thread as solved since I can login now.  Still some clean-up work to do. A new clean install might have been faster, but this was quite an intense learning experience. 

If you use phpmyadmin and receive this error message following installation: "*[Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.]("http://stackoverflow.com/questions/5013118/cannot-start-session-without-errors-in-phpmyadmin")*", it can be caused by not allowing your browser to accept cookies from the "*localhost*".  That was my case. Once I specifically enabled cookies, the phpmyadmin login screen appeared. Ironically, the login screen advices the user to have cookies enabled. But that proved difficult since I could not get to the phpmyadmin login screen.

---

