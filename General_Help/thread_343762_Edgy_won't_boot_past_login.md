---
title: "Edgy won't boot past login"
date: 2007-01-21
forum: General Help
---

### Post by Cornbreadly on 2007-01-21
This might be moved to the beginners section but I do not feel I am absolutely clueless.

Anyways, the Ubuntu splash loads and I get to the login screen.  It is a dual boot xp (wife) and I only have the one admin login for myself.  Some of what i have researched seemed to have success booting into accounts that weren't admin and implementing workarounds that way.

I enter the correct name and password, it goes to text to load for about a quarter of a second, and shoots me back to the login screen.  I can successfully log into recovery mode but any skills I have are useless there.  

I can't think of anything new I have done except for use a SD card r/w for the first time.

Right now I am in a live cd session and I have mounted my linux hd.  Everything seems to be there.  Beyond the vague description, I don't have much else to offer any would be helpers.

---

### Post by mindwarp on 2007-01-22
You might try re-wording this post if you are a non native english writer, its a bit hard to understand the problem.

Here are my suggestions:

[LIST=1]
[*]Log in from the command line -- hit crtl-alt-f1 to get to console mode, and from there make sure you are in your home directory, and rm -rf the following: **.gnome, .gnome2, .gconf, .gconfd, .metacity**
[*]Check free space on the system.  **"df -h"** from the command line will show you how full file systems are.  If /tmp is 100% full you may have a problem.[/LIST]

---

### Post by Cornbreadly on 2007-01-22
Thanks it worked.  A little too zealous with bittorrent and filled up my hard drive.

Just a quick question...  I asked for help last night after having a few beers while watching the football games yesterday.  So my verb tense and pre-submit proof reading were sub-par.  Plus, this forum has a very high standard compared to the rest of the internets.  But I had a few of my friends here read my post and we have a little bet going on that you could settle.  

Did you just throw that "not a native english speaker" part in there as a backhanded way to shame a poster into using proper grammar?  Or did I just not make that much sense because of my lack of tech-speak?

Personally, I bet on the former than the latter.  I might begin to use your methods in other forums for my own enjoyment.

---

### Post by mindwarp on 2007-01-23
> **Cornbreadly said:**
> 
Did you just throw that "not a native english speaker" part in there as a backhanded way to shame a poster into using proper grammar?  Or did I just not make that much sense because of my lack of tech-speak?

Personally, I bet on the former than the latter.  I might begin to use your methods in other forums for my own enjoyment.

Ha my english is far from being great also, and no shame was intended.  I just noticed no responses, and I had to read it a few times to figure out the problem.  I have worked with a decent amount of non-native english speakers / writers and sometimes it helps if you ask them to rephrase a problem.

---

### Post by Cornbreadly on 2007-01-24
Oh well.  You accidentally discovered a new way to be a smart-***.  I thank you.  Again, thanks for the linux knowledge.

---

