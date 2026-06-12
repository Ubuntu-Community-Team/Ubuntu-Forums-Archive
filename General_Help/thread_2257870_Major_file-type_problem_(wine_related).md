---
title: "Major file-type problem (wine related)"
date: 2014-12-23
forum: General Help
---

### Post by ramidavis2 on 2014-12-23
I am running ubuntu 11.04.
I got stupid and installed office and visual studio under wine (Program versions should not matter in regards to the problem, as far as i know.) I was not too impressed with the results, so i tried uninstalling them. There was some error, i forget what exactly, so then i wiped out my wine prefix by deleting "~/.wine/" (I figured that would be like reformatting wines hard drive).
Nothing much else in my wine prefix anyway but some old windows games that i have since got to run better in vitrualbox then wine would ever think of doing. No big loss there.
Now all *.txt show up as a "microsoft visual studio solution" for type in file browser, all *.depend files and all *.layout files from my codeblocks projects, and the file "~/.epiphany" in my home folder are now "microsoft visual studio solution" and "visual studio community content installer file".
Android *.apk files, nero *.nrg disk images, the file "~/.xsession-errors" and a few other files, like some in my home folder, with a file name starting with "." are now "microsoft help attribute definition file".
I managed to set everything to open with proper linux apps like libreoffice, gedit, and codeblocks via "right click, open with other application", but there is a huge amount of
"a wine application" listed in there (I counted no less then 20 entries named that).
I have done a "complete removal" of wine and q4wine and their config files through synaptic.
I also noticed that the wine entry in the main menu was still there, along with all the program shortcuts for the microsoft programs, after uninstalling wine,
so i edited the menu via "right click, edit menus", and deleted the wine menu entry and its contents.
I rebooted and reinstalled wine and q4wine, then rebooted again.
The file types are still displaying screwed up, and the menu entry for wine is missing. Isn't the menu suppose to be updated with a "wine" entry when you install wine?
I had a hunch that maybe all i needed to do to get back the wine menu entry was to install a wine program that would try make a "start menu" entry as it was installing, so i reinstalled
a random windows match-3 game, making sure to check the box "create start menu shortcut". Still no wine entry in the linux main menu after doing this.

Any one else like me that gets the wild idea to run office or visual studio under linux: Stick it in a virtual machine. Much safer solution, as far as i can tell.

How do i get all this straightened out?

---

### Post by mörgæs on 2014-12-23
With a fresh install of 14.04.1 or 14.10. 
11.04 has been abandoned for a couple of years and your Wine install has many a configuration problem. Faster and safer to begin anew.

---

### Post by ramidavis2 on 2014-12-23
Upgrading is not really an option, sorry. (No, really.)
My particular machine hardware is fully supported by 11.04. If i upgrade to 14.04/10, i know for a fact i will have issues.
For starters, my video card is an ati, and has been classified as legacy now. The new x server in ubuntu 14 is not compatible with the last version of the ati legacy driver that would support my card.
I could keep going, but my point is this: why upgrade and lose system functionality of something that is fully working here and now?
True, hardware enable video acceleration is not mission critical, but why sacrifice it. Would you willingly give up proper functionality just for a promise of the "new and improved"? If so, i truly pity you.

---

### Post by Bucky Ball on 2014-12-23
Nothing to do with 'new and improved'. If you are online, you are running a vulnerable machine with totally out of date software and no security updates for over two years. 

Your chances of support are minimal as your release and software are so old. Not sure too many of us would even remember how to fix 11.04.

---

### Post by mörgæs on 2014-12-23
You don't have to pity me. I feel good knowing that my system receives all security fixes, but if I were running a system not bugfixed for two years I would be worried. It's not about new stuff but about security.

Anyway, I have no better suggestion so I'll sign out.

---

### Post by Bucky Ball on 2014-12-23
> **mörgæs said:**
> 

Anyway, I have no better suggestion so I'll sign out.

Same. About the only thing I could suggest would be to install a newer release on a spare partition and see how you go. Good luck whatever you decide, but things doubtfully will get much better as you have no repos available to aid in your fix of very outdated software.

---

### Post by Mike_Walsh on 2014-12-23
Hallo, ramidavis2.

I'm unclear about one thing. I fully agree with morgaes, and Bucky Ball.....11.04 has been unsupported for a couple of years now, and per se, it is NOT safe.

However, you say that your machine has a 'legacy' ATI graphics card, and that you 'know' you're going to have 'issues'. My machine is 10 yrs old. It has an ATI Radeon Xpress200 graphics card. I'm running 14.04.1 LTS, and make full use of the Compiz 'special effects', and many other features of Unity, and Ubuntu. The Xpress200 was classified as 'legacy' something like 4 or 5 years ago.....yet it works perfectly with the open-source drivers in Ubuntu, and has done so ever since the original 3.13-0.24 kernel, upon first release.

Give 14.04.1 a try, in a separate partition. For the time it takes to download  it, burn it to disc, and try the LiveDVD, you may be pleasantly surprised; it's doubtful that support for ATI 'legacy' cards has been dropped, 2-3 years down the line. In my (admittedly limited) experience, that's NOT the way the open-source community works.

On the whole, the community tends to go out of its way to try to keep older hardware going for as long as possible. But Wine, generally speaking, is a PITA at the best of times; unless you're lucky enough to have a piece of Windows software that has the coveted 'Platinum' rating, then you're going to encounter problems with it, to a greater or lesser degree.


Regards,

Mike.

---

### Post by Impavidus on 2014-12-23
ATI may no longer provide Linux drivers for your graphics card, but the open source drivers for older ATI cards can be quite good. At least give 14.04 a test from a live disk. Use Xubuntu or Lubuntu if your hardware is to weak for Ubuntu 14.04. All of them are LTS releases. I've got a 10 year old box with an equally old ati card (forgot the exact model) still running fine. For the past 8 years (as long as it had Ubuntu installed) it has used the open source drivers.

I read too often that people can't upgrade for some vague reason. Your system is broken and will remain so, visibly or not, as long as you run an old release.

There may be some wrong file type associations left in config files in your home directory. Uninstalling software doesn't remove anything from your home directory, which you should do manually. Can't give any details. Never used wine myself.

---

### Post by DuckHook on 2014-12-23
> **ramidavis2 said:**
> ...If so, i truly pity you.When one is asking for help, it is unwise (to say the least) to insult those from whom help is being asked with such baldfaced condescension. Both mörgæs and Bucky Ball are more than capable of defending themselves, so I am not just tilting at windmills here; I am only observing&#8213;if not for your sake, then for others who might chance upon this thread&#8213;that one would be hard-pressed to find better mentors/guides/gurus on old hardware than either of these two blokes. For what it's worth, and as something of an old hardware hound myself, I agree with them: if you are intent on sticking with dead releases, no one can help you, and it's not for want of trying.

---

### Post by andrew.46 on 2014-12-23
Hi Ramidavis!

It is a small point that may help with some of the tangle you have been left with: have a look in *$HOME/.local/share/applications* and you should see a bunch of files like this *wine-extension-*.desktop*. If you are not actually using Wine and these remain simply add a _bak to the end of each of them. This may provide a start for you hopefully :)

---

### Post by mc4man on 2014-12-24
> **andrew.46 said:**
> Hi Ramidavis!

It is a small point that may help with some of the tangle you have been left with: have a look in *$HOME/.local/share/applications* and you should see a bunch of files like this *wine-extension-*.desktop*. If you are not actually using Wine and these remain simply add a _bak to the end of each of them. This may provide a start for you hopefully :)
I haven't used wine in quite some time but you've hit the nail on the head here.
However it's probably better if one wanted to keep some or all of those .desktops for future use to move them somewhere else rather than rename. In debian/ubuntu/gnome, (maybe elsewhere),  .desktops are a special case so after a rename of *the actual file *name a .desktop will always be appended to that name

---

### Post by andrew.46 on 2014-12-24
> **mc4man said:**
>  In debian/ubuntu/gnome, (maybe elsewhere),  .desktops are a special case so after a rename of *the actual file *name a .desktop will always be appended to that name

I did not realise that, so in being a bit cautious I have probably not been all that helpful. The regeneration does not seem to occur in slackware but I have not tested extensively...

---

### Post by mc4man on 2014-12-24
> **andrew.46 said:**
> I did not realise that, so in being a bit cautious I have probably not been all that helpful. The regeneration does not seem to occur in slackware but I have not tested extensively...
I think you were quite helpful, ie., addressing the issue.
If one does rename a desktop & then wants to return to orig. you have to rename without any ext. at all.
(- I never quite knew what to make of these wine .desktops, though at least back then I found if deleted it was quite hard to get wine to re-create so generally just stuck them in a folder somewhere..

---

### Post by andrew.46 on 2014-12-24
> **mc4man said:**
>  I never quite knew what to make of these wine .desktops, though at least back then I found if deleted it was quite hard to get wine to re-create so generally just stuck them in a folder somewhere..

I found them when post-installation with wine all my text files were being opened with a variation of Windows Notepad :)

---

### Post by dragonfly41 on 2014-12-24
I no longer use wine .. but there are more tips here on file association ..

[http://askubuntu.com/questions/323437/how-to-prevent-wine-from-adding-file-associations](http://askubuntu.com/questions/323437/how-to-prevent-wine-from-adding-file-associations)

---

