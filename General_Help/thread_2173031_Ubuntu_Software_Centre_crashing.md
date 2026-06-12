---
title: "Ubuntu Software Centre crashing"
date: 2013-09-07
forum: General Help
---

### Post by Utterlybewildered on 2013-09-07
Running Ubuntu 13.04, full installation, and after attempting to install ubuntu restricted extras and in the options deselecting flash player and selecting to install flash player 11.0 instead the computer crashes.  On startup again all looking good except now the Ubuntu Software centre crashes at every attempt to open it, click on the ubuntu software centre icon and it attempts to open and then crashes and disappears, and this is from a fresh startup, nothing else running, nothing else started or opened, just the ubuntu software centre icon clicked on.

Now i can't get to the software centre to see what's happened.

The reason for taking out the more recent version of flash player and installing flash player 11.0 is because flash keeps crashing and have to forcefully switch off the computer and start again.

This comes after today fully installing Ubuntu 13.04 in place of the windows/ubuntu system sharing setup, now things are cranky with the browsers, they crash, firefox and chromium.

Other things all seem to work good except Rhythmbox which crashes when trying to import music.

May be that my computer is too old to handle Ubuntu 13.04 so am considering installing full version of ubuntu 12.04 instead.

Frustrated.

---

### Post by Nico-dk on 2013-09-07
I had a similar problem in 12.04, and I never found out what was wrong. I assume it was some user setting that was screwed up.

Open a terminal and try to start SC as root
```
sudo software-center
```

If that works, try adding a new user, and see if he can get in

```
sudo adduser <username>
```

---

### Post by ajgreeny on 2013-09-07
Whilst not wishing to say anything against the software-centre, it is an application I have used only once to see if I liked it, as I got so used to using synaptic in earlier ubuntu versions.  I decided that I didn't like it and so when it disappeared from the default installation it was the first thing I added and almost always use.

It is so much more flexible that USC and much better at managing packages so can be used to install different versions of packages from the usual, can fix broken packages and much more as well.  See if that will install and run for you and you may also find that you like it better than USC.  Use command ```
sudo apt-get install synaptic
```

---

### Post by Utterlybewildered on 2013-09-07
> **Nico-dk said:**
> I had a similar problem in 12.04, and I never found out what was wrong. I assume it was some user setting that was screwed up.

Open a terminal and try to start SC as root
```
sudo software-center
```

If that works, try adding a new user, and see if he can get in

```
sudo adduser <username>
```
Gave it a try, the same happened, attempted to open and then crash closed.

---

### Post by Utterlybewildered on 2013-09-07
Trying that but it's coming up like this: 

Reading package lists... Done

and cy tree... 0%


and then nothing :(

---

### Post by Bashing-om on 2013-09-07
Utterlybewildered; Hi !

Is your last in reference to ajgreeny's advisement to install "synaptic" ?
```

sudo apt-get install synaptic

```
If so, the package management system may have a problem.
Post back the complete outputs -between code tags -  of terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
And we will have a look at the status.

[INDENT][INDENT]sometimes yes, sometimes not so yes
[/INDENT][/INDENT]

---

### Post by Utterlybewildered on 2013-09-08
From [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update[/FONT][/COLOR]

Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring Release.gpg                  
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release.gpg [72 B]             
Hit [http://archive.canonical.com](http://archive.canonical.com) raring Release                                
Get:2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates Release.gpg [933 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring Release                          
Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports Release.gpg [933 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring Release             
Get:4 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates Release [40.8 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) raring/partner i386 Packages                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Sources                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Sources                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Sources              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main i386 Packages                         
Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports Release [40.8 kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main Sources                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe i386 Packages 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main i386 Packages                     
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_GB              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe i386 Packages        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) raring/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring/universe Translation-en
Get:6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Sources [63.8 kB]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Sources [14 B]
Get:8 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Sources [71.9 kB]
Get:9 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Sources [2,264 B]
Get:10 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main i386 Packages [163 kB] 
Get:11 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted i386 Packages [14 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_GB   
Get:12 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe i386 Packages [144 kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/multiverse Translation-en_GB    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/universe Translation-en_GB
Get:13 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse i386 Packages [3,871 B]
Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Translation-en [77.7 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Translation-en
Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Sources [902 B]
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Sources [14 B]
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Sources [5,134 B]
Get:18 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Sources [1,403 B]
Get:19 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main i386 Packages [565 B]
Get:20 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted i386 Packages [14 B]
Get:21 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe i386 Packages [6,239 B]
Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse i386 Packages [1,345 B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) raring-backports/universe Translation-en_GB
Fetched 626 kB in 4s (148 kB/s)
Reading package lists... Done


and from [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade

[/FONT][/COLOR]Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


[COLOR=#000000][FONT=Ubuntu Mono]
Utterly clueless what any of it means but thankful of your help :)[/FONT][/COLOR]

---

### Post by ajgreeny on 2013-09-08
There are no problems with those two commands and no errors reported, and your system appears to be fully updated, so it looks as if the problem is with the software-centre itself.

As I don't use it personally,I am the wrong one to tell you how to solve the problem, but I will repeat my comment about synaptic.  One other alternative is to purge the software-centre then reinstall it to see if there is a problem with any of the configs for that; just be careful that it does not also remove other packages that are needed for the system to run properly, and if you're not sure about things come back again.  Also remove any hidden folders and files in your home that relate to the software-centre, probably in ~/.config.

---

### Post by Nico-dk on 2013-09-08
Synaptic is a must have.

You could try purging and reinstalling SC.

```
sudo apt-get --purge remove software-center
sudp apt-get update
sudo apt-get install software-center
```

You might have to do the above from a tty:
CTRL + ALT + F1

You can get back  with ALT + F7

---

### Post by Bashing-om on 2013-09-08
Utterlybewildered; 

+1 ^^

On you as to what you want to do.

[INDENT][INDENT]'buntu, it's fixable
[/INDENT][/INDENT]

---

### Post by Utterlybewildered on 2013-09-08
Thanks guys :)

I've done the software centre purge, something worked.......can't find the software centre at all! 

Tried the synaptic but installing didn't work, don't know how to get it separately now at all either :(

---

### Post by Bashing-om on 2013-09-08
Utterlybewildered; Hummm.. something else is going on .

You did 
"sudo apt-get install synaptic" correct ? .. and it did not install .. if that is the case .. we need to look at the status of the package management system. Show us the output -between code tags (#) - of terminal codes ..
```

sudo apt-get update
sudo apt-get upgrade

```

[INDENT][INDENT]the tale will be told[/INDENT][/INDENT]

---

### Post by ajgreeny on 2013-09-08
> **Bashing-om said:**
> Utterlybewildered; Hummm.. something else is going on .

You did 
"sudo apt-get install synaptic" correct ? .. and it did not install .. if that is the case .. we need to look at the status of the package management system. Show us the output -between code tags (#) - of terminal codes ..
```

sudo apt-get update
sudo apt-get upgrade

```
[INDENT][INDENT]the tale will be told[/INDENT]
[/INDENT]


See post #7.  The OP has already given us that info.

---

### Post by Nico-dk on 2013-09-09
> **Utterlybewildered said:**
> Thanks guys :)

I've done the software centre purge, something worked.......can't find the software centre at all! 

Tried the synaptic but installing didn't work, don't know how to get it separately now at all either :(

What about?

```
sudo apt-get install software-center
```

---

