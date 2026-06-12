---
title: "Installing JAVA &amp; Wireless"
date: 2007-09-09
forum: General Help
---

### Post by slmclarengt on 2007-09-09
I have read multiple threads about both yet nothing seems to be useful because I get to a step where no troubleshooting is given but merely a continuance to the next step. It has angered me to the point of no return - back to M$ (luckily I have it on my good computer because GRUB already ruined my hard drive causing me to reformat when I didn't expect to :-\!). 

For JAVA I've tried following:
[http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-java-runtime-environment-jre-in-ubuntu.html)

and another one that I can't find anymore. I am not new to computers (unfortunately) so I really get hot-tempered quick when nothing works. I understand the learning curve issue but if this isn't up and running within 2 days, I vouch to never waste my time with Ubuntu again. I hate it already but am TRYING to give it a chance!

Everytime I try to install JRE it brings up the license agreement but gives no way out of it. I have tried key combinations multiple times but the wretched thing remains! I was told UBUNTU would be compatible and an excellent kernel of linux - well it is the worst I've used yet - first it ruined my damn hard drive - forced to reformat making sure UBUNTU stayed way away. Then it won't let me install ANYTHING because there are errors for everything yet nothing will ever work and if it will, it's going to waste my time too damn much. I've already WASTED hours making this OS just start correctly and do BASIC functions - how pathetic, an OS that cannot come correctly configured for BASIC operation (wireless adapter + JAVA). No wonder very few home users use ubuntu - it's not capable of anything and if it is, you'll put more hours making it capable than it's going to be worth. 

Anyways, onto my next issue as I prepare my hammer for my UBUNTU laptop and all CDs associated. 

My wireless driver (D-link DWL-G120) is not being installed correctly. I read a topic on it but once again UBUNTU tossed a nice error which takes more time of mine to waste trying to remedy while losing patience & tolerance. 

I hope someone has detailed information and instructions on proper installation because if I can't get something accomplished tonight, I'll be ditching UBUNTU, probably forever or until better compatability and simplicity is built-in.

Slmclarengt

---

### Post by zvacet on 2007-09-10
Do you have all repositories open?If you don´t 
[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

For Java try 

> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

For licence agrement you have to scroll down to the end of page and ctrl+tab.Let somebody correct me if I´m wrong.

Good luck and don´t give up!

---

### Post by slmclarengt on 2007-09-10
Thank you zvacet - my JAVA now works successfully however I still am trying to workout the kinks in installing my DWL-G120 correctly. On the contrary I just ordered a NEW USB Wireless card:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833180017](http://www.newegg.com/Product/Product.aspx?Item=N82E16833180017)

So I will probably have to figure out how to install those drivers as well. I made sure there was a complete moneyback guarantee for that card as it is 1) cheap and 2) doesn't have the best ratings :-). 

Also, I am trying to figure out what the directory is for the Desktop because for some reason /Desktop/ worked with some installation but doesn't work anymore. IE: I have a file data2.cab on the desktop I'd like to extract. Also, can someone tell me how to fix the issue of "Driver Driver already installed" because after searching on forums, I couldn't find enough info. to actually fix that. 


EDIT: Also, UBUNTU really bothers me with this absolutely and utterly stupid/frustrating issue: I cannot delete a damn thing! Nothing is my property and I can't control anything via File Browser - what's the point of the stupid thing if you can't touch anything? Man I wish I could just forcefully always be using root access even with it's "unsafety" because I could actually get something done. I want to delete the Prisma02 files in the /etc/ndiswrapper/ folder because that's the only way I can think of to alleviate the issue described before about "Driver driver already installed." It has some trace of my driver but it's not actually installed or else it would work :-).


Slmclarengt

---

### Post by sumguy231 on 2007-09-10
> Also, I am trying to figure out what the directory is for the Desktop because for some reason /Desktop/ worked with some installation but doesn't work anymore
/Desktop means "A folder named Desktop, in the root directory". You should instead either move to your home directory and then 'cd desktop' or 'cd ~/Desktop' since ~ expands to your home directory automatically.

> EDIT: Also, UBUNTU really bothers me with this absolutely and utterly stupid/frustrating issue: I cannot delete a damn thing! Nothing is my property and I can't control anything via File Browser - what's the point of the stupid thing if you can't touch anything? Man I wish I could just forcefully always be using root access even with it's "unsafety" because I could actually get something done. I want to delete the Prisma02 files in the /etc/ndiswrapper/ folder because that's the only way I can think of to alleviate the issue described before about "Driver driver already installed." It has some trace of my driver but it's not actually installed or else it would work .
If you want to delete something you don't own, you'll need to do it as root. You can either:
1.) Do it from the command line:
```
sudo rm <the files you want to delete>
```
2.) Open your file manager as root and do it that way:
```
gksudo nautilus
```
The reason system files are owned by root is so that not any old user can go deleting things - only users with sudo priviledge, and then only if they confirm their password.

P.S. Remember, any new OS carries a learning curve and you'll need a while to get used to it. I know, I'm trying to use FreeBSD right now and I'm getting a bit of a "culture shock" so to speak. But also remember that using an operating system you don't like is a bad idea and will probably cause nothing but headaches. Maybe try a different one.

---

### Post by slmclarengt on 2007-09-10
Thank you very much as that was quite informative and helpful :-). I am actually formatting right now to rid my machine of Ubuntu (temporarily while I get it stable on XP), I will be back with plenty more issues - I just wish some explanations were a little more beginner-friendly as my knowledge of linux errors/terms/conditions/commands is about as much as Neanderthals knew about Televisions :-)

Slmclarengt

---

