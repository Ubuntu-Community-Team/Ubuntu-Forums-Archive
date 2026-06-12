---
title: "mythtv backend unable to set initgroups()"
date: 2005-06-10
forum: General Help
---

### Post by tihisi on 2005-06-10
Hi
I am struggling with setting up mythtv on my ubuntu.
I have come to the point where I want to start "/etc/init.d/mythtv-backend".

I do it as user Mythtv but the error I get is this:

"Starting MythTV server: mythbackendstart-stop-daemon: Unable to set initgroups() with gid 116"

I have googled and found only this: [http://www.pvrguide.no-ip.com/bbs/index.php?showtopic=4920](http://www.pvrguide.no-ip.com/bbs/index.php?showtopic=4920)  

I don't understand which script he means and what group I should add the mythtv user to. Anyone have a sugestion what I should do?

(Have about 1 month of linux experience :) )

---

### Post by tihisi on 2005-06-11
Oki solved that problem. Something with not having the rights to my mysqldatabase. Now I have another error also having to do with these rights I think.

```
When I try to start mysql-setup from user mythtv i get this message:
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2005-06-11 10:15:54.427 Unable to connect to database!
2005-06-11 10:15:54.428 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-06-11 10:15:54.429 Switching to square mode (blue)
Segmenteringsfel
```

I can run it as root. I get the same error when trying to run mythfrontend as mythtv but not as root.
Very confused here..

---

### Post by tihisi on 2005-06-11
Oki solved that problem. Something with not having the rights to my mysqldatabase. Now I have another error also having to do with these rights I think.

When I try to start mysql-setup as user mythtv i get this message:
```

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2005-06-11 10:15:54.427 Unable to connect to database!
2005-06-11 10:15:54.428 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-06-11 10:15:54.429 Switching to square mode (blue)
Segmenteringsfel
```

I can run it as root. I get the same error when trying to run mythfrontend as mythtv but not as root.
Very confused here..

---

### Post by jerrybme on 2005-06-28
[QUOTE=tihisi]Oki solved that problem. Something with not having the rights to my mysqldatabase. Now I have another error also having to do with these rights I think.

When I try to start mysql-setup as user mythtv i get this message:
```

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
2005-06-11 10:15:54.427 Unable to connect to database!
2005-06-11 10:15:54.428 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-06-11 10:15:54.429 Switching to square mode (blue)
Segmenteringsfel
```

I can run it as root. I get the same error when trying to run mythfrontend as mythtv but not as root.
Very confused here..[/QUOTE]


I'm having the same problem, did you ever figure this one out?
Cheers, 
Jerry

---

### Post by jerrybme on 2005-06-28
[QUOTE=jerrybme]I'm having the same problem, did you ever figure this one out?
Cheers, 
Jerry[/QUOTE]
 Never mind, I finally got it working, for some reason the grant priviledge command I did on mythtv user didn't take. Once I redid it, I was able to start the backend db & connect without problem.

---

### Post by lassel on 2005-07-19
I am having the same problems as you guys.

Obviously you solved your problems, but you didn't do a very good job of telling the world excatly what is was you did ....

... I can't figure out what to do  ](*,) 

"Starting MythTV server: mythbackendstart-stop-daemon: Unable to set initgroups() with gid 116"

Other issue:
When I run mythfilldatabase I get an error that it can't find tv_grab_dk. I tried tv_grab_se_swedb too, same error. Is that related? Where is your tv_grab_xxx files placed?

---

### Post by pt123 on 2005-07-20
[QUOTE=jerrybme]Never mind, I finally got it working, for some reason the grant priviledge command I did on mythtv user didn't take. Once I redid it, I was able to start the backend db & connect without problem.[/QUOTE]
 How do you do this ?

Did you have to create another user called mythTV is there anyway to run it as current user?

---

### Post by lassel on 2005-07-20
When you apt-get the mythtv package a mythtv user is automatically created.
The SERVER runs as the mythtv user. This is nice for security reasons and is standard unix procedure.

You can run the frontend as any user. You don't even have to run the frontend on the same machine.

I'm still stuck though :(

---

### Post by Jimmy The Clown on 2005-08-31
Not sure if you still need help but I'll post an answer anyways -- maybe it will help someone else. I read this post many times with the same problems and finally solved them.
To solve the .qt thing, I ran /etc/init.d/mythtv-backend start as the mythtv user. You can get around this supposedly if you copy some text file according to [www.abarbaccia.com](www.abarbaccia.com) guide. The file is in the /home/mythtv directory, but save yourself time and consequences by just running it as mythtv.

If you get that ID thing it is because the mythtv user doesn't belong to the mysql group. There is probably some wonderfully cryptic command to add this mythtv to this group, but in my newbness I simply edited "/etc/group".

So do ```
nano -w /etc/group
```
Then look for the "mysql:x:110" line (number might be different). Change this line to "mysql:x:110:mythtv" and everything should play nice.

-JTC

---

