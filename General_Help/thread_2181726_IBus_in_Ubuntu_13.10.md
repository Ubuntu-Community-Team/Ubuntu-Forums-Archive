---
title: "IBus in Ubuntu 13.10"
date: 2013-10-18
forum: General Help
---

### Post by hanjiexi on 2013-10-18
IBus is severely broken in just-released Ubuntu 13.10.

First of all, where is the IBus Preferences program? I mean I can launch it manually via terminal, but it's useless. Trying to launch the Preferences for Pinyin does nothing and gives me this error:
```
Traceback (most recent call last):
  File "main.py", line 24, in <module>
    import ibus
ImportError: No module named ibus
```

I have read on this forum to go looking for a "Region & Language" menu. There is none on Ubuntu 13.10. Yes I went to Language Support and installed Chinese and made sure Keyboard input method system was set to IBus; yes I launched im-config and rebooted; yes I opened Text Entry Settings and added Pinyin as a source. Yeah that doesn't help. If I switch to IBus via the shortcut, it still shows "En". If I click "En" and manully switch it to Pinyin, yes Pinyin input does work, but not the way I have it set. In both ibus-setup and Text Entry it's set to give me a VERTICAL list of candidates, and I'm consistently getting a horizontal list. And because I can't get to Pinyin Preferences, I can't change any Pinyin settings, which I absolutely NEED to be able to do, otherwise I'm just stuck with whatever the default settings are for Pinyin input.

It was even worse in Kubuntu beta 2 (haven't tried official release), where merely installing Chinese input changed the language in some of the applications without my knowledge or consent. Imagine a beginning Chinese student trying to read the output of apt-get in Chinese localization!

And look at this: [https://help.ubuntu.com/community/ibus](https://help.ubuntu.com/community/ibus)
> Go to System->Preferences->Ibus Preferences.

System > Preferences > Ibus Preferences? That sounds like it was written 5 years ago and never updated.

---

### Post by hanjiexi on 2013-10-18
lol guess what. The "Language Support" panel in System Settings *just vanished* into thin air. I simply don't have one anymore. Oh and now Super+Space switches the "En" icon in the panel up top to "Pi" (short for Pinyin), but um, the icon for Pinyin is gone. It's supposed to be a Chinese character, not the letters "Pi". And candidates don't show up anymore when I type in Chinese. It just puts characters there that I'm not able to control except by guessing.

---

### Post by borischan on 2013-10-18
You are not alone!! I can no longer input Japanese after upgrade to 13.10....

---

### Post by tripp98 on 2013-10-18
Im in english but what happens when you type language in dash ?

---

### Post by ping-wu on 2013-10-18
Indeed, IBus is **TOTALLY** screwed up.  Over the several versions in the past, the quality of ibus was always a concern, and experiences of regression (some very serious, but never as bad as in 13.10) abound!  For some reason, its developers have a tendendy to make drastic changes that had completely thrown me off.  For those of us whose life depends on a reliable and consistent way to input Chinese characters, I am finally saying: Enough is enough!

I strongly urge those of you who are in a similar situation as mine to completely abandon ibus.  There is a much better alternative that is widely used in China: fcitx.  If you use pinyin, I would also suggest you to use sogoupinyin &#65288;&#25628;&#29399;&#25340;&#38899;&#65289;, this is better than any pinyin method that I have used.

To install fcitx-sogoupinyin, you will need to add a ppa:

sudo add-apt-repository ppa:fcitx-team/nightly

sudo apt-get update

sudo apt-get install fcitx-sogoupinyin

You can also safely--for technical and operational reasons--remove ibus:

sudo apt-get remove ibus

Indeed, if you have a need for the Chinese language, I also strongly suggest that, instead of the "regular" Ubuntu, you install UbuntuKylin, which is developed specifically for Chinese users.  One of the best things about UbuntuKylin is that its developers have taken great pains to make sure that it is seamlessly compatible with Ubuntu.  English is my primary language, but I have no problem using UbuntuKylin in my daily work routine.

---

### Post by ZZZZA on 2013-10-19
I have the same problem. Before I use Ubuntu 13.04 on my Thinkpad and Ibus used to work just fine. Now, after Ubuntu update to 13.10, Ibus is basically not functional! I seriously doubt that this can be called a "UPDATE".

I really regret to have changed to Ubuntu system now.

---

### Post by hanjiexi on 2013-10-19
Another guy reporting the issues I had with the Text Entry system: [http://ubuntuforums.org/showthread.php?t=2181487&p=12820921#post12820921](http://ubuntuforums.org/showthread.php?t=2181487&p=12820921#post12820921)
> Beautiful Icon for Language Switching!  TERRIBLE FUNCTIONALITY.  Korean  input does not work.  Icon might swtich to KO, but it produces no Hangul  characters!  Suggestions?

BTW, I got Hangul to work through ibus-setup from command line; however,  the input does not matter what the language indicator says.  This is  such a basic function that I cannot believe that it doesn't work!!!

Yeah, I switched to UbuntuKylin to get proper Chinese input with fcitx -- a program I've had trouble with in the past on KDE, but it seems to work fine here. It was a bit confusing at first, until I realized that changing the keyboard (via Text Entry) does NOT change your input method. You only need ONE keyboard, e.g., English. Then you go to the fcitx menu and add Google Pinyin or whatever, switch with Ctrl+Space. I'll give sogoupinyin a try, too.

Unfortunately, this does not solve the more general IBus issues which affects everyone who isn't using it for Chinese, like Korean and Japanese users. I think it is partially a regression with IBus itself -- on my Slackware system, the 1.4.x versions are the last versions of IBus that are straightforward to install. Nobody seems to want to use anything from the 1.5.x series (which Ubuntu uses), because so much is changed and broken.

And it is also an issue with the Language and Text Entry settings in Ubuntu 13.10. They decided to change things, but apparently they didn't...finish in time?

**I strongly urge Ubuntu developers** (if they're reading this) to do the following:
[LIST=1]
[*]Revert to IBus 1.4.2. It is still the most widely downloaded version (see here: [http://code.google.com/p/ibus/downloads/list](http://code.google.com/p/ibus/downloads/list) ) and it has the best support. I don't think 1.5 is ready yet.
[*]Revert your changes to the Text Entry/Language settings and just handle input the same way default GNOME handles it. (I tested GNOME 3 in Ubuntu and it works fine there.) If you want to make changes to how Ubuntu's input is organized, push those changes to a later release. Don't release half-baked changes.
[/LIST]

---

### Post by hanjiexi on 2013-10-19
By the way, if anyone else here tried installing UbuntuKylin but used a non-Chinese language for the installer (since my Chinese isn't good enough yet to read the system partitioner), before input can work on the desktop you have to go into Language Support and add Chinese. Until you do that, Chinese input in Kylin will not be fully functional.

---

### Post by jhodowany on 2013-11-09
I have to agree with ping-wu above. I installed fcitx. I was wary of linking to the nightly updates, since I wanted some stability. I used fcitx from the saucy repositories, and haven't looked back. It was very easy to install. Here is a nice link for setup tips. [https://wiki.archlinux.org/index.php/fcitx](https://wiki.archlinux.org/index.php/fcitx)  Good luck All.

---

### Post by rg-pigl on 2013-12-28
iBus works for me for Chinese.  1/ install the Chinese language pack via system settings-language.  2/ my iBus icon on menu bar is a square with "En".  click on this icon and choose "text entry settings".  then search and add your language by clicking "+".

question: which pinyin system is best ?

---

