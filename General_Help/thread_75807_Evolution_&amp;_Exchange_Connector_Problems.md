---
title: "Evolution &amp; Exchange Connector Problems"
date: 2005-10-14
forum: General Help
---

### Post by screamingFit on 2005-10-14
Seems that Evolution and the Exchange Connector just weren't meant to be.  

With the crashing, exchange-backend process problems, etc. that have been with us for quite a while, does anyone know of when this will finally be fixed?  I really don't want to shell out for Crossover just to run Outlook and OWA is awful through Firefox. 

Is this a problem just with the Evolution packages in Ubuntu or would I have the same problems under SuSE?

I know with OSS, you can't really complain too much but, come on!

---

### Post by riggsd on 2005-10-14
Same issue here... I was hoping the upgrade from Hoary to Breezy would improve things, but it seems even worse for me now. The Exchange connector doesn't give me as many error messages, but it just silently stops getting new mail until I close Evolution and restart it. What a pain!

---

### Post by WickedImp on 2005-10-14
I got it mostly to work. Purged everything Evo related (also exchange stuff) and deleted .evolution in home dir. Reinstall after this and create your new exchange account. Should work - no backend crash anymore.

Problem left: I miss this red Button on the bottom left next to contact and email which was named 'Exchange'. It was the button where it was possible to browse the exchange folders and assign favorite public folders. Needed to get Public Contacts to work with EMail Contact Book.

---

### Post by elasticwings on 2005-10-14
I tried that and it doesn't work for me. :(  I'm one of those people with different login name and mailbox name.  :(

---

### Post by elasticwings on 2005-10-14
Bizzzump, help me plz. ;D

---

### Post by N6546R on 2005-10-14
[QUOTE=elasticwings]Bizzzump, help me plz. ;D[/QUOTE]

I've had trouble with Evolution and the Exchange Connector for a very long time. Unfortunately it seems to be the only game in town. I keep hoping that Thunderbird will add native support, but it doesn't look like that'll happen anytime soon.

With such a (relatively) large audience for a decent Outlook replacement, why has only Ximian stepped to the plate?

Perry

---

### Post by screamingFit on 2005-10-17
[QUOTE=WickedImp]I got it mostly to work. Purged everything Evo related (also exchange stuff) and deleted .evolution in home dir. Reinstall after this and create your new exchange account. Should work - no backend crash anymore.

Problem left: I miss this red Button on the bottom left next to contact and email which was named 'Exchange'. It was the button where it was possible to browse the exchange folders and assign favorite public folders. Needed to get Public Contacts to work with EMail Contact Book.[/QUOTE]

Well, I tried this - one gotcha was that removing the Evolution stuff, it also rips out Nautilus! (why I have NO idea!).  I deleted the .evolution directory succesfully and used Synaptic to reinstall Evolution, the Exchange stuff and Nautilus.  Seems to of still kept my Evo preferences as it used my same 'ol mailbox information and still craps out.

It's not just a problem, it's also quite embarrasing.  How long has this product been around and it still has these problems that have been around forever?  I know, if I could do it better, why don't I code something then? :)

---

### Post by daahli on 2005-10-29
I'm having the same problem. I just set up an exchange account, but the program crashed on me. Now I can't even get it to start anymore, crashes on startup. A real shame.

---

### Post by kjkrum on 2005-11-03
[QUOTE=riggsd]The Exchange connector doesn't give me as many error messages, but it just silently stops getting new mail until I close Evolution and restart it.[/QUOTE]

That's what it was doing to me under Hoary.  Under Breezy, it doesn't work at all!

When I started using Warty, I had high hopes that Ubuntu would be the long-awaited Windows killer.  But that's not going to happen if the quality keeps slipping like this.  

Exchange connectivity is of the utmost importance for those of us trying to promote Linux in the office.  The constant breakage is totally unacceptable.  Why do they keep rolling out broken updates?  Why not stick with what works?  A few minutes with Google leads me to believe that this is an upstream problem.  Somebody needs to fork the evolution-exchange project and keep it stable!

---

### Post by VR6Pete on 2005-11-03
took literally hours of playing and tweaking to make it work in Evolution, I'm finally there, apart from it being slow at times....

---

### Post by rainbowsheep on 2005-11-05
[QUOTE=VR6Pete]took literally hours of playing and tweaking to make it work in Evolution, I'm finally there, apart from it being slow at times....[/QUOTE]

How did you get it to work?  I'm having big problems here.  I can't view my inbox, but I can view the Public Folders and my calender.

Evolution 1.4 worked fine, I believe.

---

### Post by toadi on 2005-11-16
can you please tell me what you have done to get it to work?

---

### Post by Chayak on 2005-11-16
This is the result of a perfectly good system trying to connect to a M$ server... the sheer bloat and evil of this thing causes the process to wisely kill itself before it could do any harm to it's home.

---

### Post by RikoW on 2005-11-17
Hi everybody,

for me the current version on evolution with exchange works fine on breezy. I couldn't get the one on Hoary to authenticate to the exchange server. In Hoary I downgraded evolution to 2.0.4, which worked fine.

After the upgrade to Breezy, things stopped working in evo (didn't have any crashes, though) and couldn't access my exchange account anymore.

So, I removed ~/.evolution and the config files by deleting ~/.gconf/apps/evolution

After restarting evolution, I had to set-up my accounts again, but since then it is running stable in daily use.

Cheers,
                Riko

---

### Post by suRoot on 2005-11-17
Try using IMAP.  It's installed & running by default on Exchange installations - so it's probably still active unless someone turned it off.  Even if they did, you can probably talk your administrator in to turning it on for you.

I dumped the Exchange connector & did this myself after all the lockups in Evolution.  Using IMAP has given me every exchange related feature I used under Evolution.... plus no lock ups.  Plus you can use whatever mail client you like.

---

### Post by joshmachine on 2005-11-17
Hell Yeah! Thank you thank you!

I will miss only a public calendar, but wgaf.  Just so every one knows there is also a default virtual SMTP server on the exchange server as well.  Stick a fork that exchange crapper (sorry gnomes, the one in 5.10 is buggy and damn slow.)

Anyways thanks suRoot.

Later

---

