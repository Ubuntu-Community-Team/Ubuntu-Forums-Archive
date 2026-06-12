---
title: "Feisty or Gutsy &amp; Where is Ubuntu Going?"
date: 2008-01-17
forum: General Help
---

### Post by ClarkePeters on 2008-01-17
I'm trying to decide whether to keep Gutsy over Feisty or Dapper--and knowing the direction of Ubuntu's development will help me make that decision.
For me Gutsy is too buggy, my front-end speaker/headphone jack wont work, and I've tried every thread and official solution I couldfind. Mostly though, it freezes a lot!!  (can someone say Windows?).
Feisty and Dapper have been fine for me before.  
And I need, also, to know what to tell my colleagues. I have worked hard to get some of my colleagues (professors) to use Ubuntu. I've always bragged about how Ubuntu puts Windows to shame (for the kind of stuff we professors do). Now I'm a bit nervous about suggesting this if they'll be forced to move up into future versions of Ubuntu that are just not as stable, simple, clean and useful as the earlier versions.

Will I always be able to download a Dapper or Feisty  installation even as Ubuntu continues on with other upgrades or will I be forced to move on up like Windows always makes people do? (I mean, cd   install disks get lost and scratched up and such).  
Of course, I know that Ubuntu can't offer continued support for all their versions into the limitless future, but If I have a version that works for me as is, will I or my colleagues always be able to get it?

Thanks for any advice.

---

### Post by ClarkePeters on 2008-01-17
Also,  I guess what I need to know too,  is that if Dapper or Feisty is working for me or my colleagues and we buy a new laptop in the future, will Dapper or Feisty work? I mean if you invest the time to migrate from windows to Dapper, you don't want to go back to Windows in the future if you can't get Dapper on your new laptop and you don't want a heavier, buggier version of Ubuntu, right? So maybe I should ask--should we just stick with Windows?

---

### Post by Circus-Killer on 2008-01-17
you can carry on using dapper until the next LTS (long-term support) release gets....released. :P

basically, each regular release is supported for i think 18 months.
LTS releases are supported for i think 2 years.

so if you want stability more than the latest technology, then stick to the LTS releases. but you will only be able to stick with a specific LTS release for 2 years till the next one comes out. but each LTS release is focused on stability whilst the other releases are more focused on new features.

---

### Post by OrangeCrate on 2008-01-17
To the OP

For what it's worth, I've been using Gutsy since it's release, and it has been rock solid for me. If you browse the forums, most of the problems have been with the eye candy features. I've never been interested in them, so I don't use them, and maybe that's contributed to my high satisfaction with Ubuntu.

With each new release, there's always a few bugs to be worked out, but that should be expected. Even new cars need some adjustments at the first service appointment. I've always been able to find an answer here very quickly when I've run into a problem.

Hardy will be my sixth Ubuntu release, and I look forward to the new features, as I do with each release. Personally, I think of the LTS versions as more enterprise appropriate, and the fairly quick update release for the others, are aimed at individual users, as a simple way of keeping at the cutting edge of Linux development.

Bring them on, they keep getting better all the time...

---

### Post by Gina on 2008-01-17
I'm a devoted Ubuntu user and the odd (very infrequent) time I've had a need of Windoze, I cringe!  That's after waiting an age for anything to happen of course!  However, I am getting a little impatient for certain areas to be improved - mainly wireless (though the latest Hardy development builds have display problems too).  Has anyone found a wireless adapter that works "out of the box" with Ubuntu?  I haven't and I have tried 6 of them in various forms (PCI, PCMCIA and USB).  Some I have yet to get working at all.

I would dearly love to recommend Ubuntu unreservedly to ALL my computer using friends, not just the more computer literate ones, but I'm afraid these problems prevent that.  I do try to get people to at least try a Live CD or perhaps a dual boot system with their current OS.  I'm not knocking the developers - they are doing a great job - just letting off a bit of steam :lol:

---

### Post by ClarkePeters on 2008-01-17
OrangeCrate> most of the problems have been with the eye candy features. I've never been interested in them, so I don't use them, and maybe that's contributed to my high satisfaction with Ubuntu.

I'm not the list bit interested in eye candy. Functionality is my key. So how do I go about trimming down so that my Gutsy runs better.  Any ideas for trimming down in other areas besides the eye candy would also be appreciated if anyone has a suggestion.

---

### Post by ugm6hr on 2008-01-17
> **ClarkePeters said:**
> OrangeCrate

I'm not the list bit interested in eye candy. Functionality is my key. So how do I go about trimming down so that my Gutsy runs better.  Any ideas for trimming down in other areas besides the eye candy would also be appreciated if anyone has a suggestion.

The freezes are most likely to be Compiz.  From System-> Preferences-> Appearance, go to the Visual Effects tab, and select None.

See how it goes from there.

If you really want to trim things down for speed - you will have to try an alternative Window Manager  (or Desktop Environ).  Most of the auto-loaded modules in Ubuntu are part of Gnome, although my Syetem Monitor does list a few things I don't use...

As for the sound issue - does sound work at all?  If yes, then you will normally just need to turn on all the volumes to activate additional headphone sockets (alsamixer in terminal).

But if you are happy with Dapper - why not just stick with it til Hardy (next LTS).

---

### Post by ClarkePeters on 2008-01-17
OrangeCrate,
Never mind. I got to thinking, if I want to trim down or streamline my Gutsy, then what's the point of upgrading, right? :)   I think I'll just go back to Dapper or Feisty.  I do hate to lose all my configurations, renistall my favorite apps,  and lose my emails and such, but its best for now, I think.

Circus-Killer,
Thanks for explaining LTS to me. I knew that from a long time ago but sorta let it slip my mind. I thought that since Ubuntu was shipping out CDs for 7.10 that it was as stable as 6.06 and that if I didn't upgrade I'd be getting left behind.  Basically, I think what your saying is that I can just keep using Dapper (or Feisty, since it works fine on one of my laptops) and wait until Ubuntu gets another LTS version before I really HAVE to upgrade, right?

thanks all.

---

### Post by ClarkePeters on 2008-01-17
OrangeCrate,
you beat my post by just seconds.  :)
thanks for your advice! :)

---

### Post by danwood76 on 2008-01-17
> **Gina said:**
> Has anyone found a wireless adapter that works "out of the box" with Ubuntu?  I haven't and I have tried 6 of them in various forms (PCI, PCMCIA and USB).  Some I have yet to get working at all.


The atheros based wifi card in my lappy (AR5006EG) thanks to the madwifi project, also in my desktop I have the abit airpace pci-ex (AR5007) card which now works with the patched madwifi.

I also have back at my parents house a dirt cheap PCI wifi card that has an intel chipset that works perfectly.

So it short yes :)

regards,
Danny

---

### Post by ClarkePeters on 2008-01-17
fyi developers
to answer OrangeCrate. I'm using  Acer Aspire 4710g and my alsamixer only shows Master and PCM, no front end speakers or headphone thingys to unmute.  Like I said, I tried every post I could find, --installed alsa with current drivers and such from the repositories, tried OSS solutions, tried configure certain files (which I now forget what they were) to include Acer Laptops and such. No Go.   
I do have an old time degree in Management Informatin Systems, so I'm not a complete moron (well, my wife might disagree with that :)  )  so I just can't figure it, and I have other professional duties that keep me from having the time to keep this up.   

I bought my Aspire because I thought it was identical to the one used in India which comes with ubuntu preinstalled on it (live in Taiwan) so I thought I wouldn't have any problems with hardware issues at the Gutsy level. But Dapper and Feisty work just fine on my other Acer Travelmate but I have yet to try it on my new Aspire-- so here's to hoping a downgrade will work fine on this one as well.

I love all you guys/gals here, you are such good help!!  :)

---

### Post by ClarkePeters on 2008-01-17
Oops, I'd like to add one more thing to the developers.
I noticed in my searches that Gutsy seems to be getting more negative feedback than other versions, of course, I could be wrong, but I particularly noticed some first time users trying to start out with Gutsy.  At a time when people are deciding whether to go to  the trouble of switching to Vista or take the Ubuntu plunge this is a bad time to be losing people. I think we should have this big, very big, at the top of the page note or warning that says, "First time Users of Ubuntu, Please do not try any other version of Ubuntu until you have installed and thoroughly tested the LTS version for yourself. Trying any other version may give you an unfair evaluation of the power and ease of Ubuntu"  Of course I know that this general message is out there, but it isn't out front.

Well, my two cents worth anyway, I just want Ubuntu to succeed.

---

