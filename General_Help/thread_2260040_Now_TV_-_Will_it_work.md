---
title: "Now TV - Will it work??"
date: 2015-01-08
forum: General Help
---

### Post by fluctuatinganomaly on 2015-01-08
Hope general will cover the topic of this one.

Issue is Now TV - Which may or mate not be a variant / update of sky go. 

When trying to watch anything, obviously I get a message telling me its not compatible and that I need to install silverlight - I've followed through on that and installed the moonloght application - which has solved nothing. So on further investigation I have found out about Pipelight... Which I have also installed..... which also does nothing.

Is there actually ANY way for me to watch now tv on my Ubuntu laptop, with firefox?? Or is my only option going to be wiping Ubunto and going back to windows 7??

I don't really want to go back to windows 7, but I'm gonna be loaning out my laptop to my sister for a while and everything needs to work... at least on a basic level and shes getting .... well, annoyed would be the gentle word, with me that its not "just working"

I don't mind that I might have to mess a little bit to get things to work, but if I go back to windows 7 - I'll be staying there this time - simply because I don't want to have to be uninstalling / re-installing everytime I come across something that just doesn't work with Ubuntu period.

Seriously..... you would have thought that these mainstream companies and TV streaming services would up there game and have things functioning with multiple OS set-ups

~Matt

---

### Post by DuckHook on 2015-01-08
> **fluctuatinganomaly said:**
> ... you would have thought that these mainstream companies and TV streaming services would up there game and have things functioning with multiple OS set-ups...Actually, they have no incentive to do anything of the sort. The Linux community represents a very small fraction of the consumer-oriented market. Yet, to maintain a Linux port takes as much of their resources as it does to maintain Windows. The real answer is for streamer vendors to avoid straightjacketing themselves in the first place by basing their apps on jailware like silverlight, but the idea of OS or even browser agnosticism is a concept that few of them have been able to wrap their tiny little heads around until only recently.

Moonlight and Pipelight remain, at best, the efforts of the FOSS community to reverse-engineer a piece of jailware without access to that jailware's code. It will always be no more than a partial success, and is already on the road to has-been status as more and more vendors abandon jailware like silverlight for open standards like HTML5.

Sorry to hear that you won't be coming back to Linux. It's a tough decision having to choose between the jailed but wide availability of Windows versus the free and open but limited selection in Linux, and I don't envy you your dilemma. The only thing I could suggest would be running a VM or dual booting, but there are times when it's not worth the trouble. Only you (and your sister, it seems) can decide which is the best road for you.

---

### Post by fluctuatinganomaly on 2015-01-09
I'll be honest, vm didn't cross my mind. Must admit, was a little frustrated last night. mainly with my sister, but partially due to the lack of availability to services that most people these days would consider a 'standard' 

I guess a vm could work, but in all honesty, maybe too much hassle for what its going to be used for. I'm still relatively new the the VM apps and they confuse me a little. 

A dual boot had occured to me, but I believe the best way (and possibly that only real way) of acomplishing that would be to re-install win 7 then dual boot ubuntu - as opposed to having ubuntu and installing a dual boot with windows on top of that. Which seems sort of moot when this particular scenario, only begs the access to windows 7.

*sigh*

Well , thanks for you're reply. For now I guess I'll be heading back to windows - But perhaps I'll be back with the ubuntu community IF my sister ever returns my laptop to me and gets her own machine :P

I guess for now this thread can be marked as closed, unless any one else has any other input they would like to share?

~Matt

---

### Post by oldos2er on 2015-01-09
> **fluctuatinganomaly said:**
> Issue is Now TV - Which may or mate not be a variant / update of sky go. 

When trying to watch anything, obviously I get a message telling me its not compatible and that I need to install silverlight - I've followed through on that and installed the moonloght application - which has solved nothing. So on further investigation I have found out about Pipelight... Which I have also installed..... which also does nothing.

You may need to install [User Agent Overrider]("https://addons.mozilla.org/en-US/firefox/addon/user-agent-overrider/") too, although I can't say if it will work or not.

---

### Post by monkeybrain20122 on 2015-01-09
Moonlight has been dead for two/three years and it never worked anyway. 

You need pipelight (and probably user agent overrider as oldo2ser suggested) After that silverlight would work in Firefox. Basically it is running Windows' silverlight plugin in a patched and enhanced wine environment so it uses the same version of silverlight as Windows and would work on all such websites. Whereas moonlight, even when it was alive, was a crippled implementation of outdated silverlight several versions behind which didn't support drm contents ('open source implementation' permitted by MicroSoft), so it has been a pointless waste of time right from the start.


[http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html)

I agree with DuckHook that ultimately web streaming should move away from jailware like silverlight. But that unfortunately doesn't solve your problem in the mean time.

---

