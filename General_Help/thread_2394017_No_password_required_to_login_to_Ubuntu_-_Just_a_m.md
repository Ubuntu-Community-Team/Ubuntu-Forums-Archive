---
title: "No password required to login to Ubuntu - Just a mouse click!"
date: 2018-06-11
forum: General Help
---

### Post by colin162 on 2018-06-11
Dear All
I recently set up my computer to boot automatically and removed my password  as I needed to access my computer from abroad.
When I got back and tried to reset it again I encountered a few problems which I solved by logging into Ubuntu (single user mode) and resetting the password.

Now I'm practically back to normal apart from the fact, that at boot up, I'm presented with a login dialog but the password is not required. I can just press login and I'm in. I'm guessing it's something simple but I've played with all the settings in 'System Settings' and can't get it to ask me for my password even though a password is set.

I'm running Ubuntu 16.04LTS
Automatic login is set: OFF
Account type: Administrator

Any ideas appreciated.
Thanks
Colin

[IMG]www.nlasystems.com/tmp/login.jpg[/IMG]

---

### Post by deadflowr on 2018-06-11
Run
```
id
```
is nopasswdlogin listed?

---

### Post by colin162 on 2018-06-11
Yes, ran id and nopasswdlogin is listed

uid=1000(col) gid=1000(col) groups=1000(col),4(adm),5(tty),20(dialout),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),115(nopasswdlogin),128(sambashare)

---

### Post by colin162 on 2018-06-11
Yes that SOLVED it thanks 
 				 					[ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar1276577_9.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=1276577") 				 				 					 						 	[**[COLOR=#C61919][B]deadflowr**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1276577")




 sudo vi /etc/group
and removed the line 'nopasswdlogin:x:115:col'

as mentioned in this link: [https://codeyarns.com/2014/07/03/how-to-disable-automatic-login-in-ubuntu/](https://codeyarns.com/2014/07/03/how-to-disable-automatic-login-in-ubuntu/)

---

### Post by steeldriver on 2018-06-11
Always a bit risky to edit the password / group files by hand - IMHO it's better to use the provided higher-level tools e.g.

```

sudo gpasswd --delete *username *nopasswdlogin

```

If you do want to edit the file manually, at least use `vigr` (or `vipw -g`) to prevent accidental corruption

---

### Post by deadflowr on 2018-06-11
You can mark this thread as solved if you want
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

