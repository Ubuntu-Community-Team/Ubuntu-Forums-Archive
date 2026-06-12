---
title: "please help"
date: 2007-01-23
forum: General Help
---

### Post by bigearl on 2007-01-23
hello,
i recently just installed UbuntU 6.06 onto my harddrive it it runes fine and everything but im a totall noob at it,very differ from windows, and i downloaded a couple of stuff and the problem is that its .rar, ive searched this topic before posting alot and did what they said to do but maybe im doing it wrong or its for another ubuntu or soemthing but can anyone please give me step by step instructions (include like where to go extactly because im not familar with this at all) on our to extract it from a .rar because i am getting very annoyed and would very much like some help from the pro's

thanks in advance

-BiGEarL

---

### Post by jimbob on 2007-01-23
I'm not at all familiar with this type of file but check this link for instructions on handling .rar.files in linux.

[http://www.cyberciti.biz/faq/open-rar-file-or-extract-rar-files-under-linux-or-unix/](http://www.cyberciti.biz/faq/open-rar-file-or-extract-rar-files-under-linux-or-unix/)

If you are unfamiliar with the command line in linux I can see why it would be a problem.

Why don't you tell us in detail what you did and perhaps someone who has done this before will jump in and help.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by scrooge_74 on 2007-01-23
> **bigearl said:**
> hello,
i recently just installed UbuntU 6.06 onto my harddrive it it runes fine and everything but im a totall noob at it,very differ from windows, and i downloaded a couple of stuff and the problem is that its .rar, ive searched this topic before posting alot and did what they said to do but maybe im doing it wrong or its for another ubuntu or soemthing but can anyone please give me step by step instructions (include like where to go extactly because im not familar with this at all) on our to extract it from a .rar because i am getting very annoyed and would very much like some help from the pro's

thanks in advance

-BiGEarL

If you want to install programs first check if they are in the repositories so you dont have to worry about dependencies or compiling stuff.

You can make the other repositories active so you have tons of programs to try.

---

### Post by lamego on 2007-01-23
Could you be more specific ? What are you trying to do with those .rar files ?

---

### Post by bigearl on 2007-01-23
what else? extract them lol, i did nothign i just need to extract this file can anyone give me sep by step instructions???

---

### Post by bigearl on 2007-01-23
please anyone?

---

### Post by bigearl on 2007-01-23
sorry for tripple post i dunno how it happended

---

### Post by meng on 2007-01-23
Enable extra repositories (multiverse):
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Then in the terminal, type:
sudo aptitude install unrar

Now open the .rar file with the archive manager.

---

### Post by bigearl on 2007-01-23
didnt work man

can anyone help me

---

### Post by meng on 2007-01-23
> **bigearl said:**
> didnt work man
I'm happy to continue trying to help you here. You should elaborate on exactly what didn't work - adding repositories, installing, or running? It's more difficult to offer help if you don't supply the details of the problem.

---

### Post by bigearl on 2007-01-23
lol yeah sorry...ok this i dont get "adding repositories"

---

### Post by scrooge_74 on 2007-01-23
LOL ....dont worry, in your drop down menus in System >administration you have Software preference (mine is in spanish so I dont know if the translation is correct) there you can add repositories (which is from where the system gets its updates or downloads other programs) 

You can do the same from synaptic there is an option to do the same

or you can modify a file call sources.list which is in /etc/apt/ directory

---

### Post by bigearl on 2007-01-23
ok can someone tell me step by step on how to install rar so i can extract my files

please

thanks

---

### Post by scrooge_74 on 2007-01-23
Ok you need to install unrar

But for that you need to enable the multiverse repositories in synaptic

just check what I said in the previous post

EDIT: Once you enable the repositories you have to update the package information, (just click on update)  and then look for unrar 


With that package install you can open .rar files

Once you get the hang of it is very easy to use synaptic of from the command line to use apt-get

---

### Post by bigearl on 2007-01-23
that doesnt explain much for someone who just started ok im in software preferences and i clicked add then custom what now whats the line i put in there??or where do i go?

---

### Post by scrooge_74 on 2007-01-23
Ok, go to System > Administration > Synaptic package manager

Then go in the top bar to Configuration > Repositories

Then scroll down looking  for lines that says binaries (multiverse) and binaries (universe), check the picture.

click on those repositories to add them

after you have to update or reload (green arrows)

then you can scrool down until you find unrar or search for it.

Then right click mark for installation 

Apply

---

### Post by sloggerkhan on 2007-01-23
OK, here's step by step:

Menu path:
System>Administration>Software Sources
On the Tab [Ubuntu 6.10]
Click on the multiverse check box. (You may wish to enable more for later. The main reason they are all off is differentiating open source and binary software, as well some US Laws)

Then:
System>Administration>Synaptic
Click the "Search" buton.
Type in "unrar"
Click the checkmark next to it.
Click apply.

---

### Post by bigearl on 2007-01-23
ok i think i ddi this all ,how do i use it? just right click and extract?

---

### Post by scrooge_74 on 2007-01-23
Yep, or just double click

---

### Post by bigearl on 2007-01-23
not working thnaks for ur help anyways...i tried using ark but i get this error "The utility unrar is not in your PATH.
Please install it or contact your system administrator."

---

### Post by scrooge_74 on 2007-01-23
Ok, did you add the repositories?

If you did, then open a terminal window and type 

sudo apt-get update

then type sudo apt-get install unrar

That should do it

---

### Post by bigearl on 2007-01-23
from writing first line in terminal

```
Get:1 http://ca.archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://ca.archive.ubuntu.com dapper-updates Release.gpg [191B]
Get:3 http://ca.archive.ubuntu.com dapper-backports Release.gpg [191B]
Hit http://ca.archive.ubuntu.com dapper Release
Hit http://ca.archive.ubuntu.com dapper-updates Release
Hit http://ca.archive.ubuntu.com dapper-backports Release
Hit http://ca.archive.ubuntu.com dapper/main Sources
Hit http://ca.archive.ubuntu.com dapper/restricted Sources
Hit http://ca.archive.ubuntu.com dapper-updates/main Packages
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-updates/main Sources
Hit http://ca.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://ca.archive.ubuntu.com dapper-backports/main Packages
Hit http://ca.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://ca.archive.ubuntu.com dapper-backports/universe Packages
Hit http://ca.archive.ubuntu.com dapper-backports/multiverse Packages
Get:4 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:5 http://archive.ubuntu.com dapper Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://archive.ubuntu.com dapper Release
Get:6 http://wine.budgetdedicated.com dapper Release.gpg [191B]
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://wine.budgetdedicated.com dapper Release
Err http://wine.budgetdedicated.com dapper Release

Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Get:7 http://wine.budgetdedicated.com dapper Release [745B]
Ign http://wine.budgetdedicated.com dapper Release
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Ign http://wine.budgetdedicated.com dapper/mai Sources
Err http://wine.budgetdedicated.com dapper/mai Sources
  404 Not Found
Fetched 941B in 0s (1017B/s)
Failed to fetch http://wine.budgetdedicated.com/apt/dists/dapper/mai/source/Sources.gz 404 Not Found
W: GPG error: http://wine.budgetdedicated.com dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it
```

second one

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by scrooge_74 on 2007-01-23
Do you have synaptic running, forgot to mention you can not have both of them running at the same time

i see you have basically everything enable in the repositories

EDIT: You can also update your system this way

after the sudo apt-get update

the command 

sudo apt-get upgrade 

will install new versions of any package you have installed that has been udated

---

### Post by bigearl on 2007-01-23
ok the first code in etrminal worked
but  second one i get this ****

```
Reading package lists... Done
Building dependency tree... Done
Package unrar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package unrar has no installation candidate

```

---

### Post by scrooge_74 on 2007-01-23
check that this repositories were enable in synaptic
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted

and any other multiverse repository

---

### Post by bigearl on 2007-01-23
uhh i dont understand where the hell i fidn it im in that synaptic thingy in software peferences and i dont see that at all

now i get this in terminal after writing second code thingy

```
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by scrooge_74 on 2007-01-23
in the preferences it says repositories

Maybe this will help

[https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/synaptic.html](https://help.ubuntu.com/6.06/ubuntu/desktopguide/C/synaptic.html)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by bigearl on 2007-01-23
i know how to do that but ur not makign sense to me lol sorry im retarded i know but i just really wanna extract this files lol

---

### Post by bigearl on 2007-01-24
can anyone else help me extract rar files on ubuntu 6.06 drapper please i really need this

thanks

---

### Post by bigearl on 2007-01-24
anyone?

---

### Post by scrooge_74 on 2007-01-24
Hi again, try and see if you can see unrar as a package inside synaptic, if it is there installed if is not then the repositories are still not installed sorry

---

### Post by bigearl on 2007-01-24
i see..."unrar-free" is installed

---

### Post by scrooge_74 on 2007-01-24
ok then you should be able to open rar files

try in a terminal window the command either

man unrar-free

or 

man unrar

so you know the options for using the program

which probably will lead you to the command unrar -e the name of the file you want to unpack

---

### Post by bigearl on 2007-01-24
i got this

```

UNRAR-FREE(1)                                                    UNRAR-FREE(1)

NAME
       unrar-free — extract files from rar archives

SYNOPSIS
       unrar-free  [-xtfp?V]   [--extract]   [--list]   [--force]  [--extract-
       newer]    [--extract-no-paths]    [--password]    [--help]    [--usage]
       [--version] ARCHIVE  [FILE ...]           [DESTINATION]

DESCRIPTION
       unrar-free is a program for extracting files from rar archives.

OPTIONS
       These  programs  follow  the  usual  GNU command line syntax, with long
       options starting with two  dashes  (‘-’).   A  summary  of  options  is
       included below.

       -x   --extract
                 Extract files from archive (default).

       -t   --list
                 List files in archive.

```

---

### Post by bigearl on 2007-01-24
any help?

---

### Post by reclusivemonkey on 2007-01-24
> **bigearl said:**
> anyone?

I'm not sure whether its "unrar" or just "rar" in apt. I'm not at home now, so I can't check, but I am pretty sure all I did was;

```

sudo apt-get install rar
rar -e *rar-archive.rar*

```

---

### Post by bigearl on 2007-01-24
tried both and they both dont work

got this for fist one

```

Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

```

and for the second just invaid command

---

### Post by reclusivemonkey on 2007-01-24
> **bigearl said:**
> tried both and they both dont work

got this for fist one

```

Reading package lists... Done
Building dependency tree... Done
Package rar is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rar has no installation candidate

```

This implies rar is not available in your package lists. I am running Edgy and I have added a fair few repositories, so it may be that my rar package will not be available for Dapper. Have you looked for a rar .deb for Dapper?

[QUOTE=bigearl;2058149]and for the second just invaid command

Of course. If you had no package to install then of course you won't be able to run the command.

---

### Post by reclusivemonkey on 2007-01-24
> **bigearl said:**
> i got this


Try

```

unrar-free -x *your-archive-name.rar*

```

---

### Post by bigearl on 2007-01-24
ok then where can i get the package?

---

### Post by bigearl on 2007-01-24
and how i install

---

### Post by scrooge_74 on 2007-01-24
> **bigearl said:**
> i got this

```

UNRAR-FREE(1)                                                    UNRAR-FREE(1)

NAME
       unrar-free — extract files from rar archives

SYNOPSIS
       unrar-free  [-xtfp?V]   [--extract]   [--list]   [--force]  [--extract-
       newer]    [--extract-no-paths]    [--password]    [--help]    [--usage]
       [--version] ARCHIVE  [FILE ...]           [DESTINATION]

DESCRIPTION
       unrar-free is a program for extracting files from rar archives.

OPTIONS
       These  programs  follow  the  usual  GNU command line syntax, with long
       options starting with two  dashes  (‘-’).   A  summary  of  options  is
       included below.

       -x   --extract
                 Extract files from archive (default).

       -t   --list
                 List files in archive.

```

you have unrar installed did you try uncompresing the file?

---

### Post by reclusivemonkey on 2007-01-24
> **bigearl said:**
> and how i install

You've already installed it. That's why when you typed

```

man unrar-free

```

you got the manual.

---

### Post by bigearl on 2007-01-24
no sir....dont even know what that is :D

---

### Post by scrooge_74 on 2007-01-24
try unrar-free -x  the name of the file you want to open

---

### Post by bigearl on 2007-01-24
kevin@kevin-desktop:~$ unrar-free -x CD_for_Mom.part1.rar
unrar-free: invalid archive 'CD_for_Mom.part1.rar': Bad address
Usage: unrar-free [OPTION...] ARCHIVE [FILE...] [DESTINATION]
Try `unrar-free --help' or `unrar-free --usage' for more information.

lol the name is gay but i dunno why he called it that and it has 7 parts to it btw

---

### Post by bigearl on 2007-01-24
any help?!!?!

---

### Post by scrooge_74 on 2007-01-24
It seems you still need to give the destination for the file after 

unrar-free -x CD_for_Mom.part1.rar   you should give a folder as your destination for the files

---

### Post by bigearl on 2007-01-24
so like unrar blah file name then like desktop?

---

