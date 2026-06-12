---
title: "Repository problem! Is it the same for every one?"
date: 2008-05-07
forum: General Help
---

### Post by sands on 2008-05-07
I am unable to update the repo.. Is it the prob with the server, or with my sys?

```
sands@sands-laptop:~$ sudo apt-get update
[sudo] password for sands: 
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Hit http://archive.ubuntu.com hardy Release.gpg
Ign http://archive.ubuntu.com hardy/main Translation-en_US
Hit http://archive.canonical.com hardy Release 
Ign http://archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy/web Translation-en_US
Ign http://archive.ubuntu.com hardy/universe Translation-en_US
Ign http://archive.ubuntu.com hardy/multiverse Translation-en_US
Get:1 http://archive.ubuntu.com hardy-updates Release.gpg [191B]
Ign http://archive.ubuntu.com hardy-updates/main Translation-en_US
Hit http://archive.canonical.com hardy/partner Packages
Ign http://archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/web Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy-security Release.gpg
Ign http://archive.ubuntu.com hardy-security/main Translation-en_US
Ign http://archive.ubuntu.com hardy-security/restricted Translation-en_US
Ign http://archive.ubuntu.com hardy-security/web Translation-en_US
Ign http://archive.ubuntu.com hardy-security/universe Translation-en_US
Ign http://archive.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com hardy Release
Get:2 http://archive.ubuntu.com hardy-updates Release [51.2kB]
Hit http://archive.ubuntu.com hardy-security Release
Hit http://archive.ubuntu.com hardy/main Packages
Hit http://archive.ubuntu.com hardy/restricted Packages
Get:3 http://archive.ubuntu.com hardy-updates/main Packages [34.2kB]
Get:4 http://archive.ubuntu.com hardy-updates/restricted Packages [14B]
Hit http://archive.ubuntu.com hardy-security/main Packages
Hit http://archive.ubuntu.com hardy-security/restricted Packages
Fetched 85.7kB in 3s (28.5kB/s)
[B]W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.[/B]
sands@sands-laptop:~$ 
```

I deleted files from /var/lib/apt/lists.. It solved the problem..

---

### Post by Freelance Physicist on 2008-05-17
What does your /etc/apt/sources.list contain?  What files did you delete from /var/lib/apt/lists?  I'm getting the same errors and would like to know how you solved this.

---

### Post by sands on 2008-05-17
I deleted all the files from /var/lib/apt/lists
Then apt-get  update
It will say some folder is missing in /var/lib/apt/lists.
Create that folder & then again apt-get update

It will be solved. If you still get the error. try using the default repo list

Here is mine, if you need.
```

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ubuntu.cs.utah.edu/ubuntu/ hardy main restricted
deb-src http://ubuntu.cs.utah.edu/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ubuntu.cs.utah.edu/ubuntu/ hardy-updates main restricted
deb-src http://ubuntu.cs.utah.edu/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ubuntu.cs.utah.edu/ubuntu/ hardy universe
deb-src http://ubuntu.cs.utah.edu/ubuntu/ hardy universe
deb http://ubuntu.cs.utah.edu/ubuntu/ hardy-updates universe
deb-src http://ubuntu.cs.utah.edu/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ubuntu.cs.utah.edu/ubuntu/ hardy multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu/ hardy multiverse
deb http://ubuntu.cs.utah.edu/ubuntu/ hardy-updates multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://ubuntu.cs.utah.edu/ubuntu/ hardy-security main restricted
deb-src http://ubuntu.cs.utah.edu/ubuntu/ hardy-security main restricted
deb http://ubuntu.cs.utah.edu/ubuntu/ hardy-security universe
deb-src http://ubuntu.cs.utah.edu/ubuntu/ hardy-security universe
deb http://ubuntu.cs.utah.edu/ubuntu/ hardy-security multiverse
deb-src http://ubuntu.cs.utah.edu/ubuntu/ hardy-security multiverse


```

---

### Post by Freelance Physicist on 2008-05-17
I did a little investigating and found that the problems were caused by three lines in /etc/apt/sources.list:

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted web

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted web

deb http://security.ubuntu.com/ubuntu hardy-security main restricted web
```

The last repository, "web", doesn't seem to refer to any existing section of software.  Deleting that from those three lines fixed my problem.

If you go to look at your original error message ```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
``` and go to [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release), you'll see lists for "hardy", "main", and "restricted", among others, but nothing from "web".

I don't know how this got into my sources.list, but everything works fine now that "web" is deleted.

---

### Post by sands on 2008-05-17
Might be some bug..

---

### Post by neutralstorm on 2008-05-21
> **Freelance Physicist said:**
> I did a little investigating and found that the problems were caused by three lines in /etc/apt/sources.list:

```
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted web

deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted web

deb http://security.ubuntu.com/ubuntu hardy-security main restricted web
```

The last repository, "web", doesn't seem to refer to any existing section of software.  Deleting that from those three lines fixed my problem.

If you go to look at your original error message ```
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy/Release  Unable to find expected entry  web/binary-i386/Packages in Meta-index file (malformed Release file?)
``` and go to [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release), you'll see lists for "hardy", "main", and "restricted", among others, but nothing from "web".

I don't know how this got into my sources.list, but everything works fine now that "web" is deleted.


Thanks for that. 
I was pulling my hair out try to figure this one out.
And I read my sources list about five times, and I 
still could not see this. sheesh; me dense.

---

