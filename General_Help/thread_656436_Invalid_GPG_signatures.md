---
title: "Invalid GPG signatures"
date: 2008-01-02
forum: General Help
---

### Post by jms703 on 2008-01-02
I don't know why, but his problem occurs almost weekly.


```
$ sudo apt-get update
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Get:2 http://us.archive.ubuntu.com edgy Release.gpg [191B]                                         
Get:3 http://www.mclean.net.nz stable Release.gpg [191B]                                           
Get:4 http://archive.ubuntu.com edgy Release.gpg [191B]                                            
Get:5 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]                                 
Ign http://debian.websterwood.com edgy Release.gpg                                                 
Ign http://debian.websterwood.com edgy/main Translation-en_US                              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US                        
Ign http://archive.ubuntu.com edgy/universe Translation-en_US                                      
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US                               
Ign http://www.mclean.net.nz stable/contrib Translation-en_US                                      
Hit http://www.mclean.net.nz stable Release                                                        
Ign http://debian.websterwood.com edgy Release                                             
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US                          
Ign http://archive.ubuntu.com edgy/main Translation-en_US                                          
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US                         
Hit http://debian.websterwood.com edgy/main Packages                                               
Ign http://www.mclean.net.nz stable/contrib Packages                                               
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US                    
Ign http://archive.ubuntu.com edgy/restricted Translation-en_US                                    
Hit http://us.archive.ubuntu.com edgy Release                                                      
Hit http://us.archive.ubuntu.com edgy-updates Release                                              
Hit http://debian.websterwood.com edgy/main Sources                                                
Hit http://security.ubuntu.com edgy-security Release                                               
Hit http://security.ubuntu.com edgy-security/main Packages                                 
Ign http://archive.ubuntu.com edgy/multiverse Translation-en_US      
Hit http://security.ubuntu.com edgy-security/restricted Packages                           
Hit http://www.mclean.net.nz stable/contrib Packages                                               
Hit http://security.ubuntu.com edgy-security/main Sources                                          
Hit http://security.ubuntu.com edgy-security/restricted Sources                                   
Hit http://archive.ubuntu.com edgy Release                                                        
Hit http://security.ubuntu.com edgy-security/universe Packages                                    
Hit http://us.archive.ubuntu.com edgy/main Sources
Hit http://us.archive.ubuntu.com edgy/restricted Sources                      
Get:6 http://us.archive.ubuntu.com edgy-updates Release [50.9kB]              
Ign http://us.archive.ubuntu.com edgy-updates Release                         
Hit http://archive.ubuntu.com edgy/universe Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Packages
Hit http://us.archive.ubuntu.com edgy-updates/restricted Packages
Hit http://us.archive.ubuntu.com edgy-updates/main Sources                    
Hit http://us.archive.ubuntu.com edgy-updates/restricted Sources              
Hit http://archive.ubuntu.com edgy/main Packages                              
Hit http://archive.ubuntu.com edgy/restricted Packages
Hit http://archive.ubuntu.com edgy/multiverse Packages
Fetched 51.1kB in 2s (24.9kB/s)                      
Reading package lists... Done
W: GPG error: http://us.archive.ubuntu.com edgy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
```


Re-running apt-get update does not correct this problem.

What is the problem and how do I resolve this?

---

### Post by jms703 on 2008-01-02
I am behind a transparent proxy.

I verified that the problem is a caching issue.

This command works:

```
apt-get update -o Acquire::http::No-Cache=True
```

How can I set apt-get to do this all the time?

---

### Post by MalfunctioningMartian on 2008-02-11
You could try adding a bash alias.

[http://www.ss64.com/bash/alias.html](http://www.ss64.com/bash/alias.html)

---

