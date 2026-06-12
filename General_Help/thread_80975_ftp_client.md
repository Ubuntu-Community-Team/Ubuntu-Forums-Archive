---
title: "ftp client?"
date: 2005-10-23
forum: General Help
---

### Post by wrynn on 2005-10-23
i have the standard sources.lst that comes with 5.1... and i want to install an ftp client

---

### Post by XDevHald on 2005-10-23
[quote=wrynn]i have the standard sources.lst that comes with 5.1... and i want to install an ftp client[/quote]

You can install gftp by apt-get install gftp which is a great application to use :)

---

### Post by jeremyk on 2005-10-23
gFTP

---

### Post by aysiu on 2005-10-23
Konqueror works for me... even in Gnome, believe it or not.

---

### Post by Breaks on 2005-10-23
I'm another one that has to say go with gFTP, it's the only one i use and it works absolutely great. Very easy to understand and configure.

---

### Post by wrynn on 2005-10-23
[QUOTE=Steve Myers]You can install gftp by apt-get install gftp which is a great application to use :)[/QUOTE]

im assuming that isnt in the default package list?

---

### Post by LorenzoD on 2005-10-23
Just to give you alternatives: i recommend ncftp. It's a command-line ftp client that is far better than most others. I would keep that one as a handy backup in case gFTP keeps crashing on you.

If you're really, really lucky you may even be able to use Nautilus. It was working quite well for me in Gnome 2.8 and 2.10, but it seems to be problematic again.

---

### Post by Breaks on 2005-10-23
[QUOTE=wrynn]im assuming that isnt in the default package list?[/QUOTE]

Yes it is, you have to type:

```

sudo apt-get install gftp-gtk

```

as it has to install a few files as well as the actual program itself etc.. etc..

---

### Post by wrynn on 2005-10-23
i had to go into synaptic and add the community maintained repository

is there a way to make gnome refresh the menu so that the newly installed app shows up there?

---

### Post by LorenzoD on 2005-10-23
It should do that automatically. gFTP should be under Applications->Internet.

---

### Post by daditlefsen on 2005-10-23
I also tried to install the ftp client but i got this error:
[PHP]E: Kunne ikke åpne låsefila /var/lib/apt/lists/lock - open (13 Ikke tilgang)
E: Kan ikke låse listemappa
[/PHP]

In english:
[PHP]
E: Could not open lockfile  /var/lib/apt/lists/lock - open (13 error)
E: Could not open lock listfolder
[/PHP]

Could anyone help me ?

---

### Post by LorenzoD on 2005-10-23
Are you doing an apt-get update or something? This might be happening in the background as a part of a cron job. You could check the output of ps ax.

If you are sure you're not you probably have a stale lock file. In that case sudo rm /var/lib/apt/lists/lock

---

### Post by Riverside on 2005-10-23
Don't forget ordinary command line ftp, which is installed by default.

anthony@trafford:~$ ftp
ftp> quit
anthony@trafford:~$

---

### Post by brentoboy on 2005-10-23
I personally use nautilus.

ctrl+L (show location in the address bar, instead of buttons)

set your location to  [ftp://yourwebserver.com](ftp://yourwebserver.com)

it will let you log in, and you can surf your ftp site like you do your file system.

easy and you dont have to install anything extra
-b

---

