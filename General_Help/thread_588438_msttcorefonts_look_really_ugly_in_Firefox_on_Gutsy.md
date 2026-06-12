---
title: "msttcorefonts look really ugly in Firefox on Gutsy!"
date: 2007-10-23
forum: General Help
---

### Post by cank1090 on 2007-10-23
Hi,
I've got a problem on my fresh Gutsy install which I couldn't find a solution for yet. My system fonts look quite ok, everything's fine. But the msttcorefonts in Firefox look really ugly, way to thin and all. In Edgy and Feisty they were perfect, and I wonder why this changed in Gutsy. I'm experiencing this on a 19" TFT and a 17" CRT monitor as well. This problem is independent from my font settings in my system settings, and the Firefox font settings couldn't change anything, too. With msttcorefonts uninstalled, the fonts in Firefox look ok, but I really need msttcorefonts. Is there any solution for this? What could be the problem? Take a look:

[[IMG]http://img339.imageshack.us/img339/9219/screenshot1yn8.th.png[/IMG]](http://img339.imageshack.us/my.php?image=screenshot1yn8.png) [[IMG]http://img140.imageshack.us/img140/8306/screenshot2sz2.th.png[/IMG]](http://img140.imageshack.us/my.php?image=screenshot2sz2.png)

---

### Post by rubinstein on 2007-10-23
I think they look very good, and they look the same here in my Firefox.

Do you really want fuzzier fonts like in Feisty, were there was a bug so the fonts in Firefox were fuzzy?

---

### Post by cank1090 on 2007-10-23
No, they were perfect in Feisty, and even in Windows XP (virtual machine) they look normal. Something must have changed in Gutsy. Maybe you need another screenshot to understand what I mean:

[[IMG]http://img85.imageshack.us/img85/7753/screenshot1qv6.th.png[/IMG]](http://img85.imageshack.us/my.php?image=screenshot1qv6.png)

Other users experience this problem as well (I know it because there is a similar thread in the german Ubuntu forum, but no solution yet).

---

### Post by Cryptorchild on 2007-10-23
I'm having the same problem as well, straight after upgrading to Gutsy. Strangely enough this only happens with Firefox, other applications deal with msttcorefonts with no problem.

Any help would be much appreciated.

---

### Post by zakimak on 2007-10-24
I have the same problem ...
I removed msttcorefonts, and put fonts from windows XP in ~/.fonts.conf manually, but the fonts remain the same...

---

### Post by cank1090 on 2007-10-24
Yes exactly, it only affects Firefox. I also tried just to copy the .ttf data from my Windows install to Ubuntu, but the problem still remains. Can we make a Launchpad Bug Report or so? I'm not very familiar to that...

---

### Post by forestpixie on 2007-10-24
I found that [this]("http://ubuntuforums.org/showpost.php?p=1209754&postcount=1") helped - I also have changed fonts in ff

---

### Post by rubinstein on 2007-10-24
I'm sorry, I didn't get what you meant - the last screenshot explained it.

---

### Post by cank1090 on 2007-10-24
> **forestpixie said:**
> I found that [this]("http://ubuntuforums.org/showpost.php?p=1209754&postcount=1") helped - I also have changed fonts in ff

Sorry, that didn't help at all. It just made my system fonts to look as ugly as in Windows. It seems that any kind of font settings in my system doesn't affect the fonts in Firefox. I really think it's a Firefox specific problem!

---

### Post by NilsE on 2007-10-24
First of all, the font rendering in Firefox is independent of the operating system so changes there make no difference in FF.  Here is a couple of experiments.

Try going into preferences and change the fonts to DejaVu Sans etc. in other words try the DejaVu fonts at each selection that it is available.

Set all font sizes to two higher than your desktop fonts.  For example my desktop/application etc. fonts are 9 so I set all my FF fonts to 11

Now go into about:config and locate the DPI setting and change it to 90.  I think the default is -1 which tries to mimic the desktop fonts but does not work. Shut down all FF windows and reopen one to make the DPI change take effect.

Now one more thing if you want the menu etc fonts to look like your system fonts create a file called userChrome.css in your home .mozilla/"random letters".default/chrome folder and copy in this text, change the xx to two higher than the font size you set your desktop, and save it.  Restart FF.

```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */

/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes xx pt:
 */
 * {
    font-size: xxpt !important
  } 
```

This is all related to the fact that when you set DPI in the system font preferences it is actually rendering at something around 86 depending on your monitor.  Setting FF 2 higher and DPI at 90 is sort of a compromise to get it closer to the system.

---

### Post by cank1090 on 2007-10-24
@NilsE:
Thanks for the tips! Changing the value of "layout.css.dpi" in about:config actually shows an effect, but it's not satisfiying. In my system settings, my DPI is set to 96. Setting "layout.css.dpi" to something about 86 makes the fonts in the web content more readable, but it's not as good as it was in Feisty and besides the fonts of the menu bar etc. are too big.

---

### Post by NilsE on 2007-10-24
> **cank1090 said:**
> @NilsE:
Thanks for the tips! Changing the value of "layout.css.dpi" in about:config actually shows an effect, but it's not satisfiying. In my system settings, my DPI is set to 96. Setting "layout.css.dpi" to something about 86 makes the fonts in the web content more readable, but it's not as good as it was in Feisty and besides the fonts of the menu bar etc. are too big.
Yes, I agree that making it 86 makes every thing too big.  That was why I suggested setting smaller fonts in the preferences and the userChrome.css files to compensate.

I am beginning to think you may have something else going on since with the settings I gave you my fonts are perfect and clear.

---

### Post by kurgan78 on 2007-10-24
Try this:
(after installing msttcorefonts)

Go to the font configuration on the content tab under Edit->Preferences

Set it to the following:
**Default Font**: Times New Roman ** Size**: 16

Click on Advanced...
**Proportional:** Serif  **Size:** 16
**Serif:** Times New Roman
**Sans-serif:** Arial
**Monospace:** Courier New  **Size:** 13
**Minimum font size:** None
[checked]** Allow pages to choose their own fonts, instead of my selections above**

Click OK then click Close on the Preferences window. Close and re-open your browser.

This did wonders for me. The settings above are the default settings for Firefox under Windows.

---

### Post by cank1090 on 2007-10-25
@ kurgan78:
Thanks for the advice, but unfortunately, this didn't made any changes for me :(

---

### Post by Rui Pais on 2007-10-25
Hi,
in my case i didn't change any css file, just tune the 'Proportional' font (Serif/Sans-Serif, don't touched the others) and the 'Allow pages to ...' option, to make equal to default no msttcorefonts installed.
Here some pics:
No msttcorefonts installed:
[ATTACH]47745[/ATTACH]

**With** msttcorefonts installed:
[ATTACH]47746[/ATTACH] [ATTACH]47747[/ATTACH]
Serif+Allow and Serif+Don't Allow option
and setting  Sans Serif font:
[ATTACH]47748[/ATTACH] [ATTACH]47749[/ATTACH] 
Allow and not Allow option (this last the working one)

As you can see (converted to jped to make files smaller change colors a little...) set Proportional font to Sans Serif and disable the 'Allow pages ...' option, last pic, make it came back to nice look of the original one.

hth

---

### Post by cank1090 on 2007-10-25
Yes I know, with msttcorefonts uninstalled, it looks okay because Firefox uses the system fonts. But I need msttcorefonts, that's the point!

I created a Launchpad bug report:
[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/157039](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/157039)

Please comment it and post your experience, so that this problem gets the attention of the developers!

---

### Post by Rui Pais on 2007-10-25
hi, 
i think you miss my post.

At least here, setting Sans Serif and disable 'Allow ...' option **with** msttcorefonts gives the same look as the default one.

---

### Post by cank1090 on 2007-10-25
Unchecking "Allow websites to use..." is the same as uninstalling msttcorefonts! I already tried both ;)

---

### Post by srs on 2007-10-25
Hi guys,
Try this: ```
sudo dpkg-reconfigure fontconfig-config
```
For the first option, play around with Native and Autohinter, for the second option set what is most appropriate for your screen, and for the last option use No.

Then run ```
sudo dpkg-reconfigure fontconfig
``` and restart X.

This worked quite well for me after upgrading from Feisty.

Best wishes, SRS

---

### Post by Rui Pais on 2007-10-26
> **cank1090 said:**
> Unchecking "Allow websites to use..." is the same as uninstalling msttcorefonts! I already tried both ;)

sorry, not quite sure if i understand :( ...

---

### Post by cank1090 on 2007-10-26
@srs:
Thanks for the tips! I'm going to try that later and post my results.

@Rui Pais:
No problem, let me explain. Look at your first and at your last screenshot. On the first one, you have no msttcorefonts. On the last one, you do have msttcorefonts, but not Allow option. If you compare the two pictures, you will notice that the fonts are exactly the same! That's just because of the "Allow.." option, it doesn't have to do anything with msttcorefonts installed or uninstalled.
When you deactivate "Allow..." option, it means that websites don't use their own fonts. For example, a website can use "Verdana" or "Trebuchet MS". But when you deactivate "Allow.." option, Firefox will always use the fonts that you configure (like "serif" or "sans-serif"). So when you deactivate "Allow" option, it is the same like without msttcorefonts.

---

### Post by Rui Pais on 2007-10-26
> **cank1090 said:**
> 
@Rui Pais:
No problem, let me explain. Look at your first and at your last screenshot. On the first one, you have no msttcorefonts. On the last one, you do have msttcorefonts, but not Allow option. If you compare the two pictures, you will notice that the fonts are exactly the same! That's just because of the "Allow.." option, it doesn't have to do anything with msttcorefonts installed or uninstalled.
When you deactivate "Allow..." option, it means that websites don't use their own fonts. For example, a website can use "Verdana" or "Trebuchet MS". But when you deactivate "Allow.." option, Firefox will always use the fonts that you configure (like "serif" or "sans-serif"). So when you deactivate "Allow" option, it is the same like without msttcorefonts.

Hi cank1090, thanks for the explanation. I understand it now. 
From your 1st post, i get the idea that you just wanted the defaults look back with msttcorefonts installed...
May i suggest that you add something like your quote above, or a link to your previous post, that may clarify your issue, so others who may done the same reading as me, wouldn't fail to see the issue. 

btw, i don't have this problem with firefox-grandparadiso (from repos) at least rendering this page, didn't try sites with other MS specific fonts...

---

### Post by cank1090 on 2007-10-26
What is firefox-grandparadiso?

---

### Post by Rui Pais on 2007-10-26
> **cank1090 said:**
> What is firefox-grandparadiso?

The next FF (Firefox 3). It's beta stuff, but you can have both installed under Gutsy.
It's on repos. 
If you just need a browser to check how sites look with MS fonts you may want to give a try... for day-to-day work is kind unstable.

---

### Post by cank1090 on 2007-10-26
Oh I see, okay. Thank you for the tip. But I need a browser to use every day. The thing is, I just don't like the Ubuntu system fonts for webpages, I prefer msttcorefonts.

---

### Post by cank1090 on 2007-10-26
Well, srs, I really, really, really have to thank you! Your advice did the trick for me! Enabling autohinting makes my fonts look so much better. Thank you!

---

### Post by digby280 on 2007-10-28
> **srs said:**
> Hi guys,
Try this: ```
sudo dpkg-reconfigure fontconfig-config
```
For the first option, play around with Native and Autohinter, for the second option set what is most appropriate for your screen, and for the last option use No.

Then run ```
sudo dpkg-reconfigure fontconfig
``` and restart X.

This worked quite well for me after upgrading from Feisty.

Best wishes, SRS

Thanks srs. That worked really well for Firefox but I didn't like what it did to the rest of the fonts on my system.

I have swiftfox and firefox installed and interestingly swiftfox isn't effected by this even though they share settings (see screenshots below firefox left, swiftfox right).  Has anyone got any idea why?

---

### Post by stefangachter on 2007-10-29
Apart that firefox crashes when using the msttcorefonts, I observed too that the MS fonts in firefox look ugly. So far, what is the final conclusion? Why did it work smoothly in 7.04 but cause now problems in 7.10? Has anybody a simple guideline how to fix this problem? Thanks!

---

### Post by yabbadabbadont on 2007-10-29
I ran into the same issue when I reinstalled Gentoo.  (after a very bad Gutsy install)  I had my /etc/ directory backed up from Feisty, in which the fonts looked pretty good, so I started comparing file by file.  I ended up enabling both autohint and antialias, and disabling bitmapped fonts and autohinting for bold fonts.  Here is my ~/.fonts.conf just as a reference: ```
<?xml version="1.0"?>

<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<fontconfig>
  <!-- Turn on the autohinter -->
  <match target="font">
    <edit name="autohint" mode="assign"><bool>true</bool></edit>
  </match>

  <!-- Turn on antialiasing -->
  <match target="font">
    <edit name="antialias" mode="assign"><bool>true</bool></edit>
  </match>

  <!-- Don't use bitmapped fonts -->
  <selectfont>
    <rejectfont>
      <pattern>
         <patelt name="scalable"><bool>false</bool></patelt>
      </pattern>
    </rejectfont>
  </selectfont>

  <!-- Disable hinting for bold fonts -->
  <match target="font">
      <test name="weight" compare="more"><const>medium</const></test>
      <edit name="autohint" mode="assign"><bool>false</bool></edit>
  </match>
</fontconfig>
```

---

### Post by philinux on 2007-10-29
I left firefox alone and did this.

I prefer how firefox looked in Feisty. Here's how I got it

Sys Prefs Appearance

Fonts Tab then click sub pixel smoothing (i'm using an lcd)
Then click details should show smoothing lcd but then select Hinting - none

I've also got applcation font set to Ariel.

---

### Post by Baby Boy on 2007-10-29
All I can say is - Holy Cow am I glad I bumped into this thread. Philinux's and srs' instructions worked perfectly, now my Ubuntu looks better than ever. I also had the problem with those damn msttcorefonts but now everything's fine. 

BTW, I chose the option to make my fonts look fuzzy when asked in
> 
sudo dpkg-reconfigure fontconfig-config

EDIT: God these letters look good now, I love you guys 8).

---

### Post by mooscape on 2007-10-29
I am also experiencing dreadful fonts since upgrading my desktop to Gutsy from Feisty.  And not just in Firefox!  All my applications look fugly now.   I did not experience this when I upgraded my laptops. 

How do I get my old fonts back?  Attached pic to highlight what I mean....

---

### Post by Baby Boy on 2007-10-29
> 
Originally Posted by srs View Post
Hi guys,
Try this:
Code:

sudo dpkg-reconfigure fontconfig-config

For the first option, play around with Native and Autohinter, for the second option set what is most appropriate for your screen, and for the last option use No.

Then run
Code:

sudo dpkg-reconfigure fontconfig

and restart X.

This worked quite well for me after upgrading from Feisty.

Best wishes, SRS


> I left firefox alone and did this.

I prefer how firefox looked in Feisty. Here's how I got it

Sys Prefs Appearance

Fonts Tab then click sub pixel smoothing (i'm using an lcd)
Then click details should show smoothing lcd but then select Hinting - none

I've also got applcation font set to Ariel.


These two posts helped me tremendously.

---

### Post by Wolter on 2007-10-29
> **srs said:**
> Hi guys,
Try this: ```
sudo dpkg-reconfigure fontconfig-config
```
For the first option, play around with Native and Autohinter, for the second option set what is most appropriate for your screen, and for the last option use No.

Then run ```
sudo dpkg-reconfigure fontconfig
``` and restart X.

This worked quite well for me after upgrading from Feisty.

Best wishes, SRS

This works perfectly for me. I can enjoy smooth and nice fonts again. THX!:)

---

### Post by kurgan78 on 2007-10-30
It seems like most of the people having problems are those who upgraded from Feisty to Gutsy. I didn't have any problems with a clean Gutsy install.

---

### Post by Baby Boy on 2007-10-31
> **kurgan78 said:**
> It seems like most of the people having problems are those who upgraded from Feisty to Gutsy. I didn't have any problems with a clean Gutsy install.

False. I had a clean Gutsy install and as soon as I installed msttcorefonts my fonts looked like they were hand-drawn :D.

---

### Post by Wolter on 2007-10-31
> **kurgan78 said:**
> It seems like most of the people having problems are those who upgraded from Feisty to Gutsy. I didn't have any problems with a clean Gutsy install.

I have clean Gutsy installation. My fonts looked really ugly...

---

### Post by nestcrw on 2007-10-31
> **Wolter said:**
> I have clean Gutsy installation. My fonts looked really ugly...

I second this.

---

### Post by digby280 on 2007-11-02
> **mooscape said:**
> I am also experiencing dreadful fonts since upgrading my desktop to Gutsy from Feisty.  And not just in Firefox!  All my applications look fugly now.   I did not experience this when I upgraded my laptops. 

How do I get my old fonts back?  Attached pic to highlight what I mean....

It looks to me like your system font settings have been changed somehow.  Check under System -> Preferences -> Appearance -> Fonts.  If so, try changing the application font to sans.  See if that helps.

---

### Post by kurgan78 on 2007-11-02
> **Wolter said:**
> I have clean Gutsy installation. My fonts looked really ugly...

Not that I much liked the default fonts I had in Firefox either, but after doing what I posted much earlier in this thread, web pages look much, much better on my system. I didn't have any problems installing the msttcorefonts or getting them to work. I was inferring that perhaps the majority of those having problems installing or getting the msttcorefonts to work may have upgraded rather than having done a clean install.

---

### Post by bkraptor on 2007-11-10
Wow! srs' fix with autohinter really did wonders! I wonder why it wasn't like this to begin with.

---

### Post by ndavenport on 2007-11-14
> **NilsE said:**
> First of all, the font rendering in Firefox is independent of the operating system so changes there make no difference in FF.  Here is a couple of experiments.

Try going into preferences and change the fonts to DejaVu Sans etc. in other words try the DejaVu fonts at each selection that it is available.

Set all font sizes to two higher than your desktop fonts.  For example my desktop/application etc. fonts are 9 so I set all my FF fonts to 11

Now go into about:config and locate the DPI setting and change it to 90.  I think the default is -1 which tries to mimic the desktop fonts but does not work. Shut down all FF windows and reopen one to make the DPI change take effect.

Now one more thing if you want the menu etc fonts to look like your system fonts create a file called userChrome.css in your home .mozilla/"random letters".default/chrome folder and copy in this text, change the xx to two higher than the font size you set your desktop, and save it.  Restart FF.

```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */

/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes xx pt:
 */
 * {
    font-size: xxpt !important
  } 
```

This is all related to the fact that when you set DPI in the system font preferences it is actually rendering at something around 86 depending on your monitor.  Setting FF 2 higher and DPI at 90 is sort of a compromise to get it closer to the system.

This post saved my marriage! (well at least my eye sight)

I knew Firefox must render it's fonts independent of the os because whenever I updated the os fonts firefox's window title (not part of firefox) changed but nothing else did.

To fix my problem I simply went into about:config and set the dpi the same as it is System-->Appearance-->Appearance Preferences-->Fonts-->Details and then created the userChrome file and set the fonts the SAME size as my system fonts.

You may need to change you font sizes in FireFox to get them the way you like them after you update the dpi but geez does it beat squinting!

Good Luck!

---

### Post by Manan on 2007-12-06
hey guys i have tried everything mentioned in this thread but still firefox fonts (in the browser) are still very thin and appear broken:

[[IMG]http://img221.imageshack.us/img221/1023/screenshothq0.th.png[/IMG]](http://img221.imageshack.us/my.php?image=screenshothq0.png)

---

### Post by yabbadabbadont on 2007-12-06
I just change the option in firefox's advanced fonts setting to not allow websites to use their own fonts.  I force it to use Bitstream Vera fonts for everything.  It's surprising how few websites break this way.

---

### Post by Rui Pais on 2007-12-06
> **yabbadabbadont said:**
> I just change the option in firefox's advanced fonts setting to not allow websites to use their own fonts.  I force it to use Bitstream Vera fonts for everything.  It's surprising how few websites break this way.

In fact it's surprisingly amazing how better a lot of sites look that way :lol: 
Theres a lot of web sites writers with strange taste when came to fonts! (Times News Roman on page webs looks so weird as the Herald Tribune printed on Comics...)

---

### Post by mayhemt on 2007-12-25
I had the same problem, till i found solution on this thread [http://ubuntuforums.org/showthread.php?t=632306](http://ubuntuforums.org/showthread.php?t=632306)

basically, (if you have msttcorefonts package installed,) you just rename msfonts-rules.conf in /etc/fonts, now the fonts are rendered just like in Windows, without overring the default websites' fonts. 

```

mrt@Bluhills:/etc/fonts$ sudo mv ./msfonts-rules.conf ./msfonts-rules.conf.bak


```

---

### Post by andmi on 2008-03-09
> **srs said:**
> Hi guys,
Try this: ```
sudo dpkg-reconfigure fontconfig-config
```
For the first option, play around with Native and Autohinter, for the second option set what is most appropriate for your screen, and for the last option use No.

Then run ```
sudo dpkg-reconfigure fontconfig
``` and restart X.

This worked quite well for me after upgrading from Feisty.

Best wishes, SRS

By me it run perfectly, but...

First it look ugly:
[[IMG]http://img187.imageshack.us/img187/9320/pulpit4zb7.th.jpg[/IMG]](http://img187.imageshack.us/my.php?image=pulpit4zb7.jpg)

then I make dpkg-reconfigure... and aftere restart firefox look good:
[[IMG]http://img132.imageshack.us/img132/3156/pulpit5yu8.th.png[/IMG]](http://img132.imageshack.us/my.php?image=pulpit5yu8.png)

But after system restart, or only X (all the same) it again look ugly.

What I have to make to setting stayed on solid?

-- 
DISTRIB_ID=Ubuntu DISTRIB_RELEASE=7.10 DISTRIB_CODENAME=gutsy DISTRIB_DESCRIPTION="Ubuntu 7.10" KDE: 3.5.8

---

### Post by HunterK on 2008-03-13
> **NilsE said:**
> First of all, the font rendering in Firefox is independent of the operating system so changes there make no difference in FF.  Here is a couple of experiments.

Try going into preferences and change the fonts to DejaVu Sans etc. in other words try the DejaVu fonts at each selection that it is available.

Set all font sizes to two higher than your desktop fonts.  For example my desktop/application etc. fonts are 9 so I set all my FF fonts to 11

Now go into about:config and locate the DPI setting and change it to 90.  I think the default is -1 which tries to mimic the desktop fonts but does not work. Shut down all FF windows and reopen one to make the DPI change take effect.

Now one more thing if you want the menu etc fonts to look like your system fonts create a file called userChrome.css in your home .mozilla/"random letters".default/chrome folder and copy in this text, change the xx to two higher than the font size you set your desktop, and save it.  Restart FF.

```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */

/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes xx pt:
 */
 * {
    font-size: xxpt !important
  } 
```

This is all related to the fact that when you set DPI in the system font preferences it is actually rendering at something around 86 depending on your monitor.  Setting FF 2 higher and DPI at 90 is sort of a compromise to get it closer to the system.

DPI Setting worked wonders for me!!!!  :guitar:

---

