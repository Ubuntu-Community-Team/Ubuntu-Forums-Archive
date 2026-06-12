---
title: "Firefox Web Pages Don't Display Correctly"
date: 2007-12-19
forum: General Help
---

### Post by tm6148 on 2007-12-19
Apologies in advance for the newbie post if this question has been answered before, but after a lot of searching, I have been unable to find a definitive answer.  The closest I've come are the two links that follow:

[http://ubuntuforums.org/showthread.php?t=302125](http://ubuntuforums.org/showthread.php?t=302125)
[http://ubuntuforums.org/showthread.php?t=52174](http://ubuntuforums.org/showthread.php?t=52174)

But I don't think either of these guys got his problem resolved.

I have the same problem with pages not displaying correctly in Firefox.  The same pages look fine on XP, in both IE7 and Firefox.  On my machine, I'm running a fresh install of Gutsy with the standard plugins (except for Java, which I added).  My girlfriend's machine was upgraded from Edgy to Feisty and is completely vanilla.  She sees the same problems.

I'm surprised that more people haven't reported this or, if they have, why there isn't some widely known fix, or at least a disclaimer that it's something we have to live with to enjoy the benefits of Ubuntu.

What am I missing?  :confused:

---

### Post by LaRoza on 2007-12-19
> **tm6148 said:**
> 
What am I missing?  :confused:

What is the problem? What doesn't display correctly? Can you give a link to a site that doesn't work?

(I use Opera)

-EDIT Potential solutions are clearing the cache, and creating a new profile

---

### Post by Sammyf on 2007-12-19
try disabling the extension "image zoom" if it is on. A week ago, this starting causing pages and graphics to be corrupted on my machine. Disabling it (apparently it can't be deinstalled) solved it.

bbye,
Sammy

---

### Post by tm6148 on 2007-12-19
> **LaRoza said:**
> What is the problem? What doesn't display correctly? Can you give a link to a site that doesn't work?

(I use Opera)

-EDIT Potential solutions are clearing the cache, and creating a new profile

Tigerdirect.com is one but there are many others, including the ones posted in those two links I included.  BTW, I tried Opera for the heck of it.  Same problems there.

Below is a screen shot with my problem.  The search fields and the text by them are whacked and the snowflakes in the silly animation are in white boxes, which are very obtrusive, but not visible in IE7.

[[IMG]http://img132.imageshack.us/img132/4566/tigerfirefoxxz7.th.png[/IMG]](http://img132.imageshack.us/my.php?image=tigerfirefoxxz7.png)

---

### Post by LaRoza on 2007-12-19
tigerdirect.com seems to think it is cool to have snowflakes moving on the page.

The images are not transparent (or they goofed the code), blame them, it isn't the browser.

They have design issues, it isn't a browser issue.

---

### Post by tm6148 on 2007-12-19
> **LaRoza said:**
> tigerdirect.com seems to think it is cool to have snowflakes moving on the page.

The images are not transparent (or they goofed the code), blame them, it isn't the browser.

They have design issues, it isn't a browser issue.

I agree the snowflakes are stupid and the coding is probably non-standard, but I just used that example to illustrate some differences in the display of a web page not just between IE7 and Firefox, but between Windows Firefox and Ubuntu Firefox (same version 2.0.0.11).

I would have to say the the majority of the web sites I visit show some kind of misplaced text or entry fields, or both.

---

### Post by LaRoza on 2007-12-19
> **tm6148 said:**
> 
I would have to say the the majority of the web sites I visit show some kind of misplaced text or entry fields, or both.

That is the first site I have seen.

I disabled CSS in the tigerdirect site, and found that the text fields are misaligned, so it is not the CSS, which is often a problem in different browsers.

For a check, how does [http://www.amazon.com](http://www.amazon.com) look?

---

### Post by dkbg on 2007-12-19
First of all, those snowflakes on tigerdirect.com are just ridiculous! The reason they're being displayed in white boxes is because they're actually small Flash movies and the Linux flash player doesn't support transparency through an embedded flash movie yet. The problems with the input boxes in the upper left hand corner are caused by a very strange and highly inflexible implementation by the Tiger Direct website designers which makes the appearance of those text boxes very dependent on your browser's font size. I don't actually have the same problem as you when I first visit the site but if I bump my text size up (with Ctrl-+) by one, I get the exact same problem shown in your screenshot. So I'm guessing if you decrease your font size (with Ctrl -, that is Ctrl and the minus key) it will look more normal, but still not perfect (this isn't really a fix, but I'm guessing you don't see these problems too often). **EDIT:** Would you be able to provide screenshots of any sites where you encounter misaligned text boxes and such? It seems you have an unusual problem if you see problems often because I rarely, if ever, come across any problems like that.

The issues really just boil down to small differences between platforms such as which fonts you have installed and your default text size (or limitations in browser plugins like Flash) along with inflexible website designs created by incompetent designers. Even while using the same browser, but on different operating systems, things can look different. There's not really anything you can do about it unfortunately.

---

### Post by tm6148 on 2007-12-19
Amazon,com looks good.

---

### Post by tm6148 on 2007-12-20
Okay, let me rephrase my original question.  The way I see it, this is either a very common problem or it's not.  

If it's not, then what are the happy combinations of hardware, software and settings that prevent it?  Is there a key ingredient?  

Or, what is more likely IMO, this is a very common, or even universal problem.  From what I can gather, it's caused by sloppy web page design by programmers who are only interested in displaying their product on Windows.  If that's the case, then there should be a caveat prominently featured on the Ubuntu web site preparing new users for the strange browser behavior.  Everyone converting from Windows to Ubuntu has to be prepared to make a series of compromises and adjustments.  If this is one of them, then so be it.  We spend a good deal of our computing lives in our browsers so it would be nice if it were a satisfactory experience, but if we have to deal with some scrambled web pages, I for one would still be a willing convert.  Just tell us in advance to save us hours of frustration trying to research and solve it on our own.

---

### Post by opticorange on 2008-04-17
Yeah I have the same problem firefox not displaying webpage correctly and it seems ubuntu and firefox related because other systems don't seem to have a issue.

---

