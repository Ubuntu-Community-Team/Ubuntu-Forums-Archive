---
title: "Serious Java Problem Help!!"
date: 2008-01-30
forum: General Help
---

### Post by adn258 on 2008-01-30
Okay so you need Java to run certain applications through your browser like IRC chat rooms and other chat stuff.  when you go to the first link below and say you enter the chat room it says your missing a plugin so I install Java and it doesn't notice it or make it work and I can't use the one called GCJ becasue it doesn't work check the second link.  What should I do?  This is an annoying problem becasue I can't use some chat programs.  


[http://searchirc.com/search.php?F=exact&T=chan&N=2033&I=30Something](http://searchirc.com/search.php?F=exact&T=chan&N=2033&I=30Something)

[http://ubuntuforums.org/showthread.php?t=616261](http://ubuntuforums.org/showthread.php?t=616261)

---

### Post by bschleusner on 2008-01-30
if you enable multiverse on your installation sources, you can install java right off the ubuntu repository

---

### Post by adn258 on 2008-01-30
> **bschleusner said:**
> if you enable multiverse on your installation sources, you can install java right off the ubuntu repository

I figured this out dudes and a lot of people seem to have this problem you use

sudo update-java-alternatives --set java-6-sun

the command above and install java 6 when it asks but then most important you have to then remove "gcjwebplugin" from the packages synaptic package manager!!!!  I installed 6 then removed GCJ and then used the sudo update java code above at least that's the order I did it in good luck.  Below is the problem people are having!!!

[http://ubuntuforums.org/showthread.php?t=616261](http://ubuntuforums.org/showthread.php?t=616261)

---

### Post by ubuntu-freak on 2008-01-30
Install the "Essential Packages" in my easy [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Make sure you do this after
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
Nathan

---

### Post by adn258 on 2008-01-31
> **reassuringlyoffensive said:**
> Install the "Essential Packages" in my easy [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Make sure you do this after
 
**rm $HOME/.mozilla/firefox/pluginreg.dat**
 
Nathan

what is this about?

---

### Post by ubuntu-freak on 2008-01-31
> **adn258 said:**
> what is this about?

 
It includes everything you need basically. Didn't you click on the link? The restricted-extras package includes java and lots more. Plus I added even more packages to the install command. It's worth you doing.

The "rm $HOME" command forces Firefox to update its records of what plugins you have. It recreates the pluginreg.dat file later.

Nathan

---

### Post by deeann on 2008-01-31
Hey Nathan! Por Favor and edit to the include full path on this last post also? I know you're explaining it but some people might just copy/paste exactly what you posted.

adn258, the first command Nathan posted is fine and does what he says it does, though caution is good.

---

### Post by ubuntu-freak on 2008-01-31
> **deeann said:**
> Hey Nathan! Por Favor and edit to the include full path on this last post also? I know you're explaining it but some people might just copy/paste exactly what you posted.

adn258, the first command Nathan posted is fine and does what he says it does, though caution is good.

 
What do you mean? I'm directing them to my main how-to. The rm command is a reminder incase they only download the packages and do nothing else.
 
Nathan

---

