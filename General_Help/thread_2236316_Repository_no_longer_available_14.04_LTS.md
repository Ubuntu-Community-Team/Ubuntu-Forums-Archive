---
title: "Repository no longer available 14.04 LTS"
date: 2014-07-25
forum: General Help
---

### Post by xdavis1990 on 2014-07-25
Hey all, still somewhat new to Ubuntu and today I have a red excalmation mark near the top right corner of my desktop. When selected it reads:

 The update information is outdated. This may be caused by network problems or by a repository no longer being available. Please update manually by selecting 'Show Updates' from the indicator menu and watching for any failing repositories.  

When I click 'Show Updates' as requested, a Software Updater window pops up stating that my computer is up to date. Only other thing I could think of to try was ```
sudo apt-get update
```

The result was this:

> Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main amd64 Packages                       
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted amd64 Packages                 
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe amd64 Packages                   
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse amd64 Packages                 
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages                        
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages                  
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/universe i386 Packages                    
  404  Not Found [IP: 91.189.92.200 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/multiverse i386 Packages                  
  404  Not Found [IP: 91.189.92.200 80]
Fetched 1,569 kB in 13s (113 kB/s)                                             
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-amd64/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/multiverse/binary-i386/Packages)  404  Not Found [IP: 91.189.92.200 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.


I can only assume the problem is these old raring packages, which I honestly can't remember why I needed to have them on here. Are they the issue, and if so what is the best way to go about removing them. New enough I'm a little nervous to mess around with Repositories without a little guidance.

---

### Post by grahammechanical on 2014-07-25
Yes they are the problem as Ubuntu 13.04 Raring Ringtail has long reached End of Life and its archives/repositories are now closed. Try going to System Settings>Software and Updates and seeing if that will let you remove those software sources.

Regards.

---

### Post by xdavis1990 on 2014-07-25
Awesome! Thank you, so simple. Guess I just wanted it to be a lot more complex than it was. Thanks again

---

