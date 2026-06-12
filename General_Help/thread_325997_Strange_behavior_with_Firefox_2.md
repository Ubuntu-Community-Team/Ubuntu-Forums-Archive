---
title: "Strange behavior with Firefox 2"
date: 2006-12-26
forum: General Help
---

### Post by Winnie the Pooh on 2006-12-26
Hi everyone; lately my Firefox 2 browser has been acting strangely.
1. Whenever I try to close a tag or a window, all Firefox windows close.
2. Random crashes that don't seem to be website-specific.
3. I was just typing this when all of a sudden half of what I typed disappeared and I had to retype; what in the world?!
I've installed Flash 9 Beta 2 according to the instructions on the Macromedia website; videos that require Flash (YouTube, etc.) work perfectly (but, as I said, sometimes those websites crash, too, along with websites that don't require anything fancy).
I do have something installed for Firefox 2 to work in a Chinese Ubuntu (set the default language to Chinese) that I can't remember now.... And Firefox never had crashes before I installed it, but without it I cannot input Chinese nor make it work in a Chinese environment (and besides, I didn't have Flash before I installed it either).
Any help would be greatly appreciated! Thanks!!!

---

### Post by towsonu2003 on 2006-12-27
Try with a new profile:
Start Firefox using the command firefox -ProfileManager. You should now see the Profile Manager window.

Important note: From the Profile Manager you are also able to remove and rename profiles. Be very careful when deleting profiles, if you created the profile in an directory that already existed, the entire directory will be removed!

Click on the 'Create Profile...' button to start the 'Create Profile Wizard'. Click 'Next' and enter a descriptive name for the new profile. Click Finish to have Firefox create the new profile. You should now be taken back to the Profile Manager and the newly created profile should be listed. Select it and click 'Start Firefox'. Try to reproduce the bug with this new profile.

Note: you can go back to your own profile by starting Firefox using the command firefox -ProfileManager again, selecting your own profile, and clicking on 'Start Firefox'. 

if the bug isn't happening anymore, check if it still sees the plugins (go to about:plugins, if it list your plugins, the issue was with your profile / extensions.) if the bug remains, try with the older stable (!) flash plugin.

---

### Post by Winnie the Pooh on 2006-12-28
Hello and thanks for your help.... But where's the Firefox Profile Manager?:confused:  Do I just type in terminal "firefox -ProfileManager"? Because that only opens Firefox and brings me to my homepage, nothing special on it, nothing special in terminal either... Thanks again for your help!

---

### Post by Winnie the Pooh on 2006-12-28
Whoa it's acting really strangely now; I just opened a tab and thought I'd close it just to see what would happen, and nothing did - the tab closed without any mishaps. Huh! :confused: :D Would that be the end of my problems? So far I haven't had a crash yet (well I've opened Firefox for only 5 minutes).

---

### Post by towsonu2003 on 2006-12-28
> **Winnie the Pooh said:**
> Hello and thanks for your help.... But where's the Firefox Profile Manager?:confused:  Do I just type in terminal "firefox -ProfileManager"? Because that only opens Firefox and brings me to my homepage, nothing special on it, nothing special in terminal either... Thanks again for your help!

I don't know why that's happening... try: firefox --help and look for this text
> 
Start with Profile Manager

in my system, it gives:
```

~$ firefox --help
Usage: /opt/firefox/firefox-bin [ options ... ] [URL]
       where options include:

X11 options
        --display=DISPLAY               X display to use
        --sync          Make X calls synchronous
        --no-xshm               Don't use X shared memory extension
        --xim-preedit=STYLE
        --xim-status=STYLE
        --g-fatal-warnings              Make all warnings fatal

**Mozilla options**
        -height <value>         Set height of startup window to <value>.
        -h or -help             Print this message.
        -width <value>          Set width of startup window to <value>.
        -v or -version          Print Firefox version.
        -P <profile>            Start with <profile>.
        **-ProfileManager         Start with Profile Manager.**
        -UILocale <locale>              Start with <locale> resources as UI Locale.
        -contentLocale <locale>         Start with <locale> resources as content Locale.
        -safe-mode              Disables extensions and themes for this session.  -jsconsole           Open the Error console.
  -browser            Open a browser window.
Usage: firefox [-flags] [<url>]

```

it is possible that Ubuntu's Firefox may have different options...

---

### Post by Winnie the Pooh on 2006-12-29
I get the exact same thing as you did when I typed in firefox --help:
```
Winnie the Pooh@Winnie the Pooh-desktop:~$ firefox --help
Usage: /opt/firefox/firefox-bin [ options ... ] [URL]
       where options include:

X11 options
        --display=DISPLAY               X display to use
        --sync          Make X calls synchronous
        --no-xshm               Don't use X shared memory extension
        --xim-preedit=STYLE
        --xim-status=STYLE
        --g-fatal-warnings              Make all warnings fatal

Mozilla options
        -height <value>         Set height of startup window to <value>.
        -h or -help             Print this message.
        -width <value>          Set width of startup window to <value>.
        -v or -version          Print Firefox version.
        -P <profile>            Start with <profile>.
        -ProfileManager         Start with Profile Manager.
        -UILocale <locale>              Start with <locale> resources as UI Locale.
        -contentLocale <locale>         Start with <locale> resources as content Locale.
        -safe-mode              Disables extensions and themes for this session.  -jsconsole           Open the Error console.
  -browser            Open a browser window.
Usage: firefox [-flags] [<url>]

```
And this is what Firefox looks like after I type in firefox -ProfileManager (a screenshot):
I don't see anything that remotely looks like a Profile Manager....:confused:

---

### Post by towsonu2003 on 2006-12-30
must be witchcraft :) don;'t know why it isn;t working... anyway

than let's create the profile the old style :)
close firefox, ```

mv ~/.mozilla ~/Desktop/mozillaprofile
``` and restart firefox. if everything is okay now, look inside the mozillaprofile folder on your desktop for your bookmarks ;) it is named bookmarks.html

---

### Post by Winnie the Pooh on 2007-01-01
Hi; thanks for the reply; Profile Manager is currently working; I am getting fewer crashes but sometimes it's just not that stable; I think I'll try to get a stable version of Flash then. Thanks for your help! ;)

---

