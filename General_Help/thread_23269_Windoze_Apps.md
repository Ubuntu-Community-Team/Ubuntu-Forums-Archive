---
title: "Windoze Apps"
date: 2005-04-01
forum: General Help
---

### Post by ashonline on 2005-04-01
Hi

I aplogise if I posted this in the wrong forum...

I recently installed ubuntu on my laptop & was quite impressed with what I seen, but I ended up wiping it to reinstall WinXP due to my dependance on Windows applications.

I rely heavily on the following applications for work, and I can't use substitutes e.g. OpenOffice instead of MS Office.

- MS Access 97
- MS Outlook, Excel & Word 2003
- Adobe Acrobat 6 Professional
- Dreamweaver & Fireworks MX 2004
- Internet Explorer 6
- MSN Messenger 6+ (yes, it's compulsory at my work would you believe!)

I really want to get these apps up & running under ubuntu, if possible (wine?). Is there a quick way that this can be achieved with minimal configuration?  [-o< 
Or would I be wasting my time & I should stick with WinXP?

Thanks in advance for any help!

Cheers

Ashley

---

### Post by matgorb on 2005-04-01
A quick trip to [http://www.codeweavers.com/](http://www.codeweavers.com/) and 39.95 dollars should do the trick, it's wine made easy, still you can use wine itself, but it is a little (lot) intuitive, but then it is free.

You can try codeweaver's crossover for a month or so, so give it a shot.

---

### Post by bored2k on 2005-04-01
[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

Why Internet Explorer when you have Firefox? Why MSN Msgr when you have GAIM ?

---

### Post by ashonline on 2005-04-01
[QUOTE=bored2k][http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

Why Internet Explorer when you have Firefox? Why MSN Msgr when you have GAIM ?[/QUOTE]

GAIM I could probably use, however I must have IE for my work's website, which only works in IE with it's ActiveX stuff...

I use Firefox for everything else under WinXP

---

### Post by bored2k on 2005-04-01
Well yeah you have fully working MS IE 6 and most of your mentioned apps through Crossover Office. Those 2003 apps wont work too good though. You could install vmware wich is a windows emulator and run things from there ;) [you might suffer a performance drop while using it] .

---

### Post by Locomorto on 2005-04-01
[QUOTE=ashonline]GAIM I could probably use, however I must have IE for my work's website, which only works in IE with it's ActiveX stuff...

I use Firefox for everything else under WinXP[/QUOTE]
 I believe that you can get a ActiveX extension for firefox, have a quick look around. Im not too sure if it works with the latest version though.

---

### Post by Akrame on 2005-04-02
It seems that you don't like open office ... evenif it offers the same thing as Ms Office . I suggest to return under windows Xp 
good luck
akrame

---

### Post by underworld on 2005-04-03
Crossover is good. I do use it for 2 years now because at work we do use Lotus Notes for our emails and also to verify the webapplications I develop do also run under IE. You may look at their compatibility list to see if your apps are supported: [http://www.codeweavers.com/compatibility/browse/name](http://www.codeweavers.com/compatibility/browse/name)

There does also exist a menu driven installer for Wine: [WineTools](http://www.von-thadden.de/Joachim/WineTools/)

Greetings,
Daniel

---

### Post by ashonline on 2005-04-04
Thanks for everyone's help.

Maybe I should find another job that's not so Windoze-reliant!  #-o 

I could throw myself in the deep-end & use Open Office instead of MS Office, Thunderbird instead of Outlook, however Access 97 is definetly needed (unless Open Office can read/write .mdb files?).

I'm going to trial CrossOver Office on my Fedora3 server at home with apps Office, Dreamweaver etc & see how things go.

Also it would be great if anyone knows of an ActiveX plug-in for Firefox... That way I can lose IE all-together.

Ashley

---

### Post by Ozitraveller on 2005-04-04
[QUOTE=ashonline]Thanks for everyone's help.

Maybe I should find another job that's not so Windoze-reliant!  #-o 

I could throw myself in the deep-end & use Open Office instead of MS Office, Thunderbird instead of Outlook, however Access 97 is definetly needed (unless Open Office can read/write .mdb files?).

I'm going to trial CrossOver Office on my Fedora3 server at home with apps Office, Dreamweaver etc & see how things go.

Also it would be great if anyone knows of an ActiveX plug-in for Firefox... That way I can lose IE all-together.

Ashley[/QUOTE]

What sort of ActiveX plug-in are you looking for?

Too early for this "Open Office can read/write .mdb files" to happen maybe in furure version, and probably needs JRE to be OSS. And I heard this might be happening!

Doggies fan eh?

---

### Post by ashonline on 2005-04-05
Hi Ozitraveller

I tried the ActiveX plug-in for Firefox under WinXP, however it didn't seem to make a difference when trying to use my work's website - something to do with VBscript would be my guess.

It would be good to have these things working under Firefox (yes I know its a security flaw), that way I wouldn't need IE at all & would get me one step closer to Ubuntu!

I haven't had a chance to try CrossOffice under Fedora3 as yet. But it does look the goods.

Yes, born & bred Bulldogs fan. I see you're in Melbourne also. Who do you follow?

Ashley

---

### Post by emperor on 2005-04-05
[QUOTE=ashonline]
- MS Access 97
- MS Outlook, Excel & Word 2003
- Adobe Acrobat 6 Professional
- Dreamweaver & Fireworks MX 2004
- Internet Explorer 6
- MSN Messenger 6+ (yes, it's compulsory at my work would you believe!)
  Ashley[/QUOTE]

As far as Codeweavers wine is concerned:
================================
1. Fireworks MX 2004 does not work 
2. MS Access 97 is untested (However, Access 2000 does work!)
3. Word 2003 will not install
4. Adobe Acrobat 6 is untested
5, Dreamweaver MX works but the 2004 version is known not to work
6, IE6 works
7. MSN 6.1 is untested

So, I would not recommend wine.

But VMware may work!

---

### Post by Ozitraveller on 2005-04-05
[QUOTE=ashonline]Hi Ozitraveller

I tried the ActiveX plug-in for Firefox under WinXP, however it didn't seem to make a difference when trying to use my work's website - something to do with VBscript would be my guess.

It would be good to have these things working under Firefox (yes I know its a security flaw), that way I wouldn't need IE at all & would get me one step closer to Ubuntu!

I haven't had a chance to try CrossOffice under Fedora3 as yet. But it does look the goods.

Yes, born & bred Bulldogs fan. I see you're in Melbourne also. Who do you follow?

Ashley[/QUOTE]


Unfortunately, the Tigers!

---

### Post by Ozitraveller on 2005-04-05
There is linux version of Acrobat in beta, so maybe it will be out soon.

And for me Access is a problem, I have to have it, to work. And I need to Mono c# v2.0 at a minimum before I could move to linux.

---

### Post by clb137 on 2005-04-05
There is linux version of Acrobat 7 it will download and update from 5 to 7 if you already have it installed. If not just follow the instructions in the guide.

Failling all just go back to XP,  but it is worth trying to get things to work there is always a work around


Clinton

---

### Post by pizpot on 2005-04-05
Ashley,

Here is what you want to know.

1. partition your hdd into at least two parts. (you could use a win98 boot floppy or cd and fdisk command perhaps)
2. install windows xp on c:
3. boot to the ubuntu cd, install it on the other part of the drive, and say that you want SBM (Smart Boot Manager) to be used.

Then you can have both windows and linux at the same time. The SBM stuff does itself, don't worry. I actually already had a dual boot system with win98/XP and now it goes: choose windows/linux, and then win98/XP. :-) Goodness.

--
Pizpot

---

### Post by Ozitraveller on 2005-04-05
[QUOTE=pizpot]Ashley,

Here is what you want to know.

1. partition your hdd into at least two parts. (you could use a win98 boot floppy or cd and fdisk command perhaps)
2. install windows xp on c:
3. boot to the ubuntu cd, install it on the other part of the drive, and say that you want SBM (Smart Boot Manager) to be used.

Then you can have both windows and linux at the same time. The SBM stuff does itself, don't worry. I actually already had a dual boot system with win98/XP and now it goes: choose windows/linux, and then win98/XP. :-) Goodness.

--
Pizpot[/QUOTE]

Check these out first:

WindowsDualBootHowTo
[http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo/view?searchterm=dual%20boot](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo/view?searchterm=dual%20boot)

How do you easily install Ubuntu for dual-boot with Windows?
[http://www.ubuntuforums.org/showthread.php?t=16287&highlight=dual-boot](http://www.ubuntuforums.org/showthread.php?t=16287&highlight=dual-boot)

dual boot with existing winxp 
[http://www.ubuntuforums.org/showthread.php?t=23884&highlight=dual](http://www.ubuntuforums.org/showthread.php?t=23884&highlight=dual)

Problems accessing windows partition... 
[http://www.ubuntuforums.org/showthread.php?t=21296&highlight=dual-boot](http://www.ubuntuforums.org/showthread.php?t=21296&highlight=dual-boot)

There are the main ones, but there are more on dual-booting....

---

### Post by ashonline on 2005-04-13
Hi Guys

Thanks for everyone's help here.

I have a dual-boot xp/fedora box at home, but I want to avoid this on my laptop.

I see there is a new version of VMware out & am thinking of running win2k under it.

Which VMware should I download for Ubuntu? The tarball or can I install an RPM?

Ozitraveller - Tigers didn't do too bad last weekend, unfortunately!  :roll: 

Cheers

Ashley

---

### Post by Ozitraveller on 2005-04-13
[QUOTE=ashonline]Hi Guys

Thanks for everyone's help here.

I have a dual-boot xp/fedora box at home, but I want to avoid this on my laptop.

I see there is a new version of VMware out & am thinking of running win2k under it.

Which VMware should I download for Ubuntu? The tarball or can I install an RPM?

Ozitraveller - Tigers didn't do too bad last weekend, unfortunately!  :roll: 

Cheers

Ashley[/QUOTE]


Yes, who'd have thought they would win twice in a row!!!
3, surely not!!!

---

### Post by ashonline on 2005-04-13
[QUOTE=Ozitraveller]Yes, who'd have thought they would win twice in a row!!!
3, surely not!!![/QUOTE]

They just might... Wallace worked wonders with the Dogs a few years back.

---

### Post by Ozitraveller on 2005-04-13
[QUOTE=ashonline]They just might... Wallace worked wonders with the Dogs a few years back.[/QUOTE]


Yes he did! It's been so long now, that I'm not used to winning regularly, that's all!!!

---

### Post by ashonline on 2005-04-13
[QUOTE=Ozitraveller]Yes he did! It's been so long now, that I'm not used to winning regularly, that's all!!![/QUOTE]

You're not used to winning?! Dogs haven't won 2 in a row for a long long time....

---

### Post by Ozitraveller on 2005-04-13
[QUOTE=ashonline]They just might... Wallace worked wonders with the Dogs a few years back.[/QUOTE]

And we're on the lowest % in the 8 too! I ffel like I'm standing on the trap door!, Just waiting! ;-)

---

### Post by ashonline on 2005-04-13
[QUOTE=Ozitraveller]And we're on the lowest % in the 8 too! I ffel like I'm standing on the trap door!, Just waiting! ;-)[/QUOTE]

I would be feeling the same if I were a Tigers supporter too. However, like the Dogs, they can only go up (you'd hope).

Do you know if Ubuntu can install RPM files?

---

### Post by Ozitraveller on 2005-04-13
[QUOTE=ashonline]I would be feeling the same if I were a Tigers supporter too. However, like the Dogs, they can only go up (you'd hope).

Do you know if Ubuntu can install RPM files?[/QUOTE]

Try this:


Package: rpm (4.0.3-4)
Red Hat Package Manager
If you want to install Red Hat Packages then please use the alien package. Using RPM directly will bypass the Debian packaging system! 

[http://packages.debian.org/stable/admin/rpm](http://packages.debian.org/stable/admin/rpm)

---

### Post by ashonline on 2005-04-13
[QUOTE=Ozitraveller]Try this:


Package: rpm (4.0.3-4)
Red Hat Package Manager
If you want to install Red Hat Packages then please use the alien package. Using RPM directly will bypass the Debian packaging system! 

[http://packages.debian.org/stable/admin/rpm](http://packages.debian.org/stable/admin/rpm)[/QUOTE]

Excellent, thanks. Hopefully I might get a chance over the Anzac long weekend to get  Windoze running under VMWare and get to have a good bash with Ubuntu (and get to watch a bit of the footy also).

---

### Post by Ozitraveller on 2005-04-13
[QUOTE=ashonline]Excellent, thanks. Hopefully I might get a chance over the Anzac long weekend to get  Windoze running under VMWare and get to have a good bash with Ubuntu (and get to watch a bit of the footy also).[/QUOTE]


No probs! Good luck......


Debian looks as though it might release soon, I think I might get a copy of that too!

And I also Knoppix 3.8.1 for those other times!

---

