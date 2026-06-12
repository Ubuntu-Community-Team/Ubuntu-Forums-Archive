---
title: "screwed up firefox fonts"
date: 2007-06-05
forum: General Help
---

### Post by Digitallysick on 2007-06-05
I think i have ms fonts for firefox now? everything is tiny and hard to see, how i can fix the firefox fonts back to default? They arent matching my system theme

---

### Post by Pragmatist on 2007-06-05
Does this help?
[http://ubuntuforums.org/showthread.php?t=431056&page=2](http://ubuntuforums.org/showthread.php?t=431056&page=2)

---

### Post by pyros on 2007-06-05
first thing I would try would be to see if the problem is in your firefox profile.
try closing all firefox windows and running ```
 firefox -profilemanager 
``` Create a new profile and see if that one has the same problem with fonts.

---

### Post by BoneSaw on 2007-06-05
try ctrl+alt+scroll wheel.

it can make fonts larger and smaller in firefox.

---

### Post by Digitallysick on 2007-06-05
thanks, i know how to make them smaller /larger, but when i go into my options and change the font, it stays the same

---

### Post by pyros on 2007-06-05
> **Digitallysick said:**
> thanks, i know how to make them smaller /larger, but when i go into my options and change the font, it stays the same
Then go to the advanced font properties, and increase the minimum font size. **If that still doesn't work**, uncheck "allow pages to use their own fonts instead of my selections above"

---

### Post by Digitallysick on 2007-06-05
its not working, i can change the font, and uncheck what you told me, but the font stays the same

---

### Post by pyros on 2007-06-05
> **Digitallysick said:**
> its not working, i can change the font, and uncheck what you told me, but the font stays the same

have you reloaded the page in question?

---

### Post by Digitallysick on 2007-06-05
yes, when i uncheck it, then it starts to use firefoxs selected font now, whats the default firefox fonts and sizes? I dont even see Sans in the list anymore =(

---

### Post by pyros on 2007-06-05
> **Digitallysick said:**
> yes, when i uncheck it, then it starts to use firefoxs selected font now, whats the default firefox fonts and sizes? I dont even see Sans in the list anymore =(

I'm not sure what the defaults are, but try freesans, or if you have them, dejavu sans or bitstream vera sans. I belive the default proportional size is 16, and the default monospaced size is 12

---

### Post by christhemonkey on 2007-06-05
On my firefox, the default font selected is...... Nothing.

The blank entry at the top of the list of fonts.
Dont know if that helps or not.


Maybe it doesnt enforce a default font after that so j ust uses system themes? Who knows...

---

### Post by pyros on 2007-06-05
> **christhemonkey said:**
> On my firefox, the default font selected is...... Nothing.
The blank entry at the top of the list of fonts.
Dont know if that helps or not.


on the advanced window, or the firefox preferences window, in the content tab?

---

### Post by christhemonkey on 2007-06-05
In the content tab, i dont see anything about fonts in the advanced tab...

---

### Post by pyros on 2007-06-05
Tell you what, since I have you here, open a new tab and type about:config in the address, at the top of the page that loads, there should be an entry field labled "filter" type font for the filter, and let me know if any of the preference names show up as bold.

---

### Post by pyros on 2007-06-05
> **christhemonkey said:**
> In the content tab, i dont see anything about fonts in the advanced tab...

no, there should be an advanced button next to the fonts and colors in the content tab.

---

### Post by christhemonkey on 2007-06-05
Ah ok , i see what you mean now.

Ok, the defaults there are:

Fonts for: *Western*

Proportional: *Serif*, Size: [I]16
[/I]Serif: *Serif*
Sans-serif: *sans-serif*
Monospace: *monospace*, Size:* 12*
Minimum font size: *None*

*[tick!]* Allow pages to choose their own fonts, instead of my selections above.

---

### Post by christhemonkey on 2007-06-05
Ok and things that turn up bold after being filtered for font in about:config:

**font.name.serif.x-western **

Thats it. All rest are just normal.

---

### Post by pyros on 2007-06-05
> **christhemonkey said:**
> Ah ok , i see what you mean now.

Ok, the defaults there are:

Fonts for: *Western*

Proportional: *Serif*, Size: [I]16
[/I]Serif: *Serif*
Sans-serif: *sans-serif*
Monospace: *monospace*, Size:* 12*
Minimum font size: *None*

*[tick!]* Allow pages to choose their own fonts, instead of my selections above.

you could try setting a minimum font size, somewhere around 16, and unchecking allow pages to choose...

or, if you really just want it back to the defaults, follow the instructions in the post above, and tell me all of the preferences that are in bold.

---

### Post by pyros on 2007-06-05
ok, the default for that is Helvetica

have you installed anything before this happened like the mscorefonts package?

---

### Post by christhemonkey on 2007-06-05
My firefox is fine!

I was just trying to help the OP by letting him/her know what the defaults were/are.
and see my last post for the bold preferences.

---

### Post by pyros on 2007-06-05
> **christhemonkey said:**
> My firefox is fine!

I was just trying to help the OP by letting him/her know what the defaults were/are.
and see my last post for the bold preferences.

Dough! brains? scattered covered and chunked please.

---

### Post by christhemonkey on 2007-06-05
My apologies! Was just trying to help!

---

### Post by pyros on 2007-06-05
> **christhemonkey said:**
> My apologies! Was just trying to help!
Heh, that wasn't in reference to you, but to myself, I should know better than to get on the forums too early in the morning or too late at night.

---

### Post by Digitallysick on 2007-06-05
yeah i installed the ms core fonts and thats how i screwed mine up, i followed the guide to remove them and revert back but ff is still the same , i followed this and now my fonts suck

 How to improve sub-pixel font rendering for Feisty

This will dramatically improve the appearance of fonts with respect to the default Ubuntu install. The patched libraries are built against Freetype 2.3.x (not currently in feisty) and include David Turner's sub-pixel rendering patches.

    * For i386 add the following to /etc/apt/sources.list 

deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts
deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts

    * For AMD64/EMT add the following to /etc/apt/sources.list 

deb [http://ubuntu.moshen.de/falcon](http://ubuntu.moshen.de/falcon) feisty experimental
deb-src [http://ubuntu.moshen.de/falcon](http://ubuntu.moshen.de/falcon) feisty experimental

    * Packages you're about to upgrade are libfreetype6, libcairo2 and libxft2 

sudo aptitude update
sudo aptitude install libfreetype6 libcairo2 libxft2

    * After the install, you may want reconfigure font settings. The following settings work well: Native, Automatic, No bitmapped fonts. 

sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig

    * If you get errors about missing gpg key 

gpg --keyserver subkeys.pgp.net --recv-keys 937215FF
gpg --export --armor 937215FF | sudo apt-key add -

    * GPG key to repository for AMD64/EMT packages 

wget [http://ubuntu.moshen.de/2F306651.gpg](http://ubuntu.moshen.de/2F306651.gpg) -O- | sudo apt-key add -

---

### Post by pyros on 2007-06-05
this might sound stupid, but have you restarted since you removed them?

---

### Post by FrancoNero on 2007-08-27
I have a question slightly related to everything above....

is there a "reset to defaults" option in firefox somehow? i mean reset ALL settings an options to how they would be when i'd install firefox fresh. without deleting all my bookmarks, plugins, passwords etc of course

---

