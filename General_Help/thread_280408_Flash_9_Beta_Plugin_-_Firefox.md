---
title: "Flash 9 Beta Plugin - Firefox"
date: 2006-10-19
forum: General Help
---

### Post by mjpatey on 2006-10-19
I just downloaded the Flash 9 Beta plugin, and installed it to the "home/[my-username]/.mozilla" directory.  Unfortunately, while this gives me Flash 9 in the Mozilla browser, it's not working in Firefox.

On a hunch, I went to the /Firefox directory located within /.mozilla, and created a "Plugins" folder that I just copied from the /.mozilla directory.  When I restarted Firefox, still no Flash 9.

In both Firefox and Mozilla, "about: plugins" shows two Flash plugins installed, versions 7 and 9.  This is despite the fact that when I moved the new version 9 file into the directory, I renamed the old one with a ".old" extension, which I assume would render it null and void.

In any case, Mozilla seems fine with having 2 versions installed (I'm still not sure why they're both there, though), and Firefox, though it lists both versions in about: plugins, will only play Flash 7 files.

I hope my ramblings make sense to someone... if you have any idea how to get this working in Firefox, I'd greatly appreciate it!

Thanks,

-Mark

---

### Post by skymt on 2006-10-19
Why not just delete Flash 7? Tacking .old to the end won't do anything, Firefox doesn't care what the extension is named.

---

### Post by hikaricore on 2006-10-19
Where exactly did you find the flash 9 beta for linux?  Last I heard it would still be 2 week (roflmfao at the very least *rolls eyes*)  until it's coming out. O.o

---

### Post by mrashley on 2006-10-19
The Flash9 Beta can be downloaded here

[http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)

To backup my old flash9 I did this

```
cd /usr/lib/flashplugin-nonfree
mv libflashplayer.so old_libflashplayer.so
```

To get the new flash7 everywhere I did this

```

wget http://www.adobe.com/go/fp9_update_b1_installer_linuxplugin
tar xvfz FP9_plugin_beta_101806.tar.gz
cd flash-player-plugin-9.0.21.55/
mv libflashplayer.so /usr/lib/flashplugin-nonfree

```

Just restart firefox and suddenly youtube is well synced and with good framerates.
 :)

---

### Post by hikaricore on 2006-10-19
i could just about hug you right now, if i knew who the hell you are and were anywhere near you :)

p.s. post this on the HowTo forums asap if someone didn't already beat you to it :)  they've been dyin for it

---

### Post by mjpatey on 2006-10-19
I just figured out how to make it work!  I had originally copied the new libflashplayer.so file into the .mozilla/plugins directory, and what I should have done was copy it into the following directory:

/usr/lib/flashplugin-nonfree/

Now that I've done that, Flash 8 and 9 files play just fine!

Woohoo!  I can delete my Wine IE now.  :cool: 

-Mark

---

### Post by damu on 2006-10-19
if you don't want to use command line to get flash9, I would suggest to use [automatix2]("http://getautomatix.com/wiki/index.php?title=Installation")
It did the job for me ;)

---

### Post by flyingbrass on 2006-10-19
I removed the flashplugin-nonfree package, then copied the new libflashplayer.so to /usr/lib/mozilla-firefox/plugins

For Opera, I copied it to /usr/lib/opera/plugins/

Works great so far in both.

---

### Post by drpaul on 2006-10-19
I have both Ubuntu and Mozilla versions of Firefox installed. I changed every instance of libflashplayer.so [there were several] to old7-libflashplayer.so

I moved the new libflashplayer.so to /usr/lib/flashplugin-nonfree and created links to it in all of the former directories that held libflashplayer.so

When I start up Firefox it is still using version 7 in about:plugins

Any ideas what went wrong?

TIA

Paul

---

### Post by beerorkid on 2006-10-19
I just updated automatix2 and installed it.
It is so fricking strange to watch youtube in sync.  It almost seems wrong ;)

can't wait to see how buggy it is.

---

### Post by Tares on 2006-10-19
> **beerorkid said:**
> I just updated automatix2 and installed it.
It is so fricking strange to watch youtube in sync.  It almost seems wrong ;)

can't wait to see how buggy it is.

haha, you got that right !! ;-)

for the topic, I've changed .so file in /opt/flash32 and /usr/lib/firefox/plugins and works perfectly ^^

---

### Post by wolf202 on 2006-10-19
anyone get this to work with swiftfox I can only get it to work with firefox!

-wolf

---

### Post by matrooswolf on 2006-10-19
Wow! Works fine!  

Finally I can watch Borat fully syncd!  
Chenqui!

---

### Post by sktfeelsdapper on 2006-10-19
So far I haven't had any problems with the new flash.
As for buggy, everythings been moving really smooth on my computer. Even the standalone player's been up to par.

Beta my behind, don't change a thing fellas!

---

### Post by raul_ on 2006-10-19
wolf202

go to the path where u have your firefox plugins installed (probably /usr/lib/mozilla-firefox/plugins) and copy all the files to /opt/swiftfox/plugins

It worked for me

---

### Post by raul_ on 2006-10-19
But now image freezes and no sound =P

---

### Post by flankker on 2006-10-19
i can get it set up in firefox and opera, but flash 9 is really buggy for me. youtube videos only play for 3 seconds and things like that, so its back to flash 7 for me for now :(

---

### Post by mjpatey on 2006-10-19
I think I'll try Automatix2... My manual install works well for some sites, but YouTube and Google Video both just give me about a second of video playback, followed by nothing.

-Mark

---

### Post by beerorkid on 2006-10-19
[http://digg.com/linux_unix/HOWTO_Install_Flash9_BETA_in_Ubuntu_Linux](http://digg.com/linux_unix/HOWTO_Install_Flash9_BETA_in_Ubuntu_Linux)

has another howto for ubuntu

I had one youtube muck up but the flash banners up top were still working.  Strange.

---

### Post by raul_ on 2006-10-19
Exactly the same error i have

---

### Post by raul_ on 2006-10-19
mjpatey and flankker, do u use amsn? try watching youtube without amsn running (if u use) . Here i was after a log in (a la windows) and flash 9 working fine (wow the lips and the music sync) and then i opened amsn and it froze...

EDIT: Only when i open during playback. If i refresh the page it plays again.

DOUBLE EDIT: Ok it seems that it works fine if u have nothin whatsoever running =P

---

### Post by mjpatey on 2006-10-19
I don't use AMSN.  To follow up, I installed Automatix 2, selected the Macromedia Flash package, and voila!  Everything works fine!

A minor word of caution... when following the instructions on Automatix's site, make sure you're following the instructions for the right release!  I know it sounds like a no-brainer, but I just started following the first set of instructions listed, and they were for Edgy (I run Dapper).  No dire consequences, but I wasted my own time a little.

Yay, Flash!  And yay, Automatix!

---

### Post by Treviño on 2006-10-19
Excuse me, but... Does the flash player 9 for linux support for trasparency?

EDIT: sorry... It seems it does: [http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_14201](http://www.adobe.com/cfusion/knowledgebase/index.cfm?id=tn_14201) ;)
I posted becouse I saw that [here]("http://www.kirupa.com/developer/mx/transparency.htm") it wasn't working...

---

### Post by soze on 2006-10-19
Has anybody tried to use it to play the videos on [www.scifi.com](www.scifi.com) ?

What's happening for me is that the "commerical" at the beginning of the video will play, and then nothing else.

---

### Post by flyingbrass on 2006-10-19
> **soze said:**
> Has anybody tried to use it to play the videos on [www.scifi.com](www.scifi.com) ?

What's happening for me is that the "commerical" at the beginning of the video will play, and then nothing else.
Same here in Firefox.  Opera doesn't even make it that far.

---

### Post by beerorkid on 2006-10-19
heck it crashes ff for me.  Lucky I have learned to use session manager.

I got no video at all from the commercial.

I had used automatix2 at work and all was good.  But tonight at home there is no flash player install in automatix2 current version or something.

i did the download from adobe and follow the read me super simple way here at home.  All flash 9 cept the sci fi link work flawlessly.

---

### Post by sherl0k on 2006-10-19
same here, no sound at all. no idea what's causing it...

---

### Post by soze on 2006-10-19
> **beerorkid said:**
> ...  All flash 9 cept the sci fi link work flawlessly.

That's great.
After all this waiting, the ONE THING I needed it for does not work!

Oh well, I can always hope it gets fixed in the final.

---

### Post by Treviño on 2006-10-19
A good for your firefox (and not only :D) could be this: [http://www.agentprovocateur.com/miss_x/shadows.php](http://www.agentprovocateur.com/miss_x/shadows.php)

Anyway this make my firefox to use really much CPU... :o

---

### Post by beerorkid on 2006-10-19
ahh apparently the new automatix is so good that it only lists what you do not have installed, and if you do it will warn.  I uninstalled flash with it then reinstalled.

Doubt it made a difference, but I am kinda partial to automatix and know it worked.

---

### Post by rudlavibizon on 2006-10-20
I installed flash9 thru automatix2, and it works fine in mozilla but not firefox. I checked in usr/lib/firefox/plugins and libflashplayer.so is there. I tried uninstalling and reinstalling flash7 and now it doesnt work too. Does anyone have a solution for this?

---

### Post by raul_ on 2006-10-20
Probably u didn't install Flash 7 correctly
[URL="http://www.ubuntuforums.org/showthread.php?t=268838"]
http://www.ubuntuforums.org/showthread.php?t=268838[/URL]

---

### Post by Ramses de Norre on 2006-10-20
> **mjpatey said:**
> My manual install works well for some sites, but YouTube and Google Video both just give me about a second of video playback, followed by nothing.

-Mark

I have got the exact same thing..

---

### Post by arnieboy on 2006-10-20
> **beerorkid said:**
> ahh apparently the new automatix is so good that it only lists what you do not have installed, and if you do it will warn.  I uninstalled flash with it then reinstalled.

Doubt it made a difference, but I am kinda partial to automatix and know it worked.

yeah uninstalling and reinstalling will give u the latest version of an app BOK.. in this case flash 9

---

