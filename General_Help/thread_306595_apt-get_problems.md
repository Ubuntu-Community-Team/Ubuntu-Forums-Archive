---
title: "apt-get problems"
date: 2006-11-25
forum: General Help
---

### Post by dg88 on 2006-11-25
Hi. I have som problems with apt-get on my Kubuntu desktop

i get the error message
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"

so far so good but each time i try to run it my computer freezes up and i basically have to pull the plug to be able to reboot and try again. 

Any and All suggestions are welcome

---

### Post by adwait on 2006-11-25
Did you try running the command it is asking you to?
```
sudo dpkg --configure -a
```

---

### Post by dg88 on 2006-11-25
> **dg88 said:**
> 
so far so good but each time i try to run it my computer freezes up and i basically have to pull the plug to be able to reboot and try again. 


Yes. that is just my problem. each time i do my computer freezes up

---

### Post by adwait on 2006-11-26
ooh ok...didn't read your post properly :P
TRy running
```
sudo apt-get install -f
```

---

### Post by dg88 on 2006-11-26
didnt work...
still getting 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem"

starting to feel like i have to reinstall kubuntu all over

---

### Post by junglepeanut on 2006-11-26
Are you sure it is hung? i.e. does it just dtop doing anything? I am just asking because from the man pages
```

dpkg --configure package ... | -a | --pending
              Reconfigure an unpacked package. If -a  or  --pending  is  given
              instead  of  package, all unpacked but unconfigured packages are
              configured.

              Configuring consists of the following steps:

              1. Unpack the configuration files, and at the same time back  up
              the  old  configuration  files,  so that they can be restored if
              something goes wrong.

              2. Run postinst script, if provided by the package.

``` I dont know but that sounds like it could take a while. hmm I'll try on mine and let you know how long it takes.  (I dont have anything broken though).

---

### Post by junglepeanut on 2006-11-26
Yeah, I got nothing broken, it was instantaneously done. If dpkg was the package (I know it I received an update for it recently) then maybe we can just find somebody with a computer download the binary and put it in place? It may be easier to just backup and reinstall though.

---

### Post by dg88 on 2006-11-27
yes. i cant move the mouse at all. no matter how long i wait. the keyboard wont work either

---

### Post by junglepeanut on 2006-11-27
Somebody else is posting a problem very similar to yours. 
Not much success.
[http://ubuntuforums.org/showthread.php?t=307383&highlight=dpkg+-configure-a](http://ubuntuforums.org/showthread.php?t=307383&highlight=dpkg+-configure-a)

Maybe though you can see if between you something there is something of similarity and resolve the problem? Automatix or both have broken flashplugin,both lost internet connection during update not sure what the reason could be.. just guessing.

---

### Post by dg88 on 2006-11-28
thanks junglepeanut. unfortunately adwait has already suggested just about all of the important stuff from that thread. save for the sources.list wich ive already updated

---

