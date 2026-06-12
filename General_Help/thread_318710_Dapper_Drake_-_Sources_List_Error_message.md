---
title: "Dapper Drake - Sources List Error message"
date: 2006-12-14
forum: General Help
---

### Post by scottb181249 on 2006-12-14
I am a newbie and have searched the forums but the only similar case I found was for a different error. So, here I go;

E: Malformed Line 46 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.

I do not know what a repository dialogue is and when I got there I wouldn't know what to do with it.

I am pasting what I think is my sources list - it might be wrong though - any help would be appreciated.


deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#AUTOMATIX REPOS END
deb http:??archive.canonical.com/ubuntu dapper-commercial main
deb http;??archive.canonical.com/ubuntu dapper-commercial main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main


Scott

---

### Post by meng on 2006-12-14
deb http?archive.canonical.com/ubuntu dapper-commercial main
deb http;??archive.canonical.com/ubuntu dapper-commercial main
these two lines look suspicious.
Replace with http://

---

### Post by taurus on 2006-12-14
These two lines are wrong...
```

deb http?archive.canonical.com/ubuntu dapper-commercial main
deb http;??archive.canonical.com/ubuntu dapper-commercial main

```

They should be like these!
```

deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

---

### Post by scottb181249 on 2006-12-14
It looks as tho the two of you agree on what is wrong. I tried to edit the sources.list file but when I tried to save the edited file. I was told that " Could not save the file /etc/apt/sources.list.  You do not have the necessary permissions necessary to save the file. Please check that you typed the location correctly and try again."

I did not type a location - I used "search" to find the file.

I appreciate your help but need it again - How do I go about opening the correct file and saving it after editing - I can do the editing. Thanks again.

Scott

---

### Post by meng on 2006-12-14
You need superuser privileges to save an edited version of that file.
So:
sudo nano /etc/apt/sources.list
gksu gedit /etc/apt/sources.list
sudo vi /etc/apt/sources.list

---

### Post by scottb181249 on 2006-12-14
Thanks again Meng - you underestimate my stupidity - I have edited the file using your helpful instructions but domn't know how to save the edited file?

Scott

---

### Post by meng on 2006-12-14
Um, which of those programs are you using to edit with. Probably gedit (the second command) would be the easiest. By the way, when asked for a password, enter your user password.

---

### Post by mcduck on 2006-12-14
like meng told in the last post, you need to edit the file as superuser to be able to save it. So press alt-f2 and run 'gksudo gedit /etc/apt/sources.list' and now you are able to save the changes you make.

---

### Post by scottb181249 on 2006-12-14
Thank you - both of you - the changes are now saved but I am getting a new error message:

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_dapper-commercial_main_binary-i386_Packages)

How do I sort this?

Scott

---

### Post by meng on 2006-12-14
OH yeah, the same line is there four times. Delete the last three occurrences from your sources.list file.

---

### Post by scottb181249 on 2006-12-14
Thank both of you very much - my system is now back running smoothly. Thanks again.

Scott

---

