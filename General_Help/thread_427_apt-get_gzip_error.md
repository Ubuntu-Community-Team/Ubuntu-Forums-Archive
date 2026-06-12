---
title: "apt-get gzip error"
date: 2004-10-13
forum: General Help
---

### Post by eNiNjA on 2004-10-13
When running apt-get update, I get the following towards the end:

```
Hit http&#58;//archive.ubuntu.com warty/universe Sources
Get&#58;19 http&#58;//archive.ubuntu.com warty/universe Release &#91;85B&#93;
99% &#91;16 Sources gzip 0&#93;                                                                                                                                                                      230kB/s 0s
gzip&#58; stdin&#58; not in gzip format
Err http&#58;//archive.ubuntu.com warty/main Sources
  Sub-process gzip returned an error code &#40;1&#41;
Fetched 3704kB in 17s &#40;217kB/s&#41;
Failed to fetch http&#58;//archive.ubuntu.com/ubuntu/dists/warty/main/source/Sources.gz  Sub-process gzip returned an error code &#40;1&#41;
Reading Package Lists... Done

```

Anyone else get this error?

---

### Post by dandaman32 on 2006-10-30
Yeah, I get the same error, except with four repos instead of one:
```
Get:7 http://archive.ubuntu.com edgy/universe Packages [4655kB]                
99% [7 Packages gzip 0] [Waiting for headers]                         944B/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/universe Packages                           
  Sub-process gzip returned an error code (1)
Get:8 http://archive.ubuntu.com edgy/universe Packages [4655kB]                
99% [Working]                                                         944B/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/universe Packages                           
  Sub-process gzip returned an error code (1)
Get:9 http://archive.ubuntu.com edgy/universe Packages [4655kB]                
99% [Working]                                                         944B/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/universe Packages                           
  Sub-process gzip returned an error code (1)
Get:10 http://archive.ubuntu.com edgy/universe Packages [4655kB]               
99% [Working]                                                       2196kB/s 0s
gzip: stdin: not in gzip format
Err http://archive.ubuntu.com edgy/universe Packages                           
  Sub-process gzip returned an error code (1)
Fetched 1661B in 18s (88B/s)                                                   
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
```
Help anyone?

-dandaman32

---

### Post by bumblebeef on 2006-11-02
I am getting this error, too. Is there anything I can do about this?

---

### Post by hexion on 2006-11-08
Same here

---

### Post by 5h4rk on 2006-11-15
Same here...

> [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz) Sub-process gzip returned an error code (1)
[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz) Sub-process gzip returned an error code (1)

Any solution plz?

---

### Post by alvin_voo on 2006-11-17
Hey, i believe i found the answer, juz simply change the http:// tag in your sources.list into [ftp://.](ftp://.)

---

### Post by Wil0 on 2006-11-17
i cant use ftp as im behind a proxy server that doesent allow me ftp access. Is there no alternative fix?!

---

### Post by Wil0 on 2006-11-17
bump?

---

### Post by ankursethi on 2006-11-17
I used to get a similar error, but I found 2 ways to correct them :

1. Get the proper GPG keys and add them into apt. For the freecontrib packages the method to import the key is -
> wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
sudo apt-get update
Those of you who are using the default Ubuntu repos won't find it necessary to do this step.

2. Make sure the repos are alive and working. If not, comment them out.

Well, this is from a newbie so don't consider this to be the final answer.

---

### Post by Wil0 on 2006-11-20
the same thing happens, ive updated the key, but thats not for the ubuntu repository. From my web browser i can access the [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) file in my browser... Is there a way to wget it then install it?

---

### Post by Wil0 on 2006-11-20
Bump?

---

### Post by xbadger on 2007-01-01
I have the same error! U may use ftp if u can, if not uncomment the sources for a few days. Is nothing wrong with your ubuntu i guess. I think is just a problem from server update. But any answer to solve this problem is welcome.

---

### Post by strummsteel on 2007-01-13
I recently had this problem, 

 Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages                 
  Sub-process gzip returned an error code (1)

ANy official fix for this? Please help

---

### Post by jsilve1 on 2007-01-17
I had this same (very frustrating) problem. To fix it, I did this (from a Terminal (Accessories->Terminal):

```
apt-get clean
```

and then ran

```
apt-get update
```

This seemed to do the trick.

I think the problem was a result of a borked sources list download, which doesn't get updated properly on subsequent apt-get updates. Cleaning and re-updating fixed it for me.

Later...

---

### Post by digTro on 2007-01-20
I did a fresh install of Edgy, enabled the extra repos and got this error:

```
http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz: Sub-process gzip returned an error code (1)
```

> **alvin_voo said:**
> Hey, i believe i found the answer, juz simply change the http:// tag in your sources.list into [ftp://.](ftp://.)

Yeah, replacing http with ftp solved the problem. But wonder why apt is having this problem. When I try to open [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) in the browser it opens fine. So its not like the server is down. :confused:

---

### Post by charakad on 2007-01-30
I had the same issue. Selected only the following in the software sources.
*community maintained open source software (universe)
*canonical supported open source software (main)
did a update. Now it seems to be working.

---

### Post by mikewhatever on 2007-02-03
It looks like all of a sudden, within the last week, lots of people get this error. I'd say the issue is with the repository, or repositories, cause they seem to different.
> Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources [22.5kB]              
99% [5 Sources gzip 0]                                               20.9kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Sources                         
  Sub-process gzip returned an error code (1)
Fetched 5B in 6s (1B/s)                                                         
Reading package lists... Done


---

### Post by citizenr on 2007-02-17
rasz@capek:~$ sudo apt-get update 
Get:1 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy Release.gpg [191B]                     
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Translation-en_US        
Get:2 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg [191B]      
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Translation-en_US    
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release                   
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Translation-en_US   
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/multiverse Translation-en_US
Get:4 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release              
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/universe Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Get:5 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/main Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages           
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages             
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy Release
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates Release
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports Release
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Packages    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Packages
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages [36.9kB]
99% [6 Packages gzip 0] [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages     
  Sub-process gzip returned an error code (1)
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources [13.2kB]
99% [Waiting for headers]                      
gzip: stdin: not in gzip format
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Sources
  Sub-process gzip returned an error code (1)
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/universe Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/multiverse Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/main Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy/restricted Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/universe Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/multiverse Packages
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/multiverse Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/main Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/restricted Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/universe Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-backports/multiverse Sources
Get:8 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Sources [23.6kB]
99% [8 Sources gzip 0]   
gzip: stdin: not in gzip format
Err [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) edgy-updates/main Sources
  Sub-process gzip returned an error code (1)
Fetched 8B in 5s (1B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://no.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz](http://no.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/source/Sources.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
rasz@capek:~$

---

### Post by soapyfish on 2007-02-20
same prob here, I guess its not my filtering then :-( 


99% [9 Packages gzip 0]                                                                                          24.7kB/s 0s
gzip: stdin: not in gzip format
Errhttp://archive.ubuntu.com edgy/universe Packages                                                                         
  Sub-process gzip returned an error code (1)
Fetched 199B in 30s (7B/s)                                                                                                  
Failed to fetch [http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz)  301 Moved Permanently
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by nathanbriggs on 2007-04-10
I am also getting errors with apt-get update
various ones including a 
[waiting for headers]
apparently fixed by changing http to ftp
and a ridiculously slow update

figured it was me so got a new clean feisty update and found the same problems

is apt-get update deprecated now and if so what should I use as this error in the repository seems to have been around for 5 months at least

---

### Post by pcrew on 2007-06-21
I am still getting this error on fresh install of fiesty 7.0.4 on amd64.

> cat souces.list
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted 
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-security multiverse


and the errors i get:
> apt-get update
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070418) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070418) feisty/restricted Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070418) feisty/multiverse Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070418) feisty/universe Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Sources
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources [1710B]              
99% [4 Sources bzip2 0] [Waiting for headers]                       22.4kB/s 0s
bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Sources                        
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Sources                          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages [48.6kB]          
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Sources                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages              
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources [6610B]           
75% [6 Sources bzip2 0] [Connecting to proxy.vmware.com (10.16.65.254)]        
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Sources             
  Sub-process bzip2 returned an error code (2)
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Sources               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages                
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Sources [1855B]       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Sources               
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages [1304kB]                  
96% [8 Packages gzip 0] [Waiting for headers]                       22.4kB/s 2s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages                             
  Sub-process gzip returned an error code (1)
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages [7037B]             
96% [9 Packages gzip 0] [Waiting for headers]                       22.4kB/s 2s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages                       
  Sub-process gzip returned an error code (1)
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages [183kB]            
97% [10 Packages gzip 0] [Waiting for headers]                      22.4kB/s 2s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages                       
  Sub-process gzip returned an error code (1)
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources [63.5kB]            
97% [11 Sources gzip 0] [Waiting for headers]                       22.4kB/s 2s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Sources                        
  Sub-process gzip returned an error code (1)
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages [61.8kB]         
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages                     
  Error reading from server - read (104 Connection reset by peer)
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages [6102B]   
93% [13 Packages gzip 0] [Connecting to proxy.vmware.com (10.16.65.254)]       
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages       
  Sub-process gzip returned an error code (1)
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages [15.9kB]    
94% [14 Packages gzip 0]                                             262kB/s 0s
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages                
  Sub-process gzip returned an error code (1)
Fetched 5797B in 12s (471B/s)                                                  
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release amd64 (20070418)]/dists/feisty/Release  Unable to find expected entry  multiverse/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/source/Sources.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-amd64/Packages.gz)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


Troubleshooting Done:
- re-installation of Fiesty
- apt-get clean; apt-get-check; apt-get update
- deleted lists folder /var/lib/apt/ and re-created /var/lib/apt/lists and /var/lib/apt/lists/partial
- ensured that my proxy settings are configured in my shell environment, synpatics pacakge manger preferences and in apt.conf file
- changed all instances of http:// to ftp:// in the sources.list file


is there a solution to this problem ???

---

### Post by auburn on 2007-06-22
same problem here. I'm behind a NYC Dept of Education  proxy. I haven't tried ftp, yet. I get:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/feisty/unverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/feisty/unverse/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

I've also tried the US repository.

---

### Post by pcrew on 2007-11-12
Found Solution:

add the following line to /etc/apt/apt.conf

Acquire::http::Pipeline-Depth "0";


Do a sync couple of times and you should probably be all set.

---

### Post by sam.hendley on 2007-11-14
I found that deleting and recreating the /var/lib/apt/lists/partial directory (clearing out whatever was in it) seemed to do the trick.

---

