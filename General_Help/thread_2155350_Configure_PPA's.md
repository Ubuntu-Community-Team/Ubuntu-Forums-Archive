---
title: "Configure PPA's"
date: 2013-06-18
forum: General Help
---

### Post by NoobKing on 2013-06-18
Is it possible to use just one program in a ppa?

in the past i added a ppa for one program not knowing there were others on it and after an update it broke my system.

---

### Post by mc4man on 2013-06-18
Well you could install & use synaptic, it affords you a better look at what's upgradeable & you can pick & choose as desired.
It also has an "Origins" tab that lets you see all the packages in a ppa, either installed or available 
(screen 1 shows all avail. from that ppa, screen 2 shows what is installed from that ppa

Otherwise if you know the package name then use apt-get to install your ppa upgrade & nothing else from the ppa unless it's a dep of your ppa package

sudo apt-get install --only-upgrade <package name>

Ex. - if  I wanted the newer rhythmbox from the gnome 3 ppa for raring, after enabling the ppa I'd - 
```
sudo apt-get update && sudo apt-get install --only-upgrade rhythmbox
```

In that case upgrading rhythmbox would also upgrade the other rhythmbox packages & that's all.

Sometimes just a package name won't give you all you want, in that case you can add on - 
Ex. I want to upgrade mplayer & mplayer-doc from a ppa for precise. In this case there is an add. dep of libopus0, so - 

```
sudo apt-get install --only-upgrade mplayer mplayer-doc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libopus0
Suggested packages:
  opus-tools netselect fping
The following NEW packages will be installed:
  libopus0
The following packages will be upgraded:
  mplayer mplayer-doc
2 upgraded, 1 newly installed, 0 to remove and 11 not upgraded.
```


Do keep in mind you can add an -s **to any apt-get command** to simulate, nothing happens for real. It's a good way to check before doing a cli upgrade
Ex.
```
sudo apt-get [COLOR="#0000CD"]-s[/COLOR] upgrade
```
or from first Ex.
```
sudo apt-get update && sudo apt-get [COLOR="#0000CD"]-s[/COLOR] install --only-upgrade rhythmbox
```

If all is well then rerun command with the -s removed

---

### Post by NoobKing on 2013-06-18
Thank you for your well written response it was very helpful.

I liked using synaptic in the past and would prefer to do it that way then type in the command line.

i was surfing around and saw something about priorities and it said i can do it in synaptic but i do not see a way. is it the settings > internal option where i would enter a value. or would locking the whole ppa except for what i want be a better way?

---

### Post by Yellow Pasque on 2013-06-18
It would be better to put packages that you don't want "upgraded" to the PPA version on hold (Synaptic calls it "Lock Version" in the Package menu).

---

### Post by HiImTye on 2013-06-18
[http://askubuntu.com/questions/96587/is-it-possible-to-only-allow-specific-packages-updates-from-a-ppa](http://askubuntu.com/questions/96587/is-it-possible-to-only-allow-specific-packages-updates-from-a-ppa)[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by mc4man on 2013-06-19
If you are concerned about using synaptic for upgrades & still inadvertently upgrading unwanted from the ppa then I'd go with pining the ppa as described in the link in above post. Gave it a try & works fine.
Just upgrade the package(s) you do want from the ppa first before pining the ppa.

If unsure of the exact   o=LP-PPA-xxxx line to put in the  file then run apt-cache policy & you'll find it on your ppa's lines

---

### Post by NoobKing on 2013-06-19
ok i looked into everything and tried it out. my new question on this is, is there an easy to to set up a pin to include the package and its dependencies?

---

### Post by mc4man on 2013-06-19
> **NoobKing said:**
> ok i looked into everything and tried it out. my new question on this is, is there an easy to to set up a pin to include the package and its dependencies?

Not sure I understand your question's intent concerning deps

If you pin the ppa then only packages you upgraded **before pinning **will be eligible for future upgrades f**rom the ppa**, this includes any deps that the ppa provides, if any.

If the deps are installed from the normal Ubuntu repos then no reason to pin them, Ubuntu only does security & occasionally some bug fixes post release so you would not want to pin those packages to current versions

---

### Post by NoobKing on 2013-06-19
> Package: *
Pin: release o=LP-PPA-nathan-renniewaldock
Pin-Priority: 400

Package: ddclient
Pin: release o=LP-PPA-nathan-renniewaldock
Pin-Priority: 500


Using the setup from above i would need to have all the dependencies for ddclient in that ppa listed there as well otherwise it would not use them correct? so my question is there a short hand way to have the program there along with its dependencies and set a pin-priority to it?

---

### Post by mc4man on 2013-06-19
> **NoobKing said:**
> Using the setup from above i would need to have all the dependencies for ddclient in that ppa listed there as well otherwise it would not use them correct? 
No
With the ppa not pinned install/upgrade the ppa's ddclient  (in synaptic would be fine
This will also install any needed dependencies  inc. any in the ppa.
Also take a look in synaptic > Origin > that ppa for anything else you want installed/upgraded **from the ppa**

Once that's all done then just pin the ppa, no need to pin any ppa packages you've installed

If any of the previously (pre-pin),  installed packages in the ppa updates,  you'll be offered & be  able to upgrade to them.

Do note - 
If any of the ppa packages you installed are upgraded in the Ubuntu repos to a higher version than the ppa then you'll be offered to upgrade to them. At that point you decide what to do, ignore the upgrades, accept the upgrades or ignore & see if the ppa updates those packages in due course

---

