---
title: "Am I actually running Feisty Fawn?"
date: 2007-04-25
forum: General Help
---

### Post by EerFoolWVU on 2007-04-25
is there a way to check to be sure I'm actually using Feisty Fawn?


I ran the update, but a few of the features I supposedly should have (such as wobbly window) I don't have



I ran an update-manager -c -d to update, and it now says i'm up to date

---

### Post by Fireblend on 2007-04-25
Can't you find the desktop effects option under system -> preferences?

---

### Post by EerFoolWVU on 2007-04-25
no, desktop effects isn't under system -> preferences which is another reason I'm not sure the update I underwent was actually to Feisty Fawn


however, when i was messing with things in my software sources, looking at the update info, it says feisty updates, so i'm guessing i am running feisty, just don't have certain features available to me

---

### Post by johnc4510 on 2007-04-25
System>About Ubuntu

shows what flavor your using

---

### Post by EerFoolWVU on 2007-04-25
> **johnc4510 said:**
> System>About Ubuntu

shows what flavor your using

yeah, that says I'm running feisty fawn, I looked at that earlier


I'm not sure why some features don't appear for me



I updated from Ultimate Ubuntu 1.3, could this have anything to do with it?

---

### Post by johnc4510 on 2007-04-25
Hmm,

Right click on the drop down menu bar and choose: Edit Menus

Click on Preferences and see if Desktop effects is listed

---

### Post by EerFoolWVU on 2007-04-25
> **johnc4510 said:**
> Hmm,

Right click on the drop down menu bar and choose: Edit Menus

Click on Preferences and see if Desktop effects is listed




nope, not listed in there either


i might just run a clean install of feisty, but i have so much school stuff on here i can't do that until i graduate in a couple weeks

---

### Post by phidia on 2007-04-25
> lsb_release -a <enter>

That should output feisty/7.04

---

### Post by EerFoolWVU on 2007-04-25
yeah, says 7.04.....bah, oh well

---

### Post by Lord Illidan on 2007-04-25
Perhaps it wasn't a full upgrade?

---

### Post by jocko on 2007-04-25
Search synaptic and see if you have the package desktop-effects installed.
If not, install it. And if desktop-effects is not installed, ubuntu-desktop is not installed either, which mean you probably miss other packages as well...

---

### Post by EerFoolWVU on 2007-04-25
> **Lord Illidan said:**
> Perhaps it wasn't a full upgrade?

when I run "update-manager -c -d" it says there are no available updates

---

### Post by phidia on 2007-04-25
You could try   > sudo apt-get update && dist-upgrade

---

