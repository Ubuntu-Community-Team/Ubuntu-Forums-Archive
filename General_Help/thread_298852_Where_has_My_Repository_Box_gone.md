---
title: "Where has My Repository Box gone"
date: 2006-11-13
forum: General Help
---

### Post by IusedTObeSOMEONEelse on 2006-11-13
This is the 3rd time I have done a fresh install and upgrade from Dapper to Edgy then edit sources list to Feisty. Each time, when I get Feisty on and updates, I have gone to System>Administration>Synaptic Package Manager>Setting>Repositories---the Repositories window does a quick flash then message box appears telling that the Repositories list has changed to please click Reload. Well I reload and then try to open repositories window again and what do you know, The same thing!!](*,) So I reload again.  And it goes on and on and on. This is the 3rd fresh install and the same thing after each install. I believe that I am now **OBSESSED** with this problem and now I **MUST** find a solution or reason as to why is my Repositories box refusing to open. Will some one please provide me with a reasonable explanation. (please do not tell me to forget about it)

---

### Post by strabes on 2006-11-13
just change your repositories with sudo gedit /etc/apt/sources.list

synaptic is useless. why don't you just try to install edgy fresh instead of installing dapper then upgrading to edgy...?

---

### Post by taurus on 2006-11-13
You could have a better luck going from Edgy to Feisty instead of from Dapper to Edgy and finally to Feisty!!!

---

### Post by IusedTObeSOMEONEelse on 2006-11-13
Thank You strabes & taurus for your prompt replies. Hi taurus! Arrgghh! Your probly thinking "Here She goes again, that B$TCH!" ;)  HaHa. To answer why don't I just do fresh Edgy install? Each time I have burned cd's,  both my machines could not find kernel off the cd. I have burned quite a few. My other machine has been SUPER great with the upgrade to Edgy and I upgraded during the testing. Not to sound ungratefull, but you both have evaded my ORIGANAL question.Why is this happening. (I'm obsessed with this)

---

### Post by taurus on 2006-11-13
Hey, watch your language, young lady!!!  :mrgreen: 

My first question is how did you upgrade from Dapper to Edgy?  

What if you install Edgy from fresh and then upgrade it to Feisty?  Would that mess up your /etc/apt/sources.list?

---

### Post by IusedTObeSOMEONEelse on 2006-11-13
I upgraded by editing sources list then: sudo aptitude update && sudo aptitude dist-upgrade. I can not do a fresh install of Edgy as every cd that I made will not boot and I have made other cd's (puppy linux) and that worked. So with out a cd, the only option is the upgrade. I am not letting this go! I am tired of spending weekends update/upgrade. It takes the whole weekend, plus I set some things up and I lose all. Oh well :-k

---

### Post by taurus on 2006-11-13
I am so sorry but that is NOT how you upgrade from Dapper to Edgy...  Here is the right way to do the upgrading.  ;) 

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

Try that first and then modify your /etc/apt/sources.list and upgrade to Feisty...

---

### Post by IusedTObeSOMEONEelse on 2006-11-13
I am happy to inform you that I upgraded from dapper to edgy that way (update manager)(I sat through 1075 updates )successfully. But when I tried using update manager code as specified in the thread you pointed out (I used that thread Saturday) I got no response as to an upgrade to feisty available, so i edited the sources list. Thank you very much! Of course taurus, it would have to be another one of these 'Doom & Gloom" days here in N.Y. which is not helping my sanity any today. Now back to my ORIGANAL question: Is there not some kind of  "sudo " magic that will make that damm Repositories window re-appear?

---

### Post by taurus on 2006-11-13
You mean opening up or editing /etc/apt/sources.list!

```
gksudo gedit /etc/apt/sources.list
```
You might want to paste your /etc/apt/sources.list here as well...

---

### Post by IusedTObeSOMEONEelse on 2006-11-13
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

##deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main                         Here you go. How about 'downgrading ' back to Edgy and seeing if my Repositories window re-appears? It was there before I went up to feisty, (I double checked to see if it was).

---

### Post by IusedTObeSOMEONEelse on 2006-11-13
OOPs, I gotta run out, Be back in a few!

---

### Post by IusedTObeSOMEONEelse on 2006-11-13
I am sorry I had to step out longer than anticipated. But I am ready to deal with this problem of the "Disapearing Repositories" Please, Any one have any Idea's or solution(sudo) magic? :-k :-k :-k

---

### Post by IusedTObeSOMEONEelse on 2006-11-13
Bump, Some one please help. This problem is not gonna clear itself

---

### Post by IusedTObeSOMEONEelse on 2006-11-14
Yes, I Bumped it again. I can not believe that I have posted and threaded quite a few times over the last 4 weeks and I can not get a reasonable answer to my ORIGANAL question! What happened to my Repositories Box and is there not a way to put a Repositories Box, back in System>Administration>Synaptic Package Manager>Settings>>REPOSITORIES.  I am hopefull that some  one can take the time to assist, Sally...

---

### Post by IusedTObeSOMEONEelse on 2006-11-14
Hello!

---

### Post by IusedTObeSOMEONEelse on 2006-11-14
**Is this posted on Venus?** Seems as I am only talking to my self.  YES, it's my fault for boinking my system AGAIN, but could I please get some clear input?

---

