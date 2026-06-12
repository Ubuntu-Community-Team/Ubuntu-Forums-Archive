---
title: "problem installing latest Flash player on Firefox"
date: 2014-12-24
forum: General Help
---

### Post by argonvegell on 2014-12-24
I installed 'pepperflashplugin-nonfree' from the Ubuntu Software Center, then I installed Fresh Player Plugin, using this code:

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin

Next, I tested it out, I loaded Firefox, I tried YouTube, and it worked great, however, as I read further, a major problem with using 'pepperflashplugin-nonfree', there is no autoupdate, which is a security problem, and the only way to get the latest flash player plus updates is to install Google Chrome.

First, I uninstalled 'pepperflashplugin-nonfree' and Fresh Player Plugin, then I downloaded Google Chrome from here ([http://www.google.com/chrome/](http://www.google.com/chrome/)) and installed it, then I reinstalled Fresh Player Plugin, I tested it out, I tried YouTube, I'm getting this error:

Failed to load "libpepflashplayer.so".

---

### Post by 3246251196 on 2014-12-24
I always just install a package called "flashplugin-installer". It simply seems to work off the bat and I have been doing it for years. I use firefox exclusively.

I guess I would suggest

```
dpkg -l | grep pepper

```
see the status of it in the first column, expecting it to be: ii

anyway, I would apt-get autoremove pepperflashplugin-nonfree chrome-browser (or whatever the package name is)

and just ```
apt-get install flashplugin-installer
```.

oh and then use -r (or -R cannot rem) to remove the ppa and apt-get update.

But I guess ```
dpkg -l | grep pepper
``` or ```
dpkg -l | grep -v ^ii
``` would be useful

---

### Post by argonvegell on 2014-12-24
Thanks for the reply, unforunately 'flashplugin-installer' installs the 11.0 version of Flash and I need the 16.0 version, which is included with Google Chrome, the site that I go to doesn't run well with the 11.0 version, sorry.  And I don't want to use Google Chrome, the interface doesn't work will with me.

---

### Post by 3246251196 on 2014-12-24
Okay, argon. I guess this is where my help ends. I find flash to be the most bloated nonsense ever created and messing about with it even more so - so long as I can just stream video I am not entirely bothered, so selfishly flashplugin-installer does the trick for me. Hopefully someone else can help; I did do some superficial searching but I did not turn up anything useful.

---

### Post by argonvegell on 2014-12-24
> **3246251196 said:**
> Okay, argon. I guess this is where my help ends. I find flash to be the most bloated nonsense ever created and messing about with it even more so - so long as I can just stream video I am not entirely bothered, so selfishly flashplugin-installer does the trick for me. Hopefully someone else can help; I did do some superficial searching but I did not turn up anything useful.

Thanks for trying to help, I really appreciate it, the site that's having problems with flashplugin-installer is Blip.tv, the videos on there are running so slowly with the 11.0 version, I'm a big fan of the Nostalgia Critic and in order to get his latest reviews, I have to watch it on Blip.tv, well, I hope someone can help me with this, if not, I'll have to settle with just YouTube, which works well with 11.0, but for how long?

Merry Christmas!

---

### Post by Impavidus on 2014-12-24
There is Flash 11.2 that works on Firefox (flashplugin-installer). Youtube works fine on it and will continue to work fine on Flash 11.2, especially as Youtube is moving away from Flash. I rarely have to enable the flash player to watch a video on Youtube, most is html5 nowadays.

The pepper flash plugin (pepperflashplugin-nonfree) does not work on Firefox, but it does work on Chrome and Chromium. It's build-in in Chrome and can be installed via the repositories for Chromium. The installer actually downloads Chrome and draws the plugin out of the package. It doesn't seem to update automatically, but reinstalling the package just upgraded flash from 15 to 16. I rarely use Flash.

---

### Post by Holger_Gehrke on 2014-12-24
Simple workaround: use the "User Agent Switcher" Add-on in Firefox to make blip.tv believe you're on an iPhone. That will make blip.tv send the video as HTML5 video without using flash at all. You might have to right-klick on the player and choose "Play" and/or "Show Controls" from the menu. Works for me, it's unwatchable using flash on my netbook but works just fine if I masquerade as an iPhone.

Just don't forget to switch back afterwards, otherwise pages will look quite different from what you're used to.

---

### Post by Yellow Pasque on 2014-12-25
> **argonvegell said:**
> Thanks for the reply, unforunately 'flashplugin-installer' installs the 11.0 version of Flash and I need the 16.0 version, which is included with Google Chrome, the site that I go to doesn't run well with the 11.0 version, sorry.  And I don't want to use Google Chrome, the interface doesn't work will with me.

You're not going to get Flash 16 for Firefox unless you hack around with something called pipelight (google it). Flash 11 is the end of the line for Firefox Flash in Linux.

You can use Chrome, which has Flash built in, or the open source chromium browser (in conjuction with pepperflashplugin-nonfree package to make Chrome's Flash usable with chromium).

>  It doesn't seem to update automatically, 
For update, you can just run:
```
sudo update-pepperflashplugin-nonfree --install
```

---

### Post by Bucky Ball on 2014-12-25
Yea. Pepperflash has nothing to do with Firefox. It is for Chromium. It rips the flash from Chrome and actually downloads parts of Chrome to do it.

As mentioned, if you want to use the latest flash with Firefox, the only alternative is to experiment with Pipelight or install Chromium (in the repositories) and then pepperflashplugin-nonfree, or install Chrome. Have no idea where fresh player fits into all this. No experience with it.

* PS: just did a bit of research and 'Fresh Player Plugin is a new (alpha!) wrapper', which is why I've never heard of it. Guess it might be a bit hit or miss at this point. Maybe you can help out by experimenting and seeing where you can go with it. Good luck. ;)

---

### Post by argonvegell on 2014-12-25
> **Impavidus said:**
> The pepper flash plugin  (pepperflashplugin-nonfree) does not work on Firefox, but it does work  on Chrome and Chromium. It's build-in in Chrome and can be installed via  the repositories for Chromium. The installer actually downloads Chrome  and draws the plugin out of the package. It doesn't seem to update  automatically, but reinstalling the package just upgraded flash from 15  to 16. I rarely use Flash.
> **Temüjin said:**
> You're not going to get Flash 16 for Firefox unless you hack around with something called pipelight (google it). Flash 11 is the end of the line for Firefox Flash in Linux.

You can use Chrome, which has Flash built in, or the open source chromium browser (in conjuction with pepperflashplugin-nonfree package to make Chrome's Flash usable with chromium).

For update, you can just run:
```
sudo update-pepperflashplugin-nonfree --install
```

The hack I'm using is Fresh Player Plugin, which is a wrapper for the PPAPI to make it compatible with Firefox, as I said in my first post, I was successful in using Fresh Player Plugin to use Flash Player 16 in Firefox, by installing 'pepperflashplugin-nonfree', however, the issue I read on Debian forums, is that pepperflashplugin-nonfree doesn't have autoupdate, one must manually check if updates, which is a security problem, the only way to get autoupdated flash player is to install Google Chrome and using Fresh Player Plugin so Firefox can use Pepper Flash Plugin from Chrome, as described here: [http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

However, I get this error:

Failed to load "libpepflashplayer.so".

Are there any good PPAs for pepperflashplugin?

---

### Post by Yellow Pasque on 2014-12-25
> is that pepperflashplugin-nonfree doesn't have autoupdate
Like I said, you can use the update-pepperflashplugin-nonfree command. If you want it to be automatic, run it as a cron job (I'd recommend every Wednesday since Adobe usually releases Flash updates on Tuesdays).

---

### Post by monkeybrain20122 on 2014-12-25
I think you can remove pepper-flashplugin-nonfree, completely remove freshplayer, install Chrome and then reinstall freshplayer from webupd8.  It will then upgrade as soon as chrome's flash get upgraded.

I don't use it in Ubuntu so I can't tell you the exact detail. There may be some configurations you need to change manually, I compiled it from source in Fedora.

---

### Post by monkeybrain20122 on 2014-12-25
> **Temüjin said:**
> Like I said, you can use the update-pepperflashplugin-nonfree command. If you want it to be automatic, run it as a cron job (I'd recommend every Wednesday since Adobe usually releases Flash updates on Tuesdays).

I can be wrong, but I think the package in the repo is not being updated, just as Chromium from the repo isn't. So not sure how running upgrade and corn job on the user's end makes any sense.

---

### Post by flaymond on 2014-12-25
Do you ever tried this? -

```
 
sudo apt-get install ubuntu-restricted-extras 
```

It solve my problem whenever I install a flavor without Flash.

---

### Post by Yellow Pasque on 2014-12-25
> **monkeybrain20122 said:**
> I can be wrong, but I think the package in the repo is not being updated

It's not. That's why you have to manually run the upgrade script. I run Debian and do it every time new pepper Flash is released.

---

### Post by argonvegell on 2014-12-25
> **InterProg said:**
> Do you ever tried this? -

```
 
sudo apt-get install ubuntu-restricted-extras 
```

It solve my problem whenever I install a flavor without Flash.

Yes, installing 'xubuntu-restricted extras' is the first thing I install whenever I install or reinstall Xubuntu, however, the Flash Player in the restricted extras is the 11.2 version of Flash, I need 16.0 version, which comes installed in Google Chrome.

> **monkeybrain20122 said:**
> I think you can remove  pepper-flashplugin-nonfree, completely remove freshplayer, install  Chrome and then reinstall freshplayer from webupd8.  It will then  upgrade as soon as chrome's flash get upgraded.

I don't use it in Ubuntu so I can't tell you the exact detail. There may  be some configurations you need to change manually, I compiled it from  source in Fedora.

Yes, I've done this, I installed Google Chrome, then installed Fresh Player from webup8, but I still get the message 'Failed to load "libpepflashplayer.so"' whenever I view a video on YouTube or Blip.tv.

Fresh Player Plugin seems to only work with 'pepperflashplugin-nonfree'

> **Temüjin said:**
> Like I said, you can use the  update-pepperflashplugin-nonfree command. If you want it to be  automatic, run it as a cron job (I'd recommend every Wednesday since  Adobe usually releases Flash updates on Tuesdays).

Thanks, how do I do this?

---

### Post by argonvegell on 2014-12-25
It seems to me Fresh Player Plugin cannot see or recognize Google Chrome's Pepper Flash Player, but it does recognize the 'pepperflashplugin-nonfree' though, but I want to use Google Chrome's Pepper Flash Player because it automatically updates.

---

### Post by Yellow Pasque on 2014-12-25
I'm not familiar with Fresh Player and I don't use Chrome (other than extracting its Flash plugin to use with chromium).

---

### Post by argonvegell on 2014-12-25
> **Temüjin said:**
> I'm not familiar with Fresh Player and I don't use Chrome (other than extracting its Flash plugin to use with chromium).

Fresh Player Plugin is a wrapper for PPAPI so Linux users can use Pepper Flash Player on Firefox, instead of only on Chrome and Chromium, anyway, I've resigned to the fact that using Google Chrome's built-in Flash Player isn't getting me anywhere, so I've decided to stick with what works.

I've installed pepperflashplugin-nonfree and then installed Fresh Player Plugin, and it works like a charm, I'm now watching the Nostalgia Critic on Blip.tv with Flash Player 16.0.0.235 on Firefox.

My problem, how do I schedule weekly updates for pepperflashplugin-nonfree? I have Gnome Schedule installed, how do I use it?

---

### Post by Yellow Pasque on 2014-12-26
I have no idea about gnome schedule. All you need is a little script in /etc/cron.daily
```
cd /etc/cron.daily
sudo vim pepperflash  (or use 'gksu gedit' if you don't like 'sudo vim')
sudo chmod 755 pepperflash
```

This is what the pepperflash file should contain:
```
#!/bin/sh

update-pepperflashplugin-nonfree --install --quiet
```

That's it. The drawback is that the updater lags behind Flash releases because it's tied to Chrome releases, and it also depends on the Debian maintainer to update his website ( [https://people.debian.org/~bartm/pepperflashplugin-nonfree/](https://people.debian.org/~bartm/pepperflashplugin-nonfree/) ). Sometimes, I have to use the --unverifed and/or --beta flags to get pepper flash update in a timely manner. Unfortunately, it's not as easy to automate Flash update like it is in Windows.

---

### Post by argonvegell on 2014-12-26
> **Temüjin said:**
> I have no idea about gnome schedule. All you need is a little script in /etc/cron.daily
```
cd /etc/cron.daily
sudo vim pepperflash  (or use 'gksu gedit' if you don't like 'sudo vim')
sudo chmod 755 pepperflash
```

This is what the pepperflash file should contain:
```
#!/bin/sh

update-pepperflashplugin-nonfree --install --quiet
```

That's it. The drawback is that the updater lags behind Flash releases  because it's tied to Chrome releases, and it also depends on the Debian  maintainer to update his website ( [https://people.debian.org/~bartm/pepperflashplugin-nonfree/]("https://people.debian.org/%7Ebartm/pepperflashplugin-nonfree/")  ). Sometimes, I have to use the --unverifed and/or --beta flags to get  pepper flash update in a timely manner. Unfortunately, it's not as easy  to automate Flash update like it is in Windows.

Okay thanks! So this will update pepperflashplugin-nonfree on every Wednesday?

---

### Post by Yellow Pasque on 2014-12-26
Actually, it will do a quick check every day if you put it in cron.daily, which is probably a better idea than checking every Wednesday because of the unpredictability I mentioned in the last post.

---

### Post by argonvegell on 2014-12-26
> **Temüjin said:**
> Actually, it will do a quick check every day if you put it in cron.daily, which is probably a better idea than checking every Wednesday because of the unpredictability I mentioned in the last post.

Thank you Temujin for the assistance, I'll be checking if Pepper Flash Player was updated when Chrome releases a new version, thanks again, I really appreciate it!

Happy New Years!

---

### Post by Elfy on 2014-12-26
> **argonvegell said:**
> ...
Failed to load "libpepflashplayer.so".

Check for that in the firefox plugins.

> Once it's built, copy libfreshwrapper-pepperflash.so from the build folder to the browser plugin directory. For Firefox, copy it to /usr/lib/mozilla/plugins/

[http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html](http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html)

---

### Post by argonvegell on 2014-12-26
> **Elfy said:**
> Check for that in the firefox plugins.



[http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html](http://www.webupd8.org/2014/05/fresh-player-plugin-pepper-flash.html)

I'm not good at compiling, that's why I used a WebUpd8 PPA to install Fresh Player Plugin as described here: [http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html](http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html)

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin

As I said in my previous post, Fresh Player Plugin works with 'pepperflashplugin-nonfree' from the Ubuntu Software Center.

---

