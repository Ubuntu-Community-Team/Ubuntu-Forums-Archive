---
title: "software center broke after installing libdvdread4 Ubuntu 12.04"
date: 2014-06-03
forum: General Help
---

### Post by netgooroo on 2014-06-03
Hey guys, 
as you can see from the title of this thread, I managed to break my software center when I installed libdvdred4. 

It seems like to me as ubuntu "evolves" it gets farther and farther away from it's roots of being simple and "clean" like it used to be back in the days of 9.04 and before. I never used to have issues playing any media at all thanks to mediabuntu and being able to install all the codecs I needed easily. No longer the case. 

Anyway, I would appreciate any help solving this issue. 

***Technical stuff:***

I was not able to play DVD's before and had already installed Libdvdcss to no avail. Then I found a thread talking about lbdvdread4. So, I installed it using this code.. *sudo /usr/share/doc/libdvdread4/install-css.sh* which worked **GREAT** and I can now watch DVD's but, can not get updates. ](*,) 

So again, any help would be appreciated. 
Thanks!

---

### Post by bapoumba on 2014-06-03
Please post the outputs to :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by monkeybrain20122 on 2014-06-03
Well how did you install libdvdread4? if you had libdvdcss2 installed libdvdread4 has to be installed already. What are the error messages?

> It seems like to me as ubuntu "evolves" it gets farther and farther away  from it's roots of being simple and "clean" like it used to be back in  the days of 9.04 and before. I never used to have issues playing any  media at all thanks to mediabuntu and being able to install all the  codecs I needed easily. No longer the case. 

I have never had any problem playing DVDs on a variety of machines I installed Ubuntu on. The maintainer of medibuntu decided that he no longer had the time to keep it up, it had nothing to do with Ubuntu.

---

### Post by netgooroo on 2014-06-03
> **bapoumba said:**
> Please post the outputs to :
```
sudo apt-get update
sudo apt-get upgrade
```



sudo apt-get update gives 
E: Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
 
and suido apt-get upgrade gives 
E: Type '<html><head><meta' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.

and the Ubuntu internal error pop up shows up. However, if I try to "send to help fix the problem" another pop up shows up saying "Could not determine the package or source package name." 


> monkeybrain20122

    Re: software center broke after installing libdvdread4 Ubuntu 12.04
    Well how did you install libdvdread4? if you had libdvdcss2 installed libdvdread4 has to be installed already. What are the error messages?


I tried **SEVERAL** times to play DVD's once I installed libdvdcss2 with no luck. I installed it from the software center not that that matters but, yea.. there ya go. ;)

**Edit:** Also if I try to open software center to edit the sources. it closes before it's able to open all the way.

---

### Post by deadflowr on 2014-06-03
you need to disable the medibuntu repository, as it went dead some time ago.
Open the update manager and go to settings.
Then go to other software and uncheck/remove the lines for medibuntu.
Then close and reload the update manager(click on Check)

---

### Post by monkeybrain20122 on 2014-06-03
Medibuntu is long dead, so not surprising that you are getting errors. So remove medibuntu first. Open software-propreties-gtk (Software & update), go to Other Software, uncheck the medibuntu box and reload. 

For post medibuntu era [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by neyson-v on 2014-06-03
I guess the problem is that you are using medibuntu which is no longer mantained and can cause trouble in your system the best you can do is, remove the package and then the repository
```
sudo apt-get remove libdvdread4
```
remove the repository as explain in this [thread]("http://askubuntu.com/questions/223179/how-to-remove-medibuntu-repository-and-packages")

update
```
sudo apt-get update
```
and now reinstall software-center
```
 sudo apt-get install software-center 
```
now let's talked about Libdvdcss. you could install it by using a repository and thus you would keep it up of date. as indicated [Here]("http://www.videolan.org/developers/libdvdcss.html") you should do this 
open sources.list
```
sudo gedit /etc/apt/sources.list
```
add the repository
```

deb http://download.videolan.org/pub/debian/stable/ /  
deb-src http://download.videolan.org/pub/debian/stable/ /

```
add the key
```
wget -O - http://download.videolan.org/pub/debian/videolan-apt.asc|sudo apt-key add -  libdvdcss
```
update 
```
sudo apt-get update
```
and install the package
```
sudo apt-get install libdvdcss
```
also note that if you use vlc this library will be kept updated as it is part of vlc which is in the official repositories

---

### Post by netgooroo on 2014-06-03
> **deadflowr said:**
> you need to disable the medibuntu repository, as it went dead some time ago.
Open the update manager and go to settings.
Then go to other software and uncheck/remove the lines for medibuntu.
Then close and reload the update manager(click on Check)


> **neyson-v said:**
> I guess the problem is that you are using medibuntu which is no longer mantained and can cause trouble in your system the best you can do is, remove the package and then the repository
```
sudo apt-get remove libdvdread4
```
remove the repository as explain in this [thread]("http://askubuntu.com/questions/223179/how-to-remove-medibuntu-repository-and-packages")



Guys, I appreciate all the help. I **really** do. I figured out that my issue is mediabuntu but, flower, I can not get into update manager..  just like software center and sudo apt-get update/upgrade. None of those work. period..  

neyson-v I already had libdvdcss2 installed and "working". Every time I did a sudo apt-get install or update for libdvdcss2 I would always get the output..  "libdvdcss is already the newest version". I also already had VLC installed and "working" as well. However, it was not able to play any DVD's either. 

All of my media files played just fine..  .MOV, .AVI, .FLV, .MP3, etc..  for whatever reason, I was just not able to watch DVD's. **UNTIL** I installed libdvdread4.

So, I hope that clears things up for everyone. 

Whats the code to remove the mediabuntu repository on the command line?

---

### Post by monkeybrain20122 on 2014-06-03
You can manually remove medibuntu
I don't remember how things were organized in 12.04, so either 
1) ```
gksudo gedit /etc/apt/sources.list
```
and then remove all references to medibuntu, save
then run
```
sudo apt-get update
```

or, if you don't find any entry for medibuntu in /etc/apt/sources.list
```
cd /etc/apt/sources.list.d
ls
```
The "ls" command shows the list of files in the directory /etc/apt/sources.list.d
Delete the files with medibuntu in their names
```
sudo rm medibuntu*
```

Then
```
sudo apt-get update
```

---

### Post by netgooroo on 2014-06-03
> **monkeybrain20122 said:**
> You can manually remove medibuntu


Thanks monkeybrain for the help. Worked like a charm **AND** I am still able to watch DVD's. 

I appreciate the help. :D

---

