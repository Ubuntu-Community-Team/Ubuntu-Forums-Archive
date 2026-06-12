---
title: "how to use fonts"
date: 2019-02-24
forum: General Help
---

### Post by oneleded on 2019-02-24
i'm having trouble with the screen, because of my vision. it started going out some in 2000. i want to set my font's so i dont have to use Ctrl+ to have the letters, an numbers larger. i want all pages to open, to where i can see them. my browser is Firefox, i am currently using lubuntu, 18.04 LTS. my experiments with fonts sometimes works, other times it causes problems. i think, how can i get different sites i visit on the same page, as far as fonts go? in my vision, or lack there of..

---

### Post by bitsnpcs on 2019-02-24
Hello oneleded,

in Ubuntu Settings go to  -  

Universal Access>Seeing>Large Text
Slide the slider to On

Also to try is the "High Contrast" setting just above the "Large Text" setting, it is activated in the same way by sliding the slider to On.
Another option is "Screen Reader" in the same settings Menu.

**Gnome tweaks **is available in Ubuntu Software, while changing my mouse settings I noticed an interesting setting - 

Keyboard&Mouse>Mouse>Pointer Location
it is switched on by sliding the slider.

Once this is switched on if the Ctrl key is pressed it makes a coloured circle pulse fairly large around the mouse pointer, it looks a nice Accessibility function.

---

### Post by oneleded on 2019-02-24
> **bitsnpcs said:**
> Hello oneleded,

in Ubuntu Settings go to  -  

Universal Access>Seeing>Large Text
Slide the slider to On

Also to try is the High Contrast Setting just above the Large Text setting, it is activated in the same way by sliding the slider to On.
Hi bitsnpcs; i dont know how to get to Universal Access. it should be in Lubuntu. i cant find it though.

---

### Post by bitsnpcs on 2019-02-24
There is a help info on this here - [https://help.ubuntu.com/stable/ubuntu-help/a11y-icon.html.en](https://help.ubuntu.com/stable/ubuntu-help/a11y-icon.html.en)

---

### Post by oneleded on 2019-02-25
i cant seem to find the person icon. perhaps some of my settings, are preventing this.

---

### Post by bitsnpcs on 2019-02-25
Does it show if you open the Menu and begin typing, Universal Access ?

---

### Post by oneleded on 2019-02-25
i used synaptic package manager, to install Gnome Tweaks. 
how can i open the menu, so i can type though? you are not speaking of LXTerminal, nor installing Gnome Tweaks.

---

### Post by bitsnpcs on 2019-02-25
I meant open the menu of Lubuntu.

Gnome tweaks has the menu when it is opened on its left side vertically.

---

### Post by oneleded on 2019-02-25
guess im a bit thick. let me try this in the morning, as far as, open the menu of lubuntu.    //ed

---

### Post by Holger_Gehrke on 2019-02-25
I think there's a bit of confusion here: oneleded is using **L**ubuntu (with LXDE as Desktop) and bitsnpcs is giving tips for mainline Ubuntu (with Gnome). These DEs are quite different.

The original post mostly refers to trouble with page zoom in Firefox. Firefox by default stores the zoom level on a per site basis. If you set the zoom for a site, Firefox remembers this and will zoom the page to the set level the next time you open it. For pages you've never visited before it defaults to a zoom level of 100%. If you want to always zoom to a set level, independent of site and whether you've visited it before or not, enter 'about:config' in the address-bar, search for 'browser.zoom.siteSpecific' and set it to 'false'.

Holger

---

### Post by bitsnpcs on 2019-02-25
Oops yes, I need to watch for this in future, and be more careful not cause confusion.

---

### Post by oneleded on 2019-02-25
i thought some about ubuntu and lubuntu, being different this morning. it does explain why i dont have the same settings.
i also toggled, 'browser.zoom.site Specific' to false. i will let ya'all know how it turns out. thanks.
bitsmpcs; dont worry about confusing me,. i confuse myself. lol

---

### Post by bitsnpcs on 2019-02-25
Thank You for your patience :)

---

### Post by oneleded on 2019-02-25
what i am trying to accomplish is to have, all pages or sites with the same word size. the pages i go to are multi functional, so the words on a part of the page might have a different size. when i use Ctrl +, the page gets bigger here. the orange bar at the top stays the same. Quick Links | Forum Community | Ubuntu Community, start losing the bottom of the word lettering. i can disappear, the horizontal line, to the point it is gone. that is kinda where i am at for the moment.

---

### Post by oneleded on 2019-02-25
> **bitsnpcs said:**
> Thank You for your patience :)
same to you..

---

### Post by Holger_Gehrke on 2019-02-25
> **oneleded said:**
> ... when i use Ctrl +, the page gets bigger here. the orange bar at the top stays the same. Quick Links | Forum Community | Ubuntu Community, start losing the bottom of the word lettering. i can disappear, the horizontal line, to the point it is gone. ...

This surprised me because it's totally different from what I see when I zoom. The bar grow vertically and at 240% zoom the line of text at the bottom gets wrapped and "Useful Links" gets put on the next line (and vanishes since it's white text on white background). Searching around the menu I found an option in 'View' -> 'Zoom' -> 'Zoom Text only' (Retranslated from German, the actual names of menus and items may differ) which produces the effect you describe. Try setting that option **off** and see if you like that behaviour better. In case the menu-bar isn't visible for you (I think it is hidden by default, I usually have it visible all the time) hitting F10 will show the menu.

Holger

---

### Post by oneleded on 2019-02-25
view text only, may be a firefox option, for those that follow this thread.that is where i found it, and hope i got it right. in firefox, click on view/ zoom/,, and that is where i found to uncheck//  Zoom Text only....
Holger_Gehrke; you translation program is good. except for your name, i might not have suspected you spoke German. what program do you use for translation? i'm just curious.
should i reset the firefox setting,, "browser.zoom.siteSpecfic" to true, and go from there?

---

### Post by oneleded on 2019-02-26
i have to use, Ctrl +, at least 3-4 times till i can read the page.  when i mess with the font settings in firefox settings, the pages get weird. the monitor i am using is wide enough for larger letters/words. 
firefox advance font settings have; proportional, monospace, minimum font size. i think the answer may lay here.  ed

---

### Post by Holger_Gehrke on 2019-02-27
There's an extension for Firefox named "[NoSquint Plus]("https://addons.mozilla.org/en-US/firefox/addon/nosquint-plus/")". It allows you to change the default zoom level and can enforce your own choice of foreground and background colours. Found it through duckduckgo with the search terms 'firefox force zoom'.

Setting 'browser.zoom.siteSpecific' back to true is probably a good idea. As I said in post #10, this setting controls whether firefox remembers zoom settings per site.

And the translation software I use ? 'Holger's Brain v1.0" - I'm in my 50s and have been reading, writing and - on occasion - speaking English a lot for more than 30 years.

Holger

---

### Post by oneleded on 2019-02-27
i changed my settings back to default, in firefox. things seem to be working OK. not as bad as before, at lease. i am at 133% on most pages. Firefox font settings, have proportional, monospace, an, minimum font size. i dont know what these terms mean as far as a permanent setting. fonts were never explained, with windows, or any OS.
for a bit of time, i was going to look up, "Holger's Brain v1.0" program, till i caught myself. lols on me.
i did look up, NoSquintPlus. the program needed to many permissions, 'cookies and such', i decided against it. 
ed.

---

### Post by oneleded on 2019-03-03
What defines the font size? the browser, the OS or both. the size problem of the letters, or pages, seem more recent, though i did have a problem, at 1, VA.gov page. now the font problem is different, and goes across other forums, pages, with letter size. maybe an firefox update is involved. or my attempt to get it back, to my normal.
been a week, since i wrote...  i downloaded different fonts and some font helper things from synaptic package manager. i think i got the problem solved. i just have to learn the settings, within firefox, and finish downloading the proper font selections in synaptic package manager. other forums are working better. this one is also, but i got some tweaking to do. thanks for the help

---

### Post by oneleded on 2019-03-17
> **Holger_Gehrke said:**
> This surprised me because it's totally different from what I see when I zoom. The bar grow vertically and at 240% zoom the line of text at the bottom gets wrapped and "Useful Links" gets put on the next line (and vanishes since it's white text on white background). Searching around the menu I found an option in 'View' -> 'Zoom' -> 'Zoom Text only' (Retranslated from German, the actual names of menus and items may differ) which produces the effect you describe. Try setting that option **off** and see if you like that behaviour better. In case the menu-bar isn't visible for you (I think it is hidden by default, I usually have it visible all the time) hitting F10 will show the menu.
Holger
my firefox menu is visible at the top of the page. i have the zoom function. the only one i can check, on or off, is; "zoom text only" it was set off. i will try with it on..

---

### Post by HermanAB on 2019-03-18
Hmm, if your vision is degrading, then you should buy a Macbook with a Retina display - it makes an enormous difference.  Macintoshes also have very good accessibility features, screen magnifier, voice over, voice to text, etc.

Also, you need to learn how to use these features **before** your vision deteriorates too much!

---

### Post by oneleded on 2019-03-20
thanks HermanAB and all the rest that helped. i have lubuntu on the 2nd hard drive. i kinda crashed the PC, while editing the 2nd hd.. grub2 aint quite working. however, i did find the problem why my fonts were so strange. from 14.04 to 18.04,, sometimes i used the iso., with a cd, or dvd. othertimes i used the net to update the new system. i may have had more than a few problems, from doing this. some of my other problems were because i was learning. if it were not for this site, i might be using windows. now i am one my 16.10 cd., in test mode. the last windows i used was xp. i was still using it in 2016. Glad i found an alternitive. Ed

---

### Post by oneleded on 2019-03-22
at the moment i am useing, a live dvd to access this site. and,, the fonts are working as they should. i think i am using 16.10. it is of no matter. the pages are working here.. updating, and not doing a live dristo, could have been the problem/ may have been the problem. i have to mark it solved.

---

### Post by oneleded on 2019-04-16
though i marked this solved, i didn't take into account screen size, or the resolution. this is an asus monitor, unlike the tube type. i cant remember if it is led, or what ever. know i can read it, without using, Ctrl,an plus.. now when i make it bigger, it gets way bigger. 110 is comfortable, where as 130-150 worked before. just saying.

---

### Post by oneleded on 2019-07-25
things have changed some. i had to reinstall lubuntu, 1804 LTS, and now pages are working better. with that said, now i have to go back into firefox, and change a few thing's, and hope this resolves the problem. 133% works just fine, as do some of the other size settings. its not near as crazy as it was before. a fresh install, may have just changed quite a few problems.
when i find that head banging icon, it will be on my post..
bang ouch, bang ouch, bang ouch, bang ouch, for some reason, every time i hit my head on this wall, it hurts. let me try again.. [not an icon, but describes it well]

---

### Post by oneleded on 2019-08-08
i am probably not stating, the right question... at the moment i am viewing at 120%. when i switch to 133%. it is better. how do i keep the pages the same?, with lubuntu. 
all i want is a consistent size, of the letters, and numbers. i tried to get this right within Firefox. i dont know what i am doing, to keep it the same. 
the xp drive works fine. i cant seem to do this with the linux drive..

---

### Post by oneleded on 2019-08-08
bump

---

### Post by oneleded on 2019-08-16
bump

---

### Post by oneleded on 2019-10-15
i didnt go through this thread to see what i wrote, though i am asking the wrong question.. at the moment the zoom is at 133%.. how can i get this to stay permanent? different sites, or different days, i might want 120%. i just went up to 150%. now it is getting better.. on other days at this same site, i can use 120%..
i dont think its me. for some reason, it is as the definition of font size changes.. the old paper cook books dont seam to change on a day to day basis. i will grant this, it is possible, my vision could keep changing, back and forth, it dont seem plausible..
 stranger things have happened. dyslexia, and tinnitus were unknowns, once..

---

### Post by sdsurfer on 2019-10-15
For the overall desktop, try Settings->Universal access. There is an on/off toggle for large text and a setting for zoom.

If you just want it in your browser when browsing web pages, it would depend on which browser you are using, but there are settings/preferences in each browser for this also.

---

### Post by oneleded on 2019-10-17
i'm using firefox, with lubuntu 18.04 lts. you got the drift of want i need, i think. i dont explain myself well.. i want the text to be consistent, no matter what page i am on, so i dont have to zoom, all the time. besides, it seems the zoom changes. now i am at 150%. tomorrow i might be at 120%, yet the letters are the same size. go figure..  the page seems to get bigger, but i want the text to be bigger more than the page to be bigger. i dont ask for much do i. doubt i have explained this well. thanks

---

### Post by CatKiller on 2019-10-17
In Firefox you can go to Edit &#8594; Preferences &#8594; Language and Appearance &#8594; Advanced and set a minimum font size to whatever is comfortable for you to read. All webpages should then display text that's at least that big.

There's not actually any direct relationship between the font size in points and the size of the glyphs in pixels - font rendering is absurdly messy - but that should get you what you're ultimately after: every site being readable.

---

### Post by oneleded on 2019-11-08
i have not responded, due to family problems i dont intent to rest till, i have this solved.. thanks

---

### Post by oneleded on 2020-02-19
Thank's CK. i gotta work on my font definition's. //ed

---

### Post by cmcanulty on 2020-02-24
Since you use Firefox try this. I also have bad eyesight and since web pages texts varies so much this work for any page. Click on the 3 vertical lines for customize and drag the zoom buttons to your menu. Then you can quickly adjust any page to the desired size text. Also in preferences I set the default zoom to 110% you might need more and in preferences I set the default font to 16 with all those tools I can usually read anything.

---

### Post by cmcanulty on 2020-02-26
Another thing I found helpful for bad eyesight:
download chronos theme

[https://www.xfce-look.org/p/1016451/]("https://www.xfce-look.org/p/1016451/")

then save it to .themes in your home folder  (or make .themes folder in your home)

extract it to .themes

open setting manager and go to window manager and pick chronos
all it does it make the min max close buttons in different colors so they're easier to see, really helps me

---

### Post by oneleded on 2020-03-02
thanks for the help

---

### Post by oneleded on 2020-03-09
it's better. but you are right. font rendering is absurdly messy

---

### Post by oneleded on 2020-03-09
i got the program to .theme's in the home folder. i'm having trouble opening setting manager.

---

### Post by oneleded on 2020-03-11
Holger you probable speak english better than i do. we are from the country, hillbilly comes close. i have a different syntax and dialect then any of my siblings do. 
[i may speak dyslexia].. My best friend didnt understand exactly what i was saying, for at least the first 15 years. i had to reword it till he understood. HaHa
i put LXDE in my signature, it hasnt shown up yet.

---

### Post by oneleded on 2020-03-13
This will never be solved. i got plenty of good tip's. to mark it solved is wrong, not marking it solved is wrong. i'm am stuck. i am satisfied with what i learned. 
there aint nothing to mark it that way.

---

