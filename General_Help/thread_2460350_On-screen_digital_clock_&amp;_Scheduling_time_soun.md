---
title: "On-screen digital clock &amp; Scheduling time sounds."
date: 2021-04-08
forum: General Help
---

### Post by hagrid3 on 2021-04-08
Hello Folks.
I have Ubuntu Mate 18.04.5 on a desktop PC & all is generally well - except for the small ambition I had not been able to make happen.

Given that I lose track of time very badly, I have really needed a visual & audible reminders that time is passing.

This desire would be well satisfied with some sort of rather plain, digital desktop clock with either a chime function, or one that speaks.

In my quest I searched multiple times & tried several apps as well as scheduling the PC to chime or talk.

In the long time since this quest began I did find an app that sort of worked:
[https://sourceforge.net/projects/digitalclock4/files/4.7.9/](https://sourceforge.net/projects/digitalclock4/files/4.7.9/)
It is called Digital Clock 4, and is no longer developed or supported.
Trouble with it is that it sort of randomly vanishes from the screen for no obvious reason and even crashes sometimes.

What I prefer from it looks like so:
[IMG]https://i.postimg.cc/X7Z0H6sJ/myclock.jpg[/IMG]

Later, I found what looked like a great solution at this site:
[http://www.dotmana.com/weblog/2013/02/ubuntu-talking-clock-every-hours/](http://www.dotmana.com/weblog/2013/02/ubuntu-talking-clock-every-hours/)

And using this in terminal worked fine:
```
echo "current time is `date +\%-1H` oclock" | aoss festival --tts
```

But despite the installation of Gnome-Schedule, and it **appearing** to work, it did nothing.

I also found a script here, and also tried to make it work via the scheduler:
[https://ubuntuforums.org/showthread.php?t=516600&p=3128046#post3128046](https://ubuntuforums.org/showthread.php?t=516600&p=3128046#post3128046)

Excuting it from terminal worked fine, but the scheduler did nothing with it.

I seriously wondered if I needed to make some system adjustment such that Gnome-Schedule would be able to execute commands at all, or if it required some special syntax that I was ignorant of - but none of that turned out to matter, finally.

I greatly appreciate the guidance that was offered here, and now it is done & the info is in my most recent reply, down below.

[SIZE=5]Thanks for reading this thread !![/SIZE]

---

### Post by TheFu on 2021-04-08
Doesn't support for 18.04 Mate end this month?  Passed time to move to 20.04.
[https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)
> Support lifespan

The 'main' archive of Ubuntu 18.04 LTS will be supported for 5 years until April 2023. Ubuntu 18.04 LTS will be supported for 5 years for Ubuntu Desktop, Ubuntu Server, and Ubuntu Core. Ubuntu Studio 18.04 will be supported for 9 months. **All other flavors will be supported for 3 years.** 
2018 + 3 yrs = 2021. Yep, support ends this month.

I don't get why you use this complex answer when there is **xclock**?  
```
xclock  -update 1 -digital
xclock  -update 1 -digital -brief
```
You can change the colors, fonts, geometry, and format the output for anything you like.  The xclock manpage explains all.  Or you can run **xclock --help**

I don't have any clue about gnome-scheduler - never used it. Cron is the typical scheduled task tool on all Unix systems, so we use that.  It doesn't like GUI programs or anything that might be restricted to a single user.  Anacron is for tasks that don't need to run exactly at a specific time, but sometime that day, week, month, year. I suspect gnome-scheduler is just an interface into your crontab. cron jobs shouldn't interact with any GUI since they can run when nobody is logged in.

To help crontabs be easier, add these comments to the top of YOUR crontab:
```
$ crontab -l
# .---------------- minute (0 - 59) 
# |  .------------- hour (0 - 23)
# |  |  .---------- day of month (1 - 31)
# |  |  |  .------- month (1 - 12) OR jan,feb,mar,apr ... 
# |  |  |  |  .---- day of week (0 - 6) (Sunday=0 or 7)
# |  |  |  |  |
# *  *  *  *  *  /absolute/path/to/command --arg1 --arg2 file1 file2 2>&1

# Push the KeePass DB to other systems at 00:02 daily
2 0 * * * /home/thefu/bin/push_keepass_db.sh
```

---

### Post by ActionParsnip on 2021-04-08
Use absolute paths to commands and use cron, much much easier

---

### Post by hagrid3 on 2021-04-08
_**Thanks Very Much for replying to my query TheFu !!**_
Specifically regarding versions & upgrading - I support others who are end users and their PCs have been attended to - mine comes LAST.
*(This is like the cobbler with holes in his own shoes most of the time...mine will get done when I can keep it offline for a night.)*

[SIZE=5]**Xclock. **[/SIZE]
Wow. 
Nevva hoida that before your pointer - endless searching done at different times literally did not show me that option - not even ONCE !!!

I do not make any claims of being all-knowing (as an eternal learner of life) but that it NEVER popped up before is truly shocking IMO.
Looks to me to be EXACTLY what I've been seeking so fruitlessly - my gratitude for this info & I have its man page on-screen too.

*Gnome-Schedule* is indeed a GUI for cron jobs.
Elsewhere I use it for automating client backups & it works flawlessly - and yes (@ActionParsnip) I do use absolute paths, thank you for pointing that out.

Why it has refused to respond properly on my own PC remains a mystery for me...?

Lastly for now:
hough this site shows me as a *'**First Cup of Ubuntu'* user - that is not even close to being correct after ~10 years using Ubuntu Mate;
I had another account (or 2 ??) here before and those would no longer allow any log ins - so I made this new account sometime back and here we are.
I generally find whatever info I may need via open searching & given the abundance of Ubuntu info that does not always lead me to here.

When I have time to 'play' I check out other distros on my spare CPU which has its guts always wide open for such things, and;
Despite how there are so very many other distros - Ubuntu Mate suits this veteran IT Guy (as well as those whom I assist) quite well - and combined with the great size of the Ubuntu community it has remained the best choice IMO pretty much (since maybe 2006 ??) for me.
I serve no more users of that 'other' OS family, nor the fruity one anymore - Linux is ALL for me nowadays.
[U][B]
OK I'm sure that is quite enough outta me now - SO:
Thanks again for the clear & helpful replies here & I'm off to Xclock-land now !![/B][/U]

---

### Post by TheFu on 2021-04-08
There are lots of tiny X/apps that have been around for 30+ yrs, perhaps 40 yrs.  Some of them have terrible GUIs - the original xcalc sucked.  It only accepted mouse-clicks, not numbers entered via keyboard.
On our HUGE 17inch monitors, we'd need xeyes to find the cursor on the monochrome SPARC monitors.

Non-GUI people seem to understand the underlying OS more than the point-n-click sort. Perhaps we don't waste time hunting for GUIs when there are plenty of non-GUI solutions already on the system?  The AT&T guys in the early 1970s had pretty much the same needs we did, so they created all sorts of extremely efficient solutions.  When X/Windows came along about a decade later, they moved many of those tiny apps into the GUI world.  Check out gnubiff to get a visual clue about email from IMAP servers. In the olden days, we used xbiff to monitor our ~/.Mail/ directory for new messages.  For calendaring, we used 'plan' which people on the same subnet could set because all our HOMEs were NFS mounted to each workstation.  We'd leave the .plan file read-only for everyone, so they knew when we could and couldn't attend meetings.

My point is, there are lots of older programs that solved problems in 50-100 lines of code that today someone would waste 5000+ lines and a 900MB library to solve because they want a pretty GUI.

Ubuntu isn't always the best tool for the job, but it is pretty good for most people, most of the time.

---

### Post by hagrid3 on 2021-04-09
Thanks Again TheFu !!
I agree 100% with this based upon my experiences=>that *it is pretty good for most people, most of the time.*

_Regarding Xclock - I have tested it on my PC, and here is what has resulted:_
1 - Using the very clear info about it here=>
[https://www.x.org/releases/X11R7.6/doc/man/man1/xclock.1.xhtml](https://www.x.org/releases/X11R7.6/doc/man/man1/xclock.1.xhtml)

And this command:
xclock -digital -update 1 -brief

It delivers a ~1" square 24 hour clock that is about 1/2 title bar.

_These commands both fail & go right to its help screen:_
xclock -digital -update 1 -brief &#8722;twelve
xclock -digital -update 1 -brief &#8722;chime

So - unless there is a secret decoder ring which shows some tricks to make it a 12 hour digital clock that chimes somehow - (for me...) it too is a wash, sadly.

I may have to stay with the randomly vanishing Digital Clock 4 as it does most closely approach the notion of poking me with the passage of time !!

---

### Post by TheFu on 2021-04-09
> **hagrid3 said:**
> Thanks Again TheFu !!
I agree 100% with this based upon my experiences=>that *it is pretty good for most people, most of the time.*

_Regarding Xclock - I have tested it on my PC, and here is what has resulted:_
1 - Using the very clear info about it here=>
[https://www.x.org/releases/X11R7.6/doc/man/man1/xclock.1.xhtml](https://www.x.org/releases/X11R7.6/doc/man/man1/xclock.1.xhtml)

And this command:
xclock -digital -update 1 -brief

It delivers a ~1" square 24 hour clock that is about 1/2 title bar.

_These commands both fail & go right to its help screen:_
xclock -digital -update 1 -brief &#8722;twelve
xclock -digital -update 1 -brief &#8722;chime

So - unless there is a secret decoder ring which shows some tricks to make it a 12 hour digital clock that chimes somehow - (for me...) it too is a wash, sadly.

I may have to stay with the randomly vanishing Digital Clock 4 as it does most closely approach the notion of poking me with the passage of time !!

Rule #1 - use the manpages ON THE SYSTEM, not from the web.  The manpages on the system are for the exact version of the program installed, not some older or newer version that {whatever web search tool} found.

I tried both 
```
xclock -digital -update 1 -brief &#8722;twelve
xclock -digital -update 1 -brief &#8722;chime
```
And got the same.  That's because old X/Apps don't support '--' options.  That's a GNU thing and most of the old X/apps were written well before GNU.  However, 
```
xclock -digital -twelve 
```
works fine.  So does
```
xclock -digital  -brief -chime
```

BTW, I didn't see it initially either.

---

### Post by hagrid3 on 2021-04-09
**Wow, it is working as suggested, but...**
*Colour me blind ??*

Yep, I'm old & maybe visually challenged too & I cannot see the difference in this new info vs. the old ?!?
It does work & notably absent is the -update 1 part - so perhaps this is what you meant ??

_Compared with Digital Clock 4 it has some definite shortcomings, sadly:_
- The biggest being visual - it is not as nice to look at as a whole, but also ~70% of it is wasted space 
(That it MUST have a title bar, leading zero & just the small digits in a big whitespace is just silly);
- It has no way to use other than a default sound of some sort;
- It does not chime on the quarter hour.

If only _Digital Clock 4_ was still an active project and/or didn't vanish from the screen randomly !!!

_Back to what I had posted to start with, for a second before I run off for the day_=>
I still have no idea why cron stuff will not work on my own PC - vs. that it so easily does on another with the same OS & version.

If I could get a chime set up to work successfully via cron, then I could use a digital clock only app that is mute & both functions would be covered as I would prefer.

[COLOR=#800080][SIZE=5]Sincerest Thanks for being so helpful here all the same !![/SIZE][/COLOR]

---

### Post by TheFu on 2021-04-09
> **hagrid3 said:**
> **Wow, it is working as suggested, but...**
*Colour me blind ??*

Yep, I'm old & maybe visually challenged too & I cannot see the difference in this new info vs. the old ?!?
It does work & notably absent is the -update 1 part - so perhaps this is what you meant ??
No.  
```
-digital  != --digital
```
```
-twelve  != --twelve
```

> **hagrid3 said:**
> 
_Compared with Digital Clock 4 it has some definite shortcomings, sadly:_
- The biggest being visual - it is not as nice to look at as a whole, but also ~70% of it is wasted space 
(That it MUST have a title bar, leading zero & just the small digits in a big whitespace is just silly);
- It has no way to use other than a default sound of some sort;
- It does not chime on the quarter hour.
That's a WM thing. Pick a better WM. On my WM, there's no WM extras - no title bar, no wasted space.

> **hagrid3 said:**
> I still have no idea why cron stuff will not work on my own PC - vs. that it so easily does on another with the same OS & version.
It shouldn't work.  cron doesn't run with a full session, so none of the programs running under it will either.  Cron runs ever when nobody is logged in, so there isn't an audio server and certainly isn't any X/server.  GUI programs don't work without an X/server. The audio server issue can be blamed on pulseaudio, which has never been stable, IME.  Many decades ago, the Linux guys decided that when someone logs into the console, that they'd add that userid to the plugdev and audio groups (I think that's what they do).  But if we ssh in remotely, then we aren't in those groups unless we go out of our way to make it so.  This prevents someone remote from playing audio files as a joke to someone sitting on the computer.  I always add myself to the "audio" and "plugdev" groups on all my systems so I can remotely play audio from anywhere.

> **hagrid3 said:**
> If I could get a chime set up to work successfully via cron, then I could use a digital clock only app that is mute & both functions would be covered as I would prefer.
Find a tiny wav file with the chime you want to play.  Add the userid you want playing the file to the audio group manually, then try to play the file over an ssh connection.  If it refuses, check that the DISPLAY environment variable is set to :0.   Or you could setup an mpd server with a single file in the playlist and have any mpd-client program tell it to play every 15 minutes.

I think that will work.

As for the clock, put the xclock with the settings you like into the startup programs for when you login.  For font control, use the ~/.Xresources file.  This is how we did theming in the 1990s.

---

### Post by hagrid3 on 2021-04-11
**[SIZE=5]Thanks for the help !![/SIZE]**

_Here is how things have worked out for me as a very complete & final version of what I have been after all along:_
- Gave up totally on Xclock as I am perfectly content with my WM otherwise & have zero desire to change it;
- Will soon remove Digital Clock 4 as its vanishing act has been way too tiresome;
- I found & re-used a very plain, simple w32 app for making the on-screen clock & it runs flawlessly via WINE & stays 100% visible, always;
- Cron now works 100% fine via Zeit, which also has a quick & easy way to make alarms using sound files & MPV;
- The saytime script is also working as I prefer it to via Zeit at 0, 15, 45 & 30 minute intervals.

What the deal may be with the logged-on vs. not logged on I could not verify for myself, and right now, being logged on as always, the things I've added to cron are all working just as they should, and, oddly enough;
*At another PC that is also always logged on, cron works fine there via Gnome-Schedule for a daily backup task.*

_If anyone else wants it - Zeit is here:_
[https://github.com/loimu/zeit](https://github.com/loimu/zeit)

_It installed in 1 minute, thusly:_
> sudo add-apt-repository ppa:blaze/main
sudo apt update
sudo apt install zeit

This has been a good learning for me with some definite oddities, and now I'm quite satisfied as to the results of peersisting at it.

[SIZE=5]Thanks Again.[/SIZE]

---

