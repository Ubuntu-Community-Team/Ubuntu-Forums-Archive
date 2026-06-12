---
title: "Unity-revamped, Screensavers, Point Release"
date: 2013-02-12
forum: General Help
---

### Post by JiuJitsu500 on 2013-02-12
So, I have a few gripes and odds and ends sort of thing. More gripe than questions, but still... I would very much know what to look at.

I'm on precise and don't think I'll update for a very long time with this new internet search in the dash defaults being on with no option to turn it all off at install. I personally think that's intrusive and ballsy. Though it is all easy to turn off and uninstall the apps that do that once installed - it's just dumb to me that you can't install it with all of those crap options off, or even not install those things in the first place. Thus, if that isn't added (or taken away???) by the next LTS I'm done with Ubuntu. That's not the only reason, just more of the latest icing on the cake. Canonical is just becoming not my cup of tea anymore. Maybe their phone or tablet concept will be awesome.

I love Precise, but it seems support for it has gone awry. Compiz has no screensaver plugin anymore (just annoing, not a problem to me) and unity has become a burden the more I come to like it. I'm fine in the command line too, but damn it I'm getting confused and would seriously switch back to Lucid if support didn't run out in a couple months. Been here since Jaunty man!

On to questions now so I can stop complaining about essential nothings. First, the PPA for Unity-Revamped doesn't work on my machine, and it does not say there are any missing dependencies, anything. I am on Unity ~.18 as is the new build, which is currently, and has been for a few weeks, ready and good to go on launchpad. Sadly, through apt-get update && dist-upgrade after activating the ppa...blah blah blah, I get nothing. Even through direct installation of the .deb files from launchpad, nothing. It's an exact match to my already-existing Unity install. Why does this matter? One, because I want that damn behavior for a screensaver and do not like always-hidden launcher. Second because Ubuntu makers decided that window dodge and clicking on the icon to minimize wasn't cool enough and shouldn't be in any release for unity in Precise. That was also garbage to say that the "behavior wasn't testing well" and I think that behavior was deliberately removed. It worked JUST FINE on both versions prior and the ppa makes it work perfectly on every machine on earth - except mine...

MyUnity, CCSM, and any setting manager that has the "dodge" option never shows it after compiz --replace, reboot, anything. Freaking strange and very annoying. The minimize function does nothing, and in synaptic the PPA doesn't show up, though it is active and the GPG key matches. Through ppa-purge, nothing gets uninstalled.

So, what on earth can I look at to see what's wrong with that? It requires no meta-package, only the 4 unity packages themselves and their dependencies...

Next is screensavers. I used to love xscreensaver, but have come to fall out of love when I see unity deciding it's the boss and runs on top of it. The screen is locked, yes, but the launcher and panel are way too cool for school and do not hide while xscreensaver (or any screen locking program) runs. What gives? I've found work-arounds and seen quite a few bug reports, but no fixes yet. This is a reason I'd like the window dodge behavior so when xscreensaver runs outside of it's daemon and saves my screen and locks the door, the launcher isn't there (since it's a fullscreen app, technically). I can deal with the panel. But damn it, why did they make unity so resilient in the not-good and the good ways at the same time?

That is very annoying, and I now do not have any screensavers and would rather look at a black screen with a unity launcher and panel. This is a problem, and I cannot seem to find a fix.

Next, as I understand, the 2nd point release comes out on the 14th - in two days - and I have no quantal repo's activated, anything that should have the new kernel or anything related. But, running lsb_release -a yields that I'm already on 12.04.2 .... just kind of curious about that one, because nowhere else on my system does it even say I'm on .1, and I have the 3.2 kernel (latest I think is ~38.46). I'll get the upgrade when .2 is released so I'm not worried... but I am curious.

I'm thinking a clean install in two days, I've heard bad juju about the new grub 2 and the new kernel, but in a virtual machine everything works 100% with that. I've noticed the new kernel in the repos too...

Anyway. AMong other things, these things I was curious about, and why the damn 310 nvidia driver won't work for crap for me, but every older version does. That's no problem though, 310 is experimental anyway and just hates me.

I love ubuntu damn it, I don't want to switch.

**EDIT** Forgot one thing - I mostly have my laptop hooked up to a big TV through HDMI, so I normally have the laptop screen disabled in nvidia settings. But, I have to maually do this every time I boot into ubuntu. So, how can I set it to disable the laptop display any time it's hooked up to the TV, and let it be on whenever it's disconnected? I like the mirror display thing, but no reason to use it if the only screen I use is the TV...

---

### Post by zombifier25 on 2013-02-13
> **JiuJitsu500 said:**
> 
I love Precise, but it seems support for it has gone awry. Compiz has no screensaver plugin anymore (just annoing, not a problem to me) and unity has become a burden the more I come to like it. I'm fine in the command line too, but damn it I'm getting confused and would seriously switch back to Lucid if support didn't run out in a couple months. Been here since Jaunty man!

On to questions now so I can stop complaining about essential nothings. First, the PPA for Unity-Revamped doesn't work on my machine, and it does not say there are any missing dependencies, anything. I am on Unity ~.18 as is the new build, which is currently, and has been for a few weeks, ready and good to go on launchpad. Sadly, through apt-get update && dist-upgrade after activating the ppa...blah blah blah, I get nothing. Even through direct installation of the .deb files from launchpad, nothing. It's an exact match to my already-existing Unity install. Why does this matter? One, because I want that damn behavior for a screensaver and do not like always-hidden launcher. Second because Ubuntu makers decided that window dodge and clicking on the icon to minimize wasn't cool enough and shouldn't be in any release for unity in Precise. That was also garbage to say that the "behavior wasn't testing well" and I think that behavior was deliberately removed. It worked JUST FINE on both versions prior and the ppa makes it work perfectly on every machine on earth - except mine...

MyUnity, CCSM, and any setting manager that has the "dodge" option never shows it after compiz --replace, reboot, anything. Freaking strange and very annoying. The minimize function does nothing, and in synaptic the PPA doesn't show up, though it is active and the GPG key matches. Through ppa-purge, nothing gets uninstalled.

So, what on earth can I look at to see what's wrong with that? It requires no meta-package, only the 4 unity packages themselves and their dependencies...

The PPA has yet to be updated to the latest release of Unity (5.18.0-0ubuntu2), so you'll have to wait for the maintainer to update it.
> **JiuJitsu500 said:**
> 
Next is screensavers. I used to love xscreensaver, but have come to fall out of love when I see unity deciding it's the boss and runs on top of it. The screen is locked, yes, but the launcher and panel are way too cool for school and do not hide while xscreensaver (or any screen locking program) runs. What gives? I've found work-arounds and seen quite a few bug reports, but no fixes yet. This is a reason I'd like the window dodge behavior so when xscreensaver runs outside of it's daemon and saves my screen and locks the door, the launcher isn't there (since it's a fullscreen app, technically). I can deal with the panel. But damn it, why did they make unity so resilient in the not-good and the good ways at the same time?

That is very annoying, and I now do not have any screensavers and would rather look at a black screen with a unity launcher and panel. This is a problem, and I cannot seem to find a fix.

You're blaming the wrong person here. It's GNOME's decision to drop the screensavers, and Unity, being based on GNOME, must comply. But it's weird really, since last time I tried, if xscreensaver is activated, then it will go fullscreen.
I'll try again later and post back.

---

### Post by JiuJitsu500 on 2013-02-13
The PPA says it's that exact version, and has been since a few weeks ago, that's why I was confused. I still am, his version is current according to launchpad, just with an added "+ikos---dev" whatwever the name is. 

I can still blame the creators of unity for not allowing other items to run on top of it. I know GNOME took it out of the project, and xscreensaver has always been better to me anyway, but the fact that unity doesn't allow anything to run over it, even to lock the screen, is extremely annoying and cannot be a difficult fix.

Compiz's plugin even could fix that with a little better integration with unity - unity itself could integrate better with windows managers it comes installed with. That's one of my biggest gripes with unity is that it's more like a mac dock than any other environment and you can change very little, oddly enough, about it.

EDIT ** Not to mention, with GNOME 3, fallback, cinnamon, lxde, xfce, kde, or even razor and some lesser environments xscrreensaver runs like a boss without any problems - so it's a unity thing with noted bugs on launchpad that have not been resolved. It's not a problem with xscreensaver since it work on every other environment. BUT, this could be something I did on my machine, but even with other environments running, Unity is the only one that doesn't go fullscreen. Even if it's an x.org problem.... the Unity team should still be able to make this a non-issue. But, then again, I'm no coder, but unity still has issues I think could have been solved a long time ago.

Maybe I'm complaining about the wrong thing, but Unity is the only one I'm having trouble with. If I'm wrong, I'm wrong, and that would give me some faith back into ubuntu... but lately things are slipping downhill compared to older releases (except oneiric... that one still sucks).

---

### Post by zombifier25 on 2013-02-13
Can you take a screenshot of xscreensaver and post back? Since I don't get that problem over here, with the latest Unity.

And the version of Unity in the PPA is 5.18.0-0ubuntu1, not 5.18.0-0ubuntu2, so it's older and, naturally, replaced by the newer version in the repo. You can force it to install the PPA version (which has the dodge windows and other goodness) by following the instructions here: [http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/](http://www.howtogeek.com/117929/how-to-downgrade-packages-on-ubuntu/)

---

### Post by JiuJitsu500 on 2013-02-13
I re-installed everything pertaining xscreensaver from the repos except the two extra ones, bsod and some other crazy one.

Still the same issue, both in preview and in actual running. This is why I'd like the dodge behavior back too, and I installed his tarball too which matched the newer unity... and found out that's exactly what's not working since it's still an exact match.

So, turns out I was just being stupid - like a boss. Installed the hell out of my same unity package through .deb and tarballs like 5 times. Didn't even bother checking his older version. Yup, so I'll give up on being smart for a while.

Attached is a screenshot of a random image happening while running though, removed all the packages, then re-installed everything with ".... install xscreensaver*"

Still confused. I did remove a TON pf packages after install, but most of those were old kernels and fonts I can't even begin to understand, not too many system packages and I don't think I touched unity at all (decided to give it a shot after I screwed up my gnome shell install experimenting)

---

