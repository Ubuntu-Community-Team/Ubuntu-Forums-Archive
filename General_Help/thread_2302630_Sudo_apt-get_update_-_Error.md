---
title: "Sudo apt-get update - Error"
date: 2015-11-11
forum: General Help
---

### Post by jooge on 2015-11-11
I was installing a program via terminal (PPA), [http://www.ubuntumaniac.com/2015/02/soundconverter-215-is-out-install-on.html](http://www.ubuntumaniac.com/2015/02/soundconverter-215-is-out-install-on.html) - after I ran "sudo apt-get update" I was greeted with this error.


```
Reading package lists... Done
W: Duplicate sources.list entry http://archive.getdeb.net/ubuntu/ trusty-getdeb/apps amd64 Packages (/var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_trusty-getdeb_apps_binary-amd64_Packages)
W: Duplicate sources.list entry http://archive.getdeb.net/ubuntu/ trusty-getdeb/apps i386 Packages (/var/lib/apt/lists/archive.getdeb.net_ubuntu_dists_trusty-getdeb_apps_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

So I the logged in as root and ran the "apt-get update" I got that same error again. How can I delete these duplicate sources so I can continue installing my program?

---

### Post by Bucky Ball on 2015-11-12
If you open Software and Updates> Other Software you should see two entries in there for getdeb. Kill one, but be careful. You have the getdeb repo for i386 and for 64bit machines. Which do you need? Probably the amd64 one, but you'd know which. Close and the machine should update automatically. Still an issue?

If it is, open a terminal and post the output file of this:

```
nano /etc/apt/sources.list
```

PS: No need to log in as root to update, and best to avoid logging in as root. Simply open a terminal as your regular user and:
```

sudo apt-get update
sudo apt-get upgrade
```

:)

---

### Post by jooge on 2015-11-12
I ran into a wall, kinda. As you can see I have 3 installed both i386 and for 64bit (dupe of one)


[img]http://i.imgur.com/zLIvqTg.png[/img]


You are correct in saying that I only need the 64bit but I cant seem to figure out how to check which one is what as they all say the same thing :(

---

### Post by howefield on 2015-11-12
Highlight each one in turn and select edit, you should get a clue at the end of the URI field.

Or take them all out and add back the one that you need :)

---

### Post by jooge on 2015-11-13
> **howefield said:**
> Highlight each one in turn and select edit, you should get a clue at the end of the URI field.

Or take them all out and add back the one that you need :)

As you can see all 3 say the same thing, no clue ;) Thats why I am having a hard time telling what is what.

[[IMG]http://8.t.imgbox.com/BGsqxRw0.jpg[/IMG]]("http://imgbox.com/BGsqxRw0") [[IMG]http://3.t.imgbox.com/A8Hmhqpf.jpg[/IMG]]("http://imgbox.com/A8Hmhqpf") [[IMG]http://7.t.imgbox.com/jksBAsiw.jpg[/IMG]]("http://imgbox.com/jksBAsiw")

---

### Post by howefield on 2015-11-13
> **jooge said:**
> As you can see all 3 say the same thing, no clue ;) Thats why I am having a hard time telling what is what.

Well, back to the nuclear option of taking them all out :)

Or open up sources.list and edit accordingly.

```
sudo cp /etc/apt/sources.list ~/Documents
```
```
sudo nano /etc/apt/sources.list
```

Cursor down to the offending lines and remove (or comment out with a # sign at the beginning of the line).

Ctrl +O, Enter and Ctrl +X to save and exit.

---

### Post by jooge on 2015-11-13
Please check your Inbox  [**[COLOR=#990303][B]howefield**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=186490").[**[COLOR=#990303][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=186490") [**[COLOR=#990303][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=186490")

---

### Post by oscarivera9 on 2015-11-13
I would just go with what has been suggested before.  Delete all 3 first, then run sudo apt-get update then add the one that you need after that.
also, I've noticed that sometimes when a particular source is undergoing maintenance, my system will not update if I've got them as one of my sources until about a day or two later, when they complete whatever maintenance they're doing.

---

### Post by jooge on 2015-11-13
Thanks everyone for your help. Its all good now :D

---

