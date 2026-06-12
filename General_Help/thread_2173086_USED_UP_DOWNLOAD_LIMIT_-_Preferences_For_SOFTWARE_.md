---
title: "USED UP DOWNLOAD LIMIT - Preferences For SOFTWARE SOURCES - Very Confused"
date: 2013-09-07
forum: General Help
---

### Post by skyesharica on 2013-09-07
I've tried to find answers for this but, as a newbie, it's just too hard. This is my biggest problem and only serious Ubuntu hitch.


Since I've started on Ubuntu, a few months ago, I've noticed that my internet download limit is used up quickly. (Slows down to snail pace then, shaped.) Is it because the updates are huge files? I tried to change the settings of SOFTWARE SOURCES to minimise updates. I have a compatible Hewlett Packard multifunction laser printer, which needs driver updates. But I don't use any other software than what's already on the PC (except VLC Media Player [and the less important Chromium browser - just a spare.]) 


These are my SOFTWARE SOURCES settings. I'VE FORGOTTEN THE DEFAULT SETTINGS. Are these correct? Is there a better way to minimise the download size?




[CENTER][ATTACH=CONFIG]246090[/ATTACH]

[ATTACH=CONFIG]246091[/ATTACH]

[ATTACH=CONFIG]246092[/ATTACH]
[/CENTER]

---

### Post by carl4926 on 2013-09-08
Then the only part you should really be interested in is the 'Updates' tab

---

### Post by whatthefunk on 2013-09-08
What is your download limit?  Updates are usually only a few MB worth of data at most, unless its a major update.

---

### Post by stinkeye on 2013-09-08
Does your ISP have a download mirror which is not included in your quota.
eg my ISP has a "freezone" which includes an ubuntu mirror.
As you also appear to be in Australia may want to compare your ISP plan with others.
My ISP just increased my quota from 20gb to 100gb without a price increase.

I currently have a homephone/adsl bundle for $55 a month.
The 100gb quota is plenty unless your watching a lot of online video.
I rarely use more than 30gb a month even when watching a live game or two of AFL per week.

---

### Post by skyesharica on 2013-09-10
> **carl4926 said:**
> Then the only part you should really be interested in is the 'Updates' tab

[SIZE=4][FONT=comic sans ms]**[COLOR=#008000]Thankyou so much![/COLOR]**[/FONT][/SIZE]  :P

I've unticked everything else.

What about the Hewlett Packard printer ... they are Ubuntu friendly and their printer driver updates open in TERMINAL?  Will I tick (FIRST TAB) "Proprietary drivers for devices (restricted)"?

Also how will VLC Media Player update?  Can you please tell me the option - the tab?

[CENTER][ATTACH=CONFIG]246156[/ATTACH]
[/CENTER]
 
Ohhh.  I just checked the SOFTWARE UPDATER.  For several days it has said that there are about 30 updates waiting.  This time it scanned for some time - the DETAILS area showed that it was looking at quite a lot of files to update basic info from ... then it says "The Package Information Was Just Updated - There Are No Updates To Install". So was I definitely updating heaps of stuff that wasn't necessary?

[CENTER][ATTACH=CONFIG]246157[/ATTACH]
[/CENTER]

---

### Post by Mark Phelps on 2013-09-10
Proprietary drivers for devices nearly always refers to video drivers, and sometimes, networking drivers.  IF you have both already installed, you do not need to be checking for these on any regular basis as they aren't updated very often.

Also, if Additional Drivers isn't offering you any drivers, then you don't need to check for these at all -- as there aren't any available.

---

### Post by mastablasta on 2013-09-10
no, what you should do is tick only "important security updates" in the updates tab. the others can be left as they are (they are paths to sources in case you want to install soemthing new). why do you need constant drivers for printer i don't know, but likelty they are in one big file. i mena if the printer works as it should and if you didn't see any bugs then it has all the drivers it needs. the updates are ther ein case you add a new printer, to fix some bugs etc.

anyway the biggest bandwidth consumers are kernel updates. again with security patches there should only be small patches rather than new kernels. i never tried it actually. anyway these kernel updates they are about once a week and they are about 180-250 MB. so they can eat up into plan quite fast i imagine. 

i see in Debian stable you have same kernel that get's patcched with security patches.

also maybe you don't need to check for updates daily. maybe weekly is enough. depends what you are doing. i turned them off in my virtual boxinstall. and then just do them manually about once a month. but i use it mostly just for testing and it's a contained system (inside virtual box).

---

### Post by skyesharica on 2013-09-10
> **whatthefunk said:**
> What is your download limit?  Updates are usually only a few MB worth of data at most, unless its a major update.

Hi Funky LOL,  :lolflag:

I have 20 GB a month.  I noticed the file size too.  Though there are maybe 30 updates at a time ... so this adds up, but not to the amount my records show, at my ISP ... my ISP usage is like 2-3 GB on some days.  I NEVER do movies, but I OFTEN HAVE A RADIO ON.  But I've had the internet radio on for a year, and not had this trouble.  Maybe the radio file size has increased, because the downloads immediately decreased a lot after I turned off the radio?  I've left it on overnight, accidentally, a few times, too.  But this never happened before Ubuntu, and it's happened 3 times, since I started Ubuntu.  Have there been major updates in the past 3 months?

> **stinkeye said:**
> Does your ISP have a download mirror which is not included in your quota.
eg my ISP has a "freezone" which includes an ubuntu mirror.

Wow, that's gud of them.  No, not mine.

> **stinkeye said:**
> As you also appear to be in Australia may want to compare your ISP plan with others.
My ISP just increased my quota from 20gb to 100gb without a price increase.
I currently have a homephone/adsl bundle for $55 a month.

That's extremely gud of them.  No, not mine.  And locked in until March next year.  But great to know how competitive it is.  Are you American?

> **stinkeye said:**
> The 100gb quota is plenty unless your watching a lot of online video.
I rarely use more than 30gb a month even when watching a live game or two of AFL per week.

It could be my radio.  I have signed up for Calm Radio ... which is "soma" (new term for spacing out music) that I do all day long.  Since updating to Ubuntu three months ago, I was unable to attach the radio links to Rhythmbox or VLC.  They only accept iTunes or Windows Media Player.  So I've been using their website, which has a kewl thing called "MULTIMIX", which mixes up all kinds of relaxing sounds like beach waves and waterfalls etc.  I guess, that the extra 3 sound affects are like quadrupling the music download.  It was very nice.  I'll try it without the affects.

[www.calmradio.com]("http://www.calmradio.com")

:guitar:

P.S.  Oh I see from your signature that you come from the land down under too.  G'day.  Oi Oi Oi

> **Mark Phelps said:**
> Proprietary drivers for devices nearly always refers to video drivers, and sometimes, networking drivers.  IF you have both already installed, you do not need to be checking for these on any regular basis as they aren't updated very often.

Thanks for that.  What box MUST be ticked to get the HP printer driver update please?  It's easy to just check online for the latest version of VLC so I won't worry about that one.

> **Mark Phelps said:**
> Also, if Additional Drivers isn't offering you any drivers, then you don't need to check for these at all -- as there aren't any available.

Sorry, but I have no idea what option "Additional Drivers" is ... I can't find it on Ubuntu Version 12.04 LTS.

> **mastablasta said:**
> no, what you should do is tick only "important security updates" in the updates tab. the others can be left as they are (they are paths to sources in case you want to install soemthing new). why do you need constant drivers for printer i don't know, but likelty they are in one big file. i mena if the printer works as it should and if you didn't see any bugs then it has all the drivers it needs. the updates are ther ein case you add a new printer, to fix some bugs etc.

anyway the biggest bandwidth consumers are kernel updates. again with security patches there should only be small patches rather than new kernels. i never tried it actually. anyway these kernel updates they are about once a week and they are about 180-250 MB. so they can eat up into plan quite fast i imagine. 

i see in Debian stable you have same kernel that get's patcched with security patches.

also maybe you don't need to check for updates daily. maybe weekly is enough. depends what you are doing. i turned them off in my virtual boxinstall. and then just do them manually about once a month. but i use it mostly just for testing and it's a contained system (inside virtual box).

WOW - THAT'Z ALL GUD!!!

Firstly, I have tried to tick just "important security updates" ... but if I don't tick the first box, in the first tab, this other update box greys out, and can't be ticked at all.  So they both have to be ticked.

This is what it looks like 'greyed out' and un-tickable.

[CENTER][ATTACH=CONFIG]246160[/ATTACH]
[/CENTER]

This is the box that must be ticked, so that the "important security updates" can be ticked too.


[CENTER][ATTACH=CONFIG]246161[/ATTACH]
[/CENTER]

Does this look all gud?


[CENTER][ATTACH=CONFIG]246162[/ATTACH]
[/CENTER]

Oh OK ... so don't worry about those lengthy "over-written" printer driver downloads, that happen in TERMINAL.  I think they were big files, because the first one took so long, I just left it on overnight.  But if I do get a bug or something, what box will I tick to get the latest driver?  By the way, it's called a HPLIP - Hewlett Packard 'add on whatever', for Ubuntu.  This box is ticked in the PRINTER SETTINGS, so maybe updates happens anyway?  No?  But you're right, there's no bugs, so why worry.  Maybe I could just check the HP website, for the latest HPLIP file, if the printer doesn't work?!

[CENTER]
[ATTACH=CONFIG]246163[/ATTACH]
[/CENTER]

Yes, I was sure that the downloads were bigger than a few MB.  Maybe with my settings, I was always getting those kernel updates.  So that will be mostly fixed now, thanx 2 u generous folks.  Unless,  as you say, they are part of security updates.

Btw ... why are they called "security" updates ... what is the "security" word for?

 I've adjusted the updates to fortnightly, as well.

But I'm starting to think that it was the radio.  If you have time, could you look at the post above ... about my MULTIMIX sound affects ambient radio ... it went on all day?

I'm sorry, the last sentence is too advanced for me - virtual box etc.  You certainly sound like one of the geniuses here.  They blow my mind! ;)

---

### Post by stinkeye on 2013-09-10
> **skyesharica said:**
> But I'm starting to think that it was the radio.  If you have time, could you look at the post above ... about my MULTIMIX sound affects ambient radio ... it went on all day?
I just had a listen to calm radio and it downloads at about 8kbs so you would
use about 700MB in a 24 your period. Maybe more for what your listening to.
Open system monitor to the resources tab and check the usage.

May want to install indicator-multiload to easily check download activity.
[ATTACH=CONFIG]246173[/ATTACH]



If your using 2-3 GB on some days, its not ubuntu updates it's something else your doing.
P.S. When I was on 20gb, watching too much youtube would push me over my quota.

---

### Post by skyesharica on 2013-09-12
> **stinkeye said:**
> I just had a listen to calm radio and it downloads at about 8kbs so you would
use about 700MB in a 24 your period. Maybe more for what your listening to.
Open system monitor to the resources tab and check the usage.

May want to install indicator-multiload to easily check download activity.

If your using 2-3 GB on some days, its not ubuntu updates it's something else your doing.
P.S. When I was on 20gb, watching too much youtube would push me over my quota.

[COLOR=#006400][SIZE=4][FONT=comic sans ms]AUSSIE AUSSIE AUSSIE - OI OI OI  ...  Hello Australian Friend ! ! !  Where do you live now?  What state or O/S?  Just chattin'.[/FONT][/SIZE][/COLOR]  (I'd love to go to the USA ... I'm in Brisbane.)   :biggrin:

[COLOR=#696969][FONT=century gothic]Yes, I'm sure you're right.  When you add the fact that MULTIMIX radio has 3 more layers of sound files ... waves etc ... each might be a similar download ... I might average 1+ GB a day.  Maybe a few large updates were adding to the usage, but probably mostly the radio. So that explains it.  And certainly the online record looks like that.  See images - stopped the radio after the first 10 days.  I'll write to the radio creator, and ask them to make Ubuntu links for Rhythmbox or VLC.  I hope the world is picking up speed with us.
[/FONT][/COLOR]
[ATTACH=CONFIG]246201[/ATTACH][ATTACH=CONFIG]246200[/ATTACH][COLOR=#696969][FONT=century gothic]

[/FONT][/COLOR][SIZE=4][COLOR=#0000ff][FONT=book antiqua]But OMG, that was all fascinating!  I learnt so much.  What WUNDAFULL people!!![/FONT][/COLOR][/SIZE][COLOR=#696969][FONT=century gothic]
[/FONT][/COLOR]

---

