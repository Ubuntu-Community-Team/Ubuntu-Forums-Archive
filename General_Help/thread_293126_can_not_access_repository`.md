---
title: "can not access repository`"
date: 2006-11-04
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-04
when I go to Synaptic>Settings>Repository  the repository window flashes quickly then error message "The repository information has changed. You have to click on the "Reload" button for changes to take effect. Well I do that then try 'Settings>Repositories again and get the same message again. over & over & over again. What gives? I am not sure what I was doing when this started (being the **'Dumb Blonde**' that I am) as it was a few days ago I would really like some help with this, Thanks

---

### Post by civetta on 2006-11-04
dunno,

try 

cat /etc/apt/sources.list

to make sure everything is peachy. If you added a new repository recently, try deleting it to see if that's what was causing the trouble. Back up the list first!

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
source list is ok.  Is there some other sudo magic to try? haha!!

---

### Post by taurus on 2006-11-04
How do you know your /etc/apt/sources.list is okay?  Wanna share with us?

```
more /etc/apt/sources.list
```

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
Hi taurus! Here it is::                                     ~$ more /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe
 multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univ
erse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by taurus on 2006-11-04
Open a terminal and see if you can run these two commands.

```

sudo aptitude update
sudo aptitude upgrade

```
If there is an error, just paste it here.

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release.gpg [191B]  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Translation-en_US
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports Release      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Sources           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Sources       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/main Sources 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-backports/multiverse Sources
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Sources
Fetched 4B in 21s (0B/s) 
Reading package lists... Done                         $ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

### Post by taurus on 2006-11-04
Well, everything looks normal to me!  Now, what do you want to install?  ;) 

```
sudo aptitude install <program name>
```

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
I do not want to install any thing now but I still can not access the repository list through synaptic.

---

### Post by taurus on 2006-11-04
Still no luck, getting the same message as before, when you fire up synaptic!  Do you plan to modify your repos using synaptic?  What exactly do you plan to do with synaptic?

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
I guess there isn't much to do at this point, but it is rather annoying that some thing is going on that is not ok. But if I wanted to install Easy or Automatix I would have to do it with the ole terminal. Also will I be able to get updates ok?

---

### Post by taurus on 2006-11-04
I always like the good old terminal.  If you want to install Automatix2, just edit your /etc/apt/sources.list and add that line to it as described here [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29).

You can edit your /etc/apt/sources.list with

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list  <-- make a back up copy just in case you need to recall it...
gksudo gedit /etc/apt/sources.list

```

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
I am sorry to be such a "Pain in the Arse" taurus, but I still do not understand **WHY** I can not access that repo. list through synaptic and when it tells me to click reload, the same 47 things reload over and over etc.

---

### Post by taurus on 2006-11-04
I am not sure why either but you don't have to add a repo using synaptic.  You can always do it from a terminal.  Otherwise, try to reboot and see if synaptic is still acting up!!!

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
yes it still tells me to reload and the repo's window will not open up. It only flashes real quick-like the message to reload and then a repeat over and over, etc. Thanks for your help taurus. you are always willing to help when you can and it is much apreciated! No matter how silly the problem, which I sure can come up with :-k

---

### Post by taurus on 2006-11-04
I guess just use gedit to edit your /etc/apt/sources.list for now.  It's not that bad using a terminal.  And after a while, I am sure you would come to love it!!!  Oh and by the way, blondes always have more fun...  ;)

---

### Post by IusedTObeSOMEONEelse on 2006-11-04
You are so correct on all 4 counts!!!

---

