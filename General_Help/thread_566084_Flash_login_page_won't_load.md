---
title: "Flash login page won't load"
date: 2007-10-03
forum: General Help
---

### Post by ricardisimo on 2007-10-03
[This page]("https://www.citicards.com/cards/wv/home.do") won't load for me in any browser; not FF (default), Opera, Galeon, Epiphany nor Kazehakase. More precisely, it loads up for a split-second and then disappears. One exception: Konqueror worked fine while I was on Kubuntu for a day-and-a-half.

It's somewhat important since I have an account there, and I'd like to be able to check my finances. Any help would be greatly appreciated.

I'm now on Ubuntu Feisty, and all of the above browsers are latest repository versions.

---

### Post by superyounan1 on 2007-10-03
i get the same thing, it must be a flash plugin bug.

I use the site, i get around the problem by hitting "stop" on my browser before the flash file is done downloading.

you could also disable the flash plugin, i think if you dig around in browser options, it might be in there some where, but the stop trick works for me. Once you're inside, there aren't any issues.

Plus if you have kde still installed but you're in gnome, you can still run qt apps like konquerer

---

### Post by ricardisimo on 2007-10-03
I'd noticed the stop thing, but I'm normally not quick enough. Plus, I feel a bit silly having to do that; I wish it would just work. I'll try disabling java for that screen. Thanks.

P.S. - Nope. No luck. It doesn't load at all with java-scripts disabled. Any other ideas?

---

### Post by superyounan1 on 2007-10-04
disable your flash plugin, not java or javascript.

I guess my computer is slow, I usually have enough time to stop it before the swf file loads. 

If there is now straight forward way to disable it, maybe you can move or rename the plugin files temporarily, but that too feels silly doesn't it?

find instances of the flash plugin:
```
locate libflashplayer.so
```

you might get 5 or more entries. Its not clear which one is being used (i'm assuming you're using firefox). Try moving each one to its respective parent directory, for example:

making sure your browser is not running,
```

cd /usr/lib/firefox/plugins
sudo mv libflashplayer.so ../

```

and repeat for the other instances of the file, you're bind to hit the right one being used by firefox.

Doing this everytime you want to log into yoru citibank account is ridiculous, but you can make a script that will do this for you, then run your browser, and when you're done use another script to put it all back where it belongs.


OR just reboot to windows if you have it, or create a windows virtual machine and boot it up when you need.

---

### Post by ricardisimo on 2007-10-05
Would you know, by any chance, why Konqueror (with some degree of irony, given the Gnome vs. KDE debate) "just works" when the other browsers just won't? Thanks.

---

### Post by ricardisimo on 2007-12-05
I found a kind of solution, but not a definitive one. I broke down and installed Automatix2 on my Feisty system, and had it, in turn, either install or reinstall all of the pertinent flash/java/mozilla plugins and related paraphernalia. The page still doesn't look right - clearly I'm supposed to see something rather than nothing - but eventually whatever stupid crap they're trying to sell me goes away and the login reappears. It's kind of ideal, the more I think of it... I'm just skipping over the marketing BS.

My guess is that I was either missing some component or other, or perhaps everything just needed to be installed in a certain order or fashion. Give it a shot.

---

### Post by superyounan1 on 2007-12-15
The worst thing you can do to a ubuntu system is to install Automatix!! I've heard dozens upon dozens of horror stories of how it messes with yoru dependencies and potentially screws up you ability to install new software, but particularly to upgrade your system.

Do a couple google searches on this subject, and when you're convinced, get rid of Automatix

I found another solution for this problem: My computers are still slow enough where I can hit the stop button as the page loads and prevent the flash content from loading in time to mask out the entire page, but a more elegant solution to do the same thing is to install the "**FLASHBLOCK**" firefox extension. Flashblock prevents all flash content that isn't in your customizable  whitelist from displaying, instead you get a little play button, if you choose to do so you can click it and the flash loads.

The result is ideal for this problem on citibank's site, the flash won't load, no more content masking. Try it out and post back your results, i think you'll be happy

---

### Post by superyounan1 on 2007-12-15
> **ricardisimo said:**
> My guess is that I was either missing some component or other, or perhaps everything just needed to be installed in a certain order or fashion. Give it a shot.

again, you're not "missing" anything, its just a bug with the linux version of the Flash plugin where the default Z-index of swf files is on top of the HTML on the page (I'm assuming since thats exactly the observed behavior). On the citi site, there is a large flash file that loads and has a lot of white space that is supposed to sit underneath the html content, but because of this big, it sits on top and covers everything.

There is nothing wrong with your computer or the website, its a bug with the flash plugin care of Adobe / Macromedia. Until its fixed, we have to deal with it.

In the mean time, use the Flashblock extension for firefox i recommended above

---

