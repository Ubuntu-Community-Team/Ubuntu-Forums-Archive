---
title: "beryl public key"
date: 2006-12-20
forum: General Help
---

### Post by squidmaster on 2006-12-20
when I install beryl, the window manager didn't work.
so I restarted
and did
```
sudo apt-get update
```

but I get this
```
W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
```

i already did
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

though, so what am I doing wrong and how can I get beryl to finally work?

---

### Post by bodhi.zazen on 2006-12-20
> **squidmaster said:**
> when I install beryl, the window manager didn't work.
so I restarted
and did
```
sudo apt-get update
```

but I get this
```
W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
```

i already did
```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

though, so what am I doing wrong and how can I get beryl to finally work?

I'm not like'n that pipe !

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
sudo apt-key add root@lupine.me.uk.gpg
```

connect the two commands with && rather then | if you prefer:```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg && sudo apt-key add root@lupine.me.uk.gpg
```

---

### Post by squidmaster on 2006-12-20
> **bodhi.zazen said:**
> I'm not like'n that pipe !

```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg
sudo apt-key add root@lupine.me.uk.gpg
```

connect the two commands with && rather then | if you prefer:```
wget http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg && sudo apt-key add root@lupine.me.uk.gpg
```

yeah... umm
```
W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
```

haha.
I don't think this matters that I have ATi does it?

---

### Post by bodhi.zazen on 2006-12-20
> I don't think this matters that I have ATi does it?

No it does not matter.

for that matter, the error message does not matter either.

You can install away if you like 8)

You are just getting a warning about your sources 8)

---

### Post by squidmaster on 2006-12-20
hmm
so
then what can I do to fix it? I did all the mods to xorg.conf that are said in the tutorials.

EDIT: oh and one more thing
```
ika@ika-ubuntu2:~$ sudo apt-key add root@lupine.me.uk.gpg
gpg: key 6A7476EA was created 29614166 seconds in the future (time warp or clock problem)
gpg: key 6A7476EA was created 29614166 seconds in the future (time warp or clock problem)
gpg: key 6A7476EA was created 29614166 seconds in the future (time warp or clock problem)
gpg: key 6A7476EA was created 29614166 seconds in the future (time warp or clock problem)
gpg: key 6A7476EA: no valid user IDs

```

---

### Post by bodhi.zazen on 2006-12-20
I'm not sure about the fix :(

You should be able to install beryl without the key. You will get an "error message" that is not a fatal error, just a warning.

You can also try:

sudo apt-get update

to fix the error.

---

### Post by squidmaster on 2006-12-20
see, thats my problem
I CAN'T update it from there

```
ika@ika-ubuntu2:~$ sudo apt-get update
Password:
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com edgy Release.gpg [191B]                     
Ign http://us.archive.ubuntu.com edgy/main Translation-en_US                   
Get:2 http://security.ubuntu.com edgy-security Release.gpg [191B]              
Ign http://security.ubuntu.com edgy-security/main Translation-en_US            
Ign http://us.archive.ubuntu.com edgy/restricted Translation-en_US             
Get:3 http://us.archive.ubuntu.com edgy-updates Release.gpg [191B]             
Ign http://us.archive.ubuntu.com edgy-updates/main Translation-en_US           
Ign http://us.archive.ubuntu.com edgy-updates/restricted Translation-en_US     
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US      
Hit http://security.ubuntu.com edgy-security Release                           
Ign http://wine.budgetdedicated.com edgy Release.gpg                           
Ign http://wine.budgetdedicated.com edgy/main Translation-en_US      
Hit http://us.archive.ubuntu.com edgy Release                        
Get:4 http://us.archive.ubuntu.com edgy-updates Release [23.3kB]               
Hit http://security.ubuntu.com edgy-security/main Packages                     
Get:5 http://ubuntu.beryl-project.org edgy Release.gpg [191B]                  
Ign http://ubuntu.beryl-project.org edgy/main Translation-en_US            
Ign http://ubuntu.beryl-project.org edgy/main Translation-en_US                
Hit http://wine.budgetdedicated.com edgy Release                               
Hit http://security.ubuntu.com edgy-security/restricted Packages           
Hit http://security.ubuntu.com edgy-security/main Sources                      
Hit http://security.ubuntu.com edgy-security/restricted Sources                
Ign http://wine.budgetdedicated.com edgy/main Packages                         
Hit http://ubuntu.beryl-project.org edgy Release                            
Err http://ubuntu.beryl-project.org edgy Release                          
  
Hit http://wine.budgetdedicated.com edgy/main Packages                         
Get:6 http://ubuntu.beryl-project.org edgy Release [8194B]           
Hit http://us.archive.ubuntu.com edgy/main Packages      
Hit http://us.archive.ubuntu.com edgy/restricted Packages
Hit http://us.archive.ubuntu.com edgy/main Sources       
Hit http://us.archive.ubuntu.com edgy/restricted Sources 
Get:7 http://us.archive.ubuntu.com edgy-updates/main Packages [45.7kB]
Ign http://ubuntu.beryl-project.org edgy Release               
Get:8 http://us.archive.ubuntu.com edgy-updates/restricted Packages [14B]
Get:9 http://us.archive.ubuntu.com edgy-updates/main Sources [16.0kB]
Get:10 http://us.archive.ubuntu.com edgy-updates/restricted Sources [14B]
Hit http://ubuntu.beryl-project.org edgy/main Packages                  
Hit http://ubuntu.beryl-project.org edgy/main Packages                  
Fetched 93.6kB in 2s (45.2kB/s)
Reading package lists... Done
[B]W: GPG error: http://ubuntu.beryl-project.org edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: Duplicate sources.list entry http://ubuntu.beryl-project.org edgy/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems[/B]
ika@ika-ubuntu2:~$ 

```

(look for the bold at the bottem)

---

### Post by squidmaster on 2006-12-20
ok so the server was down
anyways

here is what I get when I try to run it. the icon loads up
but no window tops or what ever
no splash screen
here is the output
```
ika@ika-ubuntu2:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

zomg this is annoying

---

### Post by bodhi.zazen on 2006-12-21
LOL squidmaster !

> W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA

This "error" is just a warning and can be ignored :) It is just telling you the source can not be verified ;)

> W: Duplicate sources.list entry [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy/main Packages (/var/lib/apt/lists/ubuntu.beryl-project.org_dists_edgy_main_binary-i386_Packages)

Likewise I assume you have ubuntu.beryl-project.org dists edgy main listed twice. Again, no problem :)

> beryl: No manageable screens found on display :0.0

Now there is a show stopper :)

This has something to do with ATI !

I am afraid I can not help much there, I nvidia :twisted:

---

### Post by squidmaster on 2006-12-21
> **bodhi.zazen said:**
> LOL squidmaster !



This "error" is just a warning and can be ignored :) It is just telling you the source can not be verified ;)



Likewise I assume you have ubuntu.beryl-project.org dists edgy main listed twice. Again, no problem :)



Now there is a show stopper :)

This has something to do with ATI !

I am afraid I can not help much there, I nvidia :twisted:

Yeah I figured that those first two were just ignorable things, but I had to make sure.
And... well... ATi, I love it.
I don't really like nVidia, I bought a 6800GT in an almost identical system as I have right now for $200 and it did pretty good, but then like 3 months later when I built my newer system I got a x800GTO for like $170 and it out preformed the nVidia in every game. so.

well anyways back to my problem....
I reinstalled the fglrx drivers and still got the same thing.

---

