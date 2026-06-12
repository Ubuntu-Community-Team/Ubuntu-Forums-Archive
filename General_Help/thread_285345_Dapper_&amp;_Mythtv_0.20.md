---
title: "Dapper &amp; Mythtv 0.20"
date: 2006-10-26
forum: General Help
---

### Post by Lester_Burnham on 2006-10-26
Hi,

I'm fairly new to Ubuntu & Mythtv. I've been playing for months chipping away and getting nowhere, but learning a lot on the way.
I'm probably more familiar with Mythtv than Ubuntu after having run it before in knoppmyth.

I would like to thank **superm1** for the repositories he setup, they are a great help.

So, I tried installing Mythtv 0.20 last night using the trial and error method :). (try everything until nothing works anymore)

After a few tries as different users and viewing the output of terminal, I finally worked out that Mysql wasn't installed. Unistalled myth stuff again and installed Mysql then myth and voila!
Mind you I have to run it as root, but I do get TV working, no probs.

I normally use abarbaccia's or hyams home, as a guide on what to install as which user, but abarbaccia's site is down at the moment.

**Questions: **
1. When installing I just use a current user (not mythtv) and install using sudo?
2. Mythtv user was created, but doesn't have a GUI login, so do I run Mythtv in my login?
3. Mysql password on setup...do I leave it blank and add security later? (read mysql page)
Plus I don't see the myphpadmin screen when typing in local host in the browser to change the root password as in Hyams guide.
4. Mythtweb obviously has permission problems too, not letting me log in...see.htaccess file blah blah.

I'm so close now!

Any help appreciated greatly,
Lester

---

### Post by superm1 on 2006-10-26
> **Lester_Burnham said:**
> Hi,

I'm fairly new to Ubuntu & Mythtv. I've been playing for months chipping away and getting nowhere, but learning a lot on the way.
I'm probably more familiar with Mythtv than Ubuntu after having run it before in knoppmyth.

I would like to thank **superm1** for the repositories he setup, they are a great help.

So, I tried installing Mythtv 0.20 last night using the trial and error method :). (try everything until nothing works anymore)

After a few tries as different users and viewing the output of terminal, I finally worked out that Mysql wasn't installed. Unistalled myth stuff again and installed Mysql then myth and voila!
Mind you I have to run it as root, but I do get TV working, no probs.

I normally use abarbaccia's or hyams home, as a guide on what to install as which user, but abarbaccia's site is down at the moment.

**Questions: **
1. When installing I just use a current user (not mythtv) and install using sudo?
2. Mythtv user was created, but doesn't have a GUI login, so do I run Mythtv in my login?
3. Mysql password on setup...do I leave it blank and add security later? (read mysql page)
Plus I don't see the myphpadmin screen when typing in local host in the browser to change the root password as in Hyams guide.
4. Mythtweb obviously has permission problems too, not letting me log in...see.htaccess file blah blah.

I'm so close now!

Any help appreciated greatly,
Lester
Lester,

For installing, you will use the current user with sudo rights, and install using sudo.  Just be sure to install mysql-server before installing myth.

You are correct, during installation, a mythtv user is created.  This user is typically the user that runs the backend process, and if this is a frontend only machine, also the frontend process.  If this is a desktop that you want to use for a backend, frontend, and for day to day usage, you will run the frontend as your currently logged in user.

As for mysql permissions, you are welcome to secure the root user on your server however you would like.  The mythtv user for mysql has a randomly generated password that is used.   This information will be stored in /etc/mythtv/mysql.txt after you first install mythtv-database.

If you want to install phpmyadmin, the order you do things is sort of important.  Be sure apache is installed before installing phpmyadmin.

The mythweb folder permissions should be right, but you will need to modify /etc/mythtv/mythweb-htaccess.conf to reflect your password listed in /etc/mythtv/mysql.txt.  Unfortunately, this update didn't make it in in time for edgy release.

I'd appreciate if you could look at the wiki page that I have created, and add any complications that you ran into that aren't already covered about this on a seperate page and link to it from the main mythtv wiki page below.  I'll be updating the page and placing them in the appropriate location in the next coming weeks as more and more problems crop up for people.

[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)

---

### Post by Lester_Burnham on 2006-10-26
Hi superm1,

I'll help out any way I can, as I'm sure to find the newbie hiccups that you're looking for :)

It's Backend/Frontend combo for now.
What you said is very clear. I'll unistall Mythtv tonight and try doing it the right way.

Thanks again,
Lester

---

### Post by Lester_Burnham on 2006-11-15
Hi superm1,

Me again :)

I've been playing heavily lately and have moved to a fresh install of Edgy. I'm following your tutorial to the letter, except for lirc, as I found hexions tutorial better suited to my remote type. I'll post my findings from a newbies point of view to the wiki as soon as I'm finished.

Can you also help with this please if possible:
------------------------------------------------------
Hi,

Thanks for a great howto....

I'm using a Dvico USB Remote FusionHDTV.
I was having trouble with other tutorials, because they didn't have the same driver options as your method.
eg: USB Devices > dvico

Anyway, I've got it working and need some help on what to enter into the startup files to get it to start at boot.


```
sudo /usr/sbin/lircd --driver=dvico --device=/dev/hiddev0
```
-------------------------------------------------------------
Thanks,
Lester

---

### Post by superm1 on 2006-11-16
Lester,

I'm sorry, but i'm not sure about how the init scripts install when going from source.  Installing a debian package sets up a lot of special init script stuff and several files that aren't normally in /etc/lirc.  Once I get a lirc 0.8pre2 package assembled and hexion's fix in there, I can help you.  Sorry!

---

### Post by kamilczauz on 2006-11-16
superm1,

I installed mythtv on my ubuntu 6.06 with mythtv 0.18.

Everything works fine now, after some tweaking and stuff.

I was just wondering if theres an easy way to upgrade to 0.20?
I also cant get games to work... when i click on mythgames, it tells me i have the wrong mame installed.... current mame installed is 1.0xxx... mythtv site says it should be 0.98 for mythtv version 0.18.  Thats one of the main reasons i want to upgrade to 0.20 and also that its probably a lot better than 0.18

A quick tutorial will be very helpful.

Thanks,
Kamil

---

### Post by superm1 on 2006-11-16
Kamil,

I haven't finished porting the edgy howto to dapper to cover any rough edges, but the edgy howto should work for the most part at this page:

[http://help.ubuntu.com/community/MythTV](http://help.ubuntu.com/community/MythTV)

---

### Post by kamilczauz on 2006-11-16
superm1,

Thanx.  Ive seem that tutorial, its great.  But i dont see any tutorial for an upgrade.  I dont know about the repositories for edgy, but for dapper the only mythbackend and frontend are version 0.18 and thats what i used to install my system.  I dont know how to download the binaries from the mythtv site and compile and intall them.

Thanks again,
Kamil

---

### Post by Lester_Burnham on 2006-11-16
Hi,

Maybe you could change all your repositories to edgy, where it says Dapper and backup mysql.
If you're using superm1's myth repositories, you can replace them with the ubuntu ones for edgy as far as I understand.
But I'm sure superm1 will answer your question with confidence :)

Thanks superm1...
I just found the other version of the tutorial heaps easier for my remote, as I couldn't find anywhere, what driver I should use. I then went to lirc remote support and it said dvico, none, dvico in the table.
I have made a launcher on the desktop that starts it. So, maybe I can call it dvico and put it in sbin and run it as root at start up.

Lester

---

### Post by superm1 on 2006-11-16
I completely thought I was replying to a different post......

Okay what i was going to say for this post.

For dapper repositories that I've brought 0.20 onto, follow this page:
[https://help.ubuntu.com/community/MythTV/Install/Server/Dapper/Repositories](https://help.ubuntu.com/community/MythTV/Install/Server/Dapper/Repositories)

Just be sure to backup your mysql database prior to the upgrade in case something doesn't go smoothly.

---

