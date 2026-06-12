---
title: "After install and config of Chinese and Japanese input method (iBus), nothing works."
date: 2014-06-18
forum: General Help
---

### Post by Cbhihe on 2014-06-18
Hello,
I installed  the panel language switch icon to show 4 keyborad configuration for input. 
I use iBus and 2 of my languages are Chinese and Japanese.
I still     cannot write anything that is not based on roman characters.
    
    I run a recent version of Trusty Tahr (Ubuntu 14.04 LTS) with every     package up to date.
    
    Here is what my im-config file says:*Current configuration for the input method:** * Active configuration: ibus (normally missing)** * Automatic configuration: ibus (normally ibus or fcitx or         uim)** * Number of valid choices: 2 (normally 1)**The configuration set by im-config is activated by         re-starting X.**Explicit selection is not required to enable the automatic         configuration, if the active one is default/auto/cjkv/missing.**  Available input methods: ibus xim**Unless you really need them all, please make sure to         install only one input method tool.*
        
        After configuring it I did reboot my machine* as recommended by Pinyin Joe's excellent how-to:      [http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm](http://www.pinyinjoe.com/linux/ubuntu-12-chinese-setup.htm)*
    When I choose Chinese (Pinyin) for input the correct keyboard icon does appear with my choice.
Pinyin input Preferences are available. Everything on the GUI seems to be perfectly     functional.
    
    However whenever I try to actually write something in Chinese, in     any application including on the desktop - e.g. to rename a folder -     , I do get to enter Pinyin, iBus offers possible hanzi phonetic      translations and when I select one, all I get is:

     [Invalid UTF-8]&#12288;&#65288;&#65308;-     in this case I tried to write "ni hao" in simplified Chinese).
    
I also noticed that I have little in the way of  Chinese fonts on     my systems in spite of an apparently faultless install.
I saw no way to download those fonts on the       web pages I visited.  I also have not tried any repo for       lack of info on them.
      
      Has somebody experieince with that ? Any help welcome !
-ced

---

### Post by davidvandoren on 2014-06-18
I had a problem with IBUS the other day not offering me any input options on Flashback desktop.

Open the Terminal and type ```
ibus-setup
```

Added my input methods which then were available through the ibus interface.

---

### Post by Cbhihe on 2014-06-18
Thank you for the input davidvandoren. 
I had access to the setup via the gui already. I nevertheless went through the moves of launching ibus-setup from a term shell... and got to what I had already available through the GUI.
Nothing has changed. It stumps me. 
I must be missing something basic because even the correct selection of characters is shown by iBus when I type the pinyin "guanyu wo de diannao de wenti ..." in Pinyin mode. 
Only when I try to select the correct hanzi in the selection of characters, do I get one instance of "[Invalid UTF-8]" for each character I select with the space bar.

Could not that  simply be UTF-8 config related ? Or Chinese font related ? Or both ?
-ced

---

### Post by Cbhihe on 2014-06-18
I am not bumping this thread, I just made the Japanese Input method work by switchin from the plane Japanese to the "Japanese Anthy" input method available in Ibus.
&#19990;&#30028;&#20170;&#26085;&#12399;&#12288;or &#12495;&#12525;&#12539;&#12431;&#12539;&#12523;&#12489;&#12290; ("Hello world" loosely translated.). 
Still nothing going on the Chinese front though. 
Any help welcome.
-ced

---

### Post by Cbhihe on 2014-06-18
I am really not bumbing it...., but following what I did for Japanese and discarding Chinese (Pinyin) as the logical choice for an Ubuntu noob such as myself, and choosing instead "Chinese (SunPinyin)" in the Text Entry method selection window yields: &#25105;&#30340;&#38382;&#39064;&#19981;&#32764;&#32780;&#39134;. ("My problem suddenly vanished ."), although I don't like the clumsy method of selecting characters out the SunPinyin selection.
-ced
[closed]

---

