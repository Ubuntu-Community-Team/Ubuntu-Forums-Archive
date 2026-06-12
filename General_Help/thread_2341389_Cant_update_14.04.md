---
title: "Cant update 14.04"
date: 2016-10-27
forum: General Help
---

### Post by linuxyogi on 2016-10-27
When I try to update I am getting this 

```
$ sudo apt-get update 
Ign http://extras.ubuntu.com trusty InRelease
Get:1 http://extras.ubuntu.com trusty Release.gpg [72 B]
Get:2 http://extras.ubuntu.com trusty Release [11.9 kB] 
Ign http://archive.ubuntu.com trusty InRelease     
Get:3 http://archive.ubuntu.com trusty-updates InRelease [65.9 kB]
Hit http://extras.ubuntu.com trusty/main Sources           
Hit http://extras.ubuntu.com trusty/main amd64 Packages                  
Hit http://extras.ubuntu.com trusty/main i386 Packages                     
Get:4 http://archive.ubuntu.com trusty-backports InRelease [65.9 kB]           
Get:5 http://archive.ubuntu.com trusty-security InRelease [65.9 kB]        
Get:6 http://archive.ubuntu.com trusty Release.gpg [72 B]                  
Get:7 http://archive.ubuntu.com trusty-updates/main Sources [383 kB]
Ign http://extras.ubuntu.com trusty/main Translation-en_IN
Ign http://extras.ubuntu.com trusty/main Translation-en
Get:8 http://archive.ubuntu.com trusty-updates/restricted Sources [5,360 B]    
Get:9 http://archive.ubuntu.com trusty-updates/universe Sources [169 kB]       
Get:10 http://archive.ubuntu.com trusty-updates/multiverse Sources [7,531 B]   
Get:11 http://archive.ubuntu.com trusty-updates/main amd64 Packages [910 kB]   
Get:12 http://archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.9 kB]
Get:13 http://archive.ubuntu.com trusty-updates/universe amd64 Packages [387 kB]
Get:14 http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages [15.0 kB]
Get:15 http://archive.ubuntu.com trusty-updates/main i386 Packages [870 kB]    
Get:16 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [15.6 kB]
Get:17 http://archive.ubuntu.com trusty-updates/universe i386 Packages [389 kB]
Get:18 http://archive.ubuntu.com trusty-updates/multiverse i386 Packages [15.5 kB]
Get:19 http://archive.ubuntu.com trusty-updates/main Translation-en [443 kB]   
Get:20 http://archive.ubuntu.com trusty-updates/multiverse Translation-en [7,931 B]
Get:21 http://archive.ubuntu.com trusty-updates/restricted Translation-en [3,699 B]
Get:22 http://archive.ubuntu.com trusty-updates/universe Translation-en [205 kB]
Get:23 http://archive.ubuntu.com trusty-backports/main Sources [9,646 B]       
Get:24 http://archive.ubuntu.com trusty-backports/restricted Sources [28 B]    
Get:25 http://archive.ubuntu.com trusty-backports/universe Sources [35.2 kB]   
Get:26 http://archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B] 
Get:27 http://archive.ubuntu.com trusty-backports/main amd64 Packages [13.3 kB]
Get:28 http://archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:29 http://archive.ubuntu.com trusty-backports/universe amd64 Packages [43.2 kB]
Get:30 http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:31 http://archive.ubuntu.com trusty-backports/main i386 Packages [13.3 kB] 
Get:32 http://archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:33 http://archive.ubuntu.com trusty-backports/universe i386 Packages [43.2 kB]
Get:34 http://archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:35 http://archive.ubuntu.com trusty-backports/main Translation-en [7,493 B]
Get:36 http://archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:37 http://archive.ubuntu.com trusty-backports/restricted Translation-en [28 B]
Get:38 http://archive.ubuntu.com trusty-backports/universe Translation-en [36.8 kB]
Get:39 http://archive.ubuntu.com trusty-security/main Sources [120 kB]         
Get:40 http://archive.ubuntu.com trusty-security/restricted Sources [4,064 B]  
Get:41 http://archive.ubuntu.com trusty-security/universe Sources [44.7 kB]    
Get:42 http://archive.ubuntu.com trusty-security/multiverse Sources [3,202 B]  
Get:43 http://archive.ubuntu.com trusty-security/main amd64 Packages [542 kB]  
Get:44 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Get:45 http://archive.ubuntu.com trusty-security/universe amd64 Packages [141 kB]
Get:46 http://archive.ubuntu.com trusty-security/multiverse amd64 Packages [5,199 B]
Get:47 http://archive.ubuntu.com trusty-security/main i386 Packages [503 kB]   
Get:48 http://archive.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Get:49 http://archive.ubuntu.com trusty-security/universe i386 Packages [141 kB]
Get:50 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [5,360 B]
Get:51 http://archive.ubuntu.com trusty-security/main Translation-en [298 kB]  
Get:52 http://archive.ubuntu.com trusty-security/multiverse Translation-en [2,848 B]
Get:53 http://archive.ubuntu.com trusty-security/restricted Translation-en [3,206 B]
Get:54 http://archive.ubuntu.com trusty-security/universe Translation-en [84.3 kB]
Get:55 http://archive.ubuntu.com trusty Release [11.9 kB]                      
Get:56 http://archive.ubuntu.com trusty/main Sources [1,064 kB]                
Fetched 7,261 kB in 1min 9s (105 kB/s)                                         
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by Bashing-om on 2016-10-27
linuxyogi; Well :

> 
Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)


Let's verify the sources.list file:
Post back :
```

cat -n /etc/apt/sources.list

``` see if that is the cause .

[INDENT][INDENT]of not one thing
[INDENT][INDENT][INDENT]then another
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by linuxyogi on 2016-10-27
```
$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Lubuntu 14.04 LTS _Trusty Tahr_ - Release amd64 (20140416.2)]/ trusty main multiverse restricted universe
     2    
     3    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4    # newer versions of the distribution.
     5    deb http://archive.ubuntu.com/ubuntu trusty main restricted
     6    deb-src http://archive.ubuntu.com/ubuntu trusty main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted
    11    deb-src http://archive.ubuntu.com/ubuntu trusty-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team. Also, please note that software in universe WILL NOT receive any
    15    ## review or updates from the Ubuntu security team.
    16    deb http://archive.ubuntu.com/ubuntu trusty universe
    17    deb-src http://archive.ubuntu.com/ubuntu trusty universe
    18    deb http://archive.ubuntu.com/ubuntu trusty-updates universe
    19    deb-src http://archive.ubuntu.com/ubuntu trusty-updates universe
    20    
    21    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22    ## team, and may not be under a free licence. Please satisfy yourself as to 
    23    ## your rights to use the software. Also, please note that software in 
    24    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    25    ## security team.
    26    deb http://archive.ubuntu.com/ubuntu trusty multiverse
    27    deb-src http://archive.ubuntu.com/ubuntu trusty multiverse
    28    deb http://archive.ubuntu.com/ubuntu trusty-updates multiverse
    29    deb-src http://archive.ubuntu.com/ubuntu trusty-updates multiverse
    30    
    31    ## N.B. software from this repository may not have been tested as
    32    ## extensively as that contained in the main release, although it includes
    33    ## newer versions of some applications which may provide useful features.
    34    ## Also, please note that software in backports WILL NOT receive any review
    35    ## or updates from the Ubuntu security team.
    36    deb http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
    37    deb-src http://archive.ubuntu.com/ubuntu trusty-backports main restricted universe multiverse
    38    
    39    deb http://archive.ubuntu.com/ubuntu trusty-security main restricted
    40    deb-src http://archive.ubuntu.com/ubuntu trusty-security main restricted
    41    deb http://archive.ubuntu.com/ubuntu trusty-security universe
    42    deb-src http://archive.ubuntu.com/ubuntu trusty-security universe
    43    deb http://archive.ubuntu.com/ubuntu trusty-security multiverse
    44    deb-src http://archive.ubuntu.com/ubuntu trusty-security multiverse
    45    
    46    ## Uncomment the following two lines to add software from Canonical's
    47    ## 'partner' repository.
    48    ## This software is not part of Ubuntu, but is offered by Canonical and the
    49    ## respective vendors as a service to Ubuntu users.
    50    # deb http://archive.canonical.com/ubuntu trusty partner
    51    # deb-src http://archive.canonical.com/ubuntu trusty partner
    52    
    53    ## This software is not part of Ubuntu, but is offered by third-party
    54    ## developers who want to ship their latest software.
    55    deb http://extras.ubuntu.com/ubuntu trusty main
    56    deb-src http://extras.ubuntu.com/ubuntu trusty main
```

---

### Post by Bashing-om on 2016-10-27
linuxyogi; Huuumm ..

Looks OK to me .. maybe a momentary glitch in the mirror site??

Try the update/upgrade again see if the " Hash Sum mismatch " is resolved at the mirror .

Else:
[INDENT][INDENT]we get the more aggressive, and "assume" a corrupted control file on your system
[/INDENT][/INDENT]

---

### Post by linuxyogi on 2016-10-27
The hash sum mismatch is gone this time

```
~$ sudo apt-get update 
[sudo] password for lub: 
Ign http://extras.ubuntu.com trusty InRelease
Ign http://archive.ubuntu.com trusty InRelease
Hit http://extras.ubuntu.com trusty Release.gpg
Hit http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://extras.ubuntu.com trusty Release [11.9 kB]
Hit http://archive.ubuntu.com trusty-backports InRelease   
Get:2 http://archive.ubuntu.com trusty-security InRelease [65.9 kB]      
Get:3 http://extras.ubuntu.com trusty/main Sources [14 B]                      
Hit http://archive.ubuntu.com trusty Release.gpg                           
Get:4 http://extras.ubuntu.com trusty/main amd64 Packages [14 B]
Hit http://archive.ubuntu.com trusty-updates/main Sources              
Get:5 http://extras.ubuntu.com trusty/main i386 Packages [14 B]    
Hit http://archive.ubuntu.com trusty-updates/restricted Sources    
Hit http://archive.ubuntu.com trusty-updates/universe Sources     
Hit http://archive.ubuntu.com trusty-updates/multiverse Sources  
Hit http://archive.ubuntu.com trusty-updates/main amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-updates/main i386 Packages    
Hit http://archive.ubuntu.com trusty-updates/restricted i386 Packages
Ign http://extras.ubuntu.com trusty/main Translation-en_IN          
Hit http://archive.ubuntu.com trusty-updates/universe i386 Packages 
Ign http://extras.ubuntu.com trusty/main Translation-en             
Hit http://archive.ubuntu.com trusty-updates/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-updates/main Translation-en
Hit http://archive.ubuntu.com trusty-updates/multiverse Translation-en
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en
Hit http://archive.ubuntu.com trusty-updates/universe Translation-en
Hit http://archive.ubuntu.com trusty-backports/main Sources
Hit http://archive.ubuntu.com trusty-backports/restricted Sources
Hit http://archive.ubuntu.com trusty-backports/universe Sources
Hit http://archive.ubuntu.com trusty-backports/multiverse Sources
Hit http://archive.ubuntu.com trusty-backports/main amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/restricted amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/universe amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/multiverse amd64 Packages
Hit http://archive.ubuntu.com trusty-backports/main i386 Packages
Hit http://archive.ubuntu.com trusty-backports/restricted i386 Packages
Hit http://archive.ubuntu.com trusty-backports/universe i386 Packages
Hit http://archive.ubuntu.com trusty-backports/multiverse i386 Packages
Hit http://archive.ubuntu.com trusty-backports/main Translation-en
Hit http://archive.ubuntu.com trusty-backports/multiverse Translation-en       
Hit http://archive.ubuntu.com trusty-backports/restricted Translation-en       
Hit http://archive.ubuntu.com trusty-backports/universe Translation-en         
Hit http://archive.ubuntu.com trusty-security/main Sources                     
Hit http://archive.ubuntu.com trusty-security/restricted Sources               
Hit http://archive.ubuntu.com trusty-security/universe Sources                 
Hit http://archive.ubuntu.com trusty-security/multiverse Sources               
Hit http://archive.ubuntu.com trusty-security/main amd64 Packages              
Get:6 http://archive.ubuntu.com trusty-security/restricted amd64 Packages [13.0 kB]
Hit http://archive.ubuntu.com trusty-security/universe amd64 Packages          
Get:7 http://archive.ubuntu.com trusty-security/multiverse amd64 Packages [5,199 B]
Hit http://archive.ubuntu.com trusty-security/main i386 Packages               
Get:8 http://archive.ubuntu.com trusty-security/restricted i386 Packages [12.7 kB]
Hit http://archive.ubuntu.com trusty-security/universe i386 Packages           
Get:9 http://archive.ubuntu.com trusty-security/multiverse i386 Packages [5,360 B]
Hit http://archive.ubuntu.com trusty-security/main Translation-en              
Get:10 http://archive.ubuntu.com trusty-security/multiverse Translation-en [2,848 B]
Hit http://archive.ubuntu.com trusty-security/restricted Translation-en        
Get:11 http://archive.ubuntu.com trusty-security/universe Translation-en [84.3 kB]
Get:12 http://archive.ubuntu.com trusty Release [11.9 kB]                      
Get:13 http://archive.ubuntu.com trusty/main Sources [14 B]                    
Fetched 213 kB in 9s (23.0 kB/s)                                               
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/trusty/Release  Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by Bashing-om on 2016-10-27
linuxyogi; Ouch ...

I am stuck here too :
> 
Unable to find expected entry 'restricted/source/Sources' in Release file (Wrong sources.list entry or malformed file)

As again, I find no fault in the /etc/apt/sources/list file /

I do not know what to make of "expected entry 'restricted/source/Sources" ; or what could generate the warning in this format.
Wiser heads I hope come to our rescue.

[INDENT][INDENT]inquiring minds do want to know
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2016-10-28
linuxyogi; Welp ...

As no one has proffered a better idea ... 
Let's check the 3rd party sources list also.
```

tail -v -n +1 /etc/apt/sources.list.d/*

```

[INDENT][INDENT]there is a cause
[INDENT][INDENT][INDENT]that effects
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by linuxyogi on 2016-10-29
I am using Manjaro LXDE now. I will try the next LTS.

---

