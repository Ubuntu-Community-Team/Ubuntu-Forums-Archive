---
title: "How can I log into root to re-enable my login as Administrator? [Resolved]"
date: 2007-04-30
forum: General Help
---

### Post by bkmangum on 2007-04-30
In my log-in I unchecked Administrator and set to Desktop privileges. Like an idiot I didn't set up another account for administrator. I thought I would be able to do it through root. So I hit Esc at grub then selected recovery. I then typed sudo passwd root and set a password thinking it would now let me log in as root administrator but when  I logged in it would let me log in as root. So somehow I need to log in as a administrator to set myself up as a administrator. I would appreciate any help with this anyone could give me. I'm new to Linux. I know windows fairly well but this is totally new territory for me. Thanks in advance.

---

### Post by craigsharp on 2007-04-30
Just found this out,  I made a backup admin user first.   Since you've already set a password for  root,  go to Applications - Accessories and open up a terminal window.  Then type    "su"  (without "")  enter your password.  then type user-admin       That should launch your User control panel.


If it does'nt work, let me know

---

### Post by craigsharp on 2007-04-30
sorry that command is "users-admin"    users with an s at the end

---

### Post by zvacet on 2007-04-30
Boot in recovery and type

```
adduser your_user_name admin
```



Of course you will replace** your_user_name** with your real user name

No need for sudo,because in recovery you are sudo allready

---

### Post by aysiu on 2007-04-30
More details here of what zvacet's talking about:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by bkmangum on 2007-04-30
Thanx!!! That did the trick. You'll never know how grateful I am for that. Thanks also for the quick replies.

---

### Post by peiserma on 2007-05-03
I ran into the same problem, but the website did not help me.short story is when i tried to addgroup, It told me there was no such group as admin!!!

](*,) 

managed to solve it by creating a new admin group and changing the ID to the last one before the users begin. users begin at 1000, so when I added the group it gave admin an id of 1002. i manually edited the /etc/group so admin was 118. then i added myself back as admin

long story is:  my wife uses the computer also. I wanted a separate account for administrative purpose only. She is not very computer-literate. I love her so much I married her, but she still gets the address bar and the search menu in firefox confused. anyway, that was the motivation behind the changes. 

so i created a new user using the graphical tools. the new user was called admin. then i removed system administration privileges from our account. Next boot i tried to use the new admin account. no dice. I booted into root using recovery mode and noticed there was no such user as admin anywhere, not even in the /etc/group file. After trying various permutations of deluser and adduser with various settings, all to no avail, i hit upon the idea of adding the missing admin group.

That did the trick, but can anyone tell me what happened? very curious. maybe executing

deluser --remove-all-files admin

was what removed the group? At the time I did not realize admin was a group (used to run slackware 15 years ago, but work forced me to switch to windows, so it&#347; been a while), else i guess it would have set off flags.

---

