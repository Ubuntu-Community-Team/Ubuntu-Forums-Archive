---
title: "Most of my applications uninstalled upon removing libicu48"
date: 2013-05-10
forum: General Help
---

### Post by maluba on 2013-05-10
Hi,
I was trying to find a way to install kobo e-reader in ubuntu 12.04, got this following commands  from this forum:

sudo rm /usr/lib/libicuuc.so.44 
sudo apt-get remove libicu48 
getlibs -p libicu48 
sudo ln -s /usr/lib/libicuuc.so.48 /usr/lib/libicuuc.so.44

The problem is I lost all my installations including eclipse, libre office etc.
Is there a way or a command to restore everything without necessarily installing them all over again one by one? 
I really will appreciate your quick help on this, thanks!

---

### Post by deadflowr on 2013-05-10
Did you get a long list of "the following packages will be removed" when removing the libicu48 package?

If not, then try reinstalling that package, with install instead of remove and your programs should work again.

Also, could you point to where the instructions you followed can be found.

---

### Post by QIII on 2013-05-10
*Moved to **General Help***

---

### Post by maluba on 2013-05-10
I think I got carried away with the whole thing, didn't even bother to read much but I remember puting y for yes, the next thing I saw was removing...
I got it here [http://ubuntuforums.org/showthread.php?t=2045621](http://ubuntuforums.org/showthread.php?t=2045621).
I did try sudo apt-get install libicu48 but nope! I have nothing restored.

---

### Post by monkeybrain2012 on 2013-05-10
Did you copy those commands from this thread? [http://ubuntuforums.org/showthread.php?t=2045621](http://ubuntuforums.org/showthread.php?t=2045621) It didn't seem to have a happy ending. :(

Well I think calibre is a good advice for managing and reading ebooks. It is free and won't screw up your desktop. :) (see post #4)

---

### Post by maluba on 2013-05-10
For now I just want a quicker way to restore all the removed applications. They are too many, it's almost imposible to install them one-by-one

---

### Post by deadflowr on 2013-05-10
Not sure if this is the easiest way, but run

```
cat /var/log/apt/history.log | grep Remove
```

which should show the list of packages that where removed.

Then simply copy the listed packages and add sudo apt-get install in front.

If you need help, post the out here.
Please use the code tags (the symbol # in the reply box tool bar) when posting outputs as such.

---

### Post by maluba on 2013-05-10
Thanks deadflowr,
I had already reinstalled the desktop, but I like your method better. I'm actually picking out applications not installed through the desktop & reinstalling them one at a time. Thanks

---

