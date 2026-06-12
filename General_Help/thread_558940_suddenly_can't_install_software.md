---
title: "suddenly can't install software"
date: 2007-09-24
forum: General Help
---

### Post by PHY on 2007-09-24
When i try and install software through "add /remove" or directly through Synaptic Manager I get error message. Also the auto update tells me I have one update, but there is nothing listed when I open it up - then way I do install update the error message below comes up. The update "star" in my toolbar continues to tell me I have one update. ther is no problem with my internet connection.

E: /var/cache/apt/archives/tar_1.16-2ubuntu0.1_i386.deb: subprocess dpkg-deb --control returned error exit status 2

Any ideas how I resole this?

---

### Post by i-tech on 2007-09-24
what does it do when you try to install software with apt-get or aptitude?  and for the update that u can't install open aptitude press U , you will see how many mb will be downloaded for update pressing g will install them.

---

### Post by Bothered on 2007-09-24
Could you type, in a terminal:

```
sudo apt-get update
```

followed by:

```
sudo apt-get install [some package]
```

where [some package] is any package you want to install, and then post the results.

---

### Post by dabl on 2007-09-24
> **PHY said:**
> 

Any ideas how I resolve this?


This series of console commands usually resolves such errors -- do them one at a time:
```

sudo dpkg --configure -a
```

```
sudo apt-get update
```

```
sudo apt-get install
```
```

sudo apt-get autoclean
```


Hope this helps!  :)

---

### Post by PHY on 2007-09-25
Tried aptitude get same error message as below

 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/linsmith_0.99.3-0ubuntu1_i386.deb
 /var/cache/apt/archives/offlineimap_4.0.16_all.deb
 /var/cache/apt/archives/ogmtools_1%3a1.5-2.1_i386.deb
 /var/cache/apt/archives/python-m2crypto_0.16-1.1build1_i386.deb
 /var/cache/apt/archives/mpe-source_1.2.7-2_all.deb
 /var/cache/apt/archives/mutella_0.4.5-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

---

### Post by PHY on 2007-09-25
Same thing happens instaling with apt as suggested by "bothered"

---

### Post by PHY on 2007-09-25
configure autoclean etc.. as also suggested makes no difference. basically I cannot install anything new. I now have 5 auto updates message but on using update manager all fail with same error message as in my previous answer

---

### Post by lavajumper on 2007-09-25
> /var/cache/apt/archives/tar_1.16-2ubuntu0.1_i386.deb

This is from the 'man' page:
```

              dpkg -e | --control filename [directory]
                  Extract control-information from a package..

```

and this is from debians dpkg docs:
```

control

    This is the key description file used by dpkg. It specifies the package's name and version,
gives its description for the user, states its relationships with other packages, and so forth.


```

Try backing up this file, removing it from /var/cache/apt/archives and rerunning update-manager. I'm guessing there may be some file corruption or other sticky stuff, and this should force the package manager to re-download the file.

If that doesn't work, the fixes I can think of are all scary. Also, I would back up the file /bin/tar (just in case something goes terribly wrong, synaptic, apt, dpkg all need access to tar in order to perform installations/updates.

---

### Post by danbh on 2007-09-25
try running:
sudo apt-get clean

That should delete all the packages, and force a redownload of the updates.  Maybe there was some corruption of data.

---

