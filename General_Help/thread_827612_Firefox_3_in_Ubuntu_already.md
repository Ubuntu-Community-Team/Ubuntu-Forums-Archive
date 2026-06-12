---
title: "Firefox 3 in Ubuntu already?"
date: 2008-06-12
forum: General Help
---

### Post by lorderico on 2008-06-12
I just upgraded to firefox 3 in ubuntu.  The out-of-beta firefox 3.  I didn't know it was available already for linux.  I thought it is supposed to be released on the 17th.  Anyone know how this is?  Also, what is different in the out-of-beta firefox?

---

### Post by AndThenWhat on 2008-06-12
Yea, I just realized this yesterday too.  One thing that sucks about the "Out-of-beta Firefox 3" is that a lot of add-ons are incompatible.

---

### Post by lorderico on 2008-06-12
Yea, I keep waiting for google toolbar to work on my system....

---

### Post by AndThenWhat on 2008-06-12
I found a work-around for getting add-ons working in FF3.

In Firefox's address bar type:

```
about:config
```

then right-click and make a new boolean called **extensions.checkCompatibility** and set it to **False**

Then get the User Agent Switcher add-on

[https://addons.mozilla.org/en-US/firefox/addon/59](https://addons.mozilla.org/en-US/firefox/addon/59)

and add a new user agent

called FF2 and put this in the User Agent box in the options:

```
Mozilla/5.0 (Windows; U; Windows NT 5.2 x64; en-US; rv:1.9a1) Gecko/20060214 Firefox/1.6a1
```

Then restart firefox and go to Tools -> User Agent Switcher -> FF2 and then you should be able to download incompatible add-ons and use them without a problem.

---

### Post by steveneddy on 2008-06-12
[COLOR="Blue"]**Firefox 3 in Ubuntu already?**[/COLOR]

Not until the 17th.

---

### Post by eriqjaffe on 2008-06-12
> **lorderico said:**
> Yea, I keep waiting for google toolbar to work on my system....googlebar lite works in 3.0...

---

### Post by lorderico on 2008-06-12
Andthenwhat: how do you know it will work properly that way? it must not be compatible for a reason.

steveneddy: uless I am much mistaken, I have version 3.0

Before I upgraded, my firefox in the top bar always said firefox 3 beta 5.  Now it just says Mozilla Firefox.  Also, when I go into help>about MF, it lists my version as 3.0

eriqjaffe: do you know what limitations this lite toolbar has?

Thanks,
Eric

---

### Post by AndThenWhat on 2008-06-13
Most of them are compatible but have been blacklisted to block the few that are specific to certain issues.  I know for a fact this works as I have "1-Click Weather" working in FF 3 when it is supposed to be incompatible.

---

### Post by cchaverri on 2008-06-14
It should be a list of installed software on an actual system _with_ actual version numbers elsewhere easily located and accessible for normal users (not technically oriented). 

I am also confused since I have upgraded from 7.10 to 8.04 and, first I saw a beta version and now a 3.0 version before the official launch date.
(could have been upgraded via a regular security update request?)

Claude

---

### Post by Nepherte on 2008-06-14
It absolutely isn't the final Firefox 3. You can check the version in a terminal:
```
dpkg -s firefox-3.0
```
It'll look something like Version: 3.0~rc1+nobinonly-0ubuntu0.8.04.1 It's just that in the Help > About Mozilla Firefox menu, they don't bother to list the rc anymore since it's pretty much as final as it will get.

---

### Post by anjilslaire on 2008-06-14
You can also see the version in Synaptic.

---

### Post by Rainstride on 2008-06-14
some times there are unofficial releases to beta testers of the stable version, to be sure the officially released version works right. so we still arnt quite in full stable till the official release even though it says we are. besides iv noticed there are some things in the program still locked (updater).

---

### Post by XemeX on 2008-06-14
The update option will be locked since the updating process is usualy processed by the package manager (as it needs root privilidges for example). This option is normally used in Windows version.
Nevertheless the current version is RC so it is more or less working :)

---

### Post by avtolle on 2008-06-14
Even though it says "Firefox 3" on screen, this is rc 1, as has been pointed out a few times already.

---

### Post by lorderico on 2008-06-15
I see now.  Thanks for clearing that up.

---

### Post by lcherryholmes on 2008-06-16
Does anyone know why it was included in the release of Hardy Heron?  I don't think this was a good move.  What do you think?

lcherryholmes

---

### Post by Joeb454 on 2008-06-16
I think that's a topic for another thread, in the Recurring Discussions section of the Community Cafe.

It's discussed on the ubuntu.com website. And to sum it up - Hardy is supported for 3 years - Mozilla stop support for Firefox 2 the end of this year, so why would they include FF2?

Besides, the final version of Firefox 3 is out tomorrow (17th June). And Ubuntu 8.04.1 will be out next month (with FF3 final as standard I presume)

---

### Post by VMC on 2008-06-16
> **Nepherte said:**
> It absolutely isn't the final Firefox 3. You can check the version in a terminal:
```
dpkg -s firefox-3.0
```
It'll look something like Version: 3.0~rc1+nobinonly-0ubuntu0.8.04.1 It's just that in the Help > About Mozilla Firefox menu, they don't bother to list the rc anymore since it's pretty much as final as it will get.

Here's what mine says:

[B]Version: 3.0+nobinonly-0ubuntu0.8.04.1
[/B]
I don't see rc anything on the output of that command.

---

### Post by MichaelBKK on 2008-06-19
The Google Toolbar is also now available for FF 3.  Unfortunately, Canonical have somehow managed to retain the bug with makes FF hang if you attempt to open more than 3 windows with the toolbar enabled.  AFAIK they still haven't agreed that this is their problem, even though it only happens in Ubuntu.

---

