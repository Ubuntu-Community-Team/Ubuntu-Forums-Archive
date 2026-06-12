---
title: "Ubuntu 12.10 Install Help"
date: 2013-02-01
forum: General Help
---

### Post by Bradley129 on 2013-02-01
[SIZE=2]Hi guys ;) This is my first post on the forums :D Im so happy to be here :popcorn: To bad It couldn't be under better circumstances :( Well heres my Problem.[/SIZE]


[SIZE=2]Noob Question here i just tried to install Ubuntu 12.10 on a separate partician with nomodeset (thats the only way ubuntu will work on my radeon graphic Cards.[SIZE=2])[/SIZE]Well it installed succesfully except it didnt boot it just stayed on a black screen :o well i happen to have another live usb with ubuntu 12.04.1 LTS on it it was worth a try installed it with nomodeset and it worked PERFECTALY:p Great graphics EVERYTHING!So my question is why does ubuntu 12.04 work when 12.10 doesn't?:confused:[/SIZE]

[SIZE=2]Some details:I have 190gb set apart just for Ubuntu
                         :Graphics: Radeon 6480g Discrete Class Graphics
                         : The rest of my Specs Are in the Screen shot[/SIZE][IMG]http://www.freeimagehosting.net/3j24j[/IMG]


[SIZE=1]Does anybody know if theres any Say Hi threads around here? i whanna boost my post count without spamming or bothoring people[/SIZE]

---

### Post by Grinage on 2013-02-01
it could be that you have two different versions of Ubuntu, ie one is I386 and one is x64 or one is a Server CD and the black screen you're seeing is actually just the empty terminal login.  If you have 12.04 installed and running correctly it's easy to do a distribution upgrade.  Enter the following from a terminal

sudo apt-get dist-upgrade

---

### Post by Bucky Ball on 2013-02-01
Welcome to the forums.

I have edited your post. Take note, from the forum Code of Conduct:

[QUOTE=CoC]Use color and font properties for highlighting portions of your text, and not for all of the text in your post. Please use the default font color and properties unless you need to highlight or draw attention to a part of your post. ALL CAPS is interpreted as screaming. [size=2][COLOR=pink]Funky[/size][/COLOR] _non-uniform font size/color is difficult for those who are visually impaired. _If you are having problems with reading the font, please adjust your browser.[/QUOTE]

The answers to your questions are many and varied and a bit like looking for needles in haystacks. Hardly worth the search unless you are going to actually try to fix 12.10 on your machine. I'd just enjoy 12.04 and the learning curve to start with.

They are two different releases, they vary. 12.04 LTS is a long-term support release, been around for about 10 months and is stable, as LTS releases are designed to be. Had more updates and will work with more machines for the moment. A good place to start.

Install 12.10 on another partition once you are getting to know the ropes and try to get it working and this will teach you plenty about Ubuntu. Keep the 12.04 LTS as your stable, production release. Good luck.

You could immediately upgrade to 12.10 through update manager, but why? 12.04 is current til 2017 and rock solid, 12.10 supported til April 2014 and the upgrade could cause more problems than you had when you simply tried to install it. And if so, then you won't have an operational 12.04 either. Reinstall.

I'd stick with 12.04 and start getting into it. Meaning I would forget the dist-upgrade for now. It has the potential to set you on a merry chase. Enjoy! ;)

---

### Post by Bradley129 on 2013-02-01
> **Grinage said:**
> it could be that you have two different versions of Ubuntu, ie one is I386 and one is x64 or one is a Server CD and the black screen you're seeing is actually just the empty terminal login.  If you have 12.04 installed and running correctly it's easy to do a distribution upgrade.  Enter the following from a terminal

sudo apt-get dist-upgrade Thank you for your quick reply i can confirm both are desktop 64bit edition  also after seeing the below post i may just wait ;) but thanks for the update code ill kept that in mind incase i ever take the plunge :D

> **Bucky Ball said:**
> Welcome to the forums.

I have edited your post. Take note, from the forum Code of Conduct:



The answers to your questions are many and varied and a bit like looking for needles in haystacks. Hardly worth the search unless you are going to actually try to fix 12.10 on your machine. I'd just enjoy 12.04 and the learning curve to start with.

They are two different releases, they vary. 12.04 LTS is a long-term support release, been around for about 10 months and is stable, as LTS releases are designed to be. Had more updates and will work with more machines for the moment. A good place to start.

Install 12.10 on another partition once you are getting to know the ropes and try to get it working and this will teach you plenty about Ubuntu. Keep the 12.04 LTS as your stable, production release. Good luck.

You could immediately upgrade to 12.10 through update manager, but why? 12.04 is current til 2017 and rock solid, 12.10 supported til April 2014 and the upgrade could cause more problems than you had when you simply tried to install it. And if so, then you won't have an operational 12.04 either. Reinstall.

I'd stick with 12.04 and start getting into it. Meaning I would forget the dist-upgrade for now. It has the potential to set you on a merry chase. Enjoy! ;) Thanks im sorry i didnt intend to "scream at all" but thanks for the advice and quick reply :) ive just a bleeding edge kind of guy im running custom firmware on my android i beta tested windows 8 ect. and just addicted to being on the bleeding edge lol

---

### Post by Bucky Ball on 2013-02-01
> **Bradley129 said:**
> I'm just a bleeding edge kind of guy ... and just addicted to being on the bleeding edge lol

In that case I would suggest setting up a stable install, 12.04 LTS say, as your fall back and installing 13.04 on another partition to play around with. It is currently testing and not released until April. You could even go the bleeding edge daily builds. You would learn a lot and help the devs but expect unexpected breakages, specially with the daily.

Good luck.

---

### Post by Bradley129 on 2013-02-02
> **Bucky Ball said:**
> In that case I would suggest setting up a stable install, 12.04 LTS say, as your fall back and installing 13.04 on another partition to play around with. It is currently testing and not released until April. You could even go the bleeding edge daily builds. You would learn a lot and help the devs but expect unexpected breakages, specially with the daily.

Good luck.

sign me up for 13.04 beta lol wheres the nightlies page. alsowould 13.04 overwrite my grub becouse i like my 12.04 grub becouse i know its reliable and will pull through for me lol i use this computer for online classses and dont need it breaking lol :popcorn:

---

### Post by Bucky Ball on 2013-02-02
Install the 13.04 grub on the same partition as 13.04. Boot into 12.04 and:

```
sudo update-grub
```

That will pick up the other installs (all OSs on the machine) and add them to your existing 12.04 grub.

---

### Post by arpanaut on 2013-02-02
> **Grinage said:**
> it could be that you have two different versions of Ubuntu, ie one is I386 and one is x64 or one is a Server CD and the black screen you're seeing is actually just the empty terminal login.  If you have 12.04 installed and running correctly it's easy to do a distribution upgrade.  Enter the following from a terminal

sudo apt-get dist-upgrade

FYI the ```
sudo apt-get dist-upgrade 
``` command will NOT upgrade to the newest release.
See: ```
man apt-get
```It will only upgrade packages that are new versions of said packages.

The correct command is ```
sudo update-manager -d  
```That will get you to the next newest release.

---

### Post by Bucky Ball on 2013-02-02
Don't think OP wants to upgrade the stable 12.04 to 12.10. Not mentioned. Not sure why it is being discussed. ;)

---

