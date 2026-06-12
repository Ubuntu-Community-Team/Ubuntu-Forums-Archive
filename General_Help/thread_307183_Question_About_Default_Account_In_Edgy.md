---
title: "Question About Default Account In Edgy"
date: 2006-11-26
forum: General Help
---

### Post by pretty colors on 2006-11-26
Can someone help me out here, maybe put my mind at ease?  I've run Breezy and Dapper for a while but I'm still a bit of a newb... so please forgive if this seems like a dunder headed question.

Should I have these entries in my auth.log:

Nov 26 05:55:12 *mymachine* su[4175]: Successful su for *myusername* by root
Nov 26 05:55:13 *mymachine* su[4175]: + ??? root:*myusername*

These show up every time I log on. That second line appears with the + ???.
What are these?  I never noticed them in my Breezy or Dapper. It makes me wonder if my default account runs with more rights than I thought?  Any help would be appreciated.

---

### Post by bapoumba on 2006-11-26
Hi,
I have not been looking into these in details, but I get the same messages on login. My guess is it has to do with setup on boot or login into the session.

I did some commands using sudo, and they got recorded in /var/log/auth.log properly.

As long as you are in the admin group, which is declared in the /etc/sudoers file with :
ALL=(ALL) ALL
priviledge, my guess is that everything is fine.

Does anybody have a deeper explanation ?

---

### Post by pretty colors on 2006-11-26
Thank you for your response bapoumba. Good to know that you have the same entries, and that I didn't accidentally change some setting on install to cause that?

I can also go to System/Administration/Users and Groups, select the root account, properties, and set the password without having to sudo. At least it looks like it--I haven't actually tried clicking apply yet.  Was this possible in previous versions? I was thinking it was fine to run as the initial account because of the locked root/sudo thing, but maybe I should actually set up a more limited account for day to day use? I'm sure I'm misunderstanding all of this.  Input anyone?

Also, do the

Nov 26 05:55:12 *mymachine* su[4175]: Successful su for *myusername* by root
Nov 26 05:55:13 *mymachine* su[4175]: + ??? root:*myusername*

lines indicate that I'm running with more privileges than in previous versions--the *successful su *part, I mean?  

Sorry for being so dizzy.  After all the fretful noob questions, I should mention that the Edgy install went quite smoothly on this bargain laptop. I had been running previous Ubuntu versions on a 500something mhz Celron w/256? meg ram, a weird pci graphics card, and a motherboard that apparently wouldn't allow the onboard video to be disabled. For me, obviously, this Edgy install pretty much RAWKED!  Just have those few questions.

---

### Post by bapoumba on 2006-11-26
You should read about [sudo]("https://help.ubuntu.com/community/RootSudo"). Ubuntu choose not to enable the classical Linux root user, but rather use sudo. The first user can use sudo, because it is in the admin group.
Having another user for day to day use is not, imho, necessary. I eventually made additional users for my kids, and did not put them in the admin group ;)

I just went to the "user and groups" window in the administration menu, and noticed that I was not prompted for a password. This is not the way it used to be, I'll look into this ...

edit : [found a bug]("https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/59946")

---

### Post by pretty colors on 2006-11-28
Hey thanks for following up with the bug-report link bapoumba. I went over there and had a look, but I'm not sure I understood everything... Okay, I think I was able to pick out the relevant posts and maybe understand enough, and understanding helps.

Still wondering what

Nov 26 05:55:12 *mymachine* su[4175]: Successful su for *myusername* by root
Nov 26 05:55:13 *mymachine* su[4175]: + ??? root:*myusername*

is because I'm curious and things like this are part of what have helped me learn the little bit I've learned so far. Is there a way to check it using the 4175 portion? Is the entry just me being put into the administrators group, or  process being handed over or something?

---

### Post by bapoumba on 2006-11-29
Okay, two things :

1- open a terminal. What does your prompt look like ?
If you have **<user_login>@<hostname>:~ $**, the $ sign means you are connected as a regular user. Try **apt-get update** without the sudo, you will be prompted with an error message. Try it with the sudo (**sudo apt-get update**), then apt-get will read your /etc/apt/sources.list file, and check the repositories, because sudo + pwd made your user gain root priviledges.
To be able to use the sudo, a user has to be in the admin group.
If you have **<user_login>@<hostname>:~ #**, the # sign means you are logged as root, wich is not normal for a standard Ubuntu installation. We'll have to look into this further.

2- The System > Administration > Users and Groups thing now.
Are you willing to perform a test ? (I've done it to check).
Create a new user (**sudo adduser <new_user_login>**). Give it a pwd (twice), just hit return and leave blank personnal informations. This new_user, by default, is not in the admin group. Now logout, and login with this new_user. Go to System > Administration > Users and Groups, you'll be prompted with an error message ;)

As far as I understand, with edgy, users in /etc/sudoers file (ie users in the admin group in Ubuntu), can access Users and Groups screen without entering a pwd again, because they have already been identified when they logged in.

For you two lines, I've got them too (and my prompt is $). My guess is it has to do with setup on boot or login into the session. I'll look into it :)

---

### Post by pretty colors on 2006-11-29
Yep, my results are same as yours. Thanks. You are a patient person bapoumba. ;) I guess my install was so easy I kept thinking, Surely I did something wrong. Now on to the fun stuff... customizing and, oh yeah, free software. :mrgreen:

---

### Post by bapoumba on 2006-11-29
Enjoy :)

---

