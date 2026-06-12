---
title: "Errors when installing...skype"
date: 2014-11-02
forum: General Help
---

### Post by kim3 on 2014-11-02
I have tried every guide I can find regarding installing skype on my ubuntu 14.04 OS.

Everything seems fine until the end when I get this message>>

[I]You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 google-chrome-stable : Depends: libappindicator1 but it is not going to be installed
 skype : Depends: skype-bin
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).[/I]

Can anyone help please?

---

### Post by lisati on 2014-11-02
What happened when you ran the suggested command?
```
sudo apt-get -f install
```

---

### Post by jhay2 on 2014-11-02
maybe try download the official package from skype . :)

---

### Post by kim3 on 2014-11-02
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
  linux-image-3.13.0-32-generic linux-image-extra-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.

---

### Post by kim3 on 2014-11-02
ubuntu 14.04 is not their options of my distro!

---

### Post by jhay2 on 2014-11-02
actually that was not really a problem .. . im using skype from their official release (dynamic) to my 14.04 system . it runs no problem .. try it first and then let us see the result,

---

### Post by Bucky Ball on 2014-11-02
As far as I know:

Software Sources>Other Software tab>Enable 'Canonical partners'>open a terminal and:
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install skype
```

You really should only need:

```

sudo apt-get update
sudo apt-get install skype
```

... but may as well get the machine totally up to date while you're at it. ;)

It is really easy to install Skype. You don't need to do what you've been doing. See [HERE]("http://linker99.wordpress.com/2014/05/07/install-skype-on-ubuntu-14-04-lts/"). Three steps.

You say you tried every guide you could find, but give us links to none of them so we have no idea what you've tried or how you eventually installed it. The way I've outlined is standard. Once you enable the Canonical Partners repo and update it should be right there in Software Centre and you just need to click to install. Good luck.

PS: Post back any error messages you get or any other problems you experience using this method. What you've done so far may cause a conflict.

---

### Post by kim3 on 2014-11-02
Brilliant! I tried the second route, had the same message...quoting google chrome. Not sure what that means. Then tried the first and voila...it worked perfectly, no errors whatsoever and skype seems perfect. Many thanks indeed!

this is indeed the wrong place to ask, but when such professionals are aiding me and my other post regarding the matter has no response...I must ask!

the only other problem I have with this new laptop and ubuntu installation is the touchpad. when using one finger to scroll and the other to left click the cursor jumps to the recycle bin which opens. I read about a patch to cure this problem with the dell inspiron 3137 but have no idea how to install a patch. any ideas?

---

### Post by Bucky Ball on 2014-11-02
> **kim3 said:**
> 

the only other problem I have with this new laptop and ubuntu installation is the touchpad. when using one finger to scroll and the other to left click the cursor jumps to the recycle bin which opens. I read about a patch to cure this problem with the dell inspiron 3137 but have no idea how to install a patch. any ideas?

Nope. This doesn't belong here. ;)

Please post a link to the other thread and we'll have a look. 

Please mark this thread as 'solved' by following the second link in my signature (it doesn't close the thread, just helps future travellers). 

Good news that it worked and glad to help. Enjoy! ;)

---

### Post by kim3 on 2014-11-02
also...i am close to sure there is an integrated webcam on my laptop but ubuntu does not find it!?

---

### Post by Bucky Ball on 2014-11-02
> **kim3 said:**
> also...i am close to sure there is an integrated webcam on my laptop but ubuntu does not find it!?

Please read my last post and post new threads for these other questions. The thread title here has nothing to do with them and you greatly decrease your chances of getting support with them. One support request per thread, please. Improves your chances of help and avoids confusion. Plenty of room here. ;)

---

### Post by kim3 on 2014-11-02
[http://ubuntuforums.org/showthread.php?t=2250617](http://ubuntuforums.org/showthread.php?t=2250617) (sorry!)

---

