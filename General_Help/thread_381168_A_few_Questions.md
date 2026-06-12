---
title: "A few Questions"
date: 2007-03-10
forum: General Help
---

### Post by Eminem on 2007-03-10
I just got Ubuntu to work now here is a few questions that I need answered.

1. How do I get extensions for Firefox and can I upgrade between different versions of Firefox?
2. How do I get Flash Player for Firefox?
3. How do I install new programs like Beryl?
4. Where can I locate software for Ubuntu Dapper Drake and how can I install them?
5. How do I change my screen resolution because when I go to System > Preferences > Screen Resolution, the highest is 1024 by 768 when my Display is supposed to be 1280 by 1024?

Any help would be greatly appreciated.

---

### Post by strabes on 2007-03-10
1) addons.mozilla.org. Edgy and Feisty come with firefox 2.0.

2) Go to Applications > Accessories > Terminal, and type "sudo apt-get install flashplugin-nonfree" and type in your password.
It will download and install the mozilla flash 9 plugin I believe. Restart firefox and you should be good to go. If not, you can always go directly to adobe's website at [http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4) and follow the instructions there.

3) If you have an unsupported ATI video card installing beryl is a BIG pain. However, if you have an nvidia card or a supported ATI card it is a breeze. However first you should install your video card drivers. See #5.

4) If you don't want to deal with the command line, you can go to Applications > Add/Remove to find lots of software to download and install. Programs don't install like they do in windows. Also check this page out for additional help: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

5) [https://help.ubuntu.com/community/Video](https://help.ubuntu.com/community/Video)
Go there and follow the instructions pertaining to your video card. When you're done you should restart X with Ctrl+Alt+Backspace and everything should work correctly.

There are a lot of things that new users should check out. Look through the links in my signature, especially the "How to help yourself" one.

---

### Post by bettlebrox on 2007-03-10
Check out the UbuntuGuide for Dapper:

[http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

At this point, I'd suggest upgrading to Edgy and a new release is due in a few months.

Luck.

---

### Post by Eminem on 2007-03-10
How can I play .mp3s?

---

### Post by strabes on 2007-03-10
ubuntu doesn't ship with ANY proprietary software. mp3 is a proprietary codec. you can play mp3s though, and it's pretty easy: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

