---
title: "How do I disable the adware that comes pre-installed within 12.10 (Quantal)"
date: 2013-04-14
forum: General Help
---

### Post by steviematt on 2013-04-14
So basically I have noticed that my dash in Ubuntu 12.10 was full of adware. At first this didn't bother me but then I realised that I support the free and open source community and any ad-supported OS is a 100% complete violation of this.

My question is how do I disable this awful invasion of privacy and security?
I mean... Canonical surely aren't stupid enough to suddenly destroy Ubuntu, right?

It's not difficult to vote with our feet when it comes to Linux so why damage your reputation this much and embed all of this [adware/spyware]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Controversy") in Ubuntu?

If there is a simple way to disable 12.10's hideous adware and spyware i want to hear it. 

In reality the solution should be stickied on the forums but i searched the forums and found no reference to 12.10's adware. 

Maybe this means this topic will be deleted because it is seen as Ubuntu bashing and others like it have been deleted too because it seems that this awful new direction the Canonincal/Ubuntu team are going is hardly a secret and any user and supporter of the free and open software community will just simply ditch an operating system that becomes an ad-supported OS.

---

### Post by snowpine on 2013-04-14
the link **you** posted tells how to disable this feature. I can only assume that you already know the answer to the question and are just trying to stir things up. :)

---

### Post by steviematt on 2013-04-14
> **snowpine said:**
> the link **you** posted tells how to disable this feature. I can only assume that you already know the answer to the question and are just trying to stir things up. :)


Upon installation I made sure that online search results were disabled within the privacy settings but how do you explain why this is still happening:

[ATTACH=CONFIG]241308[/ATTACH][ATTACH=CONFIG]241309[/ATTACH]

---

### Post by 3rdalbum on 2013-04-14
There are plenty of articles on Google about how to apt-get remove the shopping lens, or how to use the Privacy panel in Ubuntu to stop the lenses from going online.

Actually, you'd better not search Google - it is ad-supported too. Still I've given you enough information to figure it out. I think you might be trolling though.

---

### Post by sffvba[e0rt on 2013-04-14
Hmmm... I see that the picture is showing hits from the Software Center and not some other online search... Have you tried disabling for purchase apps in the Software Center?


404

---

### Post by steviematt on 2013-04-14
> **3rdalbum said:**
> There are plenty of articles on Google about how to apt-get remove the shopping lens, or how to use the Privacy panel in Ubuntu to stop the lenses from going online.

Actually, you'd better not search Google - it is ad-supported too. Still I've given you enough information to figure it out. I think you might be trolling though.

One of the first thing i did was was uninstall all of the lenses out of frustration only to relaise i couldn't search my files and apps so i reinstalled only those two. 

As for being a troll... if a concerned user can't ask for advice about **serious** issues without being called a troll then the vast majority of people on the ubuntu forums will obviously fit your description of a troll.

---

### Post by steviematt on 2013-04-14
> **not found said:**
> Hmmm... I see that the picture is showing hits from the Software Center and not some other online search... Have you tried disabling for purchase apps in the Software Center?

Thanks for your suggestion... without sounding completely idiotic: How do i "disable for purchase apps" in the Software Centre?

I opened up software centre and i didn't see any option where i could do that. I looked through my privacy options again and everything is disabled...

---

### Post by sffvba[e0rt on 2013-04-14
I found this [http://askubuntu.com/questions/47997/how-to-remove-the-for-purchase-section-from-the-software-center?lq=1](http://askubuntu.com/questions/47997/how-to-remove-the-for-purchase-section-from-the-software-center?lq=1) but it does seem to be a heavy work around (and I am not 100% convinced it will remove the items from the dash, as this just disables it in the software center.


404

---

### Post by r-senior on 2013-04-14
You can disable available apps in the Dash using dconf editor (which you might need to install). This will remove all available apps (paid and free) from Dash results though.

---

### Post by steviematt on 2013-04-14
> **r-senior said:**
> You can disable available apps in the Dash using dconf editor (which you might need to install). This will remove all available apps (paid and free) from Dash results though.

Thanks!!! This worked a treat.
Already had dconf installed and now I have all the unwanted ads off my dash. 

Hopefully in future releases all of this useless bloat will be disabled by default otherwise... need i say more...

---

### Post by Bucky Ball on 2013-04-14
Please mark this thread as solved by editing the first post, click 'Go Advanced' and change the prefix of the title to 'Solved'. Thanks.

---

