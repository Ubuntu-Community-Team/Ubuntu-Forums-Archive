---
title: "Ubuntu won't update packages correctly"
date: 2007-03-03
forum: General Help
---

### Post by darkenemy on 2007-03-03
im fairly new to Linux.  I'm running Ubuntu edgy and while i have been in the process of installing various things (vlc, wine, beryl/xgl) nothing has quite got the job done.  

when i type:
> sudo apt-get update

or

> sudo aptitude update
into the terminal, something that pops up near the end i think is the reason for some of my problems.  everything else seems to go fine, except for this bit at the end.

> Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [4655kB]
99% [5 Packages gzip 0]            
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 5B in 4s (1B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


also, when i open System>Administration>Software Sources
i get this message when i try to close
> The information about available software is out-of-date

To install software and updates from newly added or changed sources, you have to reload the information about available software.

You need a working internet connection to continue.

it gives me the option to reload, and when i do it gives me these results
> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
and just under that
> [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

can anyone help?  i would really like to get all this resolved.

---

### Post by bulldog on 2007-03-03
I think that the listed repositorie is the one who gives you the trouble.
Try to set a # in front of it in the sources.list.
##[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:)
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by darkenemy on 2007-03-03
when i type what you told me into the termal i get
> (gedit:8542): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


it also opens the soruce.list (/etc/apt) -gedit window
which displays
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse universe main #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

where do i add something?

---

### Post by annda on 2007-03-03
you can delete the word universe in the second line and a few lines below that. if you put a hash (#) in front of it, everyting until the end of the line will be ignored - meaning: main repository. but you can switch those two words and have lines like this:

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse main #universe  #Added by software-properties

and

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse main #universe #Added by software-properties

however, there seems something to be wrong with the file itself. it exists but cannot be unzipped, so i would wait a while and try again before changing your configuration. the file in the repositories will probably be fixed soon.

---

### Post by darkenemy on 2007-03-03
ok i did that, it the sources.list (/etc/apt) - gedit looks like this now
> 
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy restricted multiverse main #universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted main
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates restricted multiverse universe main #universe #Added by software-properties

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted main
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security restricted multiverse #universe main #Added by software-properties
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


now when i type this into the termanal
> sudo apt-get update

at the end of it i still get lines that look like this
> Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [4655kB]
99% [4 Packages gzip 0] [Connecting to wine.budgetdedicated.com]            
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages         
  Sub-process gzip returned an error code (1)
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release.gpg [191B]   
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Packages
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy/main Sources                          
Fetched 5B in 6s (1B/s)                                                        
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


what else can i do?  how can it fix itself over time? does linux do that?

---

### Post by annda on 2007-03-03
you still have universe uncommented in line 7 (it's double, delete the first one).

that should fix the error, but it's not cool not to have universe repositories enabled.

---

### Post by darkenemy on 2007-03-03
how do i enable the universal thingies?

---

### Post by darkenemy on 2007-03-03
sorry but i dont know what that means exactly.  i deleted the 7th line where it said #repository.
i tried to open add/remove applications again and it still gave me the same thing, saying that 
> ould not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)

how do i stop this from happening?  is it possible you could paste exactly what i need to have in my resource list that way there's no questioning that i did it wrong.  help much appreciated!:)

---

### Post by darkenemy on 2007-03-03
anyone?

---

### Post by axcairns on 2007-03-27
I'm getting the same error messages ('not in gzip format') on edgy-security/restricted and a similar bzip2 error on edgy-security/universe.

```
Get:18 http://security.ubuntu.com edgy-security/universe Packages [33.4kB]                                               
Get:19 http://archive.ubuntu.com edgy-proposed/multiverse Packages [3084B]                                               
Get:20 http://archive.ubuntu.com edgy-proposed/universe Packages [30.0kB]                                                        
Hit http://medibuntu.sos-sts.com edgy/non-free Packages                                                                           
Get:21 http://security.ubuntu.com edgy-security/universe Sources [3789B]                                                                
Get:22 http://security.ubuntu.com edgy-security/multiverse Packages [3786B]                                                             
Get:23 http://security.ubuntu.com edgy-security/universe Packages [33.4kB]                                                        
Get:24 http://archive.ubuntu.com edgy-backports/restricted Packages [14B]                                                         
Get:25 http://archive.ubuntu.com edgy-backports/main Packages [13.2kB]                                                   
Get:26 http://archive.ubuntu.com edgy-backports/multiverse Packages [6087B]                                                     
Get:27 http://archive.ubuntu.com edgy-backports/universe Packages [30.3kB]                                                           
Get:28 http://medibuntu.sos-sts.com edgy/free Sources [1132B]                                                                         
Get:29 http://security.ubuntu.com edgy-security/restricted Packages [5709B]                                                                  
97% [20 Packages bzip2 102400] [29 Packages gzip 0] [Waiting for headers] [27 Packages 20343/30.3kB 67%] [28 Sources 1058/1132B 93%]         
gzip: stdin: not in gzip format
Err http://security.ubuntu.com edgy-security/restricted Packages                                                                    
  Sub-process gzip returned an error code (1)
97% [23 Packages bzip2 0] [Waiting for headers] [27 Packages 20343/30.3kB 67%] [28 Sources 1058/1132B 93%]                          
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Resource temporarily unavailable
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err http://security.ubuntu.com edgy-security/universe Packages                                            
  Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages - open (2 No such file or directory)
Get:30 http://medibuntu.sos-sts.com edgy/non-free Sources [1077B]                                         
Get:31 http://au.archive.ubuntu.com edgy Release.gpg [191B]                                                                                                  
Ign http://au.archive.ubuntu.com edgy/main Translation-en_US                                                                                                 
Ign http://au.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://au.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://au.archive.ubuntu.com edgy/multiverse Translation-en_US
Ign http://au.archive.ubuntu.com edgy/universe Translation-en_US
```

I don't think this is a sources.list configuration issue - I generated a new list from sourceomatic and still got these errors. Could it be a server-side issue?

Allan

---

