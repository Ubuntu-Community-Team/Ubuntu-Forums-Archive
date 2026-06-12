---
title: "APT-GET taking a really long time? (Stays at 0%)"
date: 2016-10-22
forum: General Help
---

### Post by rolltide101x on 2016-10-22
I have a fresh install of Kubuntu 16.10 (have had it happen in Unity Ubuntu as well) and any apt-get command will just sit at 0% for 20 minutes or longer and then eventually it will decide to go. As of right now I am working of the stock repositories and have made no changes to any of them. Can someone give me some ideas of things to try? I tried googling for an answer but I can not seem to find anyone with the exact same issue as me.

---

### Post by oldos2er on 2016-10-22
I can't really make out your screenshot, sorry. What type of internet connection do you have, wired or wireless? Is there any other network slowness aside from apt? Can you post the output of ```
cat /etc/apt/sources.list
``` ?

---

### Post by rolltide101x on 2016-10-22
Happens at work and at home and nothing else to do with internet is having any issues but both were wireless. I can try wired when I get home if you think that may make a difference.








clate@clate-GE62-6QD:~$ cat /etc/apt/sources.list
```
#deb cdrom:[Kubuntu 16.10 _Yakkety Yak_ - Release amd64 (20161012.1)]/ yakkety main multiverse restricted universe

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) yakkety-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.                                                                                                             
## This software is not part of Ubuntu, but is offered by Canonical and the                                                          
## respective vendors as a service to Ubuntu users.                                                                                  
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety partner                                                                            
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) yakkety partner                                                                        
                                                                                                                                     
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security main restricted                                                               
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security main restricted                                                         
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security universe                                                                      
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security universe                                                                
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security multiverse                                                                    
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) yakkety-security multiverse
```

---

### Post by oldos2er on 2016-10-22
If you switch to the main server is it still slow?

---

### Post by rolltide101x on 2016-10-23
> **oldos2er said:**
> If you switch to the main server is it still slow?

You are a life saver! That seems to have solved it.  Thanks a ton [**[COLOR=#C61919][B]oldos2er!**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=338320")

For anyone who does not know how to switch from a regional server to a main server on Ubuntu you open up software sources
 
GUI example of doing it:    [http://i.stack.imgur.com/YGtwc.png](http://i.stack.imgur.com/YGtwc.png)



On Kubuntu I honestly am not sure how to do it via pure GUI (no option to switch to main server in Discover Center that I can see)

```
sudo kwrite /etc/apt/sources.list
```

Switch [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) 

and replace it with [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu).

---

### Post by oldos2er on 2016-10-24
Glad you got it sorted!

---

### Post by Geoffrey_Arndt on 2016-10-24
Really the best thing to do re Source Servers is "select best server" . . . let the system ping all servers and provide you the best option.   Sometimes just selecting the "Main Server" (for US or other) is not the best choice.

---

### Post by rolltide101x on 2016-10-25
I tried that on regular (Unity) Ubuntu and it did not work. I can find no such option on Kubuntu to try

---

### Post by Geoffrey_Arndt on 2016-10-25
OK, here we go:

All this should also exist on/in Kubuntu (_or a close derivation of_ . . )

>   System Settings > Ubuntu Software >  Download From > Other >  Select Best Server >  Choose Server >  Enter Password (prompt window)  >  Close  >  Reload

I hope you can get this to work, . . . it's one of the coolest features of the Ubuntu system (and I'd be amazed if Kubuntu doesn't also have this).    All servers will have issues from time to time - - this fixes it.

---

### Post by rolltide101x on 2016-10-25
> **Geoffrey_Arndt said:**
> OK, here we go:

All this should also exist on/in Kubuntu (_or a close derivation of_ . . )

>   System Settings > Ubuntu Software >  Download From > Other >  Select Best Server >  Choose Server >  Enter Password (prompt window)  >  Close  >  Reload

I hope you can get this to work, . . . it's one of the coolest features of the Ubuntu system (and I'd be amazed if Kubuntu doesn't also have this).    All servers will have issues from time to time - - this fixes it.



In 16.04 Kubuntu does indeed have that setting but in 16.10 it does not. But as I said before selecting the best server did not fix this issue even when I tried Ubuntu 16.10. But changing to the main server instead of the U.S. server

---

