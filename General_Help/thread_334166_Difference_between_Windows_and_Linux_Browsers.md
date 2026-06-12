---
title: "Difference between Windows and Linux Browsers?"
date: 2007-01-08
forum: General Help
---

### Post by em es on 2007-01-08
I apologise if this question has been asked before but I looked on here and on Google and couldn't find anything so here goes:

I'm just messing around with my site ([http://www.textuality.de]("http://www.textuality.de")) and I noticed something while testing it with different browsers:

On Linux browsers (I've tested Opera, Firefox, Konqueror and Epiphany) there is a space between the menu at the top (the black buttons) and the contents (the centered white space), you can see it better if you go over the black buttons with your mouse.

And on the Windows browsers I've tested (Firefox, IE (5, 5.5, 6, 7), Opera, Mozilla and Netscape) there is no such space. It puzzles me because I thought the Firefox in Linux and Windows were the same.

I'd obviously prefer to make my site compatible with Linux. I thought it might be something to do with the resolution (I use a bigger one in Windows) but I've checked and it hasn't got anything to do with it. All help will be appreciated. ;)

Here's a Screenshot.
[[IMG]http://img74.imageshack.us/img74/2595/screenshotpe5.th.png[/IMG]](http://img74.imageshack.us/my.php?image=screenshotpe5.png)

---

### Post by tito2502 on 2007-01-08
It could be for any number of reasons.

Getting a site to render 100% across multiple platforms can be annoying.

---

### Post by em es on 2007-01-08
Yeah, but I thought HTML rendering was to do with the Browser not the OS?

---

### Post by xShrimp on 2007-01-08
> **tito2502 said:**
> It could be for any number of reasons.

Getting a site to render 100% across multiple platforms can be annoying.
Its seems to be the problem when I visit DeviantArt with Firefox, I can't get to full view a wallpaper.

---

### Post by Sigudian on 2007-01-08
then maybe the windows port of the firefox engine runs differently enc a different browser.

---

### Post by em es on 2007-01-08
> **xShrimp said:**
> Its seems to be the problem when I visit DeviantArt with Firefox, I can't get to full view a wallpaper.

Could that be because Firefox zooms big pictures to fit the screen?
When you go over it with you mouse and click you should see it whole.

---

### Post by justifier on 2007-01-08
i dont mean to be harsh but it doesnt particularly make a massive difference to the site does it? i can see where you coming from tho, its strange how different OSes and browsers interpert it in different way, as a set rule shouldnt they all "in theory" produce the same result ?

---

### Post by em es on 2007-01-08
> **justifier said:**
> i dont mean to be harsh but it doesnt particularly make a massive difference to the site does it? i can see where you coming from tho, its strange how different OSes and browsers interpert it in different way, as a set rule shouldnt they all "in theory" produce the same result ?

No it doesn't, you're right.
But I was just wondering. And you have to start resolving issues/problems like that sometime.

---

### Post by ciscosurfer on 2007-01-08
This is a CSS rendering issue.  While the rendering engines for Firefox are gecko-based, there remain some subtle differences from platform to platform.  You can try to correct this issue by going into your CSS code and modifying it until this "bar" disappears.  You can accomplish this via CSS hacks and whatnot.  I would also make sure that your CSS within your iframe source doesn't conflict with your external stylesheet.  It may be wise to move the inline CSS into an external stylesheet, possibly consolidating it into your other stylesheet, or create a new one that points to and reflects your iframe source html code.

In any event, try playing around with the code under textuality/header.html to see if you can't get it to look the same as it does in Windows.

Also, I'm not sure I see the benefit of creating your tab selectors from within an iframe.  You can accomplish your entire page without calling an external page from an iframe.  I suppose it's a matter of preference though.

---

### Post by em es on 2007-01-08
> **ciscosurfer said:**
> This is a CSS rendering issue.  While the rendering engines for Firefox are gecko-based, there remain some subtle differences from platform to platform.  You can try to correct this issue by going into your CSS code and modifying it until this "bar" disappears.  You can accomplish this via CSS hacks and whatnot.  I would also make sure that your CSS within your iframe source doesn't conflict with your external stylesheet.  It may be wise to move the inline CSS into an external stylesheet, possibly consolidating it into your other stylesheet, or create a new one that points to and reflects your iframe source html code.

In any event, try playing around with the code under textuality/header.html to see if you can't get it to look the same as it does in Windows.

Also, I'm not sure I see the benefit of creating your tab selectors from within an iframe.  You can accomplish your entire page without calling an external page from an iframe.  I suppose it's a matter of preference though.

Thanks for the answer. I've been using an embedded frame because it makes it much easier to change the whole site. I'm going to go on messing around with it in any case. Any ideas what those subtle difference in the gecko-based engines are, so that I can find the problem?

---

### Post by ciscosurfer on 2007-01-09
> **em es said:**
> Thanks for the answer. I've been using an embedded frame because it makes it much easier to change the whole site. I'm going to go on messing around with it in any case. Any ideas what those subtle difference in the gecko-based engines are, so that I can find the problem?I wish I could tell you something specific.  I am just aware of the slight differences (nothing concrete, I'm afraid :-()

Keep toiling -- you'll get it!

---

### Post by em es on 2007-01-09
I will.
thanks...

---

### Post by reclusivemonkey on 2007-01-10
Try removing all the whitespace from your table. Sounds crazy but this is often the source of small gaps in HTML. Also, you may well benefit from using <DIV>s and <SPAN>s rather than tables for your design. Its considered by most web designers to be preferable than using tables to space things.

---

### Post by em es on 2007-01-10
I tried it with <DIV>s, I didn't get the menubar centered with them, but I could see that there's still a space. I tried with white-space in the CSS, that's a no-go too: Nothing changed.
Thanks for the idea though :-)

---

### Post by reclusivemonkey on 2007-01-10
> **em es said:**
> I tried with white-space in the CSS, that's a no-go too: Nothing changed.

Nope. White space in the *HTML*, specifically in the table.

---

### Post by reclusivemonkey on 2007-01-10
> **em es said:**
> I tried it with <DIV>s, I didn't get the menubar centered with them

No offence, but that's nothing to do with the <DIV>s, its your use of HTML and CSS. I've had a play with the header.html and your gaps are down to the mish-mash of spans, divs and tables. What you want is essential a very simple layout, but you've thrown too much html/css at it.

If I get time, I will create a clean header.html for you, but I can't make any promises as I have a six month old baby who takes precedence.

I would suggested heading over to 
[http://www.csszengarden.com/](http://www.csszengarden.com/)
for enlightenment.

Good luck :-D

---

### Post by reclusivemonkey on 2007-01-10
> **reclusivemonkey said:**
> 
If I get time, I will create a clean header.html for you, but I can't make any promises as I have a six month old baby who takes precedence.


I managed it. Take a look;

[http://www.reclusivemonkey.com/~monkey/textuality/header.html](http://www.reclusivemonkey.com/~monkey/textuality/header.html)

I've tested it very little; just FF2 and IE6 on Linux, but I just wanted to show you the principal more than anything else. As you can see; no gaps, less html and less css.

---

### Post by emarkay on 2007-01-10
Did you validate it?

[http://validator.w3.org/](http://validator.w3.org/)

---

### Post by em es on 2007-01-10
Wow, thanks mate :-)

emarkay: It's not valid, but that's because of the DTD, I can polish them out easily.

Thanks reclusivemonkey.

I'll check it under my Windows browsers tomorrow.

---

