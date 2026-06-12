---
title: "Pakage Manager Error"
date: 2007-09-30
forum: General Help
---

### Post by lfever on 2007-09-30
I recently did a fresh Feisty Fawn install. During some downloads and installations I now get the following error and cannot use the Synaptic Package Manager.

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Encountered status field in a non-version description, E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'

Please Help!
Thanks lfever  :sad:

---

### Post by faceless-21 on 2007-09-30
do you remember offhand what it was that you downloaded(or perhaps failed to download/install...  or at least I get that message alot after failed installs) before this happened?
  I used the "sudo dpkg --remove --force-remove-(etc..) commands to remove things like virtual box...
try using the "sudo dpkg --configure -a" command(followed by your pw) and tell me what you see...

---

### Post by lfever on 2007-09-30
Hi faceless-21

I don't remember what I was downloading and installing but here is what I got doing your
suggestion:

msswanson@msswanson-laptop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 14670 package `libscim8c2a':
 `Replaces' field, invalid package name `

Hopefully this will help.

---

### Post by faceless-21 on 2007-09-30
ok try "sudo apt-get install -f" and then post the results...

---

### Post by lfever on 2007-09-30
Here are the results:

Reading package lists... Error!
W: Encountered status field in a non-version description
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

---

### Post by faceless-21 on 2007-09-30
Ok lol, seeing as I am rather new to linux, I have just been researching all this on my own...  So any of my advice should be takin with a "grain of salt".  So here is my idea...  open up a folder browser and copy and paste this "/var/lib/dpkg/status" then do a search for "Package: libscim8c2a"  And see if the status has an error or break in it...  I am kinda running out of steam.  So if we cant fix this soon I am gonna have to call it a night...  No wait.  A morning haha.
  Goodluck!

---

### Post by lfever on 2007-09-30
Here is what my search found:

Package: scim-modules-socket
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 296
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: scim
Version: 1.4.4-7ubuntu1
Replaces: scim-config-socket, scim-frontend-socket, scim-server-socket
Provides: scim-config-socket, scim-frontend-socket, scim-server-socket
Depends: libc6 (>= 2.5-0ubuntu1), libgcc1 (>= 1:4.1.2),[COLOR="Red"] libscim8c2a[/COLOR], libstdc++6 (>= 4.1.2)
Conflicts: scim-config-socket, scim-frontend-socket, scim-server-socket
Description: socket modules for SCIM platform
 SCIM (Smart Common Input Method) is an input method (IM) platform.
 .
 This package provides the socket modules for SCIM.  SCIM can use a local or
 inet socket as the front end and connect to the configuration and IM engine
 modules.  Then other computers and/or environments can share these input
 methods by connecting to the socket with socket IM engine module and socket
 configure module.
 .
 For more information about SCIM, please see the description of scim package.
Original-Maintainer: Ming Hua <minghua@rice.edu>

---

### Post by faceless-21 on 2007-09-30
eh ok that is deffinetly beyond me at this point...  Here is a page I was looking into whilst trying to help you. [http://www.linuxquestions.org/questions/showthread.php?t=155478](http://www.linuxquestions.org/questions/showthread.php?t=155478)  One guy had good luck with using a backup status file.  Or deleting the status file(make sure to back it up first!)  look through that and see if you can find any help...  

  Also, if you google part of the error message(I used the "E: Problem with MergeList /var/lib/dpkg/status" part) that will usually lead you in the right direction.  maybe following it with something like "Ubuntu" which many times leads you to ubuntuforums archives.

  Anyways I gotta get to bed.
  Take care and good luck :D
         faceless

---

### Post by R15I23D05D14Y on 2007-09-30
Open up /var/lib/dpkg/status and search it for "Package: libscim8c2a". Copy that block, and maybe the one after it. Something is probably malformed there.

---

### Post by lfever on 2007-09-30
Thanks for your help.

I will look this over after I get some zzzzzzzzzzzzzzz's myself 

Thanks again
lfever

---

### Post by lfever on 2007-09-30
Hi Again,

After considerable head scratching and reading I believe I have narrowed things down a bit more but, I'm not sure what to do at this point :confused:

msswanson@msswanson-laptop:~$ dpkg -l
dpkg-query: parse error, in file `/var/lib/dpkg/status' near line 14670 package `libscim8c2a':
 `Replaces' field, invalid package name `

Any help would be greatly appreciated.

Thanks
lfever

---

### Post by SeanTater on 2007-09-30
Have you tried to update the package list from the internet?

```
sudo apt-get update
```

It may not help, but there's no reason not to try..

---

### Post by lfever on 2007-09-30
Hi SeanTater,

Yes I have tried apt-get update, here is what I get:

msswanson@msswanson-laptop:~$ sudo apt-get update
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Translation-en_US  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/restricted Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/main Packages           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources                
Fetched 4B in 6s (1B/s)                                                        
Reading package lists... Error!
W: Encountered status field in a non-version description
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.


Any ideas????? :sad:

---

### Post by lfever on 2007-10-04
***Success at last.** * :)

The problem was in the dpkg status file. I couldn't figure out just what the problem was but saved a copy of it to study over and see if I can figure it out. I replaced the status with the status-old and all is well. 

Thanks to all for the help ):P
lfever

---

