---
title: "Installing 32bit libraries for Steam"
date: 2013-05-10
forum: General Help
---

### Post by zombifier25 on 2013-05-10
So after a long period of absense (final exams and all), I'm back on the forum :)

Anyway, I installed 64bit 13.04 and so far, it is perfect, and I must say, it's probably the best Ubuntu yet.  I have been trying to install Steam on Ubuntu for my gaming needs. When it starts, it says:
```
Steam needs to install these additional packages: 
	libgl1-mesa-dri:i386, libgl1-mesa-glx:i386

```
However, when I choose to install them, it gave this error:
```
Package libgl1-mesa-glx:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libgl1-mesa-dri:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgl1-mesa-glx

E: Package 'libgl1-mesa-dri:i386' has no installation candidate
E: Package 'libgl1-mesa-glx:i386' has no installation candidate

```

I never had this problem with 12.04, on which I managed to get Steam (and Team Fortress 2) to run successfully. Any help? If this helps, I ran this command before:
```
sudo dpkg --add-architecture i386
```
but it didn't help. Whenever I apt-get update, it threw this:
```
W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_raring_universe_source_Sources  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_raring_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch bzip2:/var/lib/apt/lists/partial/archive.ubuntu.com_ubuntu_dists_raring_universe_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by mc4man on 2013-05-10
Things got messed up in 13.04 so you should try this way - 
(Steam installer in USC is old & requires "buy"info - screen1

Get latest from [here]("http://media.steampowered.com/client/installer/steam.deb")
After downloaded open it in USC - screen 2
After it installs run the installer (screen 3
It will install the needed libs for you (screen 4

(the latest installer version is 1.0.0.38, that's screen 2

---

### Post by zombifier25 on 2013-05-11
Thanks for the tip. I actually installed Steam from their website the first time around.

I purged Steam from my system and tried again. Same results. The 3rd screen from your post does not show up. but when I start Steam, the terminal from pic 4 does show up asking me to install the missing libs. And, once again, it gave me
```
Package libgl1-mesa-glx:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

Package libgl1-mesa-dri:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libgl1-mesa-glx

E: Package 'libgl1-mesa-dri:i386' has no installation candidate
E: Package 'libgl1-mesa-glx:i386' has no installation candidate
```

It may have something to do with my connection (though I seriously doubt it) I'll try again later, any more help is appreciated.

---

### Post by zombifier25 on 2013-05-11
Nevermind, it DOES have something to do with my connection, specifically with the mirror I'm using. I switched to a different server in Software Sources and it seems all is fine :) .
Mark as Solved. err how do you mark a thread as solved? I can't find it in the new layout.

---

### Post by mörgæs on 2013-05-11
The solved-function has been missing for some time. I have changed it for you.

---

