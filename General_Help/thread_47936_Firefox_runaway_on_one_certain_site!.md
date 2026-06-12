---
title: "Firefox runaway on one certain site!"
date: 2005-07-10
forum: General Help
---

### Post by uberlinux on 2005-07-10
I am using firefox as my browser, and everytime I go to [www.shortnews.com](www.shortnews.com), firefox becomes a runaway process, as soon as I leave that site, the CPU time goes back to normal, what is the deal with that site?!

---

### Post by dave9191 on 2005-07-10
well i decided to have a look and i get the same thing. my guess without shifting throught their html is that they have a dably written javascript somewhere that goes into some long loop that firefox keeps evaluating. If you are botherd, give them an email and ask them about it :)

---

### Post by uberlinux on 2005-07-10
[QUOTE=dave9191]well i decided to have a look and i get the same thing. my guess without shifting throught their html is that they have a dably written javascript somewhere that goes into some long loop that firefox keeps evaluating. If you are botherd, give them an email and ask them about it :)[/QUOTE]
Thank's for the confirm, I just tried it with Epiphany and it seems to fix itself after about 4 seconds, I'll have to send them an E-mail;  Also, I will try it after disabling Javascript...  If anyone uses IE, I would love to see what happens when you browse to the site with that...  I would try, but you know...  I havent seen IE in like a year and a half... \\:D/

---

### Post by dave9191 on 2005-07-11
I might try later if i remember when I get home, only have my laptop with me. I run a windows box for gaming. 

Dave

---

### Post by uberlinux on 2005-07-11
well, I found a windows machine at school, and tried with Firefox and IE, and both didn't flinch, so I guess that it is a problem with either *gasp* Ubuntu or the Linux version of Firefox, this sucks, I always hate finding something that windows can do better...

---

### Post by jonrkc on 2005-07-11
[QUOTE=uberlinux]well, I found a windows machine at school, and tried with Firefox and IE, and both didn't flinch, so I guess that it is a problem with either *gasp* Ubuntu or the Linux version of Firefox, this sucks, I always hate finding something that windows can do better...[/QUOTE]
 This is a common problem with Firefox under both Windows and Linux, and there are dozens of posts about it on the Mozillazine forums.  From what I can tell, nobody knows the solution to it.  I have Firefox "run away" with the CPU every now and then and the only way to stop my machine from overheating is to kill Firefox and start it up again.  I'd say it happens about two or three times a month with me; with some people it's almost every time they use Firefox.  And it seems not to matter whether it's under Windows or Linux, so it's definitely not a Ubuntu or a Linux problem.

---

### Post by dave9191 on 2005-07-11
on the note of firefox running away, my dad has that problem on his computer (windows laptop). I often find that his cpu fans are on full speed while just browsing the web. But I dont think it has anything to do with this website. Ive never come accross it anywhere else on windows on linux before.

---

### Post by uberlinux on 2005-07-11
[QUOTE=dave9191]on the note of firefox running away, my dad has that problem on his computer (windows laptop). I often find that his cpu fans are on full speed while just browsing the web. But I dont think it has anything to do with this website. Ive never come accross it anywhere else on windows on linux before.[/QUOTE]
Same here, this seems different.  Also, it dosent worry me that I can't easily view this site in Firefox, it's just the fact that THIS DOSENT HAPPEN IN WINDOWS WITH FIREFOX and I don't like anything that puts Linux users at a disadvantage.  What if this was harnessed to 'select' who can easily view someones website, or was HIGHLIGHTED as one more thing that goes wrong in Linux as opposed to windows.

Are there any HTML/JavaScript gurus that can look at the content of [www.shortnews.com](www.shortnews.com) and help me figure exactly what is going on, so that it can be submitted to Mozilla coherently?

Thanks,
--Uber

---

### Post by Caboto on 2005-07-11
I don't know if it's really that easy, but closing the litte ticker at the bottom of the website solves the problem for me...
It seems to have something to do with wrong JavaScript Code or with the Gecko Engine interpreting it wrong.

---

### Post by dave9191 on 2005-07-11
[QUOTE=Caboto]I don't know if it's really that easy, but closing the litte ticker at the bottom of the website solves the problem for me...
It seems to have something to do with wrong JavaScript Code or with the Gecko Engine interpreting it wrong.[/QUOTE]

Yup, does the trick, Ill have a look at the code if I have some spare time. Right now, im fairly busy tho (thats why im checking forums :p). 

Dave

UPDATE: the javascript for the ticker is encoded, that might be the reason. either way, if i have more time later ill decode it and look over it.

---

### Post by uberlinux on 2005-07-11
Thanks, everyone

---

