---
title: "Kernel Update Failed?"
date: 2015-02-28
forum: General Help
---

### Post by ken0069 on 2015-02-28
Ubuntu 14.04 Mate

Got a failed download during a kernel update and can't get it to finish it??  I've changed download servers trying to get one that will complete this download to no avail as it sat all night long again last night and never finished.  Other updates work but not the kernel??

Here is what it shows on that download screen:

> linux-image-3.13.0-46-generic
downloaded 11.5 MB of 15.2 MB

And it says that it's downloaded 75% and each time I restart it doesn't download any more?

And BTW, I'm having a similar problem with Mint 17 kernel update also.

---

### Post by v3.xx on 2015-03-01
```
sudo dpkg  --configure -a
```
or
```
sudo apt-get -f install
```
do anything?

---

### Post by ken0069 on 2015-03-01
```
xxx@xxxxxxx:~$ sudo dpkg  --configure -a
[sudo] password for xxx: 
xxx@xxxxxxx:~$ 

```

After this first one it again downloaded 75% of the file then quit?  Which is the same thing it's been doing.  

```
xxx@xxxxxxx:~$ sudo apt-get -f install
[sudo] password for xxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
xxx@xxxxxxx:~$ 

```

This one didn't do anything.

---

### Post by deadflowr on 2015-03-01
Try purging the cache and reload them again
to purge to cache
```
sudo apt-get clean
```
and then reload the package list
```
sudo apt-get update
```
then run the upgrade command.

See if that helps.
Sometimes starting over works...

Since the download phase was stuck, the actual installation never started, so clearing out the messed up downloaded files should give you a chance to start fresh.
And reloading the package list should pull in the absolute latest packages to install.

well, my two cents anyway...

---

### Post by ken0069 on 2015-03-01
Tried again this afternoon but it was a no go even after running your "clean" command.  I did manage to download and install the new version of Firefox 36 though so I guess one could "assume" that the internet connection itself isn't the problem???  

So does that "clean" command actually remove all the downloaded files that haven't been installed or just incomplete downloads?

Thanks

---

### Post by deadflowr on 2015-03-01
apt-get clean clears the cache, which includes all the downloaded archives, partial and complete.
(You can look at the cache in /var/cache/apt/archives.
All partial/incomplete downloads are in the partial sub-folder; everything complete will be in the main folder)

A more specialized command is the command apt-get autoclean.
It only removes packages that you wouldn't use anymore.
Mostly it clears packages which have newer versions, like if you had firefox35 it would remove that, since you now have firefox36.

But besides that, could post the output for
```
sudo apt-get update
```
and 
```
sudo apt-get dist-upgrade
```

---

### Post by ken0069 on 2015-03-02
Time Out!  Last night I tried to download the new version of Firefox via HTTP on my Windows system and it failed at 20.6MB of 39MB??  Later I tried again from a different system after changing the IP address and got the exact same results, ie, download failed at 20.6MB of 39MB so it might be the Internet connection again after all.  

I've contacted my ISP to have them check on the connection and will reply again once I hear back from them.

Thanks

---

### Post by ken0069 on 2015-03-04
Well, looks like this problem has been fixed by my ISP??  When it first started it was limited to the kernel update but when that Firefox download failed multiple times on different systems I kinda thought that one of my old ISP problems had manifest itself again.  

Yesterday I was able to update the kernel on my two Ubuntu systems without any problems so I guess it's going to be OK.  

And thanks for your help!!  I did learn some things in the process and that's always a positive thing!

Ken

---

