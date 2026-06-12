---
title: "Installing software from a PPA"
date: 2012-10-30
forum: General Help
---

### Post by gpaper on 2012-10-30
I use a fitbit; a souped up pedometer that syncs an online profile through a base station. Unfortunately the base station needs to be plugged into a computer that is running a software programmer that was written for Windows or Mac. I found out that someone wrote [a linux version]("http://askubuntu.com/questions/162074/how-do-i-configure-libfitbit") of this software.

That's great! If only I knew how to install it.

I run the latest version of Ubuntu but the only way I know how to install software is through the built in Ubuntu Software Center or when companies make really easy links (like Google for installing Chrome).

Would someone be able to get me started? Apparently its also available as a PPA if that makes it easier.

---

### Post by zeroseven0183 on 2012-10-30
Hi gpaper, you can add the libfitbit PPA to your Ubuntu using this command through a Terminal

```
sudo add-apt-repository ppa:cwayne18/fitbit
```then run

```
sudo apt-get update
```to refresh. Then proceed installing libfitbit by

```
sudo apt-get install libfitbit
```

---

### Post by jerrrys on 2012-10-30
The fitbit PPA is only available for Precise 12o4.

---

### Post by gpaper on 2012-10-30
jerrrys: I just confirmed that this is the version I am running.

zeroseven0183: Thanks, but when I opened up terminal and typed in the first command I get:

sudo: add-apt: command not found

---

### Post by jerrrys on 2012-10-30
That should be:

sudo add-apt-repository ppa:cwayne18/fitbit

Also if you notice in the PPA (in blue) "[COLOR=Blue]read about installing[/COLOR]"

[https://launchpad.net/~cwayne18/+archive/fitbit](https://launchpad.net/~cwayne18/+archive/fitbit)

The rest should work fine  :)

---

### Post by zeroseven0183 on 2012-10-30
Wooppps. Missed the hyphen between apt and repository.

Thanks jerrrys for the quick correction.

---

### Post by bogan on 2012-10-31
Should not that be: ```
sudo apt-add-repository ppa:xxxxx
``` ?? 

Chao!,** bogan**.

---

### Post by Cheesemill on 2012-10-31
> **bogan said:**
> Should not that be: ```
sudo apt-add-repository ppa:xxxxx
``` ?? 

Chao!,** bogan**.

It doesn't matter which you use.
The program used to be called apt-add-repository but has been changed to add-apt-repository in 12.10 and newer. However, there is a symlink in place so that you can still use either.
```
rob@raring:~$ ls -lh /usr/bin/*repository 
-rwxr-xr-x 1 root root 7.9K Oct 29 14:00 /usr/bin/add-apt-repository
lrwxrwxrwx 1 root root   18 Oct 29 14:00 /usr/bin/apt-add-repository -> add-apt-repository
```

---

### Post by rmockler on 2013-04-17
I have successfully added the ppa and installed the library libfitbit, but now how do I get the program active to cause it to sync my fitbit device with wi-fi to fitbit.com?

---

### Post by mike_southey on 2013-10-13
> **rmockler said:**
> I have successfully added the ppa and installed the library libfitbit, but now how do I get the program active to cause it to sync my fitbit device with wi-fi to fitbit.com?

I think I am at this point too, now what? reboot?
:confused::confused:

---

