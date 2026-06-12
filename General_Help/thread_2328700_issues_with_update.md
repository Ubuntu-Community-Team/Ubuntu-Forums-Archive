---
title: "issues with update"
date: 2016-06-23
forum: General Help
---

### Post by kaky951357 on 2016-06-23
hello,
when I want update my ubuntu 15.10 system, it doesn't want ,and it telling me "Check your Internet connection"
even if my laptop have good, stable internet connection 
thank you for help.

---

### Post by gametaunt on 2016-06-23
what version of ubuntu are you currently running, perhaps the version is EOL and your repo is no longer available?

---

### Post by Impavidus on 2016-06-23
Is that a normal upgrade of the 15.10 software or are you attempting a release upgrade to 16.04? 15.10 has about a month of support left.

The error message means that the updater cannot reach the server (at least one of them) where it should find the new packages or the new index. It could be a temporary server problem or a PPA that is no longer supporting 15.10.

Run```
sudo apt-get update
sudo apt-get upgrade
```to get more diagnostics. You can post the output here in [noparse]```
code tags
```[/noparse].

---

### Post by kaky951357 on 2016-06-23
hello,
i tried to change the uptade server and it doesn't want, its tell me an other time i'm that i'm not connected to internet, here the feedback of ```
sudo apt-get update
``` : 
```
Atteint http://ppa.launchpad.net wily InRelease                                Atteint http://archive.ubuntu.com wily InRelease                               
Atteint http://ppa.launchpad.net wily InRelease                                
Réception de : 1 http://archive.ubuntu.com wily-updates InRelease [65,9 kB]    
Atteint http://ppa.launchpad.net wily InRelease                                
Ign http://ppa.launchpad.net wily InRelease                                    
Ign http://dl.google.com stable InRelease                                      
Atteint http://archive.ubuntu.com wily-backports InRelease                     
Atteint http://dl.google.com stable Release.gpg                                
Réception de : 2 http://archive.ubuntu.com wily-security InRelease [65,9 kB]   
Atteint http://dl.google.com stable Release                                    
Atteint http://dl.google.com stable/main amd64 Packages                        
Ign http://ppa.launchpad.net wily Release.gpg                                  
Atteint http://ppa.launchpad.net wily/main amd64 Packages               
Atteint http://ppa.launchpad.net wily/main i386 Packages                       
Atteint http://ppa.launchpad.net wily/main Translation-en                      
Atteint http://ppa.launchpad.net wily/main amd64 Packages                      
Atteint http://ppa.launchpad.net wily/main i386 Packages                       
Atteint http://ppa.launchpad.net wily/main Translation-en                      
Atteint http://ppa.launchpad.net wily/main amd64 Packages                      
Atteint http://ppa.launchpad.net wily/main i386 Packages                       
Atteint http://ppa.launchpad.net wily/main Translation-en                      
Ign http://ppa.launchpad.net wily Release                                      
Réception de : 3 http://archive.ubuntu.com wily-updates/main Sources [83,7 kB]
Réception de : 4 http://archive.ubuntu.com wily-updates/restricted Sources [3 741 B]
Réception de : 5 http://archive.ubuntu.com wily-updates/universe Sources [26,6 kB]
Réception de : 6 http://archive.ubuntu.com wily-updates/multiverse Sources [3 207 B]
Réception de : 7 http://archive.ubuntu.com wily-updates/main amd64 Packages [229 kB]
Ign http://dl.google.com stable/main Translation-fr_FR                         
Ign http://dl.google.com stable/main Translation-fr                            
Réception de : 8 http://archive.ubuntu.com wily-updates/restricted amd64 Packages [13,3 kB]
Ign http://dl.google.com stable/main Translation-en                            
Réception de : 9 http://archive.ubuntu.com wily-updates/universe amd64 Packages [102 kB]
Réception de : 10 http://archive.ubuntu.com wily-updates/multiverse amd64 Packages [6 257 B]
Réception de : 11 http://archive.ubuntu.com wily-updates/main i386 Packages [226 kB]
Err http://ppa.launchpad.net wily/main amd64 Packages                   
  404  Not Found
Err http://ppa.launchpad.net wily/main i386 Packages                           
  404  Not Found
Ign http://ppa.launchpad.net wily/main Translation-fr_FR                       
Réception de : 12 http://archive.ubuntu.com wily-updates/restricted i386 Packages [13,4 kB]
Ign http://ppa.launchpad.net wily/main Translation-fr                          
Ign http://ppa.launchpad.net wily/main Translation-en                          
Réception de : 13 http://archive.ubuntu.com wily-updates/universe i386 Packages [99,3 kB]
Réception de : 14 http://archive.ubuntu.com wily-updates/multiverse i386 Packages [6 683 B]
Réception de : 15 http://archive.ubuntu.com wily-updates/main Translation-en [108 kB]
Réception de : 16 http://archive.ubuntu.com wily-updates/multiverse Translation-en [3 156 B]
Réception de : 17 http://archive.ubuntu.com wily-updates/restricted Translation-en [3 024 B]
Réception de : 18 http://archive.ubuntu.com wily-updates/universe Translation-en [58,2 kB]
Atteint http://archive.ubuntu.com wily-backports/restricted Sources            
Atteint http://archive.ubuntu.com wily-backports/multiverse Sources            
Atteint http://archive.ubuntu.com wily-backports/restricted amd64 Packages     
Atteint http://archive.ubuntu.com wily-backports/multiverse amd64 Packages     
Atteint http://archive.ubuntu.com wily-backports/restricted i386 Packages      
Atteint http://archive.ubuntu.com wily-backports/multiverse i386 Packages      
Atteint http://archive.ubuntu.com wily-backports/multiverse Translation-en     
Atteint http://archive.ubuntu.com wily-backports/restricted Translation-en     
Réception de : 19 http://archive.ubuntu.com wily-security/main Sources [51,4 kB]
Réception de : 20 http://archive.ubuntu.com wily-security/restricted Sources [2 854 B]
Réception de : 21 http://archive.ubuntu.com wily-security/universe Sources [12,9 kB]
Réception de : 22 http://archive.ubuntu.com wily-security/multiverse Sources [2 785 B]
Réception de : 23 http://archive.ubuntu.com wily-security/main amd64 Packages [163 kB]
Réception de : 24 http://archive.ubuntu.com wily-security/restricted amd64 Packages [10,9 kB]
Réception de : 25 http://archive.ubuntu.com wily-security/universe amd64 Packages [54,2 kB]
Réception de : 26 http://archive.ubuntu.com wily-security/multiverse amd64 Packages [6 257 B]
Réception de : 27 http://archive.ubuntu.com wily-security/main i386 Packages [160 kB]
Réception de : 28 http://archive.ubuntu.com wily-security/restricted i386 Packages [10,8 kB]
Réception de : 29 http://archive.ubuntu.com wily-security/universe i386 Packages [54,2 kB]
Réception de : 30 http://archive.ubuntu.com wily-security/multiverse i386 Packages [6 438 B]
Atteint http://archive.ubuntu.com wily/main Sources                            
Atteint http://archive.ubuntu.com wily/restricted Sources                      
Atteint http://archive.ubuntu.com wily/universe Sources                        
Atteint http://archive.ubuntu.com wily/multiverse Sources                      
Atteint http://archive.ubuntu.com wily/main amd64 Packages                     
Atteint http://archive.ubuntu.com wily/restricted amd64 Packages               
Atteint http://archive.ubuntu.com wily/universe amd64 Packages                 
Atteint http://archive.ubuntu.com wily/multiverse amd64 Packages               
Atteint http://archive.ubuntu.com wily/main i386 Packages                      
Atteint http://archive.ubuntu.com wily/restricted i386 Packages                
Atteint http://archive.ubuntu.com wily/universe i386 Packages                  
Atteint http://archive.ubuntu.com wily/multiverse i386 Packages                
Atteint http://archive.ubuntu.com wily/main Translation-fr                     
Atteint http://archive.ubuntu.com wily/main Translation-en                     
Atteint http://archive.ubuntu.com wily/multiverse Translation-fr               
Atteint http://archive.ubuntu.com wily/multiverse Translation-en               
Atteint http://archive.ubuntu.com wily/restricted Translation-fr               
Atteint http://archive.ubuntu.com wily/restricted Translation-en               
Atteint http://archive.ubuntu.com wily/universe Translation-fr                 
Atteint http://archive.ubuntu.com wily/universe Translation-en                 
Atteint http://archive.ubuntu.com wily-backports/main Sources                  
Atteint http://archive.ubuntu.com wily-backports/universe Sources              
Atteint http://archive.ubuntu.com wily-backports/main amd64 Packages           
Atteint http://archive.ubuntu.com wily-backports/universe amd64 Packages       
Atteint http://archive.ubuntu.com wily-backports/main i386 Packages            
Atteint http://archive.ubuntu.com wily-backports/universe i386 Packages        
Atteint http://archive.ubuntu.com wily-backports/main Translation-en           
Atteint http://archive.ubuntu.com wily-backports/universe Translation-en       
Atteint http://archive.ubuntu.com wily-security/main Translation-en            
Atteint http://archive.ubuntu.com wily-security/multiverse Translation-en      
Atteint http://archive.ubuntu.com wily-security/restricted Translation-en      
Atteint http://archive.ubuntu.com wily-security/universe Translation-en        
1 654 ko réceptionnés en 30s (54,2 ko/s)                                       
W: Impossible de récupérer http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/wily/main/binary-amd64/Packages  404  Not Found


W: Impossible de récupérer http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/wily/main/binary-i386/Packages  404  Not Found


E: Le téléchargement de quelques fichiers d'index a échoué, ils ont été ignorés, ou les anciens ont été utilisés à la place.


 
```
i have the problem when i use the graphical tool : update manager [COLOR=#212121][FONT=arial]

[/FONT][/COLOR]

---

### Post by Bashing-om on 2016-06-23
kaky951357; Hello;

The package manager is telling you the truth:
[http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/)
is not supported in wily.

You need to disable this source and again run update/upgrade.

[INDENT][INDENT]it is a thing
[INDENT][INDENT][INDENT]it matters
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kaky951357 on 2016-06-23
hello ,
it work's , when i remove the ppa the update manager work , removing [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/) mean that tor will not be updated ?
thanks for help dude

---

### Post by Bashing-om on 2016-06-23
kaky951357; Yeah;

you have the right :
> 
mean that tor will not be updated ?

of it . That PPA has not had any activity in several years .
There may be another alternative source for tor .

[INDENT][INDENT]maybe
[/INDENT][/INDENT]

---

### Post by kaky951357 on 2016-06-24
hello, 
where can i find the alternative?
in the tor browser it propose me updates and when i agree it do it, the ppa is not working then where the browser get updates is that the alternative ?
thanks for answer

---

### Post by Bashing-om on 2016-06-24
kaky951357; Hey;

What to advise for an alternative tor .. I just do not know. Searching the repo for "tor" yields so may results it is difficult to filter them down to  meaningful choices.
I am sure that those who run a tor client can advise better.

[INDENT][INDENT]sometimes, I just do not know
[/INDENT][/INDENT]

---

### Post by QDR06VV9 on 2016-06-24
> **kaky951357 said:**
> hello, 
where can i find the alternative?
in the tor browser it propose me updates and when i agree it do it, the ppa is not working then where the browser get updates is that the alternative ?
thanks for answer
Just Download Tor Browser from:[https://www.torproject.org/download/download.html.en](https://www.torproject.org/download/download.html.en)
Extract it, Double Click the Start Tor Browser Icon let it do its thing...and Done.
It will Alert you to new updates automatically.
Cheers

---

### Post by Bashing-om on 2016-06-24
@runrickus; :)

Ole friend, As always, appreciate !

[INDENT][INDENT]All in knowing how
[/INDENT][/INDENT]

---

### Post by kaky951357 on 2016-06-25
ok i will do so :D appreciate your help guys, have nice day

---

