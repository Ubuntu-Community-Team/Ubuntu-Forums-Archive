---
title: "Trojan in SecondLife?"
date: 2007-06-07
forum: General Help
---

### Post by Pay87 on 2007-06-07
Hello!
I have a simple question.
My little son downloaded SecondLife from here:
[http://www.getdeb.net/release.php?id=944](http://www.getdeb.net/release.php?id=944)

The file loaded the game and made everything ready to play it.
That all worked fine but somebody told me that this game would spy my firefox browser.
I remember while installing it, i saw something installing in the mozilla runtime folder..
Besites of that i don't know how to watch my autostart programs and services/deamons because i am very new to linux.

I deinstalled the game but i am not sure if the package manager just had deinstalled the getdeb file or also the downloaded file.
Is there somebody who can tell me what to do?
Is there a security risk on my pc?
Should i reinstall? :(

---

### Post by EndPerform on 2007-06-07
When you uninstalled, it should have taken the files it installed with it.  SecondLife does have a mozilla component to it which they are using to browse their help files, but this is the first I've heard of this 'spy' issue, and I've been running the Linux client for a while now.

---

### Post by H3g3m0n on 2007-06-07
I am fairly sure that Second Life itself hasn't got any spyware, the client is OpenSource for starters with enough people looking through the code that someone would have spotted something, also if there was some spyware added (such as to the installer) it would most likely be Window specific (since porting spyware would be a huge pain).

The only google results for secondlife spyware was for a spyware remover called second life (which actually seemed like it would be more likely to be spyware itself.

Its possible that the deb distributed on there has something nasty added into it since its just a 3rd party build, did the person who told you it was spying on you mean specifically the Ubuntu deb you downloaded or just Second Life in general?

If they meant Second Life in general then I think its fairly likely that they don't have a clue what they are talking about, there would have been heaps of pissed of people angry about it, the community around Second Life would make spyware unfesable as there are quite a lot of tech people and its entirely based on the community who would revolt, there would also probally be a SecondLifeLite (like Kazaa lite), and from what I've heard of Linden Labs they don't seem the kind of company to do it.

---

### Post by Pay87 on 2007-06-07
Thanks, i asked him and he told me that he installed the same file as i did.
How can i find out if there is something nasty in the deb file above?
As you told me there is no spyware in second life, but is there something in this deb?

Another generel question is:
if a deb file downloads something from the www and i uninstall the deb file, does it automatically delete the third party downloaded files, too?

thanks, you made my mind more relaxe than before! :)

---

### Post by H3g3m0n on 2007-06-08
Unfortunately debs afaik are installed as root, so it might be possible to code them to slip in stuff that wouldn't be uninstalled if there was an intention. As for the files it downloads it depends on how the deb is coded to work when uninstalled.

The only sure was to locate any nasties would be installing under a clean environment and comparing any changes to the original install fresh install (such as md5 hash sums on files). Also checking the SL binary with the version that Linden Labs produces.

I would find out more about why your friend thinks it includes some kind of spyware, he might have just seen the word mozilla while it was installing and panicked, also there would be quite a lot of people downloading the debs from getdeb and it would be fairly important to get them removed if they do have something nasty in them and there could be stuff in other packages too. Spyware might be common place for Windows, but I've never seen any in Linux, Trojans would be a possibility though, and there have been cases in the past such as the Apache repos getting hacked and a trojan put into the source code (although it was spotted fairly quickly).

Looking at the getdeb site there does seem to be a training/recruitment system in place, so its less likely there is something bad there since its not possible that just anybody can put files on there. I personally doubt theres much to worry about and I wouldn't be reinstalling but its always worth checking out.

You can get the official Second Life client from their website, it won't install like the debs do but you can just extract the folder to somewhere (/opt is a good place for precompiled packages) and then make a link to the executable in /usr/local/bin

[http://secondlife.com/community/linux-alpha.php](http://secondlife.com/community/linux-alpha.php)

---

### Post by NULL712 on 2007-06-16
how did you uninstall second life? because I have had a hard time trying to figure that out.

---

