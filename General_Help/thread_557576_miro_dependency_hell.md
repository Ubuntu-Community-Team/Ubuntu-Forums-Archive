---
title: "miro dependency hell"
date: 2007-09-22
forum: General Help
---

### Post by Darth_tater on 2007-09-22
Over the last few weeks , i have come to *love* miro.  I had to reinstall Ubuntu 7.04 because of a hard drive crash, and now when i try to install miro, i get the below error.


I think this could be solved if i can force ubuntu to downgrade my installed python version?  
somebody  please help me!

miro:
  Depends: python (<2.5) but 2.5.1-0ubuntu3 is to be installed
 Depends: mozilla-dev  but it is not installable
 Depends: mozilla-psm  but it is not installable

---

### Post by p_quarles on 2007-09-22
Ubuntu comes with both Python 2.4 and 2.5, so that is likely not the problem. Try running the following:
```
sudo apt-get install mozilla-dev mozilla-psm
```
This should give you a warning telling you that other packages would need to be removed in order to install these.

In my experience, there's a conflict between Miro and Blackdown Java, so I wouldn't be surprised if that shows up as the problem. Most users don't need that package, so you should be able to get rid of it safely.

---

### Post by Darth_tater on 2007-09-22
i don't fully understand what this means

```
$ sudo apt-get install mozilla-dev mozilla-psm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mozilla-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnspr-dev
E: Package mozilla-dev has no installation candidate

``` 

does that mean i need to install libnspr-dev  ?

also, i tried the Mozilla-psm package seperatly.

```
$ sudo apt-get install mozilla-psm
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package mozilla-psm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libnss3
E: Package mozilla-psm has no installation candidate

```

---

### Post by p_quarles on 2007-09-22
What version of Ubuntu are you using? And which repository are you installing Miro from, Ubuntu's or Miro's?

You could try installing those packages, and then see if the dependency problem clears up, but I still suspect the problem lies elsewhere.

---

### Post by Darth_tater on 2007-09-22
7.04 x32

their repos.


i shall try to install the alternate packages... but look at the original error in my first post...

```
python (<2.5) but 2.5.1-0ubuntu3 is to be installed
```

does that mean miro wants python 2.5 but it wont install because 2.5.1 is installed?

---

### Post by p_quarles on 2007-09-23
I believe that means that Miro wants something lower than 2.5, and as I mentioned in the earlier post, Ubuntu ships with both 2.5 and 2.4. You could try reinstalling 2.4 to make sure it's there and not broken. 

Actually, you could just try making sure everything is correctly configured:
```
sudo apt-get -f
```

---

### Post by Darth_tater on 2007-09-23
> **p_quarles said:**
> I believe that means that Miro wants something lower than 2.5, and as I mentioned in the earlier post, Ubuntu ships with both 2.5 and 2.4. You could try reinstalling 2.4 to make sure it's there and not broken. 

Actually, you could just try making sure everything is correctly configured:
```
sudo apt-get -f
```


did you mean

```
sudo apt-get install -f
```

?

if so, that does nothing... i even tried installing the two 'suggested' packages.  nothing.

---

### Post by p_quarles on 2007-09-23
Had to get some sleep, but I think I figured it out (crossing fingers). Found some interesting stuff [here]("https://develop.participatoryculture.org/trac/democracy/wiki/GTKX11BuildDocs"). The relevant part is:
> **On Feisty** mozilla-dev and mozilla-psm are replaced with firefox-dev and libnspr-dev, so the command would be
```
sudo apt-get install subversion python2.4 libboost-python-dev python2.4-gnome2 python2.4-gnome2-extras python-gnome2-extras-dev python2.4-pyrex python2.4-gtk2 python2.4-glade2 python-gtk2-dev libnspr-dev firefox-dev libxine-dev gettext libxine-extracodecs libxmu-dev python-pysqlite2 libxv-dev libx11-dev
```
That should ensure that all the dependencies are properly installed.

---

### Post by Darth_tater on 2007-09-23
nope... the above command did *nothing* still get the same error.

im going to backup some of my important files and then start over.  i used the exact same install disk... on teh exact same hardware, only this install is giving me hell for some reason!

this is the one downside to linux;  there is no exe. then next -> next -> i agree -> next-> install -> finish -> run.

oh well.

---

### Post by Darth_tater on 2007-09-23
Oh, p_quarles,  Thanks soo much for the quick responses and providing all the help!

i really appreciate it!

---

### Post by p_quarles on 2007-09-23
No problem. Sorry I wasn't able to help you resolve the issue. 

Sometimes installation disks can get scratched/corrupted, especially with the cheap CDs that most of us use for these things. If I were you, I'd try burning a new disk to reinstall with.

---

### Post by Darth_tater on 2007-09-23
> **p_quarles said:**
> No problem. Sorry I wasn't able to help you resolve the issue. 

Sometimes installation disks can get scratched/corrupted, especially with the cheap CDs that most of us use for these things. If I were you, I'd try burning a new disk to reinstall with.



no, the Cd was/is fine..

i just reinstalled and everything is fine.

im not sure what it was that i did... but its working now, so its all good!

---

