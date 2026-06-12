---
title: "apt-get update problems"
date: 2007-10-19
forum: General Help
---

### Post by Stochastics on 2007-10-19
Hi everyone,

When trying to update the apt, i have the following message :

steeve@steeve-laptop:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Translation-en_CA             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Translation-en_CA           
Get:3 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Translation-en_CA
Get:4 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty Release [57.2kB]
Get:5 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates Release [50.9kB]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Packages  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/restricted Sources
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Packages                  
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Packages            
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/main Sources                   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty-updates/restricted Sources             
Get:6 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages [4912kB]           
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Sources                       
99% [6 Packages gzip 0]                                             17.8kB/s 0s
gzip: stdin: not in gzip format
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) feisty/universe Packages                      
  Sub-process gzip returned an error code (1)
Fetched 108kB in 19s (5419B/s)                                                 
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

What's the problem with my Ubuntu ?

Stochastics

---

### Post by atlfalcons866 on 2007-10-19
do you have synaptic package manager open?

---

### Post by Stochastics on 2007-10-19
Hi,

No, I have no updater open at the time...

---

### Post by atlfalcons866 on 2007-10-19
try restarting then do it again

---

### Post by Stochastics on 2007-10-19
Same things happen...after the restart

---

### Post by davidjmayo on 2007-10-19
I've seen this one come up a couple of times before. Seems the Canada repos is a bit temperamental at times (ie it doesn't work properly all the time sometimes for days)

go into synaptic and change your repos to the US or any other one (there should be a small list to choose from). I don't use Gnome but in one of the menus there is the option to change the repositories you use (probably in Edit and called manage repositoires or something similar). Do that then exit synaptic then do your sudo apt-get update again to point to the new repos. Then continue what you were trying to do

---

