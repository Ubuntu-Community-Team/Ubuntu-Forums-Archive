---
title: "[SOLVED] Why isn't there an update for Rhythmbox in Synaptic?"
date: 2007-07-26
forum: General Help
---

### Post by keyboardashtray on 2007-07-26
I want to edit tags from within Rhythmbox. I don't want an external program to do it, because I want to fix inconsistencies on the fly, if I have to launch a program just to change the name of Beatles to The Beatles, I'm not going to bother.

I also would like to stay with Rhythmbox, but if someone told me about a player that did everything like Rhthmbox but also auto deleted old podcasts I might check that out.

According to [http://live.gnome.org/Rhythmbox/TagWriting](http://live.gnome.org/Rhythmbox/TagWriting) version 0.10.6 can edit the tags on .ogg files. Why isn't there an update for it in Synaptic, or better yet automatically with the update manager? It is the default music player for the default desktop of the Ubuntu family. Do I have to wait for the next release of Ubuntu just for the easy way to get the new Rhythmbox? Or do I have to check "Proposed" from the update sources?

---

### Post by kevinlyfellow on 2007-07-26
If you're up to it, you can compile your own version of Rhythmbox.  This website does a great job guiding you through the process [http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html](http://thecrosstalk.blogspot.com/2007/06/how-to-install-rhythmbox-with.html)

---

### Post by keyboardashtray on 2007-07-26
I'll bookmark the link - but is that the only way to update it?

---

### Post by Steveway on 2007-07-26
You could just wait till the update comes into the repos.
WHOOOO!!!!!!!!!!!!!! What the FSCK was that? A fraking damn lightning bolt outside. Sorry for the interupt but that really suprised me.

---

### Post by keyboardashtray on 2007-07-26
Ok, so bottom line, there is no "easy way" button I'm missing, or checkbox I haven't checked, that would allow me to update Rhythmbox?

Apparently they are up to version [11.1]("http://en.wikipedia.org/wiki/Rhythmbox#Changelog")

---

### Post by kevinlyfellow on 2007-07-26
The link I posted is actually copy and paste stuff.  

But I've never made a deb from source.  I'll give it a try and if I succeed, I'll post it here.

---

### Post by keyboardashtray on 2007-07-27
Oh man, I hope you don't go to any trouble for lil ol' me. I appreciate the help, but I was more or less checking if I am missing the obvious way to simply update it.

I could manage to follow the tutorial you linked to, but I scroll down and I see people have problems. This is why I hesitate to mess around in the console. It isn't just about ability - I dodge the console by default. Could I copy and paste? Yes. Would I know what I'm doing? No - and there the problem lies. I like the integrated update features - I like the Ubuntu Approved feel to doing things,  and I don't want to lose Rhthmbox in my application menu or end up with a slew of other problems that will send me back here.

Thanks for the help, though :) - I'll assume that the answer is no. I guess my question was 25 percent How? and 75 percent Why? as in "why doesn't Ubuntu offer the most recent version of it's music player?"

---

### Post by keyboardashtray on 2007-07-27
> **Steveway said:**
> You could just wait till the update comes into the repos.


How long does that take? I'm on .10 and apparently they are up to .11.1.

---

### Post by kostkon on 2007-07-27
Ubuntu does not try to be bleeding edge. The only updates you get in Ubuntu are security updates. If you want to get feature updates, first of all, you have to activate your backports repository. Then, If you activate it and won't get a new version of Rhythmbox, you'll have to ask the guys at the backports repository to backport it for you (and for the rest of us, of course). 

By saying backport, I mean they will make the version of Rhythmbox that the newest version of Ubuntu has (in our case Gutsy) available to an older version, if this is possible (in our case, Feisty).

Thus, go to the [launchpad page of the feisty backports]("https://launchpad.net/feisty-backports") and fill a bug report asking to backport the version of Rhythmbox that Gutsy has to Feisty (in our case Rhythmbox 0.11.1). Don't forget to search if someone else has already done a similar bug report.

You have to be a registered user of launchpad to do this, unfortunately.

After this, if they say that a backport is possible and they are going to do it, then the only thing you have to do is wait for the update to come.

---

### Post by keyboardashtray on 2007-07-28
> **kostkon said:**
> Ubuntu does not try to be bleeding edge. The only updates you get in Ubuntu are security updates. If you want to get feature updates, first of all, you have to activate your backports repository. Then, If you activate it and won't get a new version of Rhythmbox, you'll have to ask the guys at the backports repository to backport it for you (and for the rest of us, of course). 

By saying backport, I mean they will make the version of Rhythmbox that the newest version of Ubuntu has (in our case Gutsy) available to an older version, if this is possible (in our case, Feisty).

Thus, go to the [launchpad page of the feisty backports]("https://launchpad.net/feisty-backports") and fill a bug report asking to backport the version of Rhythmbox that Gutsy has to Feisty (in our case Rhythmbox 0.11.1). Don't forget to search if someone else has already done a similar bug report.

You have to be a registered user of launchpad to do this, unfortunately.

After this, if they say that a backport is possible and they are going to do it, then the only thing you have to do is wait for the update to come.

Thank you Kostkon... this is exactly the information I was looking for - I've read somewhere about how Ubuntu updates are mainly security, but I wasn't entirely clear about which programs fell under the umbrella of backports or proposed. Right now I have them all checked (from the update list) and manually pick them. 

I'll go look into launchpad, I'm sure somebody already suggested it but it'd be neat to know if the team is considering it.

---

