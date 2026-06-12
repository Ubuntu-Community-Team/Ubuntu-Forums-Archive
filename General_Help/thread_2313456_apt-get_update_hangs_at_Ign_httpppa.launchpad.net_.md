---
title: "apt-get update hangs at Ign http://ppa.launchpad.net wily/main Translation-en"
date: 2016-02-12
forum: General Help
---

### Post by btnadiga on 2016-02-12
apt-get update produces 

                                                  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                                                      
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                                                       
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en_US                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                                                      
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main amd64 Packages                                                      
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main i386 Packages                                                       
  404  Not Found
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en_US                                                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) wily/main Translation-en                                                      
100% [Waiting for headers]                                                                                 

and hangs here. What sources do I get rid of and how do I get rid of them??
Thanks

---

### Post by ajgreeny on 2016-02-12
Show us the output of ls ```
/etc/apt/sources.list.d
```and we can tell you what to remove.

Or you can open software-sources GUI, "Other software" tab and look for the entry (or entries) for launchpad.net wily/main and deselect them, then refresh the repos.

---

