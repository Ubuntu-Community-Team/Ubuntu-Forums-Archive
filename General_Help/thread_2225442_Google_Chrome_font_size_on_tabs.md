---
title: "Google Chrome font size on tabs"
date: 2014-05-21
forum: General Help
---

### Post by Alley_Oop on 2014-05-21
Many of you know about the problem of the font size on Google Chrome tabs, bookmarks bar, other bookmarks, and menu being far too small to be readable. Well this has been a problem with Chrome for** 5 years** now and Google has still not fixed the problem (I am using Chrome **[COLOR=#303942][FONT=Ubuntu]Version 36.0.1985.18 dev[/FONT][/COLOR]**[COLOR=#303942][FONT=Ubuntu])[/FONT][/COLOR]

The only solutions I have found are:
(a) Quit using Chrome and switch back to Firefox or Opera etc.
(b) Lower your display resolution.

So if you want the fonts to be usable you have to give up using the best resolution for your display, which is ridiculous but companies such as Google and Simply Accounting insist that this the [B]only solution.
[/B] I have a LG 24" widescreen with a native resolution of 1920x1080 (16:9) but in order to make the fonts readable I had to lower my resolution to 1680x1050 (16:10).

This may be a problem when watching HD movies or playing some games. Which ones I can't say for sure.

If you still want to change your resolution use **Screen Display.** In Gnome go to: **Applications -> System Tools -> Preferences -> Screen Display **lower your resolution and click **Apply**
 a screen will pop up with a timer giving you chance to keep or abandon the new resolution.

Don't forget if you do lower you resolution you will need to change several settings back to normal such as default fonts, magnification, scaling and accessibility or they will be [SIZE=4]far too large![SIZE=2]

[SIZE=1]I really hope somebody actually fixes this issue because I really like Google Chrome.

[/SIZE]What did you finally decide to do?
[/SIZE]
[/SIZE]

---

### Post by robbie 348 on 2014-05-21
Can't you just increase the font size?

---

### Post by Alley_Oop on 2014-05-21
> **robbie 348 said:**
> Can't you just increase the font size?

Actually this has been suggested thousands of times in the last 5 years, but no it does not solve the problem. Google Chrome completely ignores any system font changes, at least for the problem described.

Thanks anyway robbie.

---

### Post by timgood on 2014-05-22
What's wrong with the font size on the tabs? Mine seems fine - see attached.

---

### Post by vasa1 on 2014-05-22
> **timgood said:**
> What's wrong with the font size on the tabs? Mine seems fine - see attached.
It's subjective. Some people would like the font size to be adjustable. I don't think it's an unreasonable request. Maybe it's technically difficult for Google's engineers.

---

### Post by timgood on 2014-05-22
OP said fonts were unreadable. On my system, the tab fonts are bigger than the menu fonts. Both are readable and I can't see the problem.

---

### Post by Bashing-om on 2014-05-22
Alley_Oop;

I just did a version upgrade to Google-Chrome this morning, and now the fonts in the tabs are 'large'. Menu fonts are about 1/2 the size of the tab's font, but very readable.

Maybe the developers addressed that issue ?

[INDENT][INDENT]wonders never cease
[/INDENT][/INDENT]

---

### Post by Alley_Oop on 2014-05-22
On my system the fonts on tabs/bookmarks bar/other bookmarks are about 8 px or less.

This issue can be found from many people.

Chrome 36 (Problem remains)
Ubuntu 14.04
AMD Phenom 9850 2.5Ghz
LG 24 " 1920x1080 (16:9)
Nvida 460
8 GB RAM

---

### Post by mdurham on 2014-05-22
> **Alley_Oop said:**
> On my system the fonts on tabs/bookmarks bar/other bookmarks are about 8 px or less.

This issue can be found from many people.

Chrome 36 (Problem remains)
Ubuntu 14.04
AMD Phenom 9850 2.5Ghz
LG 24 " 1920x1080 (16:9)
Nvida 460
8 GB RAM

How about a screenshot?

---

### Post by vasa1 on 2014-05-22
> **timgood said:**
> OP said fonts were unreadable. On my system, the tab fonts are bigger than the menu fonts. Both are readable and I can't see the problem.
And **I** said it's subjective. What is not a problem for one person (or even the majority) maybe a problem for another person. That's what accessibility issues are all about. *It's fine for me* is quite irrelevant to the person who has a problem.
>  Making Google accessible

As part of Google’s mission to make the world’s information universally accessible and useful, we’re committed to making accessibility a reality for **all** of our users, including those with disabilities. 
Source: [Accessibility]("https://www.google.co.in//accessibility/")
I bolded the "all" in the quote.

I hope things are clear now.

What OP needs to understand is that some aspects of Google Chrome are just not customizable, even with extensions. Use a more customizable browser. Firefox is the most customizable currently though that may change.

Here' a partial quote (to avoid forum issues) from somewhere:
> ... the serenity
     to accept the things I cannot change;
     courage to change the things I can;
     and wisdom to know the difference.

---

### Post by Alley_Oop on 2014-05-23
This issue has become moot since it is entirely a Google issue, nothing can be changed in Ubuntu to address the problem since Chrome just ignores any changes. So that being said I will no longer post about this issue UNLESS Google changes something in the future.

**For now I will switch back to Firefox,,, sigh..**

Thank you very much to all of you who tried to help!

---

### Post by birdsarah on 2015-02-24
Hi, I know it's late, but I was suffering the same issue I think and recently solved it by starting chromium with the --force-device-scale-factor option

chromium-browser --force-device-scale-factor=2

(my problem is actually that the font is too big, so I am using 0.5 not 2, but this might be useful)
[FONT=courier new][/FONT]

---

### Post by Mike_Walsh on 2015-02-24
Well; I'm using the current stable version of Chromium in Puppy Linux as of this very moment. I would judge the tab and menu font sizes to be the same.....about 10 px, or thereabouts. I've had to wear glasses since the age of 4 (over 50 years now), and I have to admit to wishing they were perhaps a WEE bit bigger.....but they're perfectly readable.

[ATTACH=CONFIG]260204[/ATTACH]

Regards,

Mike.

---

### Post by vasa1 on 2015-02-24
> **birdsarah said:**
> Hi, I know it's late, but I was suffering the same issue I think and recently solved it by starting chromium with the --force-device-scale-factor option

chromium-browser --force-device-scale-factor=2

(my problem is actually that the font is too big, so I am using 0.5 not 2, but this might be useful)
...
Very interesting! What is your Chromium version number and operating system? Whenever I read about an option or switch that interests me, I visit [Peter Beverloo's site]("http://peter.sh/experiments/chromium-command-line-switches/") to learn more.

In this instance, I couldn't find "force-device-scale-factor" but did find ```
--device-scale-factor[4] &#8855; 	Device scale factor passed to certain processes like renderers, etc. &#8618;
```

Then I looked at [4] to see this: ```
The constant OS_WIN must be defined.
```

---

### Post by Umbrello on 2015-04-17
I decided to give chromium another try today, and got the same problem as many in this thread, everything was very small. The web site results, the menu bar, the icons, everything.

Adding chromium-browser --force-device-scale-factor=1 to the startup command helped!

Thank you birdsarah!

---

### Post by chrisl-r on 2015-05-18
force-device-scale-factor this changes the entire UI scale though, which is not what I was looking for, it's just the fonts of the tabs and bookmarks that are the issue... but --force-device-scale-factor=0.95 works pretty well for me. Thanks.

[Edit]

Also note that there is some UI weirdness when defining force-device-scale-factor, I'm seeing text boxes and buttons missing their borders on some pages and text seems to re-render on other pages.

---

### Post by werowe on 2015-12-05
> **timgood said:**
> What's wrong with the font size on the tabs? Mine seems fine - see attached.

Because you are young and have healthy eyes.  I had eye surgery and am 54 and cannot read it.

---

### Post by him610 on 2016-07-04
Gee, I seem to have gotten to the party late, but the random issue of tiny, tiny font sizes in chrome tabs, bookmark bars, and dropdown lists seems to have reappeared.

With Google Chrome Version 51.0.2704.106 (64-bit) and ubuntu 14.04.4  installed; then tried the recommended solution from Post #12, *chromium-browser --force-device-scale-factor=2* which did not work,
then tried with a modification, *google-chrome-stable --force-device-scale-factor=2* which worked, but the font size was too large.

Adjusted the previous on by trying *google-chrome-stable --force-device-scale-factor=1* which resulted in the font size appearing normal, or at least, close to normal.

I have other versions of Ubuntu 14.04 installed on this computer and other computers, but this is the only one where Google Chrome tiny, tiny font size issue is seen.

---

### Post by Sigster on 2017-02-13
> **birdsarah said:**
> Hi, I know it's late, but I was suffering the same issue I think and recently solved it by starting chromium with the --force-device-scale-factor option  chromium-browser --force-device-scale-factor=2  (my problem is actually that the font is too big, so I am using 0.5 not 2, but this might be useful) 

Thank you for that.  For me the problem appeared after a recent Opera update (on Xubuntu 16.10)

Starting Opera with

opera --force-device-scale-factor=1

changes the  menu- and tab-font-size to a readable size again,
they had changed to impossibly small after the update - probably 7pt or so.

---

### Post by lisati on 2017-02-13
@Sigster: Opera and Google Chrome are not the same browser.

Closed: may this old thread rest in peace.

---

