---
title: "FireWall? Mediaplayer?"
date: 2007-12-22
forum: General Help
---

### Post by Dojan5 on 2007-12-22
I didn't find any software forum, so i thought it'd probably fit here.
I surfed around like 3 hours ago, and i discovered, I HAVE NO FIREWALL I THINK!!!!
Umm, yer, i did think i think, :S.
A couple of hours earlier i copied all my files from my Mp3 and discovered Amarok, it said it installed Mp3 support and asked me to restart Amarok.
So i did, and it repeated itself, so i went on with that until i gave up. It install the codec but it ignores it and installs it again?

Well, is there any other Media Player software for Kubuntu?
And WHERE do i find a firewall that work with Kubuntu? ZoneAlarm?
Thanks for bothering!!!

---

### Post by santiagoward2000 on 2007-12-22
> **Dojan5 said:**
> I didn't find any software forum, so i thought it'd probably fit here.
I surfed around like 3 hours ago, and i discovered, I HAVE NO FIREWALL I THINK!!!!
Umm, yer, i did think i think, :S.
A couple of hours earlier i copied all my files from my Mp3 and discovered Amarok, it said it installed Mp3 support and asked me to restart Amarok.
So i did, and it repeated itself, so i went on with that until i gave up. It install the codec but it ignores it and installs it again?

Well, is there any other Media Player software for Kubuntu?
And WHERE do i find a firewall that work with Kubuntu? ZoneAlarm?
Thanks for bothering!!!

Hi!
About the Firewall, you shouldn't be worried. X/K/Ubuntu comes with a firewall already installed called iptables. If you want, you could install something like **Firestarter** or **guarddog** (which may fit better on KDE), which are just interfaces, and let you configure it. You can find it in Ubuntu's repositories, just open **Adept** and look for it there.
Cheers!

---

### Post by Dojan5 on 2007-12-22
Hiyas
Thanks for the reply, but now i have a problem...
When i open adept this message comes up:
"The ATP database could not be opened! This may be caused by incorrect ATP configuration or some similar problem. Try running ATP-setup and ATP-get update in the terminal and see if it helps to resolve the problem"
What should i do?
Id rather not stick to Konsole the rest of my life :S
Thanks

---

### Post by pyronaut on 2007-12-22
if you use synaptic .. thats the frontend for apt. Depending on whether you are using KDE or gnome you will be able to configure apt accordingly. My recoomendation will be to google for the unofficial ubuntu starter guide and most of your questions ar answered in a step- by step manner there

---

### Post by Dojan5 on 2007-12-22
I have read a bit of it.
But, ```
System-->Administration-->Software Sources-->Third-party software-->Add
```
There we have a problem, i don't have any System>ADMINISTRATION
And i am the computer admin.
Ain't there a Kubuntu guide?

---

### Post by santiagoward2000 on 2007-12-22
Well, I'm not really familiar with Adept, you probably need to enable Ubuntu's universe and multiverse repositories. I guess you should have a **Software Sources** somewhere, but I haven't used Kubuntu in a while, so I'm not really sure where that could be, sorry!

---

### Post by pyronaut on 2007-12-22
thats not the code....that's the menu list under gnome.. if you go the the sytem tab on th e panel and click on it .you'll see administration  and .. click on that it'll show you synaptic and when you click on it it'll autmotically ask you for your rot passwork. Another simple way open a terminal and type sudo synaptic ..or alt+f2 .. bring up the run console and type gksu synaptic

---

### Post by Dojan5 on 2007-12-22
> **pyronaut said:**
> thats not the code....that's the menu list under gnome.. if you go the the sytem tab on th e panel and click on it .you'll see administration  and .. click on that it'll show you synaptic and when you click on it it'll autmotically ask you for your rot passwork. Another simple way open a terminal and type sudo synaptic ..or alt+f2 .. bring up the run console and type gksu synaptic

I know its not the code, its just nevigating through the menus...
But, i dont have that sort of menu.
The system menu in KUBUNTU contains Documents, home, storage, remote and users... Thats all, no administration thingy, thats Ubuntu.
And, i don't think [COLOR="Red"]**Kubuntu**[/COLOR] have synaptic to be honest...

---

### Post by Dojan5 on 2007-12-22
Grr, i cant edit the posts, i dunno why...
Well, anyway, i don't get what synaptic (whatever that is) have to do with Xine or firewalls or something...
And yes, i found Xine, but i cant install it :S
Im kinda raiding the net to find it...

---

### Post by pyronaut on 2007-12-22
In KDE you have the system tab and you'll find synaptic under it you shoudl also see software sources under it if you want to edit your apt sources. Basically, the intial system comes only with the base ubuntu software repositories so that a lot of other software thats  out there eg universe, mutliverse etc are not enabled by default, this i think is to keep Canoncial from being embroiled in hacks etc. So once you enable these thrid party repositories you'll find a lot more software once you have updated the packages list

---

### Post by pyronaut on 2007-12-22
best bet is to again lok at the unofficila ubuntu site where they have step by step methods.. if they are using gnome ...you can always log off and log in to agnome session

---

### Post by Dojan5 on 2007-12-22
My whole computer system crashed while entering Gnome..
I dont think i did everything correct...

---

