---
title: "Are these any good?"
date: 2022-02-24
forum: General Help
---

### Post by wyattwhiteeagle on 2022-02-24
> 1. FSlint: Clear duplicate file's and broken symlink's.
2. gtkorphan: Remove orphaned package's.
3. Debfoster: Keep track of what you have installed.
4. localepurge: Remove locale files.
5. Preload: Reduce application startup time.
6. zRam: Improve speed.
7. Ananicy: Prioritize your apps.

Has anyone heard of these?
Are they any good?
Are there better suggestion's?

---

### Post by TheFu on 2022-02-25
I would encourage you to learn the details of what each of those things do, so you can do it manually first.  Then you'll be in a better position to decide if loading 50,000 1-trick programs is really something useful for your needs.

Of all of those, only zram may be something you can't do with a 2 line script yourself. I've not used it, but think that zswap is default the last 5 yrs. I did load zswap on a very limited laptop and it did help make the most of available swap on that 2GB RAM system.

If you have load time issues, there are likely other problems to be solved on the system. Feels like someone was trying to copy what MSFT did due to a different OS architecture since Windows processes are at least 10x heavier than Unix processes.

**Off topic follows: **
Do you know about AlternativeTo.net?  That similar to the Software Equivalents list.

Trying to make Unix behave like Windows is a road to frustration. They have vastly different architectures and goals.  _The UNIX Philosophy_ (or one of 500 summaries) points out the goals of Unix systems.  [https://en.wikipedia.org/wiki/The_unix_philosophy](https://en.wikipedia.org/wiki/The_unix_philosophy) is reasonable.
[LIST]
[*]    Write programs that do one thing and do it well.
[*]    Write programs to work together.
[*]    Write programs to handle text streams, because that is a universal interface. 
[/LIST]
I'd ask whether all the programs in the list above meet all those requirements? 

Shifting into Unix-think isn't easy, but once you do, your brain will start mixing and matching existing tools on your system (or tools/tiny scripts you've written) to solve problems.  Here's an attempt to explain the differences: [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed)

---

### Post by GhX6GZMB on 2022-02-25
> **wyattwhiteeagle said:**
> Has anyone heard of these?
Are they any good?
Are there better suggestion's?

Those look like the kind of useless junk that's bundled with Win10/11, cluttering up a system, but making a new user feel "empowered".
Leave it and learn to work with UNIX/Linux.

---

### Post by Frogs Hair on 2022-02-25
>  gtkorphan: Remove orphaned package's. This is an old GTK 2 application that's no longer updated , I wouldn't recommend it. 

[http://www.marzocca.net/linux/gtkorphan.html](http://www.marzocca.net/linux/gtkorphan.html)

---

### Post by oldfred on 2022-02-25
I used to use fslint, but it is python2 and not updated to python3.
I do not allow obsolete python2 apps on my system.

---

### Post by wyattwhiteeagle on 2022-02-26
> **TheFu said:**
> ...If you have load time issues, there are likely other problems to be solved on the system...

Speaking of load time issue's, I need to expound on this.

I was out of town all day yesterday.
When I got home, I noticed that my system was taking 3x longer to load things up.

I opened google, took it abt 2 minutes to load up where before...it took only like 20 secs.

same issue with the terminal, before yesterday...it took the terminal less than 10 secs...now, it takes terminal between 20 and 30 secs to load up.

Do I continue this here, or do I post a new thread and which forum is best for this?

---

### Post by TheFu on 2022-02-26
> **oldfred said:**
> I used to use fslint, but it is python2 and not updated to python3.
I do not allow obsolete python2 apps on my system.

fdup or something similar is popular.

10 yrs ago, someone asked about a duplicate file finder tool, I had some free time, so I wrote my own which I still use, because some of the intermediate steps I use are good for other needs.  If I were not interested in my own script, I'd use fdup or **fdupes** ... whatever it is called. It is C.  [https://www.tecmint.com/fdupes-find-and-delete-duplicate-files-in-linux/](https://www.tecmint.com/fdupes-find-and-delete-duplicate-files-in-linux/)

---

### Post by dragonfly41 on 2022-02-26
> [COLOR=#000000]Are they any good?[/COLOR]
[COLOR=#000000]Are there better suggestion's?[/COLOR]
Good for what?  I don't think I have learned from your discussions what your *aims* are.
There are tools which can be suggested .. but do they meet your aims?

---

### Post by wyattwhiteeagle on 2022-02-26
> **dragonfly41 said:**
> Good for what?  I don't think I have learned from your discussions what your *aims* are.
There are tools which can be suggested .. but do they meet your aims?

Well...

Good for keeping Ubuntu clean, lean and with optimal performance.

TheFu's suggestion about 20+ GUI programs and application packages seem's reasonable.
I'd rather keep the GUI content at a minimal.

I'm beginning to not trust GUI as much due to "hidden" items such as tracker's and key-logger's.
Or...the "click here and use this" only to find out that it's a link for the user to pay money to have that feature.

---

### Post by dragonfly41 on 2022-02-26
So if we are looking at performance monitoring tools
I suggest [Stacer]("https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,all%20in%20one%20system%20utility.") .. although it is another GUI.

There seems to be reluctance to use GUI's instead of classical Unix CLI (htop etc).
But I do not support that view (for my own project development workflows).
There are just too many command strings I have to learn/contend with.
So for example I take the output from .. man rdiff-backup .. pipe > to a text file, 
then in Python extract/parse all the --arguments to place in a GUI menu.
From this I *compose* my command lines.

If we take your other recent thread on rdiff-backup (a marathon) I have picked up
tips/ideas from that (I am new at applying rdiff-backup) and I am now writing my own GUI which composes commands
to be run in terminal (my choice is yakuake, over gnome-terminal).

If you are worried about embedded trackers in GUI's then write your own GUI's.
Python3 and Node.js offers the building parts.
I can create an Electron app in quick time. In fact I'm taking that approach after looking at rdiffweb.

Stacer is an Electron app.

You might explore gnome-system-monitor.

And in my apps in Ubuntu 20.04 I launch lynis as an auditor from time to time.

So I would add automation scripting to your list. Install Actiona.

Also install Albert and learn how to write/use python extensions, for example.

Again I use Krusader as my mainstay file manager and write Krusader useractions.

The bottom line is I use hybrid GUI and command line scripts in *toolchains*.

If you get around to installing Actiona (automation tool) as I suggest I can send an example script (but here again you must *trust* the authors of such scripts since they can be very powerful). In Actiona all variables are written in a javascript file.

---

### Post by wyattwhiteeagle on 2022-02-26
GUI vs CLI

The GUI approach seems to be taking 1 single package to do one single thing.
I believe that's one of the reason's TheFu made the suggestion he made.

If there are 20 things to do in order to keep the system goin the way it's going, that's 20 different GUI to do only 1 thing each.

The scripting, it seems a long road...but when the script is good...it takes up a lot less time.

Take Preload for example.
It say's "reduce startup time".
But in the tutorial, the user installs it and adds applications to it to startup at boot.

I'm not sure how preloads "behind-the-scene" works but it would seem that if 20+ things are loading up at boot and then someone install's preload and put's 20 other things in preload, wouldn't that make the system slower due to loading up 40+ items at boot?

Stacer, I've used it before.

One of the things about stacer is that it show's the user that brltyy or brltty...i forget what the exact name is but it's for blind people who need Braille.
In stacer I clicked to disable that. I closed and reopen stacer...it was going again.
So I disabled it again and completely rebooted...opened stacer...goin again.

So I checked stacer's website...
Apparently, the creator of stacer doesn't like to maintain stacer when everyone is trying to tell him about an issue with his product.
They speak of the same issue.
One of the issue's they speak of is stacer not disabling services.
Seem's as though if he himself doesn't experience the issue...he doesn't look into it and chock's it up as the user's fault for the issue.

If it was me, if 500+ people is telling me about the exact same issue, I would definitely look into it before blaming the user.

Now, I know how to purge things from the system.
I don't need anything for the blind...I'm not blind...so I CLI remove, purge and block that.

---

### Post by TheFu on 2022-02-26
> **wyattwhiteeagle said:**
>  
The GUI approach seems to be taking 1 single package to do one single thing.
I believe that's why TheFu made the suggestion he made.


I'm afraid that isn't what I meant and I don't know how to state it in a different manner for better clarity. Completely my failure. Sorry.

---

### Post by wyattwhiteeagle on 2022-02-26
> **TheFu said:**
> I'm afraid that isn't what I meant and I don't know how to state it in a different manner for better clarity. Completely my failure. Sorry.

Nope, not a failure.
I completely understood it the way you meant it.
I just restated it in my own way to save room in the post that I was typing up.

I edited that post to reflect that properly

---

### Post by dragonfly41 on 2022-02-26
Stacer is in Ubuntu repo. If you have Synaptic installed search "Stacer".
 
 sudo apt install stacer
 
 [https://github.com/oguzhaninan/Stacer/issues](https://github.com/oguzhaninan/Stacer/issues)
 
 I could not find reference to brltty (Braille) in Stacer issues.
 
 Perhaps you meant vtop?
 
 [https://github.com/brltty/brltty](https://github.com/brltty/brltty)
 
 BRLTTY is a background process (daemon) providing access to the Linux/Unix
console (when in text mode) for a blind person using a refreshable braille
display.

[https://www.saashub.com/compare-vtop-vs-stacer?ref=compare](https://www.saashub.com/compare-vtop-vs-stacer?ref=compare)
 
 vtop is a graphical command-line tool that uses unicode braille to chart CPU and memory usage.   

My conclusion.
[h=3]&#8220;*you can lead a horse to water, but you can&#8217;t make it drink*.&#8221;[/h]

---

### Post by wyattwhiteeagle on 2022-02-26
> **dragonfly41 said:**
> 
 [https://github.com/oguzhaninan/Stacer/issues](https://github.com/oguzhaninan/Stacer/issues)
 
 I could not find reference to brltty (Braille) in Stacer issues...
Brllty itself isn't in the stacer issue's page.
Stacer not disabling services is what's in the stacer issue page.

There is some good things about stacer.

I will look into vtop.
Thank you for that info.

*update*

it seems vtop isnt installed by default.
I'm not talking about vtop...but brltty

---

### Post by dragonfly41 on 2022-02-27
[P.S.]

I will just try to correct this impression you have.

> [COLOR=#000000]If there are 20 things to do in order to keep the system goin the way it's going, that's 20 different GUI to do only 1 thing each.[/COLOR]

In fact you can have *one* GUI which derives each of the "20 things" to run from a single config file.
The "20 things" are just commands to be pasted into a terminal and run.

Some time back there was a CLI GUI named clicompanion (now not supported although there is clicompanion2).

Ubuntu has another GUI app named "zenity" .. but there are several.  I do suggest that you examine Albert as I mentioned in earlier post.

[P.P.S]
Somehow I lost a lengthy post preceding this. I thought that this post was editing the previous one. Oh well.

---

### Post by wyattwhiteeagle on 2022-02-27
> **dragonfly41 said:**
> [P.S.]

I will just try to correct this impression you have.



In fact you can have *one* GUI which derives each of the "20 things" to run from a single config file.
The "20 things" are just commands to be pasted into a terminal and run.

Some time back there was a CLI GUI named clicompanion (now not supported although there is clicompanion2).

Ubuntu has another GUI app named "zenity" .. but there are several.  I do suggest that you examine Albert as I mentioned in earlier post.

[P.P.S]
Somehow I lost a lengthy post preceding this. I thought that this post was editing the previous one. Oh well.

You have some very impressive idea's. Some of which I've already considered.

Back in 2014/2015 (Ubuntu 14.04) I had mentioned something about doing things "all in one script."
I know now that "all in one script" is more-less a theory rather than a reality.

However, there are "reality's" that have bloomed from that "all in one script" idea.

When I had checked into getting things in the software store, money needed to be payed to have it there.
I've noticed that most things I use may not be in the software store.
Not using the software store is the reason I'm not sure if those things are there.

So, if I do this, there are some stipulation's that I will need to follow...

1. It must stay within the "free and open source" guideline's.
2. It must be available across Ubuntu and all of it's flavour's but not restricted to only those but also available to other Linux distro's with the possibility of expanding into Windows.
3. It must stay "free of charge" meaning the end-user must not be charged for using any feature in the product.
4. All feature's in the product must be effective.
5. Last but not least, there are no distribution cost's.

I'm not saying you have to follow these stipulation's with your product's.

Can those 5 thing's be guarantee'd?
If so, I will start making move's toward doing what you suggest.

---

### Post by TheFu on 2022-02-27
> **wyattwhiteeagle said:**
>  
3. It must stay "free of charge" meaning the end-user must not be charged for using any feature in the product.


Very MS-Windows way of thinking.  Do you consider the program taking your information and/or data without approval as "paying?"  I do.

Free as in (no $$$ exchanged) isn't good enough, IMHO.   We want NO STRINGS ATTACHED too.  I block as much of google, facebook, insta-whatever and similar trackers as I can at the network layer with weekly updates, since those things change all the time. My android devices are almost always in airplane mode and use non-Google app stores. 1 doesn't have any google code, besides the base android OS on it.  Google makes the vast majority of their money by taking data and information from each of us, without our explicit permission AND they never delete anything.

I've never used Canonical's "Software Store". This helps avoid most of the packages that have licenses I wouldn't like, through Canonical is putting a few wrapped in APT packages to trick us into using less-than-great package types, which probably have tracking included since they phone-home 4x a day, by default.

The huge data companies scare me the most. They have their fingers grabbing information from nearly every connection online. Even with network-based blocking, it is hard to completely remove your data from their systems, since it isn't illegal for them to grab and hold it. We need better laws for better privacy.  If the data were all separate, that won't be nearly as concerning. It is the correlation of the data that really scares me. The big-guys make the correlated data available for a price and claim it is anonymized.  That's been proven to be much, much, harder than just changing 1 part of the data as they've done for decades.

IMHO.  Other people will have different options.

BTW, you can create a script that does everything.  But it would look a lot like a shell, say like bash.

---

### Post by wyattwhiteeagle on 2022-02-27
> **TheFu said:**
> Very MS-Windows way of thinking.  Do you consider the program taking your information and/or data without approval as "paying?"  I do.

Free as in (no $$$ exchanged) isn't good enough, IMHO.   We want NO STRINGS ATTACHED too.  I block as much of google, facebook, insta-whatever and similar trackers as I can at the network layer with weekly updates, since those things change all the time. My android devices are almost always in airplane mode and use non-Google app stores. 1 doesn't have any google code, besides the base android OS on it.  Google makes the vast majority of their money by taking data and information from each of us, without our explicit permission AND they never delete anything.

I've never used Canonical's "Software Store". This helps avoid most of the packages that have licenses I wouldn't like, through Canonical is putting a few wrapped in APT packages to trick us into using less-than-great package types, which probably have tracking included since they phone-home 4x a day, by default.

The huge data companies scare me the most. They have their fingers grabbing information from nearly every connection online. Even with network-based blocking, it is hard to completely remove your data from their systems, since it isn't illegal for them to grab and hold it. We need better laws for better privacy.  If the data were all separate, that won't be nearly as concerning. It is the correlation of the data that really scares me. The big-guys make the correlated data available for a price and claim it is anonymized.  That's been proven to be much, much, harder than just changing 1 part of the data as they've done for decades.

IMHO.  Other people will have different options.

BTW, you can create a script that does everything.  But it would look a lot like a shell, say like bash.

I believe there are some incorrect assumption's.

The targeted user's would be those of low or no income.
They are having to spend every dime they have just to make end's meet at home.
The last thing they need or want is something else they need to pay for.

I agree that there needs to be some safe-guard's in place.

---

### Post by TheFu on 2022-02-27
Everyone deserves to choose whether their data is taken without approval or not.  Free is seldom actually free.
I wasn't assuming any income level at all, BTW. I am guilty of assuming a technical skill level and that someone would care about their privacy.

---

### Post by wyattwhiteeagle on 2022-02-27
> **TheFu said:**
> Everyone deserves to choose whether their data is taken without approval or not.  Free is seldom actually free.
I wasn't assuming any income level at all, BTW. I am guilty of assuming a technical skill level and that someone would care about their privacy.

As I said, there need's to be some safe-guard's in place.

---

### Post by dragonfly41 on 2022-02-27
> 1. It must stay within the "free and open source" guideline's.
2. It must be available across Ubuntu and all of it's flavour's but not restricted to only those but also available to other Linux distro's with the possibility of expanding into Windows.
3. It must stay "free of charge" meaning the end-user must not be charged for using any feature in the product.
4. All feature's in the product must be effective.
5. Last but not least, there are no distribution cost's.


I read from your posts that you (and your users) do not want to pay for any features.

I am guessing that you hope to develop some form of cross platform service or app and you do not wish to have any upfront outlay until possibly you start generating income.

You appear to be targetting users with limited incomes (including yourself) to pay for services/products (MS Windows style) .. but at the same time you need to protect your endeavours and data.

You can beat the large companies at their own game by separating your development into different compartments. That is, do not put all your eggs in one basket.

You might have a desktop app which draws on remote services.

You might develop a desktop app which offers users commercial licences, but these are difficult to protect.

But really .. it is pointless theorising when we have no idea what product/service you plan to develop (and protect intellectual property). Can you unlock this mystery and briefly explain what is the end product you have in mind (without revealing too much)?

---

### Post by wyattwhiteeagle on 2022-02-27
> **dragonfly41 said:**
> I read from your posts that you (and your users) do not want to pay for any features.

I am guessing that you hope to develop some form of cross platform service or app and you do not wish to have any upfront outlay until possibly you start generating income.

You appear to be targetting users with limited incomes (including yourself) to pay for services/products (MS Windows style) .. but at the same time you need to protect your endeavours and data.

You can beat the large companies at their own game by separating your development into different compartments. That is, do not put all your eggs in one basket.

You might have a desktop app which draws on remote services.

You might develop a desktop app which offers users commercial licences, but these are difficult to protect.

But really .. it is pointless theorising when we have no idea what product/service you plan to develop (and protect intellectual property). Can you unlock this mystery and briefly explain what is the end product you have in mind (without revealing too much)?

I'll try to keep this breaf summary short.

I'm disabled. I make 4x less than the average worker. 
Yes, I had myself in mind when I considered which "user's" I would be targetting.
I don't want anything in return, not money anyway.
I'm not wanting any "personal gain's" from my product...commercial or otherwise.

As for the product, in brief...

Stacer cleans area's that bleachbit doesn't touch, and vice-versa.
Stacer and Bleachbit doesn't clean certain thing's under Wine and PlayOnLinux.

It would be nice to have one tool that clean's all of the area's.
A CLI script with a graphical interface, 100% guaratee'd no-cost.

---

### Post by dragonfly41 on 2022-02-27
> As for the product, in brief...

Stacer cleans area's that bleachbit doesn't touch, and vice-versa.
Stacer and Bleachbit doesn't clean certain thing's under Wine and PlayOnLinux.

It would be nice to have one tool that clean's all of the area's.
A CLI script with a graphical interface, 100% guaratee'd no-cost.


Now we can offer more focussed ideas.
I will not question why you use Wine. I prefer to distance myself from legacy Windows.

There is a source of code snippets you should bookmark and research..
It is codegrepper.com

[https://www.codegrepper.com/code-examples/shell/how+delete+all+wine+files+in+linux](https://www.codegrepper.com/code-examples/shell/how+delete+all+wine+files+in+linux)


[https://www.linuxlinks.com/bleachbit/](https://www.linuxlinks.com/bleachbit/)


Instead or wine and PlayOnLinux

R-Linux running on Ubuntu can delete Windows files.


This discusses VM vs PlayonLinux.  VirtualBox on Ubuntu is free.

[https://www.pclinuxos.com/forum/index.php?topic=153266.0](https://www.pclinuxos.com/forum/index.php?topic=153266.0)

You can then clean VM's from within Ubuntu.


Regarding the GUI wrapper as I wrote earlier you can try different free apps.

Actiona
Zenity

I use both.

It is then a matter of gathering the scripts to run.

If we take as one example the script to delete Wine files

sudo rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*


This can be written as a javascript variable thus in wine.js file (untested - BEWARE):

var remove_wine = [
"sudo rm -rf $HOME/.wine &&
rm -f $HOME/.config/menus/applications-merged/wine* &&
rm -rf $HOME/.local/share/applications/wine &&
rm -f $HOME/.local/share/desktop-directories/wine* &&"
];

This variable can be selected in a GUI and pasted into terminal to be run. Multiple variables (scripts) can be added. Each one will be selected from a GUI menu.  So you might have many scripts/actions to choose from a simple menu list/

If you install Actiona and Zenity we can try these ideas. But ensure that you have backups.

sudo apt install actiona zenity


[P.S.] For editing js files (your variables) I suggest installing gnome-builder since it nicely checks javascript syntax.

---

### Post by wyattwhiteeagle on 2022-02-27
> **dragonfly41 said:**
> Now we can offer more focussed ideas.
I will not question why you use Wine. I prefer to distance myself from legacy Windows.

There is a source of code snippets you should bookmark and research..
It is codegrepper.com

[https://www.codegrepper.com/code-examples/shell/how+delete+all+wine+files+in+linux](https://www.codegrepper.com/code-examples/shell/how+delete+all+wine+files+in+linux)


[https://www.linuxlinks.com/bleachbit/](https://www.linuxlinks.com/bleachbit/)


Instead or wine and PlayOnLinux

R-Linux running on Ubuntu can delete Windows files.


This discusses VM vs PlayonLinux.  VirtualBox on Ubuntu is free.

[https://www.pclinuxos.com/forum/index.php?topic=153266.0](https://www.pclinuxos.com/forum/index.php?topic=153266.0)

You can then clean VM's from within Ubuntu.


Regarding the GUI wrapper as I wrote earlier you can try different free apps.

Actiona
Zenity

I use both.

It is then a matter of gathering the scripts to run.

If we take as one example the script to delete Wine files

sudo rm -rf $HOME/.wine
rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*


This can be written as a javascript variable thus in wine.js file (untested - BEWARE):

var remove_wine = [
"sudo rm -rf $HOME/.wine &&
rm -f $HOME/.config/menus/applications-merged/wine* &&
rm -rf $HOME/.local/share/applications/wine &&
rm -f $HOME/.local/share/desktop-directories/wine* &&"
];

This variable can be selected in a GUI and pasted into terminal to be run. Multiple variables (scripts) can be added. Each one will be selected from a GUI menu.  So you might have many scripts/actions to choose from a simple menu list/

If you install Actiona and Zenity we can try these ideas. But ensure that you have backups.

sudo apt install actiona zenity


[P.S.] For editing js files (your variables) I suggest installing gnome-builder since it nicely checks javascript syntax.

This laptop is 10+/- yrs old.
The original spec's of this laptop was 500g internal HDD and 4g RAM
I upgraded to 1T internal HDD and 8g RAM
It has the original dual-core processor.
I don't do dual-booting, so it's a full minimal Ubuntu install.
Do I need to switch to the less resource-hungry Lubuntu before starting this venture?

I use IMVU.
Many people claim it is a game. It isn't a game.
IMVU is an instant messenging 3d chat client.
Where the game idea come's from is many people use it for role-playing. Thus, a "role-playing game".
Though the percentage of all IMVU user's doing role-playing is only like 20%.

Under Linux, some Windows app's use some feature's that will work only under the staging branch in Wine.
Nothing else allow's those specific feature's to work outside of MS-Windows.
IMVU is one of those app's.
Thus, I use Wine-staging.

There is a little-known Windows app called IMVU-Cache-Cleaner.
Since it is a Windows *.exe app, I have to install it under Wine-staging.
Thus, another cleaner doing only 1 specific thing.

That app doesn't even clean out all of the cache's for IMVU.

IMVU's "Virtual Goods" creator's (most of them are "end-user's") are stuck with *.pickle and *.chkn file's even when using the imvu-cache-cleaner.
These files are having to be manually deleted by the end-user when they are done with 'em.

The weird part...
IMVU, a Windows app, is based on 8 to 12 "free and open source" packages.
Though they allow it...IMVU, Inc doesn't support the use of their product on Linux and it's derivative's.

If you notice, most of the copyrights are out-of-date...

> 

===================================================================


About IMVU
<IMVU logo>
IMVU version 543.0    Copyright 2021 IMVU, Inc All rights reserved
------------------------------------------------------------------------
IMVU is based on, in part or whole, the following software


7-Zip LGPL v2.1    Copyright 1999-2006 Igor Pavlov
Audiere LGPL v2.1    Copyright 2001-2006 Chad Austin; Additional copyright: Matt Campbell, Jacky Chong, Theodore Reed, Ben Scott
Boost
Cal3D LGPL v2.1    Copyright 2001-2003 Bruno "Beosil" Heidelberger; Additional copyright: Laurent Desmecht, Justin Hare, Chad Austin
CPUInfo        Copyright 2005 Chad Austin
GLee            Copyright 2009 Ben Woodhouse
jpeglib        This software is based in part on the work of the Independent JPEG Group
libogg            Copyright 2002 Xiph.org Foundation
libvorbis        Copyright 2002-2008 Xiph.org Foundation
Mozilla XULRunner SDK    Mozilla Public License v1.1
ParticleLib LGPL v3    Copyright 1997-2007 by David K. McAllister
Protocol Buffers    Copyright 2008 Google Inc
py2exe            Copyright 2002-2008 Thomas Heller, Mark Hammond, Jimmy Retzlaff
pylzma LGPL v2.1    Copyright 2004-2006 Joachim Bauch
PySQLite        Copyright 2004-2007 Gerard Haring
Python            Copyright 2001-2009 Python Software Foundation
Python Imaging Library    Copyright 1997-2009 Secret Labs AB; 1995-2009 Fredrik Lundh
pywin32        Copyright 1994-2008 Mark Hammond
TransGaming SwiftShader    This product includes SwiftShader Software GPU Toolkit, copyright 2003-2012 TransGaming Inc.
OpenSSL        Copyright 1998-2017 The OpenSSL Project


All Rights Reserved


=======================================================================




---

### Post by dragonfly41 on 2022-02-28
If you take the two steps of:
Install Actiona (Linux) in Ubuntu (sudo apt install actiona)
AND
Install Actiona (Windows) in Wine (select the download for Windows)
[https://wiki.actiona.tools/doku.php?id=en:start](https://wiki.actiona.tools/doku.php?id=en:start)

I can then post an example Actiona script to start you off.
Note that Actiona is cross platform and works across Ubuntu and Wine/Windows.
It is quite suitable for orchestrating workflows such as IMVU. In fact one of its common uses is automating game play.

Post back when Actiona is installed on Ubuntu/Wine.

The example script will show how to automate running this process:

[https://help.imvu.com/s/article/How-to-clear-the-IMVU-cache?language=en_US](https://help.imvu.com/s/article/How-to-clear-the-IMVU-cache?language=en_US)


[P.S.] Answering this question:

[COLOR=#000000]"Do I need to switch to the less resource-hungry Lubuntu before starting this venture?"

No.
[/COLOR]

---

### Post by wyattwhiteeagle on 2022-02-28
> **dragonfly41 said:**
> If you take the two steps of:
Install Actiona (Linux) in Ubuntu (sudo apt install actiona)
AND
Install Actiona (Windows) in Wine (select the download for Windows)
[https://wiki.actiona.tools/doku.php?id=en:start](https://wiki.actiona.tools/doku.php?id=en:start)

I can then post an example Actiona script to start you off.
Note that Actiona is cross platform and works across Ubuntu and Wine/Windows.
It is quite suitable for orchestrating workflows such as IMVU. In fact one of its common uses is automating game play.

Post back when Actiona is installed on Ubuntu/Wine.

The example script will show how to automate running this process:

[https://help.imvu.com/s/article/How-to-clear-the-IMVU-cache?language=en_US](https://help.imvu.com/s/article/How-to-clear-the-IMVU-cache?language=en_US)[COLOR=#000000]
[/COLOR]
Ok
Both Actiona are installed.

---

### Post by dragonfly41 on 2022-02-28
> 
[COLOR=#000000]Ok[/COLOR]
[COLOR=#000000]Both Actiona are installed.
[/COLOR][COLOR=#000000]

Good. Quite painless. It is a bit late here (U.K.) so I will post a first rough script tomorrow.

Meanwhile take some time playing with Actiona in Ubuntu to start with.
The Windows Actiona version is needed when you target the IMVU client window (and any other Wine apps).

You can start by launching the IMVU Client in the usual way.
When you are in Wine, maximise the IMVU Client window so we have a fixed layout.
Take note of the x:y coordinates of each button which is clicked in the four steps.
An alternative approach is to grab screenshots of the buttons regions and place in a folder to be accessed by Actiona script.
The target positions will be placed into a javascript file as array of variables

var targets = [
["target1", "x1:y1"],
[/COLOR][COLOR=#000000]["target2", "x2:y2"],
[/COLOR][COLOR=#000000]["target3", "x3:y3"],
[/COLOR][COLOR=#000000]["target4", "x4:y4"],[/COLOR][COLOR=#000000]
];

Then later Actiona will run through Actions in GUI like a macro.

This tutorial shows how arrays are defined.
[/COLOR]https://www.w3schools.com/js/js_arrays.asp

[COLOR=#000000]If we write a javascript array as follows: [/COLOR]
[COLOR=#0000FF][FONT=&amp]var login = [[/FONT][/COLOR][COLOR=#0000FF][FONT=&amp]["username", "me"],[/FONT][/COLOR][COLOR=#0000FF][FONT=&amp]["password", "whiteknuckle"],[/FONT][/COLOR][COLOR=#0000FF][FONT=&amp]];

[/FONT][/COLOR]we can refer to these as: 

[COLOR=#0000FF][FONT=&amp]$login[0][0];[/FONT][/COLOR][COLOR=#0000FF][FONT=&amp]$login[0][1];[/FONT][/COLOR][COLOR=#0000FF][FONT=&amp]$login[1][0];[/FONT][/COLOR][COLOR=#0000FF][FONT=&amp]$login[1][1];

[/FONT][/COLOR]Actiona objects are documented as below. 

[https://wiki.actiona.tools/doku.php?id=en:code](https://wiki.actiona.tools/doku.php?id=en:code)


More tomorrow.

Also as introduction browse the forum for ideas (English / French)..

[https://forum.jmgr.net/](https://forum.jmgr.net/)


In summary, think back to Flash days when Actionscript was in vogue.

ActionScript: The Definitive Guide
Author Colin Moock
O'Reilly

---

### Post by dragonfly41 on 2022-03-01
These are my findings after I installed Wine and PlayOnLinux (after many years away from this).
I felt that I had to understand Wine rather than theorise how to use it from memory.

1. There is no need for a second installation of Actiona in Wine as I suggested, since the Ubuntu
installation of Actiona can "drive"  Win apps. Simpler. Only if you needed access to Win registry would the Actiona tool be needed in Wine.  Read registry and Write registry for example. They are disabled in the Linux version of Actiona although they can be seen in the Objects panel.

2. Rather than asking for target x:y coordinates it is easier to take clips of images (buttons etc.)
to search for.  For this I use Flameshot (sudo apt install flameshot) although you might use an alternative tool. 

3. I positioned installed WordPad.exe window and I was able to use Flameshot to take clips of the button regions. These target images are used in the Actiona Find Image object (Image to find) . When  image is found the object exits to run other actions in sequence starting with Click or Key.  Clips were taken of all WordPad.exe top buttons. The same approach can be used with IMVU window and any other window in focus on screen.

---

### Post by wyattwhiteeagle on 2022-03-06
My apologie's
I was gonna continue here until I noticed that my Timeshift was messing up.

I feel I need to get a "simple system restore" going before I continue here.

Will update when it's ready to go.

---

