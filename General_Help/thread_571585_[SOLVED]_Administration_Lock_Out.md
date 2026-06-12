---
title: "[SOLVED] Administration Lock Out"
date: 2007-10-09
forum: General Help
---

### Post by widowmaker on 2007-10-09
Hello to All,

Down to business. I have been running Ubuntu 6.06 (Dapper Drake) LTS. The system is current on all its updates as far as I can tell. I am liking what I see so far. Oh, I am a newbie of Linux. I inherited this CD from a friend of mine and loaded it on an extra PC I had sitting on the shelf.

Anyway, I have been running the Drake for about 2 weeks, getting the feel and playing with the setup and what not and really running right along without any problems to speak of until 2 nights ago.

I was in the users and groups section playing around with adding users to groups and trying various things out, you know how it goes. I was just playing and experimenting. I thought that I had set everything back the way it was when I started messing with it and exited out of the Users and Groups section. I then shut the system down and changed keyboards to one that all the keys worked on and booted backup without incident, so I thought.

Now when I go to system\administration and press on anything in administration that I have to sign into as root/administrator, I get these messages.

Failed to run gdmsetup:
The underlying authorization (sudo) does not allow you to run this program. Contact your system administrator.

Failed to run /usr/bin/gnome-language-selector:
The underlying authorization (sudo) does not allow you to run this program. Contact your system administrator.

It seems whatever I try to run that I have to have root privledges for comes across as a Failed to run??? (whatever) followed by: The underlying authorization (sudo) does not allow you to run this program. Contact your system administrator.

Everything worked fine until I was in the Users and Groups section playing around 2 nights ago. I hope I don't have to reload this system as I like it and have spent some hours on the setup and getting it to where I like it. It would be a shame to scrap it but if I can't login as root to change anything what good is it??

Any help would be appreciated. Please remember that I am new to Linux and really still don't have a clue as to the ins and outs of this system. So , please keep your suggestions and tips to an idiot level of someone learning something new. Just assume that I don't know anything about what you are talking about when you are explaining something in your reply. Please keep in mind that my Linux command line knowledge is zero.

Hope I didn't break it to bad. Thanks for the help in advance.

WidowMaker

---

### Post by zvacet on 2007-10-09
It is seems that you don´t have admin privileges anymore.To correct that **users&groups>select user>properties>chek for admin prrivileges**.If that doesn´t help boot in recovery mode and type

```
adduser username admin
```

---

### Post by widowmaker on 2007-10-10
zvacet,

Just wanted to say thanks for your reply to this forum post. Your suggestion worked half way. I just went through the terminal as su then did the adduser myusername admin. This produced an error saying that the admin group did not exist. So I had to do a addgroup admin first, then adduser myusername admin. Each step processed and said done upon completion. I rebooted and went to system\administration\Users and Groups, the box came up for root password, I entered it and bingo. It let me in with no error messages like I was getting before. 

Thanks to your partial suggestion I get to keep my system that I am liking more and more each day. I am considering this post closed and the problem resolved.

---

### Post by zvacet on 2007-10-10
> Your suggestion worked half way. I just went through the terminal as su then did the adduser myusername admin. This produced an error saying that the admin group did not exist.

That is the reason why I say to you to boot in recovery mode wich you can see in grub.That way you have admin privileges but still you have to add admin goup to user.Anyway,I´m glad you solved your problem.

---

