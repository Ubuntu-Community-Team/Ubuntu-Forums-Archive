---
title: "[SOLVED] What firefox plugin to fix this"
date: 2008-02-03
forum: General Help
---

### Post by paydaydaddy on 2008-02-03
The local newspaper website "www.kitsapsun.com" has added a couple of adds that render as white boxes covering parts of pages. This doesn't happen if viewing the page on my MS machine with either IE or FF. Makes me think that I am missing a FF plugin on my Ubuntu (7.10) machine. I tried viewing the page source but didn't come up with any clues. Anybody here have any ideas short of actually having the paper delivered to my house?:guitar:

---

### Post by ~LoKe on 2008-02-03
Flash plugin is a likely culprit.

---

### Post by edm1 on 2008-02-03
It renders perfectly for me. Type 'about:plugins' in the address bar in firefox and see what flash version you are using. Are you 64-bit?

---

### Post by paydaydaddy on 2008-02-03
32bit system. typed in 'about plugins' in the browser window and it takes me to:
[http://erfurtwiki.sourceforge.net/AboutPlugins](http://erfurtwiki.sourceforge.net/AboutPlugins)
I am guessing that this is not the expected result. I will modify and try again.

---

### Post by ~LoKe on 2008-02-03
It's...
about:plugins

---

### Post by PurposeOfReason on 2008-02-03
He meant like this
```
about:plugins
```

---

### Post by paydaydaddy on 2008-02-03
You mean I wasn't supposed to include the smiley? I got it. Here is a link to the results of 'about:plugins'
[http://homepages.tscnet.com/payday/plugins](http://homepages.tscnet.com/payday/plugins)

If I messed up the link, I will post again and just paste in the text.

---

### Post by paydaydaddy on 2008-02-03
bump

---

### Post by ~LoKe on 2008-02-03
Jesus, no, in the address bar, type:
> about:plugins
Exactly as you see it.

---

### Post by paydaydaddy on 2008-02-03
Please don't call me Jesus. That is my twin brother (pronounced 'hey suse'), and he is a real dick. You can call me Jose (pronounce 'hose A'). Anyway, I posted a link above to my current list of plugins. Synaptic shows that I have adobe flashplayer installed. Maybe some library to support? Lookin' for ideas here.

---

### Post by seventhc on 2008-02-03
I would dl this
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
then:
[LIST=1]
[*]Save the .tar.gz file to your desktop and wait for the file to download                   completely.
[*]Unpackage the file. A directory called install_flash_player_9_linux will be created.
[*]In terminal, navigate to this directory and type ./flashplayer-installer                   to run the installer. Click Enter. The installer will instruct                   you to shut down your browser(s).[/LIST]This is from their website.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by edm1 on 2008-02-03
> **paydaydaddy said:**
> You mean I wasn't supposed to include the smiley?

Ha. Bloody smileys! As already mentioned it's ```
about:plugins
```.

---

### Post by paydaydaddy on 2008-02-03
> **seventhc said:**
> I would dl this
[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
then:
[LIST=1]
[*]Save the .tar.gz file to your desktop and wait for the file to download                   completely.
[*]Unpackage the file. A directory called install_flash_player_9_linux will be created.
[*]In terminal, navigate to this directory and type ./flashplayer-installer                   to run the installer. Click Enter. The installer will instruct                   you to shut down your browser(s).[/LIST]This is from their website.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

I appreciate the suggestion but I will wait for additional suggestions before trying it because I already have ShockwaveFlash 9 installed. Any other ideas?

---

### Post by seventhc on 2008-02-03
Did you install it this way?? I have installed the flash plugins and I still have trouble unitil I install it the way I mentioned. I can view the page you talk about.
Regardless of that, it isn't going to hurt anything.

---

### Post by edm1 on 2008-02-03
I just checked the site again and this time i did get a big white ad that blocked the page. To get rid of it install the firefox extension 'Adblock plus' and block the site 'http://adsremote.scripps.com/'.

---

### Post by paydaydaddy on 2008-02-03
> **edm1 said:**
> I just checked the site again and this time i did get a big white ad that blocked the page. To get rid of it install the firefox extension 'Adblock plus' and block the site 'http://adsremote.scripps.com/'.

I did this and it worked perfectly. The ads were a minor irritation, but an irritation just the same. Thank you abundantly.

---

