---
title: "wierd page displays"
date: 2006-07-11
forum: General Help
---

### Post by TheRingmaster on 2006-07-11
why do some sites look scrunched and the font is small. I try to increase the font but to no avail. Ebay for example is really messed up. Is there an option like fit to width?

---

### Post by fluffington on 2006-07-12
I wasn't aware that the E-bay site was ever not messed up. As for a fit to width option, check out Opera; that's one of my favorite features (opera is in the new dapper-commercial repo, see [here](http://ubuntu.wordpress.com/2006/07/08/introducing-the-dapper-commercial-repository/) for details).

---

### Post by TheRingmaster on 2006-07-13
also some websites are not filling the browser's width. Please help :(

---

### Post by scxtt on 2006-07-13
it mostly comes down to how they're coded ... so unless you start coding for ebay, not much you can do about it ...

---

### Post by TheRingmaster on 2006-07-13
> **scxtt said:**
> it mostly comes down to how they're coded ... so unless you start coding for ebay, not much you can do about it ...

does your firefox do this (see attachment above)

I never had this problem with windows[-(

---

### Post by scxtt on 2006-07-13
yes, ebay looks the same for me w/ Firefox in dapper ... when you say "i never had this problem w/ windows" did you use IE?

---

### Post by Polygon on 2006-07-13
i believe this is normal... or semi normal at least

most major websites are coded for best viewing at 800x600 resolutions, that way everybody can view the website easily, instead of having the webiste coded for 1024x768, which leaves 800x600 users in the dark, with a harder to use webpage where they have to scroll left and right to see stuff

usually websites like this are centered in the middle, i dont know why this one is all the way on the left

or maybe its a problem that we are using the linux version of firefox... and its set to display a different way for a different operating system/browser.

---

### Post by fluffington on 2006-07-13
> **Polygon said:**
> usually websites like this are centered in the middle, i dont know why this one is all the way on the left

It has to do with the way IE positions blocks. To center a block in IE, you put *text-align: center* on the parent block, and to center in anything else, you put *margin-left: auto; margin-right: auto;* on the block you want to center. You have to do both to make it look the same everywhere, but Ebay only does the former, which is why it looks different in Firefox.

---

### Post by TheRingmaster on 2006-07-13
> **scxtt said:**
> yes, ebay looks the same for me w/ Firefox in dapper ... when you say "i never had this problem w/ windows" did you use IE?

I mainly used firefox and opera. Rarely did I use IE.

---

### Post by fluffington on 2006-07-13
I just checked, and on Windows (in both IE and Firefox), the Ebay site looks exactly like the screenshot posted earlier.

---

### Post by TheRingmaster on 2006-07-13
on my windows, My sites always fit the width of the screen. This is for sure a problem with ubuntu.

---

### Post by TheRingmaster on 2006-07-13
My websites should not look like this!

---

### Post by fluffington on 2006-07-13
> **jpazindustries said:**
> My websites should not look like this!

That's exactly what that site should look like. The only way for xubuntu.info to fill the width of you screen, aside from using Opera's zoom feature, is to set your monitor to 800x600 resolution.

---

