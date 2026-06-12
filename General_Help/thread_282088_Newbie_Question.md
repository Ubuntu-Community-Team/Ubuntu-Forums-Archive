---
title: "Newbie Question"
date: 2006-10-22
forum: General Help
---

### Post by IslandGuy on 2006-10-22
First off i would like to appologise in advance if i use the wrong termonology etc.  I a very new to Linux and want to learn, i have no programming background, but keen to learn!!!!

I have recently put Ubuntu on a dell Inspiron 8600, the problem i have is when i want to update the package in Synaptic Package Manager.  It says it wants to download 1- of 5 files.  But every time i do it, it fails, saying the site may be down or i have no internet connection.

I am writting this thread throgh the machine so i have a valid internet connection.  Any. ideas?  i have looked at the sourse.list and changed the preferences within Synaptic Package Manager to universal and multicast

Any help would be appricated!!!

---

### Post by Najand on 2006-10-22
Can you run:
```

more /etc/apt/sources.list

```
and copy and paste the output here?

Then I will help you to arrenge it.

---

### Post by IslandGuy on 2006-10-22
Here is the outut file, thanks for you quick responce!!

deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiversedeb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by Bartender on 2006-10-22
Not sure if [this]("https://help.ubuntu.com/community/Repositories/Ubuntu") will help but try it.

---

### Post by IslandGuy on 2006-10-22
I don't know if i am missing something, but i feel i have done everything on that link, which was supplied.  But i could be wrong!!

Any other ideas

---

### Post by John.Michael.Kane on 2006-10-22
Heres a clean sources.list

Run: ```
**sudo gedit /etc/apt/sources.list**
```

Replace your current list with this one.

```
## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 
```

Run ```
**sudo aptitude update**
```

Followed by

```
**sudo aptitude upgrade**
```

---

### Post by IslandGuy on 2006-10-22
I have copied the new clean source.list and saved, but i think now it is not a problem with the sourse.list.  i think it must be somthing to do with connection to the net.  i can not still seem to log on to the respective repository.  any ideas how i can check this now?

---

### Post by John.Michael.Kane on 2006-10-22
The repositories should be fine.they are working on my end. I'm not sure why you would not be able to download the respective updates.

---

### Post by IslandGuy on 2006-10-22
thanks for your help, i will take the laptop work tomorrow and see if i can download from there.  it might be my network setup.  but all the other machines in the house work fine.  even the Ubuntu machine surfs the net well.

thanks

ps.  if anyone else has any ideas, would appriciate

---

### Post by IslandGuy on 2006-10-23
Took the machine work this morning and downloaded all fine, must have a problem at home with my netwrk config.  Does anybody know what ports i have to have open?

---

