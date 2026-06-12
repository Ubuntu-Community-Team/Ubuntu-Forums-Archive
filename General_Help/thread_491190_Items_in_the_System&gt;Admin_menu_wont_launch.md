---
title: "Items in the System&gt;Admin menu wont launch"
date: 2007-07-03
forum: General Help
---

### Post by moneymike on 2007-07-03
Just installed Ubuntu FF 7.0.4 last night and am totally new to linux. I used root to add my normal username to the group admin. Now some of the items in the Sys>Admin menu wont launch. When I edit the launch path from say gksu users-admin to just users-admin, the program will launch fine. Why is this? and what group should I make myself part of so I have complete control of the system. 

for instance, when I first logged on with my normal username, I wasn't able to edit the date and time setting, I would right click the clock in the bottom right panel, click adjust time and date settings, then it would prompt me for the root password. i type in the root password and then get an error that I am unable to sudo to root and run time-admin. In short, it took me about an hour to figure out how to eventually change the time.

What group do I need to set my user name to so that Ubunutu 'just works'  like they claim its supposed to.

Thanks.

---

### Post by m.musashi on 2007-07-03
In short, you don't do anything. When you install, the first user you create is giving the ability to become "root" while working on someting. You use the "sudo" command to do this or simply type your password when requested. I suspect by changing the  admin group you ended up duplicating something and now it's conflicting. Just undo whatever you did. The default install is set to work just fine. No need to tweak.

You can read more here [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by moneymike on 2007-07-03
yeah thats what every guide ive read says - that the initial user should have access to do whatever. When i logged on as the initial user, half the system>admin menu was missing. It wasnt until I added the initial user to the group admin that I even saw the Users and Groups item in the Sys > Admin menu. Once I added the initial user to the admin group, the Users and Groups item appeared as well as the Synaptic Package Manager in addition to a few other items.

---

### Post by m.musashi on 2007-07-03
This happend the very first time you logged in after installing? If so, I'd say that your install was somehow corrupt. The fact that you would need to modify the admin group in order to see the menu also suggests that the install was not exactly perfect. In any case, this doesn't sound right. If the problems exited at install then I would suggest just doing a new install - less than 30 minutes usually and you'll be good to go. You want to use a different CD though. It's possible the problem is with the burn itself. If the problem occurred after some system changes you can try and backtrack and undo them.

Other than that, I'm afraid I don't have an answer. I guess you could open synaptic (if it's working) and click edit and fix broken. If the problem is due to missing dependencies it should fix them. There is a terminal command for this too but I'm not certain what it is. I don't know if there is a command to check everything and reinstall anything that is broken (not just dependencies).

---

### Post by moneymike on 2007-07-04
yeah i think reinstalling is my best bet for now. even though synaptic will run, I get a msg when it starts that the program is starting without administrative privileges - wtf. 

To answer your question before, yes the very first time I logged on there were only like 5 things in the Sys > Admin menu - I specifically remember the Users and Groups item and the Synaptic item being missing. I then added myself to the group admin while logged in as root after I started a rescue boot or whatever. It was only then that the Sys > Admin menu became populated with all the items - even though some wont run.

One possbility is that I used Expert Mode text install from the alternate cd. I may have messed something up during all the questions about root and then setting up the inital user.

Thanks for the replies and the help - I'm off to reinstall.

---

