---
title: "Anomalous browser rendering"
date: 2022-11-21
forum: General Help
---

### Post by nickdc on 2022-11-21
I'm seeking assistance troubleshooting a bizarre webpage anomaly.

I've recently helped my partner and her friend to transfer a small website from Weebly, where it was created largely by the friend, to a new host, where my partner already has a site (and the additional one is accommodated within her plan without extra cost). It wasn't a completely smooth process, but with help from the support staff at eUKhost the transfer was apparently successful. The site displays perfectly on my desktop (Manjaro Gnome), my Android tablet, my partner's Windows laptop, and an old Sony Vaio laptop running Lubuntu and Windows Vista. But it doesn't display correctly on my partner's desktop running Ubuntu Mate: eg. the two images on the home page are out of alignment, the descriptive panel above them is in bolder font and, most serious, the drop-down menu for the central "ARCHIVE" component doesn't work when the mouse is hovered above it. (I can't get this to show on the screenshots as it disappears as soon as the mouse moves away to take the screenshot, but it can be seen on the live site: [www.mappingmemory.co.uk]("http://www.mappingmemory.co.uk"))

We have installed Chrome (had so far been trying in Firefox) but the same issues arise, so presumably it's not browser specific. And browsers on a virtual installation of Ubuntu 22.04 running in VirtualBox on the same machine, render correctly, so presumably it can't be a hardware issue. The computer in question was running Ubuntu Mate 20.04, so we have upgraded it to 202.04. That process has just completed and I'd hoped it would resolve the issue, but not so. What on earth could be causing this behaviour?

Perhaps worth adding that my partner's own site on the same host renders perfectly on her machine.

---

### Post by &amp;KyT$0P# on 2022-11-21
I can't access your link -
> Hmm. We’re having trouble finding that site.

We can’t connect to the server at www.mappinmemory.co.uk.

If you entered the right address, you can:

    Try again later
    Check your network connection
    Check that Nightly has permission to access the web (you might be connected but behind a firewall)

But looking at your screenshots, is the non-working system missing some installed fonts compared to the working systems?

---

### Post by nickdc on 2022-11-21
Apologies - I made a typo inputting the URL. It's mappin**g**memory, with a g.

Thanks for pointing it out and your suggestion re fonts. I don't see how the latter could affect the main problem, though, which is the failure in the ARCHIVE drop-down menu.

---

### Post by &amp;KyT$0P# on 2022-11-21
The alignment works fine for me.  Check that you don't have an ad blocker blocking the stylesheet at
```
https://www.mappingmemory.co.uk/files/main_style.css?1668433246
```

However I too saw the failure of the Archive dropdown.  On my setup, it's due to the site specifying to serve most of the script files from cdn2.editmysite.com specifically over plain HTTP, and:
[LIST]
[*]My browser is set to HTTPS-only mode,
[*]My NoScript config only allows the HTTPS version of *.editmysite.com,
[*]NoScript is unaware that these requests will be upgraded to HTTPS by my browser, so it blocks the scripts.
[/LIST]

On my end, I got it working by Temp. Trusting the plain-HTTP version of editmysite.com in NoScript.  But since the site owners are personally involved in this case, this is not a great solution.

To fix this on the site end, either specify to load the scripts over HTTPS, e.g.
```
https://cdn2.editmysite.com/js/site/main.js?buildTime=1234
```
or remove the protocol to just let it load over the same protocol as the top-level site, e.g. try specifying them like
```
//cdn2.editmysite.com/js/site/main.js?buildTime=1234
```

All that said, I have no idea whether the cause of this issue on my system has anything to do with what's causing it on your system. :-?

---

### Post by nickdc on 2022-11-22
Thanks so much for your troubleshooting on this. My problem is that I don't really understand code, so for me it's like looking for a needle in a haystack. But now you've identified where the problem is probably located - and I strongly suspect it **is** what's causing it on my system - I'll hopefully be able to modify that section along the lines you suggest once I get my head round it. Many thanks again for your input. I'll mark the thread solved once I've managed a successful edit of the code.

---

### Post by nickdc on 2022-11-22
Having downloaded the index.html page to have a look at it I think I need a bit more help with this! I'm assuming I need to find every instance of 

```
http://cdn2.editmysite.com/
```    

and change it, but just wondering if it's structured so there's a "master line" as it were, which once edited will change all the rest. (Really ignorant here, but keen to learn.)
Also, is there any advantage or argument on lines of "best practice" between the two solutions you suggested?

---

### Post by dragonfly41 on 2022-11-22
CDN's are explained here:

[https://en.wikipedia.org/wiki/Content_delivery_network](https://en.wikipedia.org/wiki/Content_delivery_network)

But also regarding checking W3C compliance of web site content, and &#8220;best practice&#8221;, this is a deep subject.


Try this tool

[https://validator.w3.org/](https://validator.w3.org/)

But it is a rigorous validator and if we apply it to this ubuntuforums thread we also see many errors.


[https://ubuntuforums.org/showthread.php?t=2481189](https://ubuntuforums.org/showthread.php?t=2481189) 


So do not worry too much if there are some errors.

Let us go to the root page ...

[http://www.mappingmemory.co.uk/](http://www.mappingmemory.co.uk/)


[https://validator.w3.org/nu/?doc=http%3A%2F%2Fwww.mappingmemory.co.uk%2Findex.html](https://validator.w3.org/nu/?doc=http%3A%2F%2Fwww.mappingmemory.co.uk%2Findex.html)


Lots of warnings.

There is a broken link in this page.


[http://www.mappingmemory.co.uk/participate.html](http://www.mappingmemory.co.uk/participate.html)


Rolling back I see the content is built by Weebly.com


[https://www.weebly.com/uk?utm_source=internal&utm_medium=footer&utm_campaign=2](https://www.weebly.com/uk?utm_source=internal&utm_medium=footer&utm_campaign=2)


Checking weebly.com in w3c validator I see many errors.


[https://www.weebly.com/](https://www.weebly.com/)


Just keep an open mind on choice of tools.  I tend to develop/author on desktop first, validate, then publish.


My conclusion.

The web site is a very good idea. 

There are some parallels with


[https://archive.org/web/](https://archive.org/web/)


[https://archive.org/projects/](https://archive.org/projects/)


[https://www.archive-it.org/](https://www.archive-it.org/)


Archive Preservation Tools
[https://www.archive-it.org/blog/learn-more/](https://www.archive-it.org/blog/learn-more/)




The way forward.


It might be the hosting service at fault - but that is a guess based on quickly validating their site.

I would suggest, before relying on any one website builder tool:

&#8226; prepare the content locally on a Ubuntu desktop environment and later server so that it can be viewed by author(s) across a number of browsers.

&#8226; multiple authors can contribute their works to a central pool to be validated.

&#8226; use markdown for the internal content creation (including citations embedded).

&#8226; use a markdown editor such as Zettlr.
[https://docs.zettlr.com/en/](https://docs.zettlr.com/en/)

&#8226; for multiple citations use Zotero with BetterBibTex extension.

&#8226; research Pandoc

&#8226; research using Scribus as content editor. But this is a much deeper subject and requires a pipeline of document production. Remember that there will be authors good with words but not images and vice versa.

&#8226; Google search &#8220;cross-browser testing tools&#8221;.

&#8226; Your content might be viewed in different platforms and should be validated/trusted first.


This note was prepared using CherryTree editor. Another useful authoring tool.

---

### Post by nickdc on 2022-11-22
Wow! dragonfly41 - what an incredibly helpful post! I'm greatly indebted to you. Lots to learn but some very helpful signposts. 

I've edited the index page as suggested by halogen2 and that's sorted the drop-down menu (and the alignment problem). We've now realised that audio and video are not showing on some browsers either, so that's the next step, hopefully as easily sorted as the drop-down menu.

My plan always was to set up a local test site on one of our desktops and I still intend to do that. Unfortunately I had to do it the other way round as the transfer from Weebly was under pressure of time and an opaque process (hence my needing help ironing out the glitches) and it seemed sensible to get a properly functioning site on the new host which we can then download to mirror locally for further development.

---

