---
title: "Apt question"
date: 2005-08-26
forum: General Help
---

### Post by MdaG on 2005-08-26
When I do a apt-get update I get this:

```
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]             
Get:2 http://se.archive.ubuntu.com hoary Release.gpg [189B]                    
Get:3 http://security.ubuntu.com hoary-security Release [16.9kB]               
Get:4 http://se.archive.ubuntu.com hoary-updates Release.gpg [189B]            
Hit http://se.archive.ubuntu.com hoary Release                                 
Hit http://se.archive.ubuntu.com hoary-updates Release                         
Ign http://se.archive.ubuntu.com hoary Release                                 
Hit http://se.archive.ubuntu.com hoary/main Packages                           
Hit http://security.ubuntu.com hoary-security/main Packages                    
Hit http://security.ubuntu.com hoary-security/restricted Packages              
Hit http://security.ubuntu.com hoary-security/main Sources                     
Hit http://security.ubuntu.com hoary-security/restricted Sources               
Hit http://se.archive.ubuntu.com hoary/restricted Packages                     
Hit http://se.archive.ubuntu.com hoary/main Sources                            
Hit http://se.archive.ubuntu.com hoary/restricted Sources                      
Hit http://security.ubuntu.com hoary-security/universe Packages                
Hit http://security.ubuntu.com hoary-security/universe Sources                 
Hit http://se.archive.ubuntu.com hoary/universe Packages                       
Hit http://se.archive.ubuntu.com hoary/universe Sources     
Hit http://se.archive.ubuntu.com hoary-updates/main Packages
Hit http://se.archive.ubuntu.com hoary-updates/restricted Packages
Hit http://se.archive.ubuntu.com hoary-updates/main Sources 
Hit http://se.archive.ubuntu.com hoary-updates/restricted Sources
Get:5 http://archive.ubuntu.com hoary Release.gpg [189B]    
Hit http://archive.ubuntu.com hoary Release           
Ign http://archive.ubuntu.com hoary Release
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/multiverse Sources
Fetched 17.4kB in 2s (7444B/s)
Reading package lists... Done
W: GPG error: http://se.archive.ubuntu.com hoary Release: The following signatur es were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <f tpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com hoary Release: The following signatures  were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpm aster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

```

What am I doing wrong?

---

### Post by heimo on 2005-08-26
You're probably doing nothing wrong. I was using se-mirrors and got this problem just little time ago, switched to using us mirrors for now - mirror admins will hopefully fix this. Or you can try fi mirrors, if that's faster for you. (edit /etc/apt/source.list or using Synaptic)


EDIT: reread your message. Not sure if that'll fix all of those.

---

