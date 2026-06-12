---
title: "Gcompizthemer cgwd &gt;= 0.9?"
date: 2006-08-03
forum: General Help
---

### Post by LoungeAct on 2006-08-03
Hello!

When I try to install the compiz themer, I get this error

```
gcompizthemer: Depends: cgwd (>= 0.9) but it is not going to be installed
E: Broken packages

```

I know I have my repositories right 'cause the gcompizthemer is showing up in synaptic.  Looking at the current version of cgwd, it says it's only 0.3?  Where can I get 0.9 and above?  ](*,) 


Please help!

---

### Post by Dr. Nick on 2006-08-03
whats the version on gcompizthemer? I have 0.3.3 and cgwd .9 look at your sources.list file and see what it looks like, I will post the 2 compiz lines from mine, depending on how you set up compiz in the first place it might mess you up to use these, Shouldnt but thier is always a chance i guess.

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

---

### Post by LoungeAct on 2006-08-03
Copy and paste of my sources.list

```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
```

They appear correct to me...

---

### Post by fantan on 2006-08-03
Hi, 

I have the same problem after todays update too.
During update gcompizthemer and gcompizthemer-themes packages Synaptic has removed the cgwd package.
Now the xgl/compiz feature is missing from my configuration.

What to do? (Of course I know, I must wait for the fix!)

fantan

---

### Post by LoungeAct on 2006-08-03
> What to do? (Of course I know, I must wait for the fix!)

I was hoping it wouldn't come to that :(

---

### Post by Dr. Nick on 2006-08-03
weird, mine hasnt done that at all.

I was looking at the wrong thing though, my compizthermer is .22

I assume you have run 

sudo apt-get update

Are you using compiz-vanilla?

---

### Post by gmc on 2006-08-03
cgwd now includes the functionality of qcompizthemer. I haven't had a chance to look at how to this functionality is implimented but there was a note about it on the compiz forums. See[ here ]("http://www.compiz.net/viewtopic.php?id=2451") for more details...

G.

---

### Post by mcduck on 2006-08-03
yes, separate package for gcompizthemer is not needed any more. Just get update cgwd and the old gcompizthemer package will be removed.

But you should also note that the theming also has changed a bit, and old themes aren't compatible with the latest cgwd.. And after update you'll need to open the themer and select 'legacy' theme engine. (there isn't any others yet, but now we have everything needed to support separate theme engines, like a metacity one as soon as somebody actualy makes one ;))

---

### Post by brt on 2006-08-03
ok, but when i click "Themes" in the systemtray menu nothing happens :(

is there another way to start the themer?

---

### Post by brt on 2006-08-03
ok, but when i click "Themes" in the systemtray menu nothing happens :(

is there another way to start the themer?

[edit]
i found the solution:

mv ~/.compiz/cgwd/theme.ini ~/.compiz/cgwd/theme.ini.bak

restart compiz amd themer is accessible via Systemtray-Menu :D

---

### Post by Bionic_Beefpile on 2006-08-03
gmc has it right, the gcompizthemer is built into CGWD now.
However, it seems to be a bit buggy on aiglx...
Check out the thread he links above, it has some good info.
(here is the link again: [http://www.compiz.net/viewtopic.php?id=2451](http://www.compiz.net/viewtopic.php?id=2451))

One thing to note: if your titlebars disappear, it's probably because the themer has set all colors to black and opacity to zero.  You can manually adjust this in gcompizthemer so that you'll be able to see what's happening. I just made a quick custom theme for now until there is a fix released.

---

### Post by Dr. Nick on 2006-08-03
OK, I see this now. My updates seemed to be seriously lagging behind, just forced a manual dist-upgrade and see that gcompizthemer and the themes are tagged for removal and cgwd and many others are awaiting updates. 

Guess the updates just hit different people at differnet times, hopefully he integration will make it smoother in the future,

---

### Post by LoungeAct on 2006-08-03
Thanks for the replies, I got it to work!

---

### Post by melkor12 on 2006-08-08
> **LoungeAct said:**
> Thanks for the replies, I got it to work!

I am having the same problem, how did you do it?

ok, sorry, missed the post above, it is working now...:D

---

