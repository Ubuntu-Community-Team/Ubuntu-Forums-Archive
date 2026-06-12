---
title: "Distro-Upgrade failed to fetch"
date: 2013-10-27
forum: General Help
---

### Post by patrycjusz-rozanski on 2013-10-27
Hi all
I have try to upgrade 13.04 automaticly it stops and not getting humanity-icon-theme


So i try to make it by console to see what hapend and hire is my problem:

```

 Continue [yN]  Details [d]y


Fetching
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4 
  Connection failed [IP: 91.189.91.15 80]                                      
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4 
  Connection failed [IP: 91.189.92.176 80]                                     
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4 
  Connection failed [IP: 91.189.92.200 80]                                     
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4 
  Connection failed [IP: 91.189.92.202 80]                                     
Fetched 0 B in 6s (0 B/s)                                                      
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4                                     
  Connection failed [IP: 91.189.91.15 80]                                                                          
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4                                     
  Connection failed [IP: 91.189.92.176 80]                                                                         
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4                                     
  Connection failed [IP: 91.189.92.200 80]                                                                         
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4                                     
  Connection failed [IP: 91.189.92.202 80]                                                                         
Fetched 0 B in 6s (0 B/s)                                                                                          
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4                                     
  Connection failed [IP: 91.189.91.15 80]                                                                          
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4                                     
  Connection failed [IP: 91.189.92.176 80]                                                                         
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4                                     
  Connection failed [IP: 91.189.92.200 80]                                                                         
Err http://archive.ubuntu.com/ubuntu/ saucy/main humanity-icon-theme all 0.6.4                                     
  Connection failed [IP: 91.189.92.202 80]                                                                         
Fetched 0 B in 6s (0 B/s)                                                                                          


Could not download the upgrades 


The upgrade has aborted. Please check your Internet connection or 
installation media and try again. All files downloaded so far have 
been kept. 


Failed to fetch 
http://archive.ubuntu.com/ubuntu/pool/main/h/humanity-icon-theme/humanity-icon-theme_0.6.4_all.deb 
Connection failed [IP: 91.189.92.202 80] 



```

I cant pass upgrade becouse Icon THEME?
and i don't know what to do with it.

When i'm going to this addres on the web browser I can download it. Don't know why console (upgrade) cant fetch it.
Any sugestions?

---

### Post by ibjsb4 on 2013-10-27
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) saucy/main humanity-icon-theme all 0.6.4

That address is not correct.  Did you manually add this address?  I ask because it has two typo's in it (a space before saucy and no slash after main) and leads to nowhere.  Look at the difference:

[http://archive.ubuntu.com/ubuntu/dists/saucy/main/](http://archive.ubuntu.com/ubuntu/dists/saucy/main/)

Are you using the software center to install humanity-icon-theme?

---

