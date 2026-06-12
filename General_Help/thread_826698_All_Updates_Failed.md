---
title: "All Updates Failed ??"
date: 2008-06-12
forum: General Help
---

### Post by Masterart on 2008-06-12
Whenever I try to Install updates with update manager, terminal
or synaptic the installation fails with error:
var/cache/apt
files lists file for 'language pack en' missing final newline.

Now i can't install any thing.:(

please help.

---

### Post by kesman on 2008-06-12
In terminal, run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
and post the output here with copy/paste.

---

### Post by Masterart on 2008-06-12
It gives an error :


```

user@comp:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/main Translation-en_IN
Ign cdrom://Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423) hardy/restricted Translation-en_IN
Get:1 http://download.tuxfamily.org ./ Release.gpg [197B]                      
Hit http://security.ubuntu.com hardy-security Release.gpg            
Ign http://security.ubuntu.com hardy-security/main Translation-en_IN 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_IN
Hit http://in.archive.ubuntu.com hardy Release.gpg                   
Ign http://in.archive.ubuntu.com hardy/main Translation-en_IN        
Ign http://download.tuxfamily.org ./ Translation-en_IN                         
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_IN     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_IN       
Hit http://security.ubuntu.com hardy-security Release                          
Ign http://in.archive.ubuntu.com hardy/restricted Translation-en_IN            
Ign http://in.archive.ubuntu.com hardy/multiverse Translation-en_IN            
Ign http://in.archive.ubuntu.com hardy/universe Translation-en_IN              
Hit http://security.ubuntu.com hardy-security/main Packages                    
Hit http://security.ubuntu.com hardy-security/restricted Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/main Sources                     
Get:2 http://download.tuxfamily.org ./ Release [956B]                          
Ign http://download.tuxfamily.org ./ Release                         
Hit http://security.ubuntu.com hardy-security/restricted Sources    
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Get:3 http://download.tuxfamily.org ./ Packages [9639B]                        
Hit http://in.archive.ubuntu.com hardy Release                                 
Hit http://in.archive.ubuntu.com hardy/main Packages                           
Hit http://in.archive.ubuntu.com hardy/restricted Packages                     
Hit http://in.archive.ubuntu.com hardy/multiverse Packages
Hit http://in.archive.ubuntu.com hardy/main Sources
Hit http://in.archive.ubuntu.com hardy/restricted Sources
Hit http://in.archive.ubuntu.com hardy/universe Packages
Hit http://in.archive.ubuntu.com hardy/universe Sources
Fetched 10.8kB in 34s (316B/s)
Reading package lists... Done
W: GPG error: http://download.tuxfamily.org ./ Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 73E6B0FAA42A6CF5
W: You may want to run apt-get update to correct these problems

```

---

### Post by kesman on 2008-06-12
Seems like you have added a tuxfamily repository, which isn't working as it should be. Go to system -> software sources -> 3rd party repositories and remove the tuxfamily thing, then run the given commands again.

---

### Post by Masterart on 2008-06-12
I have Already removed unknown repositories.

But still the error installing :
```

E: /var/cache/apt/archives/fglrx-control_8-3+2.6.24.13-18.41_i386.deb: 
files list file for package `language-pack-en' is missing final newline

```Now What does that means?

Is some very very important system file missing?

---

### Post by kesman on 2008-06-12
Dunno, but I'd suggest you to reinstall those packages and see if it helps.
First remove them completely with
```

sudo apt-get purge packagenamehere

```
and the install them again.

---

### Post by Masterart on 2008-06-12
That is the problem !

Nothing will reinstall / update !!

All packages are downloaded but there is problem installing them.

I've tried that too, "language-pack-en" reinstalls without any error!

---

### Post by kesman on 2008-06-12
Run
```

sudo apt-get clean
sudo apt-get autoclean
sudo dpkg --clear-avail

```
and then again updating.

---

### Post by Masterart on 2008-06-12
Nothing, same error again.

Can you please give any idea where to report/investigate this error ?

---

### Post by kesman on 2008-06-12
Well seeing that error message points to a single .deb -file, that is in the apt's cache directory, I can't see any other way than removing or renaming that file and then trying to download it again.
There's tons of threads about almost the same problem. Try googling with the errormessage, or parts of it.

---

### Post by Masterart on 2008-06-12
Ok . Got it . 

[http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/](http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/)

the error was :

files list file for package `language-pack-en' is missing final newline 

the .list file corresponding to that package is corrupted.(why ? I don't know)

the list files are located in[**   /var/lib/dpkg/info/packagename.list **

corrupted list file has a different icon (Unknown file) from other list files (text files)
so you can easily find packagename.list file

Simply moved it to somewhere as a backup. And completely removed that package.
reinstalled that package . and every thing works fine.

Hope this helps others with such problem.

---

