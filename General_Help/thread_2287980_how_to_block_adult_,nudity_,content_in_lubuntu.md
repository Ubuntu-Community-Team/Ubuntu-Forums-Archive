---
title: "how to block adult ,nudity ,content in lubuntu"
date: 2015-07-23
forum: General Help
---

### Post by legendaryman on 2015-07-23
this may be a guide ,rather than a question ,if you answer it 
ok  i block 18+ adult on my home pc  using k9 web protection when i use windows xp 
1. simply download the file .exe
2. get licence number via email
3 .enter licence number while installing 
5. create  your own   password
6.block categories by enter  your password at login  which created after simply login on k9 port
my trick was after setting k9 to block nudity ,porn ,adult ,i change its password  to some random password (which i also don't remember) ,so in future i cannot change it
viola! i can't logon to any adult website without reinstalling windows as because i also don't know the password  
but on lubuntu there is no support for k9 web ,i already searched over 2 hours on google ,there is no alternative like this 
what i found working is only open dns 
*.now i am using and it is blocking content which i want
*problem how to make lubuntu not to change its dns without a seperate random password 
*or how could i make dns changing setting in accessible (unchangable) , 
*to make any  changes to dns  ,it should need reinstall of whole lubuntu.
*dns should also not get changed by using my root password in any way 
[COLOR=#ff0000]hope you get my point ,sorry my bad grammar [/COLOR]

---

### Post by raja.genupula on 2015-07-23
Hello

Please go through these below links

[http://askubuntu.com/questions/158572/what-is-the-best-way-to-restrict-access-to-adult-content](http://askubuntu.com/questions/158572/what-is-the-best-way-to-restrict-access-to-adult-content)
[https://help.ubuntu.com/community/ParentalControls](https://help.ubuntu.com/community/ParentalControls)
[http://itsfoss.com/how-to-block-porn-by-content-filtering-on-ubuntu/](http://itsfoss.com/how-to-block-porn-by-content-filtering-on-ubuntu/)

---

### Post by legendaryman on 2015-07-24
> **raja.genupula said:**
> Hello

Please go through these below links

[http://askubuntu.com/questions/158572/what-is-the-best-way-to-restrict-access-to-adult-content](http://askubuntu.com/questions/158572/what-is-the-best-way-to-restrict-access-to-adult-content)
[https://help.ubuntu.com/community/ParentalControls](https://help.ubuntu.com/community/ParentalControls)
[http://itsfoss.com/how-to-block-porn-by-content-filtering-on-ubuntu/](http://itsfoss.com/how-to-block-porn-by-content-filtering-on-ubuntu/)
i already got that in my research earlier 
so it could not solve my problem,
can you simply tell me is any way to do that ,what i asked above 
or is there any seperate linux destro available

---

### Post by ian-weisser on 2015-07-24
> **legendaryman said:**
> 
*to make any  changes to dns  ,it should need reinstall of whole lubuntu.
*dns should also not get changed by using my root password in any way 


Not conveniently possible. Root can change just about anything. That's why it is root.

---

### Post by legendaryman on 2015-07-24
which destro have a less terminal usage ,i mean windows like destro ,in windows xp we do not need use command prompt  more frequently ,all is done by lunching application but ubuntu we neeed learn the code first ,i hate this thing ,so is any version windows xp ,i am talking about look but about functions

---

### Post by Vladlenin5000 on 2015-07-25
> **legendaryman said:**
> which destro have a less terminal usage ,i mean windows like destro ,in windows xp we do not need use command prompt  more frequently ,all is done by lunching application but ubuntu we neeed learn the code first ,i hate this thing ,so is any version windows xp ,i am talking about look but about functions

Why don't you keep Windows then? Preferably a supported version (XP is EoL and a giant security hole of which "18+" contents should be the LEAST of your concerns).
Regarding your "project" there's a lot that can be done but I won't comment further - and you already have the pertinent links to start with anyway - because I'm against censorship and whenever I see someone "worried" by such contents, invariably it has been, directly or indirectly, religion driven. For that fact alone, *no way, José*...

---

### Post by PaulW2U on 2015-07-25
> **legendaryman said:**
> which destro have a less terminal usage ,i mean windows like destro ,in windows xp we do not need use command prompt  more frequently ,all is done by lunching application but ubuntu we neeed learn the code first ,i hate this thing ,so is any version windows xp ,i am talking about look but about functions

I'm not really sure what you're saying here.

All Linux distributions are pretty much the same, they just have different defaults, desktop environments and package management systems. You don't **have** to use the command prompt in Linux but sometimes it's so much easier to do so. You certainly **don't** need to "learn the code first" as you say. I'm not a coder and I've been here for more than five years now.

In some ways Linux is very much like Windows from a point and click point of view but in other ways it is very different and it may take some getting used to especially if you've been using Windows for sometime.

---

### Post by speartip on 2015-07-25
If you login to your router & change the DNS servers to those of opendns, then every internet appliance in the house will be protected.
To lock it down, change your router password so no one can login & change it back. Obviously if you change the password to one you can't remember, you will need to do a hard reset of the router to access it again. But that should work.

@vladlenin5000 - I use opendns to protect my family's web viewing. It has nothing to do with religion, & everything to do with being a responsible adult. Censorship is there for a protection not a restriction.

---

