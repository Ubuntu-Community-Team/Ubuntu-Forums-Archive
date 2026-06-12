---
title: "Korean Input SCIM ....how to?"
date: 2005-04-29
forum: General Help
---

### Post by mrbass on 2005-04-29
I really want to get Korean input (Japanese and Chinese are easy)...now I don't know Korean and search Korean but saw maybe 2 or 3 Ubuntu Korean users...blah.  Anyway yeah I can input currently but I don't think it's correct as it doesn't give you multiple choices.  I tried all five scim methods.  

Now gentoo or was it freebsd someone mentioned scim-hangul but that package doesn't exist in ubuntu universe repositories.  Here's my Korean notes.

hangul, imhangul, hanja, baekmuk-fonts, korean-romaja
gdick korean dictionary client..
now James Su (developer of scim) posted in July 2004 that someone was interested in porting the popular AMI input method but he didn't hear back.


language-pack-ko-base - translations for language Korean
language-pack-ko - translation updates for language Korean
ttf-baekmuk - Baekmuk series TrueType fonts
imhangul - A Hangul (Korean) input module for GTK+
language-support-ko - metapackage for Korean language support
mozilla-firefox-locale-ko - Mozilla Firefox Korean Language/Region Package
mozilla-locale-ko - Mozilla Korean Language/Region Package
nabi - A Korean X input method server plus imhangul status monitor
openoffice.org-help-ko - OpenOffice.org office suite help (Korean)
ttf-alee - A Lee's GPL'd Hangul truetype fonts
ttf-unfonts - Un series Korean TrueType fonts
openoffice.org-l10n-ko - Korean language package for OpenOffice.org
uim-utils - Utilities for uim
uim - Simple, secure, and flexible input method collection and library
uim-common - Common files for uim
uim-gtk2.0 - GTK+2.x immodule for uim
libuim0 - Simple, secure, and flexible input method collection and library
uim-xim - A bridge between uim and XIM

any ideas?
I'm trying to input these basic Korean characters
[http://www.mct.go.kr/hangeul/chapter1.html](http://www.mct.go.kr/hangeul/chapter1.html)

---

### Post by mrbass on 2005-05-03
scim-hangul is now availabe...finally

---

### Post by tiger338 on 2005-05-03
Don't you want to use Nabi?

it works for me..

    ** apt-get install nabi**

Add the following lines into ~/.gnomerc

   [B] export XMODIFIERS="@im=nabi"
    export GTK_IM_MODULE=xim[/B]

and Click System -> Preferences -> Sessions  from Tab menu "Startup Program"
insert program "/usr/bin/nabi"

restart gdm by "ALT+CTL+BACKSpace"

Is SCIM better than nabi?

---

### Post by mrbass on 2005-05-03
well it looks like you couldn't have NABI and SCIM running at the same time.  I don't know any Korean and only know a little bit of Japanese.  Could you tell me which one you prefer?

The SCIM uim Korean input methods are;
UIM-m17n-ko-hangul2
UIM-m17n-ko-romaja
UIM-romaja
UIM-hangul3
UIM-hangul2

Korean tables are:
3bul 2bul-shifted
3bul No-shift
Hangul
Hanja
3bul Yetgeul
3bul Final
3bul 390
2bul

If nabi is superior in most Korean's opinion then let's hope someone will port nabi or ami to scim.

Not sure be it looks like nabi is simliar to canna and kinput2 for Japanese input method.  It was a crude hack and didn't work in all applications.  Does nabi work in firefox and openoffice with no additional modifications?
To get an idea of what had to be modified for Japanese input just awhile ago before SCIM check out my Japanese input guide for mepis (it's dated obviously).
[http://mrbass.org/linux/mepis/japaneseinstall/](http://mrbass.org/linux/mepis/japaneseinstall/)
[http://mrbass.org/linux/mepis/japaneseinput/](http://mrbass.org/linux/mepis/japaneseinput/)

---

### Post by &#44032;&#49828;&#48148; on 2007-05-11
Ok,

In short:
**Have SCIM Manager installed**
**Install scim-tables-ko**
**Select your chosen input type in SCIM Global Setup**
**Restart Ubuntu**
Sounds easy right...

Let me try to make some sense for people wanting to type Korean.
First of all you need to install SCIM Manager. It handles the different keyboard layouts for you.
As I am the type of person with medium Windows experience I prefer a window to handle my installations...
Choose from Ubuntu Menu: System>Administration>Synaptic Package Manager
Press de find button and search for "SCIM". Once the list is populated find the package "scim" and mark it for installation.

Next, find "romaja" with search button.
(In case you didn't find it, go to Settings>Repositories on the tab "Ubuntu software" and make sure all items from "Downloadable Software" are marked)
You'll find scim-tables-ko. (Thank you to the persons who wrote it).
Mark the package for installation and press Apply. Get a bottle of soju from the cooler.

Now you will find in the top panel an icon that looks like a typewriter? on the left of you volume setting and date.(If not, restart Ubuntu now). Click with your rightmouse button on it and choose SCIM setup. From the dialogmenu choose IMEngine>Global Setup en find the language Korean:
Click on the triangle to see all input methods available. There are many methods but I suggest you make a choice between 2bul or Hangul Romaja

**Which one to choose?**
**2bul** (equivalent to dubeolsik I think) is your choice if you think you will ever want to be able to use a Korean keyboard when you get there... It is the most used version in Korea as far as I could find information on it. The downside is that it has no logical mapping with the romanised qwerty keyboard layout so you will have to learn a complete new letter/key combination. And you will have to use the shift key as well...
For example the roman letter a does not relate to the Korean letter &#12623;. Instead, you will find the Korean letter &#12623;under the roman letterkey k... There are different pictures for the keyboardmapping elsewhere in this forum but Googling on pictures with "dubeolsik" works quite nice too.

**Hangul Romaja** (which is the easiest choice for qwerty keyboard users) follows more or les the qwerty characters and the standards given by the Korean government. To me it seems a great solution as I have been able to type Hangul within a day or two.
For example, a = &#50500; (to get the &#12623; alone you have to press shift, but that doesn't happen to often) and yeong = &#50689;. Forcing a characterbreak when a third character is expected, just press the spacebar. Please check the site from the [[COLOR="Blue"]Korean Ministry of Culture[/COLOR]]("http://www.mct.go.kr:8080/english/K_about/Language04.html") to find which keyboard characters correspond to the Hangul characters.

Now you have made your choice (by selecting either of the two or both) you can accept the new setting with OK and now you have to restart Ubuntu to load te new settings. Open the bottle of soju and drink directly from the opening.

It might be confusing, but SCIM works already. But you will still not be able to select the new input method (keyboard language setting if you wish). For that you need to have a cursor place in a document, textfield or any field that brings up the cursor. Open a brower or textapplication en place the cursor somewhere. Now you can press the typewriter? in the top panel and you will be able to select the new input method!!!! (there might actually be two of them, one working... don't know why as I am a beginner as well). If you need to quickly shift betweent English and Korean Keyboard layout, you might consider checking the shortcuts in the SCIM settings (Front End>Global Setup, field Next Input Method).

And yeah... typing Koreans really feels great! So much more fun by changing characters on the fly.

I hope this instruction works out just as fine as it does for me.
In case you want to check your Korean writing, you might want to consider this [[COLOR="Blue"]translation site[/COLOR]]("http://www.kordut.be/wordsearch1.php").

Kind regards,

&#44032;&#49828;&#48148;

---

### Post by jrleek on 2007-09-15
Personally, I had much better luck with nabi that with SCIM on Ubuntu Edgy Eft.  I fought with SCIM for about 4 hours, and it never worked properly, the input was very odd.  For example, if I pressed the 'p' key I got '&#12621;'.  Rather than '&#12628;'. Perhaps my keyboard layout was set wrong?  I never figured it out.

Following the directions above, nabi worked right off, and I've never had a problem with it.  Although, the directions on nabi's website don't work for ubuntu.  So, YMMV.

---

### Post by Edaw 0 on 2007-10-14
SCIM's working great now; had to reboot twice for some reason, but it's  all good now.
&#44160;&#49324;&#54745;&#45768;&#45796;!

---

### Post by madtinkerer on 2007-10-15
Hi,

I've followed the instructions in the post above but I can't get it to work.  I have no input icon at the top of the screen despite installing all the needed software and rebooting.  I'm running ubuntu 7.10rc.  I'm not exactly sure how to troubleshoot the problem.  Any hints?

---

### Post by Edaw 0 on 2007-11-12
> **madtinkerer said:**
> Hi,

I've followed the instructions in the post above but I can't get it to work.  I have no input icon at the top of the screen despite installing all the needed software and rebooting.  I'm running ubuntu 7.10rc.  I'm not exactly sure how to troubleshoot the problem.  Any hints?
Try here: [http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

---

