---
title: "Depency problems ..."
date: 2016-01-13
forum: General Help
---

### Post by Simanis on 2016-01-13
Gaah! I'm brand new to all things Linux and Ubuntu since only three weeks, but everything has run real smooth ... until now. Something went wrong starting with my Adobe Flash apparently being outdated (or so it said), and for a time any videos wouldn't play. That however was fixed, but in the process Audacity disappeared, and now refuse to be re-installed, due to dependency problems. While trying to sort that out - being a complete novice - I seemed to make matters only worse. Now I get a System Program Problem on every startup, and I don't know what to do.

I hope someone will help me, but I'm afraid I also need to help to know what kind of information I should provide - and how to find it!

---

### Post by grahammechanical on 2016-01-13
The dialog that is informing you that there is a system problem should also be asking you if you want to report the problem. Accept that offer and an attempt will be made to collect various log files. The next dialog should have a Show Details button. Clicking that button will give more information as to what actually crashed. There will also be a box that is ticked to confirm the reporting of the crash. Untick that box and nothing will be sent to the Ubuntu developers but you will now have some information as to what utility or system service crashed.

Also you should run these two commands and post the output from the commands into this thread.

```
sudo apt-get update
sudo apt-get upgrade
```

At the moment you have more knowledge of the problems than we do. 

Regards.

---

### Post by Simanis on 2016-01-13
Thank you for your reply. First, I have to say that my machine is in Swedish. I tried changing it back to English, but I can't seem to do that now with these problems. Hopefully, you'll still be able to help me.

I got the system problem dialogue box before, but now I don't seem to get it anymore. I only a have a red circle with a white line in the upper line to the right, where it says that there is an error "BrokenCount>0", and that it normally means that my system has dependency problems.

"sudo apt-get update" gives me this:
```
user@user-desktop:~$ sudo apt-get update
[sudo] password for user: 
Bra [http://repository.spotify.com](http://repository.spotify.com) stable InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Läs:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease [64,4 kB]           
Läs:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease [15,5 kB]                      
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Bra [http://repository.spotify.com](http://repository.spotify.com) stable/non-free amd64 Packages               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty InRelease                              
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Bra [http://repository.spotify.com](http://repository.spotify.com) stable/non-free i386 Packages                
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main amd64 Packages                        
Läs:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [103 kB]         
Läs:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates InRelease [64,4 kB]          
Bra [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Läs:5 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages [17,4 kB]            
Läs:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports InRelease [64,5 kB]        
Läs:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages [16,8 kB]             
Läs:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [4 035 B]  
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-sv_SE            
Läs:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [32,7 kB]    
Läs:10 [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en [10,5 kB]           
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-sv               
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en_US            
Ign [http://repository.spotify.com](http://repository.spotify.com) stable/non-free Translation-en               
Läs:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [2 357 B] 
Läs:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [404 kB] 
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release.gpg                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-sv_SE                     
Läs:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Sources [248 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-sv                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en            
Läs:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [13,0 kB]
Läs:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [123 kB]
Läs:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Sources [5 359 B]
Läs:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Sources [146 kB]   
Läs:18 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [4 798 B]
Läs:19 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [379 kB]  
Läs:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Sources [5 161 B]
Läs:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main amd64 Packages [683 kB]
Läs:22 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [12,7 kB]
Läs:23 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [123 kB]
Läs:24 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [4 955 B]
Bra [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en             
Bra [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en       
Bra [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en       
Bra [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en         
Läs:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted amd64 Packages [15,9 kB]
Läs:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe amd64 Packages [333 kB]
Läs:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse amd64 Packages [13,0 kB]
Läs:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main i386 Packages [659 kB] 
Läs:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted i386 Packages [15,6 kB]
Läs:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe i386 Packages [334 kB]
Läs:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [13,1 kB]
Läs:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/main Translation-en [343 kB]
Läs:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/multiverse Translation-en [6 832 B]
Läs:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/restricted Translation-en [3 699 B]
Läs:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-updates/universe Translation-en [175 kB]
Läs:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Sources [8 221 B]    
Läs:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Sources [28 B] 
Läs:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Sources [33,2 kB]
Läs:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Sources [1 898 B]
Läs:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main amd64 Packages [9 402 B]
Läs:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted amd64 Packages [28 B]
Läs:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe amd64 Packages [39,7 kB]
Läs:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse amd64 Packages [1 571 B]
Läs:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main i386 Packages [9 411 B]
Läs:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted i386 Packages [28 B]
Läs:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe i386 Packages [39,7 kB]
Läs:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse i386 Packages [1 552 B]
Läs:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/main Translation-en [5 549 B]
Läs:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/multiverse Translation-en [1 215 B]
Läs:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/restricted Translation-en [14 B]
Läs:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty-backports/universe Translation-en [34,6 kB]
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty Release                                
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Sources                           
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Sources                     
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Sources                       
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Sources                     
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main amd64 Packages                    
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted amd64 Packages              
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe amd64 Packages                
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse amd64 Packages              
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main i386 Packages                     
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted i386 Packages               
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe i386 Packages                 
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse i386 Packages               
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-sv                    
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en                    
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-sv              
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en              
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-sv              
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en              
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-sv                
Bra [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-sv_SE                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/main Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-sv_SE           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/multiverse Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-sv_SE           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-sv_SE             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) trusty/universe Translation-en_US             
Hämtade 4 645 kB på 30s (155 kB/s)                                             
Läser paketlistor... Färdig
W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free amd64 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-amd64_Packages)
W: Duplicate sources.list entry [http://repository.spotify.com/](http://repository.spotify.com/) stable/non-free i386 Packages (/var/lib/apt/lists/repository.spotify.com_dists_stable_non-free_binary-i386_Packages)
W: Du kan möjligen rätta till problemet genom att köra "apt-get update"
```

"sudo apt-get upgrade" gives me this:
```
user@user-desktop:~$ sudo apt-get upgrade
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Du bör köra "apt-get -f install" för att korrigera dessa.
Följande paket har beroenden som inte kan tillfredsställas:
 vdpau-va-driver : Beroende av: libvdpau1 (>= 0.2) men det är inte installerat
E: Otillfredsställda beroenden. Prova med -f.
```

So after this I also tried with "sudo apt-get install -f", which gives me this:
```
user@user-desktop:~$ sudo apt-get install -f
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Korrigerar beroenden... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  libdrm-amdgpu1 libllvm3.7 libomxil-bellagio-bin libomxil-bellagio0
  libswscale2 libva-glx1 libva-x11-1 libvdpau-va-gl1
Use 'apt-get autoremove' to remove them.
Följande ytterligare paket kommer att installeras:
  libvdpau1
Rekommenderade paket:
  vdpau-driver-all vdpau-driver
Följande NYA paket kommer att installeras:
  libvdpau1
0 att uppgradera, 1 att nyinstallera, 0 att ta bort och 7 att inte uppgradera.
2 är inte helt installerade eller borttagna.
Behöver hämta 0 B/27,8 kB arkiv.
Efter denna åtgärd kommer ytterligare 124 kB utrymme användas på disken.
Vill du fortsätta? [J/n] j
(Läser databasen ... 205687 filer och kataloger installerade.)
Förbereder att packa upp .../libvdpau1_1.1.1-3~gd~t_amd64.deb ...
Packar upp libvdpau1:amd64 (1.1.1-3~gd~t) ...
dpkg: fel vid hantering av arkivet /var/cache/apt/archives/libvdpau1_1.1.1-3~gd~t_amd64.deb (--unpack):
 försöker skriva över delad "/etc/vdpau_wrapper.cfg" som skiljer sig från andra instanser av paketet libvdpau1:amd64
Fel uppstod vid hantering:
 /var/cache/apt/archives/libvdpau1_1.1.1-3~gd~t_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Apologies for some things being in the Swedish language!

---

### Post by ian-weisser on 2016-01-13
> **Simanis said:**
> Apologies for some things being in the Swedish language!
You do not need to change your system language to get output in English. Instead, run the text through any online translator.
It's quick and easy. I used Google Translate to read your output.

Read through the error messages, and you will find one easy issue:
> **Simanis said:**
> Följande paket har installerats automatiskt och är inte längre nödvändiga:
  libdrm-amdgpu1 libllvm3.7 libomxil-bellagio-bin libomxil-bellagio0
  libswscale2 libva-glx1 libva-x11-1 libvdpau-va-gl1
Use 'apt-get autoremove' to remove them.
Do it. Remember to prepend 'sudo'.

Now to the heart of your issue:
> **Simanis said:**
> /libvdpau1_1.1.1-3~gd~t_amd64.deb (--unpack):
försöker skriva över delad "/etc/vdpau_wrapper.cfg" som skiljer sig från andra instanser av paketet libvdpau1:amd64
That's a *file conflict*.
A file can be provided by only one package.

Two packages are trying to provide the same file.
The file is /etc/vdpau_wrapper.cfg
The two packages are libvdpau1:amd64 and libvdpau1_1.1.1-3~gd~t_amd64.deb.
You can only have one of those packages installed at a time. The two packages *conflict* with each other.

How to fix it:
Software comes from repositories.
You have unwisely added a repository that provides software that breaks your system.
1) Delete that lousy repository (source)
2) Uninstall the conflicting package 
3) Delete the conflicting package that has already downloaded to your package cache (**sudo apt-get clean libvdpau1_1.1.1-3~gd~t**)
4) Update your package database without the lousy source (**sudo apt update**)
5) Test that your fix is effective (**sudo apt upgrade**)
If you get error messages, please post the entire output here.

Which release of Ubuntu are you running? 14.04? 15.10?
Which media player were you trying to install?
Was the version in the Ubuntu repositories inadequate?
Were you following some instructions? A link to those instructions would help.

---

### Post by mörgæs on 2016-01-13
> **ian-weisser said:**
> You do not need to change your system language to get output in English. Instead, run the text through any online translator. It's quick and easy.

...and creates a mess.

Better to run the command **export LC_ALL=C** before the actual command.

---

### Post by Simanis on 2016-01-13
"sudo apt-get autoremove" gives me this:
```
user @ user-desktop: ~ $ sudo apt-get autoremove
 [sudo] password for user:
 Reading package lists ... Done
 Building dependency tree
 Reading state information ... Done
 You should run "apt-get -f install 'to correct these.
 The following packages have dependencies that can not be satisfied:
  vdpau-va-driver: Depends: libvdpau1 (> = 0.2) but it is not installed
 E: Unmet dependencies. Try using -f.
```


Thank you for pointing out my main problem. How do I find what release of Ubuntu I am running? I think it is 14.04, but I don't actually know.

I wish I knew where my problems started. Maybe when I was trying to install VLC. But I did that through the Software Center. I have no idea what instructions I followed! (I sound so irresponsible, don't I. But I guess I've been trying to find me way around Ubuntu quite in the dark, hoping that nothing bad would happen. I was wrong.) But then I had these Adobe Flash problems, and after they were solved I lost Audacity, and tried to install that. But by that time, my system was already having problems.

How can I find the correct repository to delete? I suppose there is no use following the other steps until I know what repository to delete. (And, if I knew what it is, should I be deleting a whole folder or something else?)

Sorry for not knowing the basics. :(

---

### Post by ian-weisser on 2016-01-13
> **Simanis said:**
> How do I find what release of Ubuntu I am running? I think it is 14.04, but I don't actually know.
Try the 'uname' command.
Or the settings menu next to the clock --> About this computer

> **Simanis said:**
> I wish I knew where my problems started.
That's easy. This problem started when you added a non-Ubuntu source.
Happily, it's easy to fix. And you will learn something today.

 Open the Settings Menu --> System Settings --> Software & Updates.
Look for the 'Other software' Tab.
Uncheck everything (except 'Canonical Partners' and 'dl.google.com')
There, you disabled all the strange, untested sources. Close the window and proceed with step 2.

It's likely that you disabled sources that you want to keep.
Once your system is working, re-enable one source at a time, and do steps 2,3,and 4 each time.
When one of those sources breaks your system again, then uncheck it (delete it - you won't be using it!), and fix your system.
Continue until all your sources are either enabled (checked) or deleted.

---

### Post by mc4man on 2016-01-13
I'mnly on a windows machine atm so only in general -   at some point you added the oibaf ppa
 [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)
Note that that ppa for mesa on Trusty is only for 14.04 & 14.04.1 image installs, if used on 14.04.2 or 14.04.3 image installs will cause problems.
Also once that ppa is added & used it must be left enabled.

So - what image did you install from, or post the results of this which may tell..
uname -a

If you did install mesa packages from that ppa then best to add it back if disabled & then possibly use ppa purge on it to return to default Ubuntu packages

---

### Post by Simanis on 2016-01-14
Thank you both for help so far. "uname -a" gives me this:
```
@user-desktop:~$ uname -a
Linux user-desktop 3.16.0-57-generic #77~14.04.1-Ubuntu SMP Thu Dec 17 23:20:00 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

So I am running 14.04.1. Now I'll start with the steps 1-4.

When I try to delete the already downloaded package cache "sudo apt-get clean libvdpau1_1.1.1-3~gd~t", nothing happens, just a new line in the terminal. (First time I tried it, I gave the password, but the second time I tried it I only got a new line in the terminal.)

Because of that, "sudo apt upgrade" gave me this:
```
user @ user-desktop: ~ $ sudo apt upgrade
 Reading package lists ... Done
 Building dependency tree
 Reading state information ... Done
 You should run "apt-get -f install 'to correct these.
 The following packages have dependencies that can not be satisfied:
  vdpau-va-driver: Depends: libvdpau1 (> = 0.2) but it is not installed
 E: Unmet dependencies. Try using -f.
```

So I guess I got stuck on the delete part. What can I do to delete the faulty file?


And mc4man, yes, I must have added that. But how do I use "ppa purge" on it?

---

### Post by matt_symes on 2016-01-14
@simanis

Please use code tags for any any output from the terminal.

You use code tags like this

[noparse]```
Output from terminal
```[/noparse]

to get output like this

```
Output from terminal
```

Code tags preserve formatting and help make the output much easier to read.

I have edited your previous posts for you.

---

### Post by Simanis on 2016-01-14
Aah, thank you. I didn't know about that.

---

### Post by mc4man on 2016-01-14
> **Simanis said:**
> Thank you both for help so far. "uname -a" gives me this:
```
@user-desktop:~$ uname -a
Linux user-desktop 3.16.0-57-generic #77~14.04.1-Ubuntu SMP Thu Dec 17 23:20:00 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

So I am running 14.04.1. Now I'll start with the steps 1-4.

When I try to delete the already downloaded package cache "sudo apt-get clean libvdpau1_1.1.1-3~gd~t", nothing happens, just a new line in the terminal. (First time I tried it, I gave the password, but the second time I tried it I only got a new line in the terminal.)



So I guess I got stuck on the delete part. What can I do to delete the faulty file?


And mc4man, yes, I must have added that. But how do I use "ppa purge" on it?

Well that kernel came with 14.04.2, not 14.04.1
Anyway the ppa page tells you what to do, that's one several ppa's that no one should post commands to use, they should just provide a link to the ppa page.

Assuming you removed the ppa, - 
add back - 
```
sudo add-apt-repository ppa:oibaf/graphics-drivers
```
Update sources
```
sudo apt-get update
```
Install ppa-purge
```
sudo apt-get install ppa-purge
```
If that ^ fails due to current issues then run this before purging
```
sudo apt-get dist-upgrade
```
Then install ppa-purge if not already

To purge ppa - 
```
sudo ppa-purge ppa:oibaf/graphics-drivers
```

---

### Post by Simanis on 2016-01-14
Thank you. However, I haven't succeeded any further than before, as "sudo apt-get dist-upgrade" gives me this:
```
user @ user-desktop: ~ $ sudo apt-get dist-upgrade
 Reading package lists ... Done
 Building dependency tree
 Reading state information ... Done
 You should run "apt-get -f install 'to correct these.
 The following packages have dependencies that can not be satisfied:
  vdpau-va-driver: Depends: libvdpau1 (> = 0.2) but it is not installed
 E: Unmet dependencies. Try using -f.
```

And "sudo apt-get -f install" still gives me this:
```
user @ user-desktop: ~ $ sudo apt-get -f install
Reading package lists ... Done
Building dependency tree
Reading state information ... Done
Corrects dependencies ... Done
The following packages were automatically installed and are no longer necessary:
  libdrm-amdgpu1 libllvm3.7 libomxil-Bellagio-bin libomxil-bellagio0
  libswscale2 libva-glx1 libva-x11-1 libvdpau-va-GL1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libvdpau1
Recommended packages:
  vdpau-drives-all vdpau driver
The following NEW packages will be installed:
  libvdpau1
0 To upgrade, 1 newly installed, 0 to remove and 16 not upgraded.
2 not fully installed or removed.
Need to get 27.8 kB archives.
After this operation, additional 124 KB of space used on the drive.
Do you want to continue? [Y / n] j
Read: 1 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu/ trusty / main libvdpau1 amd64 1.1.1-3 ~ GD ~ t [27.8 KB]
Downloaded 27.8 kB of 0s (144 KB / s)
(Reading database ... 205687 files and directories currently installed.)
Preparing to decompress ... / libvdpau1_1.1.1-3 ~ GD ~ t_amd64.deb ...
Unpack libvdpau1: amd64 (1.1.1-3 ~ GD ~ t) ...
dpkg: error processing the archive /var/cache/apt/archives/libvdpau1_1.1.1-3~gd~t_amd64.deb (--unpack):
 trying to overwrite shared "/etc/vdpau_wrapper.cfg" that differ from other instances of the package libvdpau1: amd64
E: Sub-process / usr / bin / dpkg Returned an error code (1)
```

I still don't know what to do.

Meanwhile (that is, while I still don't know what else to do), I think I'm starting to understand what is actually found in the Softwares & Updates' Other software tab. But I don't have much there, only six entries as follows:

Canonical Partners
Canonical Partners (source code)
Independent third-party
Independent third-party (source code)
[http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu](http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu) trusty (main)
[http://repository.spotify.com](http://repository.spotify.com) stable (non-free)

I don't know why there are double entries as listed above. But if I understood correctly, I should disable everyone of them except for the Canonical Partners and the ppa.launchpad.net one. However, even when I have disabled everything (even the ones I shouldn't disable), still nothing happens when I try to run "sudo apt-get clean libvdpau1_1.1.1-3~gd~t". Why is that?

Now I have enabled Canonical Partners and ppa.launchpad.net again.

Edit:
I finally found a solution for my problem through another forum. Someone suggested someone else with the same problem to rename /etc/vdpau_wrapper.cfg thus:
```
sudo mv /etc/vdpau_wrapper.cfg /etc/vdpau_wrapper.cfg.BAK
```
After I did that, I could run apt-get update, apt-get upgrade and things were finally back to normal again!

Thanks everyone who patiently helped me to learn a little bit more about running an Ubuntu machinery!

---

