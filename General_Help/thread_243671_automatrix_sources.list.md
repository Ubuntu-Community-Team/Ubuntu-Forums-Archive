---
title: "automatrix sources.list"
date: 2006-08-25
forum: General Help
---

### Post by dta on 2006-08-25
ok, i am new to this, and i dont know what i am doing. i installed dapper drake, and all is good. now i get the base sources.list from here and all is fine, and then i install automatrix and accidently hit cancel and it changes my sources.list and i dont think thats a big thing right, since its a new install. so its good and all and start choosing what i want to install and such. and all is good, and i wanted to install mainly wine so i can play wow, and have a java program so i can see stuff on youtube, and i still havent been able to do that. so i guess i have the sources.list from automatrix, is that bad? 
also, i had wine installed before automatrix, is that ok also? 
so i visit a webpage and it still says i need a java player or what have you, so whats going on? 
also now that i have done this sources.list change i get this error at the top of my panel bar that says "A error occured, please run package Manager from the right-click menu or apt-get on a terminal to see what is wrong. The error message was:'Error: BrokenCount >0'

so i click on the error thing, its like a orange square, and then it says:
Software index is broken:
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f in a terminal to fix this issue. 

now i am stuck. what do i do? 
i am a newb!! help!!
thanks everyone

---

### Post by bswilson on 2006-08-25
Friend,

You need to restore the original sources.list in order to be able to do other updates.  You should've answered 'No' to the Automatix prompt.  But, hey, too late now for that.  Here's a copy of the original sources.list file.  What you need to do is the following:

1. Copy the following data to your clipboard:

```

deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

2. Next, run this command to open gedit as the root user (you'll need these permissions to overwrite sources.list):

```
gksudo gedit /etc/apt/sources.list
```

3. Paste the stuff from your clipboard over whatever is in that file.

4. Save and exit; you're all set.

---

### Post by dta on 2006-08-25
so i did what you said, and then i ran an update and i got this:

```
 sudo apt-get update
Get:1 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:3 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://security.ubuntu.com dapper-security Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Get:4 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:6 http://us.archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://us.archive.ubuntu.com dapper Release
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://us.archive.ubuntu.com dapper-backports Release
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Sources
Hit http://us.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/universe Sources
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Fetched 6B in 15s (0B/s)
Reading package lists... Done
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

so what do i do now? 
also, do i go back to the automatrix and do the install again? 
i mean it is still on my computer right? so i have to uninstall it or does it override it? 
please help me? i mean im more of a newb than youthink, so i need a know it all holding my every step. hehe.
thanks again!

---

### Post by h00s on 2006-08-25
It looks like you have just appended what bswilson told you insted of clearing whole file and then adding bswilson 'code'.

Clear whole file and then add sources list. Save and close and run sudo apt-get.

---

### Post by dta on 2006-08-25
I did exactly what he told me to do. 
and then i ran the update from the source list that he gave me, and put that in place of the sources.list that i had.
then i ran :sudo apt-get update, and i get that error. 
```
W: Duplicate sources.list entry http://security.ubuntu.com dapper-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

```

thats what i get! what in the world is going on?

---

### Post by dta on 2006-08-26
ok now i just did it again and it went through. 
now what do i do? for the automatrix program? do i have to do it all over again? and when i do that, do i choose the wine program also and that will cover that? 
all i want is to have a wine to play wow, and have automatrix to have the flash player. thats all i want right now.

---

### Post by songo on 2006-08-26
paste here your actual /etc/aptsources.list

---

### Post by dta on 2006-08-26
this is what i have so far. i wont touch anything else for now, since i dont know what i am really doing, so if you all can help me to get Wine working and Flashplayer. 

```
deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://www.getautomatix.com/apt dapper main
```

Thanks all for your help. 
also i dont really understand the sources.list thing. what is it for? whats the main purpose of it. i tried to find a walk through of all the basic computing on linux, like symbols to know, and what to keep an eye out for. 

any help given is greatly appreciated!
Thanks all for your fast response!

---

### Post by h00s on 2006-08-26
What happens when you comment automatix source? Does apt-get update work then?

Try comment it and let us now if it work without that source.
```
change:
deb http://www.getautomatix.com/apt dapper main

to:
## deb http://www.getautomatix.com/apt dapper main
```And just a small tip, it's automatix, not automatrix ;)

---

### Post by dta on 2006-08-26
this is what i get when i do the :sudo apt-get update. Is that good? to me i would think, but what do i know? Also, what do i do now that am done with this, (that is if i am done.) to get installed Wine and a flash player


```
sudo apt-get update Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Get:3 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:4 http://us.archive.ubuntu.com dapper Release.gpg [189B]
Get:5 http://us.archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:6 http://us.archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security Release
Hit http://us.archive.ubuntu.com dapper Release
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper-updates Release
Hit http://security.ubuntu.com dapper-security/main Packages
Hit http://us.archive.ubuntu.com dapper-backports Release
Hit http://archive.ubuntu.com dapper-updates/universe Packages
Hit http://us.archive.ubuntu.com dapper/main Packages
Hit http://us.archive.ubuntu.com dapper/restricted Packages
Hit http://us.archive.ubuntu.com dapper/main Sources
Hit http://us.archive.ubuntu.com dapper/restricted Sources
Hit http://us.archive.ubuntu.com dapper/universe Packages
Hit http://us.archive.ubuntu.com dapper/universe Sources
Hit http://security.ubuntu.com dapper-security/restricted Packages
Hit http://security.ubuntu.com dapper-security/main Sources
Hit http://us.archive.ubuntu.com dapper-updates/main Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Packages
Hit http://us.archive.ubuntu.com dapper-updates/main Sources
Hit http://security.ubuntu.com dapper-security/restricted Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://security.ubuntu.com dapper-security/universe Sources
Hit http://security.ubuntu.com dapper-security/universe Packages
Hit http://us.archive.ubuntu.com dapper-updates/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/main Packages
Hit http://us.archive.ubuntu.com dapper-backports/restricted Packages
Hit http://us.archive.ubuntu.com dapper-backports/universe Packages
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Packages
Hit http://us.archive.ubuntu.com dapper-backports/main Sources
Hit http://us.archive.ubuntu.com dapper-backports/restricted Sources
Hit http://us.archive.ubuntu.com dapper-backports/universe Sources
Hit http://us.archive.ubuntu.com dapper-backports/multiverse Sources
Fetched 6B in 18s (0B/s)
Reading package lists... Done

```

---

### Post by h00s on 2006-08-26
Yes! This is good now. The reason why did it not working is because packages from automatix were conflicting with packages from ubuntu repositories.

Obviously, you can't install automatix that way, but you can install it old fashioned way as described at automatix web page ([http://tinyurl.com/no36j](http://tinyurl.com/no36j)).

Open terminal and type:
```
wget http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
sudo dpkg -i automatix_6.4-6-6.06dapper1_i386.deb
```After that you should have automatix installed and you can install wine, flash and others with automatix.
Let me know if something goes wrong.

---

### Post by dta on 2006-08-29
sorry its been a while, but i was not at work the last two days, and since this is at work, i really didnt want to come to work for this. haha
so i do the two commands that you gave me and this is what shows up!

```
linuxbox@linuxbox:~$ wget http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
--20:00:36--  http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
           => `automatix_6.4-6-6.06dapper1_i386.deb.1'
Resolving www.getautomatix.com... 82.165.194.143
Connecting to www.getautomatix.com|82.165.194.143|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31,564 (31K) [text/plain]

100%[====================================>] 31,564         6.57K/s    ETA 00:00

20:00:42 (6.56 KB/s) - `automatix_6.4-6-6.06dapper1_i386.deb.1' saved [31564/31564]

linuxbox@linuxbox:~$ sudo dpkg -i automatix_6.4-6-6.06dapper1_i386.deb
Password:
(Reading database ... 79257 files and directories currently installed.)
Preparing to replace automatix 6.4-6-6.06dapper1 (using automatix_6.4-6-6.06dapper1_i386.deb) ...
Unpacking replacement automatix ...
Setting up automatix (6.4-6-6.06dapper1) ...
linuxbox@linuxbox:~$

```

looks good to me right? 
now after this, do i have to go to Applications<system tools < automatix and then do what? (if i have to do that in the first place!?)

---

### Post by h00s on 2006-08-29
Yep, that is good. Automatix is now installed and you can start it and install wine from it.

Go to Applications -> System Tools -> Automatix to run.
Follow the onscreen instruction (basically you only need to select wine to install, nothing complicated)

---

### Post by dta on 2006-08-31
ok i did that and chose all the apps that i wanted to get downloaded and now that it has gone through, i cant find the wine app. is there one? or do i just put something that was meant to run on windows and wine will pick it up?

---

### Post by h00s on 2006-08-31
Wine does not install to application menu but you can start wine from nautilus when you right click on some .exe files (there will be displayed "Use Wine" or something like that).
Another way is from terminal like this:
```

wine photoshop.exe

```

But before first run of wine, you must config it. Open terminal and type:
```

winecfg

```

---

### Post by MS_Prisoner on 2006-11-04
> **h00s said:**
> Yes! This is good now. The reason why did it not working is because packages from automatix were conflicting with packages from ubuntu repositories.

Obviously, you can't install automatix that way, but you can install it old fashioned way as described at automatix web page ([http://tinyurl.com/no36j](http://tinyurl.com/no36j)).

Open terminal and type:
```
wget http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
sudo dpkg -i automatix_6.4-6-6.06dapper1_i386.deb
```After that you should have automatix installed and you can install wine, flash and others with automatix.
Let me know if something goes wrong.

Hello.  I just installed Ubuntu (Dapper...for now)!  Dude it was painless!  Anyway, I'm trying to install automatrix now.  I followed the Automatrix site install instructions ([http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29)) and it isn't working for me.  I updated the sources.list...blah.  Then in my terminal I copy pasted:

```
wget http://www.getautomatix.com/apt/key.gpg.asc
```

And the result is:

```
gabriel@MS-Escape:/$ wget http://www.getautomatix.com/apt/key.gpg.asc
--13:52:33--  http://www.getautomatix.com/apt/key.gpg.asc
           => `key.gpg.asc'
Resolving www.getautomatix.com... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]
key.gpg.asc: Permission denied

Cannot write to `key.gpg.asc' (Permission denied).
gabriel@MS-Escape:/$
```

So I tried your way:

```
wget http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
sudo dpkg -i automatix_6.4-6-6.06dapper1_i386.deb
```

But I get:

```
gabriel@MS-Escape:/etc/apt$ wget http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
--13:47:56--  http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
           => `automatix_6.4-6-6.06dapper1_i386.deb'
Resolving www.getautomatix.com... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:47:56 ERROR 404: Not Found.

gabriel@MS-Escape:/etc/apt$
```

So I kept looking and I also found another thread solution:

[HTML]http://ubuntuforums.org/archive/index.php/t-220326.h[/HTML]

He suggested to download some nx fonts...but the link is dead:

[HTML]http://www.nomachine.com/download_fil2.php?Prod_Id=16[/HTML]

I'll keep looking but any of you know a solution, please let me know.  Thank you.

---

### Post by MS_Prisoner on 2006-11-04
> **MS_Prisoner said:**
> Hello.  I just installed Ubuntu (Dapper...for now)!  Dude it was painless!  Anyway, I'm trying to install automatrix now.  I followed the Automatrix site install instructions ([http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.06_i386.2Camd64_.28Dapper.29)) and it isn't working for me.  I updated the sources.list...blah.  Then in my terminal I copy pasted:

```
wget http://www.getautomatix.com/apt/key.gpg.asc
```

And the result is:

```
gabriel@MS-Escape:/$ wget http://www.getautomatix.com/apt/key.gpg.asc
--13:52:33--  http://www.getautomatix.com/apt/key.gpg.asc
           => `key.gpg.asc'
Resolving www.getautomatix.com... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]
key.gpg.asc: Permission denied

Cannot write to `key.gpg.asc' (Permission denied).
gabriel@MS-Escape:/$
```

So I tried your way:

```
wget http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
sudo dpkg -i automatix_6.4-6-6.06dapper1_i386.deb
```

But I get:

```
gabriel@MS-Escape:/etc/apt$ wget http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
--13:47:56--  http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/automatix_6.4-6-6.06dapper1_i386.deb
           => `automatix_6.4-6-6.06dapper1_i386.deb'
Resolving www.getautomatix.com... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
13:47:56 ERROR 404: Not Found.

gabriel@MS-Escape:/etc/apt$
```

So I kept looking and I also found another thread solution:

[HTML]http://ubuntuforums.org/archive/index.php/t-220326.h[/HTML]

He suggested to download some nx fonts...but the link is dead:

[HTML]http://www.nomachine.com/download_fil2.php?Prod_Id=16[/HTML]

I'll keep looking but any of you know a solution, please let me know.  Thank you.

Arggh.  Command should be:

```
sudo wget http://www.getautomatix.com/apt/key.gpg.asc
```

If it doesn't work...just add sudo. Ehhehe.

---

