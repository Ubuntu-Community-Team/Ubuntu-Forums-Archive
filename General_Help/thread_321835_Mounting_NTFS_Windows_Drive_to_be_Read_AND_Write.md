---
title: "Mounting NTFS Windows Drive to be Read AND Write"
date: 2006-12-19
forum: General Help
---

### Post by computerwiz3491 on 2006-12-19
I was wondering if anyone knows of a way, besides for the one listed on the unofficial Ubuntu guide, for me to mount my NTFS Drive in Ubuntu.

Thanks

---

### Post by meng on 2006-12-19
I'm not sure what method is listed in the unofficial guide, and I'm not going to waste my time trying to google the answer. I merely suggest:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by computerwiz3491 on 2006-12-19
That's the method I was reffering to. I get 

```
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
  ntfs-3g: Depends: fuse-utils (>= 2.5) but it is not installable
           Depends: libfuse2 but it is not installable
```

Can anyone figure out what's wrong?

Thank You

---

### Post by bodhi.zazen on 2006-12-19
Not to ask the obvious, but have you enabled your repositories?

---

### Post by tari on 2006-12-19
I'd surmise that fuse-utils is in either the universe or multiverse repository.  Enable those, the n try again.

---

### Post by computerwiz3491 on 2006-12-19
> **bodhi.zazen said:**
> Not to ask the obvious, but have you enabled your repositories?

I did enable my respositories, and just now, I double checked and got the same thing as before. 

I don't know if this is important, but when I did 
```
sudo apt-get install ntfs-3g
```

I got ```
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]                     
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                   
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US        
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://ntfs-3g.sitesweetsite.info edgy Release.gpg
Ign http://ntfs-3g.sitesweetsite.info edgy/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy/universe Translation-en_US
Ign http://ntfs-3g.sitesweetsite.info edgy Release
Hit http://security.ubuntu.com edgy-security/main Packages
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com edgy-updates/universe Translation-en_US
Get:4 http://us.archive.ubuntu.com edgy-backports Release.gpg [191B]
Ign http://us.archive.ubuntu.com edgy-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com edgy-backports/restricted Translation-en_US
Ign http://ntfs-3g.sitesweetsite.info edgy/main Packages
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://ntfs-3g.sitesweetsite.info edgy/main Packages
Ign http://us.archive.ubuntu.com edgy-backports/universe Translation-en_US
Ign http://us.archive.ubuntu.com edgy-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com edgy Release
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates Release
Get:5 http://us.archive.ubuntu.com edgy-backports Release [23.3kB]
Ign http://us.archive.ubuntu.com edgy/main Packages
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources
Hit http://us.archive.ubuntu.com edgy/universe Packages
Get:6 http://us.archive.ubuntu.com edgy/universe Sources [1068kB]
Hit http://us.archive.ubuntu.com edgy/universe Packages                        
Hit http://us.archive.ubuntu.com edgy-updates/main Packages                    
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages              
Hit http://us.archive.ubuntu.com edgy-updates/main Sources                     
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources               
Hit http://us.archive.ubuntu.com edgy-updates/universe Packages                
Get:7 http://us.archive.ubuntu.com edgy-backports/main Packages [1301B]        
Get:8 http://us.archive.ubuntu.com edgy-backports/restricted Packages [14B]    
Get:9 http://us.archive.ubuntu.com edgy-backports/universe Packages [10.2kB]   
Get:10 http://us.archive.ubuntu.com edgy-backports/multiverse Packages [1583B] 
Get:11 http://us.archive.ubuntu.com edgy-backports/main Sources [685B]         
Get:12 http://us.archive.ubuntu.com edgy-backports/restricted Sources [14B]    
Get:13 http://us.archive.ubuntu.com edgy-backports/universe Sources [3325B]    
Get:14 http://us.archive.ubuntu.com edgy-backports/multiverse Sources [720B]   
Get:15 http://us.archive.ubuntu.com edgy/main Packages [1220kB]                
99% [15 Packages gzip 0] [6 Sources bzip2 892928]                   65.5kB/s 0s
gzip: stdin: not in gzip format
Err http://us.archive.ubuntu.com edgy/main Packages                            
  Sub-process gzip returned an error code (1)
Fetched 1109kB in 19s (57.1kB/s)                                               
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: Duplicate sources.list entry http://us.archive.ubuntu.com edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

Thank You

---

### Post by bodhi.zazen on 2006-12-20
sorry, I missed your reply.

Some of the error messages indicate duplicate sources, no problem per se....
[indent]you could edit /etc/apt/sources.list and eliminate (add a # in the front of) any duplicates if you wanted ... [/indent]

Te other error is a little more  problematic....

> Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main Packages

Try ```
sudo aptitude update
```And see what happens.

If OK then proceed with installing ntfs-3g ....

---

### Post by computerwiz3491 on 2006-12-21
Thank you everybody for attempting to help me. I discovered that my Ubuntu installation was flawed, and that's why I had been having trouble. I reinstalled, and everything works now.

---

