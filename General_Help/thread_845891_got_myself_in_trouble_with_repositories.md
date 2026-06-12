---
title: "got myself in trouble with repositories"
date: 2008-07-01
forum: General Help
---

### Post by earthpigg on 2008-07-01
i understand ubuntu JUST enough to get myself into trouble. part of the fun, right?

sooooo google searching random ubuntu heron stuff, i came across this site:

[SFW link]("http://http://ubuntuland.nireblog.com/post/2007/09/22/35-cool-applications-to-install-on-ubuntu-804-hardy-heron")

sooo i was reading and was like "woot! google earth for ubuntu!" and started to do what it said. cuz i trusted my noobstincts, i know... but some lessons we gotta learn for ourselves :)

specifically, i did

> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

and

> sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

one of those two commands replaced
> /etc/apt/sources.list.d 
with an html file. needless to say, my add/remove and synaptic stopped working. it seems ubuntu was smart enough to automatically backup medibuntu.list as medibuntu.list.save when i changed it, so i was able to sudo nautilus and fix it. i think.

i executed TWO commands in the terminal, but only found one thing i had to fix.... anything else i need to do?

needless to say, i only vaguely understand what either command i executed did or was intended to do.

and needless to say, i know its dumb to start executing sudo commands with no clue of what i am doing... but thats part of the fun! :)

im gonna go google search "ubuntu heron google earth install" while i wait for responses... thanks in advance :)

---

### Post by earthpigg on 2008-07-01
> **earthpigg said:**
> im gonna go google search "ubuntu heron google earth install" while i wait for responses... thanks in advance :)

disregard that. its listed right that in synaptic.

---

### Post by Vivaldi Gloria on 2008-07-01
> **earthpigg said:**
> i executed TWO commands in the terminal, but only found one thing i had to fix.... anything else i need to do?
...
im gonna go google search "ubuntu heron google earth install" while i wait for responses... thanks in advance :)

You can use medibuntu and their web page is here:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

They have howto for hardy:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Next time don't use a year old feisty code on your hardy system.

---

### Post by earthpigg on 2008-07-01
thank you, Vivaldi Gloria.

any response, specifically, to this question:

> i executed TWO commands in the terminal, but only found one thing i had to fix.... anything else i need to do?

---

### Post by Vivaldi Gloria on 2008-07-01
> **earthpigg said:**
> thank you, Vivaldi Gloria.

any response, specifically, to this question:

i executed TWO commands in the terminal, but only found one thing i had to fix.... anything else i need to do? 

Start Synaptic and find repository settings from the menu. Now in that menu have a look at the 3rd party repos tab and the tab about keys (i forgot what that tab is called now, but it's the fourth tab). 

One command adds medibuntu to the 3rd part repos, the other one adds its key. Obviously, adding medibuntu to 3rd party repos didn't work for you and your sources list got overwritten. Have a look at if the key is added in the fourth tab. If yes then delete it. Now you'll have everything restored.

What are these keys you might ask. A key uniquely identifies the medibuntu repo so that you can be sure that you are getting the software you want from them, not from a man in the middle or not a spyware etc.

If you decide to add medibuntu again then you'll see that those two commands for hardy add not only the medibuntu repos but also its key.

Have fun.

---

### Post by earthpigg on 2008-07-01
thanks, chief.

---

### Post by soccerboy on 2008-07-01
The first thing you did was add the encryption key from the repository and then you added the repository.  You can remove the encryption key from System>Administration>Software Sources in the Authentication tab.  Be careful though.

---

