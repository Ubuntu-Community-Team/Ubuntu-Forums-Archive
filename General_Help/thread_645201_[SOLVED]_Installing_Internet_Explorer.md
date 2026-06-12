---
title: "[SOLVED] Installing Internet Explorer"
date: 2007-12-19
forum: General Help
---

### Post by keith1 on 2007-12-19
Ok - I've read some previous posts, but don't see my particular problem mentioned. So... if I don't give enough information about my problem, please let me know.

I'm using 7.10 and FF, but I need to have IE also. I have Wine and Cabextract already installed, but I repeatedly encounter a problem. When I try to install IE4linux - I get to the point where it freezes my desktop and I have to manually turn off/ reboot my computer. It "freezes at " creating wine prefix".

The two items I installed from synaptic package manager are - wine and wine- dev. I even tried a reinstall just to be sure.

I don't know if this info will help but - when I click on the wine icon in the panel it brings up four items- 
 - programs ( notepad )
 - browse C:/ drive
 - configure wine
 - uninstall wine software

If I click on the "browse" one, nothing happens. If I click on one of the other three my system "freezes" again. I'm so............ lost here. What have I done wrong?

Thank you,

Keith

---

### Post by Rusty023 on 2007-12-19
Well, I know little about Linux, but this might apply to you.

Why do you need IE? If it's for IE-only sites, get the IE-tab add-on for FireFox. Works a charm.

---

### Post by keith1 on 2007-12-20
Rusty 023 - The reason I need IE is that on another board I frequent, I can't use the rich text format in Firefox. I believe that IE tab for Firefox is for Windows only.

What I need is just how to install IE on my Ubuntu system. Thank you for taking time to reply.

Keith

---

### Post by TeaSwigger on 2007-12-20
Hello, 

Yeah I have to use IE too, only for web design reasons. Wouldn't use it otherwise. 

Is this the WINE from the repositories, and are you letting it install it or are you doing anything custom? If not, am I correct in assuming that this is the first thing you're installing with WINE? If so, may I suggest that you first install something else that works easily with WINE - say, keynote [http://sourceforge.net/projects/keynote/](http://sourceforge.net/projects/keynote/) - just so that you can determine WINE is functional and to give you some familiarity with it.

When you first install WINE, prior to installing anything, it may be a good idea (and can't hurt) to do the following: 

In a terminal, enter:

```
wineprefixcreate
```

Wait for it to return you to the prompt. Then enter:

```
winecfg
```

which should produce the WINE configuration GUI. In it, check the drives and desktop integration tabs, ensuring they're set as you'd like. I like to allow WINE to install its own "Internet Explorer" first for sake of compatibility with some progs; it uses a Gecko (think Mozilla Firefox) browser. To do this, enter the following in a terminal:

```
wine iexplore http://www.google.com
```

You should be prompted by a popup to let it install its browser, just say ok and it'll do it for you. Then try installing Keynote or something simple and ensure it's operational. 

Alrighty with all that out of the way and WINE definitely working, then try the IEs4Linux installation. For launching it, you should be able to use the provided icon, but (having lost that icon) I use the following form, for example:

```
env WINEPREFIX="/home/MYUSER/.ies4linux/ie6" WINEDEBUG=-all wine "/home/MYUSER/.ies4linux/ie6/drive_c/Program Files/Internet Explorer/IEXPLORE.EXE" "http://www.dogpile.com"
```

The first part is a sort of context for it, the debug bit disables all debugging output and might make it a tad faster, the next is what it seems to prefer being launched with and the last is the url you want launched.

WINE can be a pain, but it's pulling off quite a complicated task. It's amazing it works at all really. Post back if you still have trouble. Good luck!

---

### Post by TeaSwigger on 2007-12-20
Oh Keith, by the way have you tried Opera? It's my vote for best browser out there, certainly the fastest full-featured browser, but alas it's not open-source so I still keep Firefox. It does however work great on Linux and might work on that forum. Nothing to lose trying. Just a thought.

---

### Post by keith1 on 2007-12-20
Ok, I'll try to keep my reply in some reasonable order. First of all, I'm not really sure where the initial installation of Wine came from. However, I did a reinstall from repositories ( wine and wine-dev ) and still had the "freeze" problem.I even tried to uninstall it and start over, but even clicking on the uninstall wine software option I get "freeze-up".

I downloaded Keynote and have a folder on my desktop called Keynote_Source. when I open it there are too many folders in there for me to understand. 

So.. in the meantime I went to your next step and put wineprefixcreate in a terminal and everything froze up in about 10 seconds.had to turn off the tower and reboot once again. I really think the problem is something to do with my original Wine installation, but I can't delete it to get a fresh start.

As far as Opera, I tried it a couple of years ago, but for some reason I didn't like it then. Too many whistles and bells if I remember correctly. Anyhow I've seen some posts that say Using Opera to access that board ( Myway ) results in question marks all through posts.I may give it another try after this is resolved.

I'm so lost right now, I hope I've provided the information you need. Just let me know.

Thank you,    Keiht

---

### Post by TeaSwigger on 2007-12-20
Yeah I know, I get completely befuddled on a regular basis lol... the two things I had the most trouble with are networking and WINE. Don't worry you'll get it. Hang in there.

> **keith1 said:**
> Ok, I'll try to keep my reply in some reasonable order. First of all, I'm not really sure where the initial installation of Wine came from. However, I did a reinstall from repositories ( wine and wine-dev ) and still had the "freeze" problem.I even tried to uninstall it and start over, but even clicking on the uninstall wine software option I get "freeze-up".

Hm. Are you experiencing any other problems? Specifically sluggishness or graphics issues. Like the screen isn't perfectly aligned etc... point being, some freezing and other troubles have been caused by graphics driver issues, and WINE seems to like finding any weak links like that I guess.

Regardless, unfortunately when you uninstall WINE, in Windows tradition, it leaves a lot behind. You have to manually remove the stuff if you want a clean reinstall. The main thing seems to be that you delete WINE's folder in your user folder. It's a hidden folder, that'd usually be /home/YOUR USER/.wine. So completely remove WINE:

```
sudo apt-get remove --purge wine wine-dev
```

then delete that .wine folder mentioned above to be more certain you're starting fresh this time. 

To clarify since they don't, the WINE uninstaller is to uninstall Windows programs installed in WINE, not to uninstall WINE itself. For that use the code above and don't forget that .wine folder.

> I downloaded Keynote and have a folder on my desktop called Keynote_Source. when I open it there are too many folders in there for me to understand.

Not the source, it's the Windows installer you want. The kntsetup_165.exe one. Should've specified, sorry. After WINE's set up and you've grabbed kntsetup_165.exe, let's say you have it downloaded to the Desktop folder, the best way to install it, like most stuff you'd install in WINE, is to enter this in a terminal, in the directory the kntsetup_165.exe is in, so that it looks like this:

```
myname@myPC: ~/Desktop$ wine kntsetup_165.exe
```

It should start the tyical Windows program installer. You finish and can start keynote right away:

```
env WINEPREFIX="/home/YOUR USER/.wine" WINEDEBUG=-all wine "c:\Program Files\KeyNote\keynote.exe"
```

And it should start up ok. If so, proceed with IEs4Linux.

If not beh... back to trouble shooting, starting with video driver stuff.

> So.. in the meantime I went to your next step and put wineprefixcreate in a terminal and everything froze up in about 10 seconds.had to turn off the tower and reboot once again. I really think the problem is something to do with my original Wine installation, but I can't delete it to get a fresh start.

Gracious. Make a note by the way. To unfreeze, it's safer to try this: restart X:

hold ctrl and alt keys and then press backspace. If this does not take you back to the login, there may be other ways but all I know is ye olde "Raising Skinny Elephants Is Utterly Boring" routine; if your system seems totally stuck, this is the routine:

Press these series of keys:
```
Alt+SysRq+r 
Alt+SysRq+s
Alt+SysRq+e
Alt+SysRq+i
Alt+SysRq+u
Alt+SysRq+b
```

As it was explained to me:

>  The SysRq = print screen. Use the LEFT Alt key. The r stands for put keyboard in raw mode. The s for sync the disk. The e for terminate all processes. The i for kill all processes. The u for remount all filesystems read only. The b for reboot the system. Use it as a procedure only if all else fails!!

Better than turning off power, restarting and crossing fingers. By the by... How you holding up? ;) 

> As far as Opera, I tried it a couple of years ago, but for some reason I didn't like it then. Too many whistles and bells if I remember correctly. Anyhow I've seen some posts that say Using Opera to access that board ( Myway ) results in question marks all through posts.I may give it another try after this is resolved.

I've only tried it recently. Yes it has too much clutter but I turn it off or ignore that stuff. I launch it with:
```
/usr/bin/opera -geometry 800x600 -nosession -nomail -notrayicon -disableinputmethods
```
since that seems fastest on my setup for my needs. Anyway if you try it, the question mark thing may (or may not, I dunno) be related to the choice of encoding on their end or yours. That you can fool with in View > Encoding. You could also try Dillo, Links2, Kazehekase free, for some examples, but there's definitely compromises invoved on those.

And it might sound funny, heck it does in fact, but if that board works in Firefox on Windows, you could even try Firefox for Windows in WINE, if it's some kind of rich text thing. Never heard of that problem though, only JavaScript & Flash issues.

> I'm so lost right now, I hope I've provided the information you need. Just let me know.

Dunno lol we'll see.

> Thank you,    Keiht

Misspelling one's own name... hm better take a break from the ol' cyber-box then ;) Good luck.

---

### Post by chips24 on 2007-12-20
> **Rusty023 said:**
> Well, I know little about Linux, but this might apply to you.

Why do you need IE? If it's for IE-only sites, get the IE-tab add-on for FireFox. Works a charm.

th IE tab is only for windows.

---

### Post by gmh on 2007-12-20
You could try this. Go to [http://chrispederick.com/work/user-agent-switcher/](http://chrispederick.com/work/user-agent-switcher/) and install to your add ons in Firefox.
It works with almost every IE only site I have come across including most of the internet banking sites.

Cheers

---

### Post by keith1 on 2007-12-21
A lot of great information to work with there - thank you. I'll get a fresh start on it when I get home from work this evening and let you know how I fare.

Keith

---

### Post by keith1 on 2007-12-21
I got rid of wine per your terminal command, checked hidden files in my home folder where I deleted all files starting with .wine. Did a fresh install of wine in synaptic package manager and nothings changed. Seems like anything I enter, click on, or even look at! - that says wine  - freezes up. Must be something screwed up in my system, or it just doesn't support wine. I just plain give up for the evening - so tired of restarting. I'll be back in the morning with a fresh start.

Thanks,    Keith

---

### Post by keith1 on 2007-12-22
I opened TOP in a terminal so I could watch what was going on at the point of "freeze up" during the IE installation. I didn't get to see much, but here are a few of the stats at time of "freeze up".
CPU - 11.4% 

MEM - 450816 total
            445360 used

SWAP - 1317288 total
              32440  used.

Did I just run out of memory ? I'm not sure what to check next.

Thanks,     Keith

---

### Post by keith1 on 2007-12-23
I finally got it to work. In a Wine forum, I somehow managed to muddle my way through to a similar situation, and decided to try their two suggestions.
   first - use standard xfree86 drivers. installed them via synaptic package manager, but my system still locked up in 5-10 seconds.  
   secondly - try different versions of nvidia drivers. I installed these-
           -   nvidia-glx
           -   nvidia-glx-dev

 Then IE installed as smooth as silk. I don't understand the "what-or-why" of it , just that it worked.

Thanks to TeaSwigger for all the help, and a lot of great procedures to keep for reference. I also got an extra bonus going through this - i really needed Keynote also, which directions were given for.

Thanks to everyone for their help,

Keith

---

### Post by nbayiha on 2007-12-28
thanks this helped me

---

