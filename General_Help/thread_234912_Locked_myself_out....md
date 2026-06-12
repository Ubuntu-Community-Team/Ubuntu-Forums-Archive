---
title: "Locked myself out..."
date: 2006-08-12
forum: General Help
---

### Post by K_V_B on 2006-08-12
Hello,

I am new to Ubuntu, but not to Linux. Previously I ran Gentoo Linux on my server, and I still run Suse on my desktops. I've alos used RedHat, Slackware and even in a distant past Yggdrasil. I recently got new hardware to replace my old server, and decided to try Ubuntu linux.

Today something happened that never happend before. I locked myself out of my server. :oops: 

This because of a feature that Ubuntu has, that in my opinion has turned out to be a major misfeature, at least on servers: Root is disabled by default. The first user created gets sudo rights. 

The idea of avoiding the necessity of becoming root does have merit. But I wanted to avoid having to do sudo for every action I did on my websites. So I maded /etc/apach2/sites* group owned by www-data, and group writable, and did the same to /var/www. Then I did "usermod -G www-data krist" to add myself to that group. The idea was simple: I would be able to edit the content, and part of the webserver config without having to become root. When I needed to restart apache I would use sudo. So far so good.

But I overlooked that "usermod -G www-data krist" adds me to the www-data group, but removes me from all other groups. One of these groups is the sudo group. So suddenly I can't sudo anymore. On a system with a disabled root password. 

Which means that I now have to do a hard poweroff on my system, carry it upstairs out of my basement to hook up a monitor and keyboard, and boot is in single user mode so I can set a root password. 
At least I hope booting in single user mode will allow me to log in as root without a password, otherwise I will have to use a boot disk. Luckily I haven't yet removed the CD drive from the machine. 

This has become a bit of a rant. But I had gotten quite enthousiastic about Ubuntu the last few weeks, and this is a bit of a put down. I can only conlcude that the "root disabled by standaard" feature is a misfeature, at least for servers. I will ofcourse enable root on this machine as soon as I gain acces to it.

---

### Post by az on 2006-08-12
> **K_V_B said:**
> I can only conlcude that the "root disabled by standaard" feature is a misfeature, at least for servers. I will ofcourse enable root on this machine as soon as I gain acces to it.

What is your issue with using sudo for tasks?

It's certainly more secure than adding a whole bunch of priviledges to another user.


Anyway, boot into recovery mode and you are root.

---

### Post by K_V_B on 2006-08-12
> **azz said:**
> What is your issue with using sudo for tasks?

It's certainly more secure than adding a whole bunch of priviledges to another user.


Anyway, boot into recovery mode and you are root.

I have no issue with using sudo for tasks. I do have an issue with how easy it was for me to shoot myself in the foot though. If you accidentally (as I did) remove yourself from the sudo group you're stuck.

That is why (after booting in to recovery mode) I will enable  root, but try to avoid using root as much as possible.

(And luckily my server is not across the country... Or it would even have been a bigger problem.)

---

### Post by ifokkema on 2006-08-12
- As mentioned, reboot into recovery mode and you're root. Fix the problem through that.
- Use `adduser <username> <groupname>` next time, to add someone to a group. It will not remove you from all others.
- If you're tired of using sudo, try `sudo su -`. You're root until you `exit`.
- If even that it too much for you, read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Hope your future experiences with Ubuntu will be better :)

---

### Post by az on 2006-08-12
> **K_V_B said:**
> I have no issue with using sudo for tasks. 

You do, since you want to circumvent it.  In doig so, you did a dumb thing.

> **K_V_B said:**
> I do have an issue with how easy it was for me to shoot myself in the foot though. If you accidentally (as I did) remove yourself from the sudo group you're stuck.

There are lots of ways to lock yourself out - that has nothing to do with sudo.

Sudo gives you a finer-grained way to manage priviledges.  It also logs all your activities.  And nothing is stopping you from settig a root password and using that.

---

### Post by MacMan on 2006-08-12
> **K_V_B said:**
> The idea of avoiding the necessity of becoming root does have merit. But I wanted to avoid having to do sudo for every action I did on my websites.

Just for your information the command:
```
sudo -s
```
gives you a shell prompt with root privileges. No need to mess with groups. I hope this helps.

Ciao.
-- 
Mac

---

### Post by K_V_B on 2006-08-12
> **MacMan said:**
> Just for your information the command:
```
sudo -s
```
gives you a shell prompt with root privileges. No need to mess with groups. I hope this helps.


I know this does it. But I don't want to be root all the time. I actually want to avoid having to be root to often, which is why I was tweaking the group ownership and permissions of the files relevant to my webserver, and added myself to the www-data group...

---

### Post by K_V_B on 2006-08-12
> **azz said:**
> You do, since you want to circumvent it.  In doig so, you did a dumb thing.

I'm sorry, but I fail to see where using user and group file permissions in a way that controls who can do what is "circumvention". AFAIK the unix file permission system is designed to make some form of fine grained control possible. 

> 
There are lots of ways to lock yourself out - that has nothing to do with sudo.


In 12 years of working with Linux (and other Unices) I have never had this happen to me. That it happens two weeks in to my first foray in the world of Ubuntu does give me the impression that locking oneself out is somewhat easier under Ubuntu.  

> 
Sudo gives you a finer-grained way to manage priviledges.  It also logs all your activities.  And nothing is stopping you from settig a root password and using that.

What I did was set a root password. I've also added my username in to the sudoers file, so this will not happen again. I still think that for servers setting a root password ought to be offered during install, as it is a better default than having the root password unset.

---

### Post by K_V_B on 2006-08-12
> **ifokkema said:**
> - As mentioned, reboot into recovery mode and you're root. Fix the problem through that.
Did that in the meantime, so now I have access again. My server however normally runs in the basement, without a monitor and keyboard atached. I did annoy me that I had to carry my server up from my basement less than an hour after I'd carried it down... :( 

> **ifokkema said:**
> 
- Use `adduser <username> <groupname>` next time, to add someone to a group. It will not remove you from all others.


I wasn't aware you could do this. Maybe I work on Solaris to much...:)

---

### Post by az on 2006-08-12
> **K_V_B said:**
> I'm sorry, but I fail to see where using user and group file permissions in a way that controls who can do what is "circumvention". AFAIK the unix file permission system is designed to make some form of fine grained control possible. 

Circumvention is the wrong word.  I meant to say avoid using sudo.  Being that your problem has nothing to do with the use of sudo, I though you were trying to completely get rid of using sudo, and in doing so, locked yourself out of your system.  

I had never heard of usermod before, and I guess I was somewhat reactionary in answering you.  Sorry.

Had I read more carefully and given you the correct answer as did ifokkema, this conversation would be over by now.

> **K_V_B said:**
> 
In 12 years of working with Linux (and other Unices) I have never had this happen to me. That it happens two weeks in to my first foray in the world of Ubuntu does give me the impression that locking oneself out is somewhat easier under Ubuntu.  

Not so.  I probably would lock myself out of a Solaris box in my first two weeks, too.

> **K_V_B said:**
> 
I still think that for servers setting a root password ought to be offered during install, as it is a better default than having the root password unset.

There were many long debates about this in the early Warty (4.10) days.  The concensus is that the installer should be as simple as possible and the number of questions asked should be minimal.  To set a root password is trivial, once you are installed, for those who do not want to use sudo.

Sudo is a more elegant way to handle priviledge escalation.  It is also very secure and so there is no reason to have a different  policy in the server release than in the desktop version.

---

### Post by Shadyman on 2006-08-28
Hey!

There is a great set of instructions on how to set the root password and how to allow root to log into Gnome at [http://ubuntuguide.org/wiki/Ubuntu_dapper#User_Administration](http://ubuntuguide.org/wiki/Ubuntu_dapper#User_Administration) :-D

---

### Post by videoguy2 on 2008-03-13
Anyone care to submit their candidate for easiest way to lock yourself out?  Here's one way to do so via a single mistaken keystroke.  Where you intend to do 

```
sudo chmod a+w /usr
```

instead do 

```
sudo chmod a=w /usr  
```

It's so easy!  Just neglect to hold down the shift key when entering the '+' character!  :lolflag:  If you are the only user and are unable to su root or have some other back door chances are you will need to reboot into recovery mode.

---

### Post by bodhi.zazen on 2008-03-13
> **MacMan said:**
> Just for your information the command:
```
sudo -s
```
gives you a shell prompt with root privileges. No need to mess with groups. I hope this helps.

Ciao.
-- 
Mac

Consider using ```
sudo -i
```

the -s flag user your user's environment and thus can cause problems if root writes to your user's /home.

-i = root's environment.

(try echo $HOME)

---

