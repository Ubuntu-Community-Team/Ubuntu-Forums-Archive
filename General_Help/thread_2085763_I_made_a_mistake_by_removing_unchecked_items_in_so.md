---
title: "I made a mistake by removing unchecked items in software sources"
date: 2012-11-18
forum: General Help
---

### Post by Dodeca on 2012-11-18
Hello all ...

I recently upgraded this computer from 10.04 to 12.04 

and I noticed a lot of unchecked items in the software sources ...

I thought I was "cleaning up" my pc ...

NOW ... I do not receive updates.

and that's not good !

I kept anything that was checked ... so I don't know what I did wrong ?


[[IMG]http://www.postimg.com/thumbs/92000/software_sources-91628.jpg[/IMG]]("http://www.postimg.com/image/92000/software_sources-91628.jpg")


[[IMG]http://www.postimg.com/thumbs/92000/update_manager_error_message-91629.jpg[/IMG]]("http://www.postimg.com/image/92000/update_manager_error_message-91629.jpg")

---

### Post by Aaron Christianson on 2012-11-18
Try removing the sources completely (with the remove button) and adding them again the same way you did at first.

If that doesn't work, there is probably a problem with the PPA itself, and you should just remove it until the problem is fixed.

---

### Post by ibjsb4 on 2012-11-18
You didn't do anything wrong.  Akirad has not been updated for 12o4; actually it hasn't been updated for 136 weeks.  Remove it  :)

[https://launchpad.net/~akirad/+archive/akirad](https://launchpad.net/~akirad/+archive/akirad)

---

### Post by Dodeca on 2012-11-19
> **Aaron Christianson said:**
> Try removing the sources completely (with the remove button) and adding them again the same way you did at first.

If that doesn't work, there is probably a problem with the PPA itself, and you should just remove it until the problem is fixed.


I tried your suggestion ... still broke.

---

### Post by Dodeca on 2012-11-19
> **ibjsb4 said:**
> You didn't do anything wrong.  Akirad has not been updated for 12o4; actually it hasn't been updated for 136 weeks.  Remove it  :)

[https://launchpad.net/~akirad/+archive/akirad](https://launchpad.net/~akirad/+archive/akirad)



ok ... something is wrong somewhere ... I get an error message and NO updates?

---

### Post by Dodeca on 2012-11-19
Let me state for clarity ... what I removed was unchecked items in the "other software" section of software sources ... just like my uploaded image shows 6 items in a list  and the middle 2 are unchecked. ( I assumed unused and I removed them )

---

### Post by ibjsb4 on 2012-11-19
Lets have a look

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And please post

---

### Post by Dodeca on 2012-11-19
> **ibjsb4 said:**
> Lets have a look

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

sudo apt-get update

And please post

Ok ... after I did this I tried and update and did come up with a "recommended update" ... so MAYBE I am getting updates .

Ok ... did some testing ... I am getting updates ... 

I thought I knew about ubuntu ... 

thanks for the help !

( I seem to have removed the error message by unchecking items in the "other software" list but not deleting those items )





```
Ign http://mirrors.se.eu.kernel.org precise InRelease
Ign http://mirrors.se.eu.kernel.org precise-updates InRelease                                          
Hit http://mirrors.se.eu.kernel.org precise Release.gpg                                                 
Get:1 http://mirrors.se.eu.kernel.org precise-updates Release.gpg [198 B]                               
Hit http://mirrors.se.eu.kernel.org precise Release                                                                                 
Get:2 http://mirrors.se.eu.kernel.org precise-updates Release [49.6 kB]                                 
Hit http://mirrors.se.eu.kernel.org precise/main Sources                                            
Ign http://security.ubuntu.com precise-security InRelease                                      
Ign http://ppa.launchpad.net precise InRelease                        
Ign http://ppa.launchpad.net precise InRelease                        
Hit http://mirrors.se.eu.kernel.org precise/restricted Sources        
Hit http://mirrors.se.eu.kernel.org precise/universe Sources
Hit http://mirrors.se.eu.kernel.org precise/multiverse Sources
Hit http://mirrors.se.eu.kernel.org precise/main i386 Packages
Hit http://mirrors.se.eu.kernel.org precise/restricted i386 Packages
Hit http://mirrors.se.eu.kernel.org precise/universe i386 Packages
Hit http://mirrors.se.eu.kernel.org precise/multiverse i386 Packages
Hit http://mirrors.se.eu.kernel.org precise/main TranslationIndex
Hit http://mirrors.se.eu.kernel.org precise/multiverse TranslationIndex
Hit http://mirrors.se.eu.kernel.org precise/restricted TranslationIndex
Hit http://mirrors.se.eu.kernel.org precise/universe TranslationIndex
Get:3 http://mirrors.se.eu.kernel.org precise-updates/restricted i386 Packages [8,374 B]
Get:4 http://mirrors.se.eu.kernel.org precise-updates/main i386 Packages [437 kB] 
Hit http://security.ubuntu.com precise-security Release.gpg                                           
Ign http://ppa.launchpad.net precise Release.gpg                                                      
Ign http://ppa.launchpad.net precise Release.gpg                                                      
Hit http://security.ubuntu.com precise-security Release                       
Get:5 http://mirrors.se.eu.kernel.org precise-updates/multiverse i386 Packages [9,661 B]
Get:6 http://mirrors.se.eu.kernel.org precise-updates/universe i386 Packages [155 kB]              
Ign http://ppa.launchpad.net precise Release                                                      
Get:7 http://mirrors.se.eu.kernel.org precise-updates/main TranslationIndex [3,564 B]
Get:8 http://mirrors.se.eu.kernel.org precise-updates/multiverse TranslationIndex [2,605 B]               
Get:9 http://mirrors.se.eu.kernel.org precise-updates/restricted TranslationIndex [2,461 B]                
Get:10 http://mirrors.se.eu.kernel.org precise-updates/universe TranslationIndex [2,850 B]                 
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                                    
Hit http://mirrors.se.eu.kernel.org precise/main Translation-en        
Hit http://mirrors.se.eu.kernel.org precise/multiverse Translation-en
Hit http://mirrors.se.eu.kernel.org precise/restricted Translation-en
Hit http://mirrors.se.eu.kernel.org precise/universe Translation-en
Get:11 http://mirrors.se.eu.kernel.org precise-updates/main Translation-en [211 kB]
Ign http://ppa.launchpad.net precise Release                                                                 
Hit http://security.ubuntu.com precise-security/main i386 Packages                                           
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages              
Hit http://security.ubuntu.com precise-security/universe i386 Packages                                      
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                       
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                 
Hit http://mirrors.se.eu.kernel.org precise-updates/multiverse Translation-en                               
Hit http://mirrors.se.eu.kernel.org precise-updates/restricted Translation-en
Get:12 http://mirrors.se.eu.kernel.org precise-updates/universe Translation-en [92.9 kB]
Ign http://ppa.launchpad.net precise/main TranslationIndex                                               
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                   
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                     
Hit http://security.ubuntu.com precise-security/main Translation-en                                           
Ign http://ppa.launchpad.net precise/main TranslationIndex             
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Err http://ppa.launchpad.net precise/main i386 Packages                
  404  Not Found
Err http://ppa.launchpad.net precise/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_US
Ign http://ppa.launchpad.net precise/main Translation-en
Fetched 976 kB in 5s (170 kB/s)                  
W: Failed to fetch http://ppa.launchpad.net/akirad/akirad/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/akirad/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

