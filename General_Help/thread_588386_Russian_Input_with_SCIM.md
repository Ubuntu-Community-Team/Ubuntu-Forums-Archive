---
title: "Russian Input with SCIM?"
date: 2007-10-23
forum: General Help
---

### Post by Kdar on 2007-10-23
Ok. I got SCIM to work. Now I am able to type in Japanese. and Change between English and Japanese input.

But how can I get the Russian input there? I mean normal Russian input. ( To type with Russian letters, not English) Since I have Russian letters on my keyboard printed.

---

### Post by Kdar on 2007-10-23
can some one help?

---

### Post by jenhsun on 2007-10-23
kdar,
1. The first thing is you have to add russian language support for ubuntu.
2. Open your SCIM gui input method setup from systems/preferences
3. Check and uncheck your russian input method as you want, and remember to setup your hotkey.

If SCIM doesn't show up in your up right panel, reboot your pc and try.
If you use Gutsy, you can just enable the support to input complex characters, it will automatic bring up the little keyboard icon in your panel.
However, it still have some bugs in Gutsy because sometimes it will freeze the keyboard.

:guitar:

---

### Post by jon.reeve on 2007-10-24
What I would do instead is, go to System -> Preferences -> Keyboard, choose the 'layouts' tab, click 'add,' choose 'Russia' from the layouts menu, add, close, then on your top panel (or wherever), you can put a keyboard layout switcher to switch between english and russian, right click on the top panel, choose 'add to panel,' and choose 'keyboard indicator.' Then you can click on the icon on your panel whenever you want to switch between layouts. I think this is a lot easier than whatever you might be doing using SCIM.

---

### Post by jenhsun on 2007-10-24
> **jon.reeve said:**
> What I would do instead is, go to System -> Preferences -> Keyboard, choose the 'layouts' tab, click 'add,' choose 'Russia' from the layouts menu, add, close, then on your top panel (or wherever), you can put a keyboard layout switcher to switch between english and russian, right click on the top panel, choose 'add to panel,' and choose 'keyboard indicator.' Then you can click on the icon on your panel whenever you want to switch between layouts. I think this is a lot easier than whatever you might be doing using SCIM.

Great, Jon, I didn't realize Russian Keyboard Layout is different than US.English.
Yours is a solution too.

---

### Post by Kdar on 2007-10-24
> **jon.reeve said:**
> What I would do instead is, go to System -> Preferences -> Keyboard, choose the 'layouts' tab, click 'add,' choose 'Russia' from the layouts menu, add, close, then on your top panel (or wherever), you can put a keyboard layout switcher to switch between english and russian, right click on the top panel, choose 'add to panel,' and choose 'keyboard indicator.' Then you can click on the icon on your panel whenever you want to switch between layouts. I think this is a lot easier than whatever you might be doing using SCIM.

yes. I know about this.
But the problem is..
I don't want to have two keyboard layout switchers.. That one and SCIM.

But I need SCIM for my Japanese input.

---

### Post by jenhsun on 2007-10-24
Kdar

Try this old solution, it might help

[http://www.mrbass.org/linux/ubuntu/scim/](http://www.mrbass.org/linux/ubuntu/scim/)

---

### Post by jenhsun on 2007-10-28
About anything related on SCIM, Problem solved.

Please take a look at this bug report
[https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)

And the most important is the document in your
/usr/share/doc/scim/README.Debian.gz

---

### Post by misha1983 on 2007-10-30
There are sources for SCIM Russian tables [here](http://www.serious-sam.net/serendipity/index.php?serendipity%5Baction%5D=search&serendipity%5BsearchTerm%5D=scim).

I made the tables for myself a while ago when there weren't any proper Russian tables (yawerty was around, but I don't use that, and don't know anyone that does).   I had plans of packaging and sharing them, but that got put on the backburner.

Read documentation on how to make SCIM tables (there are some instructions on the above page), download the source, and it should all be working.  Shouldn't take you that long, it's not that hard.

Misha

---

### Post by jenhsun on 2007-10-31
[http://ubuntuforums.org/showpost.php?p=3676651&postcount=6](http://ubuntuforums.org/showpost.php?p=3676651&postcount=6)

---

### Post by larytet on 2007-12-02
why SCIM jumps in and russian depends (?) on SCIM at all ? 
Russian is not a complex font and I think maps well on the regular keyboard. Am I missing here something ?


[Update]

From what I read Ubuntu 7.04 - the Feisty Fawn will install SCIM automatically when a user adds multilingual support. In my case I added Russian and Hebrew. 
SCIM does not have Hebrew fonts. It looks possible to add Hebrew table to the SCIM, but I discovered that keyboard switches by itself (may be i accidentally used hot keys combo, i am not sure) from English to Thai (?). I decided to remove SCIM. 
I used synaptic to remove all SCIM related files. Russian support remained intact and works find without SCIM

And "fonetic" Russian keyboard layout is really cool for those poor souls who can type in English, but not in Russian. This one maps Russian to English ala "latiniza", for example 'S' maps to '&#1057;'

---

