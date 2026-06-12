---
title: "strange massege when tryng to update..."
date: 2007-08-08
forum: General Help
---

### Post by yehudaco on 2007-08-08
when i do sudo apt-get update   i get this:
yehuda@Mr:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
yehuda@Mr:~$ 
which is also what i get when i try to update/reload synaptic/update maneger...
why, god,why??? :confused:

---

### Post by bapoumba on 2007-08-08
Only one package manager can run at a time. The lock file takes care of it. When running apt-get, please close synaptic.

---

### Post by yehudaco on 2007-08-08
i know that, i'm not trying to use more than1 package manager in the same time, and this is not the error i get..
when i'm trying to update i get:
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
 
and then:
 An error occured

The following details are provided:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

someone??

---

### Post by bapoumba on 2007-08-08
If you are used to apt-get, please run:
```
sudo apt-get clean
```

Then delete the lock file (a new one will be created when needed)
```
isabella@yeti:~ $ **cd /var/lib/apt/lists**
isabella@yeti:/var/lib/apt/lists $ **ls -la lock**
-rw-r----- 1 root root 0 2007-08-08 15:00 lock
isabella@yeti:/var/lib/apt/lists $ **sudo rm lock**
[sudo] password for isabella:
isabella@yeti:/var/lib/apt/lists $ **ls lock**
ls: lock: No such file or directory
isabella@yeti:/var/lib/apt/lists $ **sudo aptitude update**
Get:1 http://archive.ubuntu.com gutsy Release.gpg [191B]
<snip>
Hit http://archive.ubuntu.com gutsy-updates/multiverse Sources                  
Fetched 6887kB in 13s (493kB/s)                                                 
Reading package lists... Done
isabella@yeti:/var/lib/apt/lists $ 

```

And run the update again.

---

### Post by yehudaco on 2007-08-08
thanks alot for your help!!! but still, the the problem presist only get a different form...
now i get this...

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

---

### Post by bapoumba on 2007-08-08
Could you please post your sources.list ?
```
cat /etc/apt/sources.list
```

---

### Post by yehudaco on 2007-08-08
and again - thank you...


yehuda@Mr:~$ cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
yehuda@Mr:~$

---

### Post by bapoumba on 2007-08-08
That's strange, because I can access the repository from my browser.
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/]("http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/")
Can you?

---

### Post by yehudaco on 2007-08-08
yes i think so i get a page with 
 Name                                Last modified      Size  [DIR] Parent Directory                                         -   
[   ] Packages.bz2                        07-Aug-2007 23:15   61K  
[   ] Packages.gz                         07-Aug-2007 23:15   77K  
[   ] Release                             07-Aug-2007 23:24  103  
but i don't know what does that mean...
and i cant find this line in my source list - what is it has to do with this prob?

---

### Post by bapoumba on 2007-08-08
```
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
```
It's this line, you have it fine. I'm not on my feisty computer for now, I cannt check if the repos are ok (they were for me yesterday on that box).

May be something with your internet connection. Is your ISP preventing you from accessing some sites for ex ? I guess you have no proxy on your own network, but do they?

---

### Post by yehudaco on 2007-08-08
no, not really i haven't experienced such sites except the ones that are unavailable for firefox...
i have no idea what it might be..

---

### Post by bapoumba on 2007-08-08
Okay, please try to change http to ftp for the lines with security.ubuntu.com in the sources.list, and run the update again. Other than that, I have no idea (sometimes, there are some timeouts with http protocols that are not handled gracefully, that may be it). Did you experience the problem before?

---

### Post by yehudaco on 2007-08-08
not exactly the error massages i had at the begining were new, the ones that follow i'm not sure but i think i had them... i'm not sure how i got rid of it...
what is the command to edit the source list? i'll try your suggestion...

---

### Post by bapoumba on 2007-08-08
You can use nano, a small text editor that works in the terminal.

```
sudo nano -B /etc/apt/sources.list
```
(the -B option will automatically save a copy of the original file).
Then change the http --> ftp for all the security repositories.
CTRL-O to save the file (same name, hit <enter>)
CTRL-X to exit nano.
```
sudo aptitude update
```
To see if the error is still there.

---

### Post by yehudaco on 2007-08-08
it seems ok now!
do i have to change back the changes?
anyway thank you!!

---

### Post by bapoumba on 2007-08-08
I'm glad to see you got it to work!

Well, I *suppose* there is some proxy, or some_thing_ between your package manager and the repositories that prevents the http protocol to work fine. It can be random. So you may want to try http again in a couple days, see if its ok. Now you know the error and how to fix it :)
Cheers.

---

### Post by Shogun79 on 2007-08-14
Hello,

I'm getting the same problem but with a different message when I try to update. Here is my sources list.

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-proposed restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main universe restricted multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe

 I already tried to change protocol from http to ftp and seemed to work but only partially. Here is the error messeage that i get when I try to sudo aptitude update:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


Please help me out!:(

---

### Post by bapoumba on 2007-08-14
Hello Shogun79, your error message is indeed different. Are you behind a proxy?

---

