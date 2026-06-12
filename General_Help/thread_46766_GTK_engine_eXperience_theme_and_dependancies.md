---
title: "GTK engine eXperience theme and dependancies"
date: 2005-07-06
forum: General Help
---

### Post by Schonhose on 2005-07-06
Hi all,

I'm fairly new to Ubuntu but I've managed to install Warty on my laptop. First let me explain why I installed Warty instead of Hoary. Hoary has Gnome version 2.10 which has a nasty bug displayed with the eXperience theme I'm trying to install.

More info on the eXperience theme and engine can be found at [this site](http://benjamin.sipsolutions.net/Projects/eXperience).

I've edited the sources list to include
[php]deb http://benjamin.sipsolutions.net/debian/ stable/[/php] 
so I can see the program in Synaptic (Please note that universe is not enabled in this setup yet, don't know if it's important or not).

Upon selecting the package I would like to install I'm presented with the following screen: (I do apologize, cause this screen is in my native language Dutch.)

[img]http://home.wanadoo.nl/dennis.mooibroek/screen1.png[/img]

I guessed something during the install must have gone wrong so I decided to re-install the required packages using Synaptic. However, after re-installing these packages I'm still faced with the error above.

When I compared the versions they are al installed (as can be seen [here](http://home.wanadoo.nl/dennis.mooibroek/screen2.png)). 

Now I'm at a dead end and hopefully you guys can push me of in the right direction. TIA.

---

### Post by rwabel on 2005-07-07
the problem is, that your libraries are older than what gtk engine requires. You can upgrade to hoary and it will work. Otherwise try to compile it by yourself from the source. The upgrade is worth it!

---

### Post by Schonhose on 2005-07-08
[QUOTE=rwabel]the problem is, that your libraries are older than what gtk engine requires. You can upgrade to hoary and it will work. Otherwise try to compile it by yourself from the source. The upgrade is worth it![/QUOTE]

Sorry rwabel, I forgot all about this post... I managed to find out the libs where older and updated them. So now everything is working fine.

hoary is no option because of gnome 2.10 ;)

---

### Post by rwabel on 2005-07-08
no problem, can you tell me about the bug it's having in gnome 2.10?

---

### Post by Schonhose on 2005-07-08
[QUOTE=rwabel]no problem, can you tell me about the bug it's having in gnome 2.10?[/QUOTE]

Sure, have a look at : [http://freshmeat.net/projects/eXperience](http://freshmeat.net/projects/eXperience) and than the first comment made by Doug. He has attached screenshots of the problem.

Benjamin, the author of eXperience mentioned it was a known bug in Gnome:
[http://bugs.gnome.org/show_bug.cgi?id=302223](http://bugs.gnome.org/show_bug.cgi?id=302223)

Not sure how this is going to effect badger at this moment. I noticed it has Gnome 2.11, perhaps the issue is resolved in that version.

---

### Post by rwabel on 2005-07-08
[QUOTE=Schonhose]Sure, have a look at : [http://freshmeat.net/projects/eXperience](http://freshmeat.net/projects/eXperience) and than the first comment made by Doug. He has attached screenshots of the problem.

Benjamin, the author of eXperience mentioned it was a known bug in Gnome:
[http://bugs.gnome.org/show_bug.cgi?id=302223](http://bugs.gnome.org/show_bug.cgi?id=302223)

Not sure how this is going to effect badger at this moment. I noticed it has Gnome 2.11, perhaps the issue is resolved in that version.[/QUOTE]
 I see, but isn't a big problem isn't it? I just mean, you are missing quit a bit by staying with warty.

---

### Post by Schonhose on 2005-07-08
I couldn't care less, but the laptop is for my girlfriend who's only experience with computers is Windows XP.

Windows XP took a lot of resources on the laptop, so I decided to use Warty, mainly because of the Gnome bug (otherwise I couldn't use the experience theme). 

Next week I'm installing Hoary on my own machine. Not sure if I'm going to use Kubuntu or Ubuntu yet. Perhaps I will give KDE (and the XP themes) a try. This will give me a change to see if they are beter or not.

It was my understanding Gnome is the lighter windowmanager compared to KDE.

---

### Post by rwabel on 2005-07-08
I don't know which one is lighter. They are both "huge" if you compare with xfce, fluxbox etc

---

### Post by khughitt on 2007-04-23
hehe, digging this one up from the grave..

Was curious if anyone has been able to get this theme / engine working with either edgy or feisty? I've tried both the repository and the tarball to install, but neither will work. Anyone have luck with this?

---

### Post by Fafafu on 2008-06-11
Hi, i've found a repository which works on hoary...

[http://zchan.homeunix.net/pub/Ubuntu.APP/eXperience/](http://zchan.homeunix.net/pub/Ubuntu.APP/eXperience/)

---

