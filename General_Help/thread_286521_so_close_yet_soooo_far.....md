---
title: "so close yet soooo far...."
date: 2006-10-27
forum: General Help
---

### Post by maddbaron on 2006-10-27
I am so close to having my system back to normal in edgy but I keep running into broken files...I tried adding kompile since it helped me in dapper compiling stuff, it says broken.

I tried adding mplayer and it too says broken.

Is it possible that my source list is a problem?

people are saying they added Firefox 2.0 and flash 9 from automatix 2 but i didnt see them I got them installed though.

Is my source list a problem perhaps?

---

### Post by ~LoKe on 2006-10-27
We need exact error logs.

```
sudo apt-get update && sudo apt-get -f install && sudo aptitude install mplayer
```

---

### Post by maddbaron on 2006-10-27
in adept they just keep saying broken then install underneath in all red.

---

### Post by maddbaron on 2006-10-28
I followed the deb here:

[http://ubuntuforums.org/showthread.php?t=280739&highlight=gaim+beta+4](http://ubuntuforums.org/showthread.php?t=280739&highlight=gaim+beta+4)

and got this:
> maddbaron@baronworks:~$ sudo dpkg -i gaim_2.0.0+beta4-1ubuntu0_i386.deb gaim-data_2.0.0+beta4-1ubuntu0_all.deb
Password:
dpkg: error processing gaim_2.0.0+beta4-1ubuntu0_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing gaim-data_2.0.0+beta4-1ubuntu0_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gaim_2.0.0+beta4-1ubuntu0_i386.deb
 gaim-data_2.0.0+beta4-1ubuntu0_all.deb



I also entered the code for installing mplayer
and got this:
after it ran through my entire source list
> Fetched 18.4kB in 6s (2744B/s)
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/edgy/main/binary-i386/Packages.gz](http://asher256-repository.tuxfamily.org/dists/edgy/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/edgy/dupdate/binary-i386/Packages.gz](http://asher256-repository.tuxfamily.org/dists/edgy/dupdate/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://asher256-repository.tuxfamily.org/dists/edgy/french/binary-i386/Packages.gz](http://asher256-repository.tuxfamily.org/dists/edgy/french/binary-i386/Packages.gz)  404 Not Found
Reading package lists... Done
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 18B52FE3521A9C7C
W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://mrpouit.tuxfamily.org](http://mrpouit.tuxfamily.org) edgy-pouit Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


tried this too and got this:
> maddbaron@baronworks:~$ sudo apt-get install mplayer
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer: Depends: libdirectfb-0.9-22 but it is not installable
E: Broken packages


How can I get gaim beta 4 and mplayer please?

---

