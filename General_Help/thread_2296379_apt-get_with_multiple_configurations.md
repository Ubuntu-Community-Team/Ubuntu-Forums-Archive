---
title: "apt-get with multiple configurations"
date: 2015-09-25
forum: General Help
---

### Post by maxiecool2 on 2015-09-25
hi guys
i am looking for a temporary way to allow when i run apt-get update
it checks the package lists for another system/s, copies to alternative directory/s reads i copy of the installed package list
then when i run the upgrade it downloads the updated packages to a/n alternative directory/s
all when also performing the updating the "host"

the reason why i just want to do this is the internet is down, and im not into using a permanent arrangement like apt-cache etc..
just a simple configuration or a script to attach to apt-.... , while the internet is down i have to go to a friends once a week to connect.

2 of the "offline" systems use a same sources.list
another on uses a separate sources.list

ill check in next week!!

thanks

mat

---

### Post by TheFu on 2015-09-25
There are tools for "offline package management" - a quick search found this: [https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

I use apt-cacher-ng.

---

### Post by maxiecool2 on 2015-09-26
i am not looking for an advanced application, no additional configurations for cli
just A configuration script to go with the regular apt-get update /upgrade
that reads alternative package lists
deposits the package list bundles in alternative directories for the different systems im upgrading (for 2 of the systems it can be a direct copy of /var/lib/apt/lists)
reads the file of the installed packages from the different systems (i assume it it /var/lib/dpkg/status)
downloads the updated packages to alternative directories
and it is all just a temporary measure
currently i am updating at my friends, copy over the /var/lib/apt/lists and current /var/cache/apt/archives, dist-upgrade offline systems, format the sdout to form a list for uget go back to my friends and download updated packages
this method is time consuming, not to meantion that when i go back the packages that needed updating may have been upgraded
 i saw this 
"apt-get -o Dir::Etc::SourceParts=/etc/apt/sources.list.ubuntu install some-new-package"

---

### Post by TheFu on 2015-09-26
If the system is offline. The only reason to patch is for bug fixes you cannot live without. 
This is how military installations with air-gapped networks do it.
Get the largest ISO you can - a 4G DVD and make that your new "repository" as outlined in the line above.

---

### Post by maxiecool2 on 2015-09-27
i think ive found a solution
create a config file

[http://www.debianadmin.com/query-apt-configuration-using-apt-config.html](http://www.debianadmin.com/query-apt-configuration-using-apt-config.html)

Dir "/";
Dir::State "local directory of package list"; #/var/lib/apt/ for destination system
Dir::State::lists "final directory of package list/"; #lists/ for destination system
Dir::State::status "status file location"; #/var/lib/dpkg/status from destination system
Dir::Cache "cache destination directory"; #/var/cache/apt/ for destination system
Dir::Cache::archives "final cache destination directory/"; # archives/ for destination system
Dir::Etc "source list directory"; # /etc/apt/
Dir::Etc::sourcelist "sources.list"; #source list
#Dir::Etc::sourceparts "sources.list.d";  #if you use the sources list directory
Acquire::Queue-Mode "Access";  #download one file at a time (useful for slow internet connection)

created a bash file to use it
rsync to move the actual .deb packages over
scp to copy the "status" and package lists files to the destination system

apt-get update -c="newly created config file" works with upgrade, dist-upgrade and install as well

---

### Post by ian-weisser on 2015-09-27
Glad to see you got it sorted.
Thanks for sharing your solution.

---

