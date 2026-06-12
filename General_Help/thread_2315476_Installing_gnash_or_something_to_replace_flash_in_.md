---
title: "Installing gnash? or something to replace flash in firefox"
date: 2016-02-29
forum: General Help
---

### Post by Jorhel on 2016-02-29
Hi,
I'm new to xubuntu I have installed trusty tahr 14.04 on an older computer that was so far functioning relatively well on XP, I jumped boat when could not use the wifi.
I had to relinquish chrome since it does not support 32 bit computers (just discovered that was blaming it on XP...) and firefox was working on the XP version with flash player, I suspect must have been an old one.
Now that I'm on xubuntu no video works, not a problem for me but my kids use a number of online games that require flash.
I tried installing Flash player from ubuntu software centre, result it crashes firefox every time a video is opened. I discovered since that it is because I don't have SSE2 on my machine.
I'm not keen on installing an older version of flash, so my reading so far have directed me to gnash.
Problem 1 I don't seem to be able to install it from the software installer.
Problem 2 I see a lot of posts saying it's crap but they are old.
I had found somebody explaining how to do it via the terminal but can find that post back again.
Would love a simple solution I have already spent hours trying to sort it out.
Otherwise love Linux should have done it long ago
Thanks

---

### Post by howefield on 2016-02-29
Have a look at this thread..

[http://ubuntuforums.org/showthread.php?t=2311381](http://ubuntuforums.org/showthread.php?t=2311381)

---

### Post by kc1di on 2016-02-29
Hello Jorhel and welcome to Ubuntu,

Firefox also stopped supporting flash on Linux sometime ago but their is a wrapper that can be used to install the latest flash.
it's called Freshplayer you can find out how to install it from [this page.]("http://www.pcworld.com/article/2993902/browsers/how-to-get-the-latest-version-of-flash-on-firefox-for-linux-after-adobes-abandonment.html") 
good Luck

---

### Post by SeijiSensei on 2016-02-29
Another option is to install [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") and run the [Windows version]("http://pipelight.net/cms/plugin-flash.html") of Flash.

---

### Post by Jorhel on 2016-02-29
> **SeijiSensei said:**
> Another option is to install [pipelight]("http://pipelight.net/cms/install/installation-ubuntu.html") and run the [Windows version]("http://pipelight.net/cms/plugin-flash.html") of Flash.

Hi thanks,
I tried that and went on the site friv.com at first it dowloded something wine pipelight related but when I tried to open a game I got the message does not look like you have flash player please click here to download it. sending me to the adobe page. 
Installed piplight and then did :
[COLOR=#0000ff]sudo pipelight-plugin --enable flash

The following modules require a license confirmation before they can be enabled:

[*] Adobe Flash Player
    By continuing the installation you agree that you've read and accepted the
    ADOBE Personal Computer Software License Agreement:
    [http://wwwimages.adobe.com/www.adobe.com/content/dam/Adobe/en/legal/licenses-terms/pdf/Flash%20Player_11.0.pdf](http://wwwimages.adobe.com/www.adobe.com/content/dam/Adobe/en/legal/licenses-terms/pdf/Flash%20Player_11.0.pdf)

    To find out more click here:
    [http://get.adobe.com/flashplayer](http://get.adobe.com/flashplayer)

Do you accept the 1 license(s) above? [Y/N] Y
Plugin flash is now enabled[/COLOR]

seems to have done what it should did I missed something?

I didn't try the other 2 solution suggested as the both mentioned chrome and pepper which I think wont be supported by my dinosaur of a computer...
thanks for the help.

---

### Post by SeijiSensei on 2016-03-01
Restart Firefox.  What do you see in Tools > Add-ons?  My version of Flash is 20.0.

If you don't see that entry for Flash, close Firefox, then run

```
sudo pipelight-plugin --create-mozilla-plugins 
```

Any better?

I opened friv.com and ran Flash when prompted.  (I have most everything set to "Ask to Activate" in the Add-ons list.)  It complained when I tried to play a Garfield game, but when I changed to "Always Activate," it played right away.

If you see both Flash 11.2 and Flash 20.0, you can either uninstall the Ubuntu plugin, or set it to "Never Activate."

---

### Post by Jorhel on 2016-03-03
Thanks that did the trick!!

---

