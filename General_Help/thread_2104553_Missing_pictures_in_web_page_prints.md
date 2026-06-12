---
title: "Missing pictures in web page prints"
date: 2013-01-13
forum: General Help
---

### Post by paulnewall on 2013-01-13
When I print the google page, the google logo is missing.
This applies also to print preview and print to pdf, so is probably not a  problem with the printer filter?
I have xubuntu 12.10 and firefox 18.0 and cups 1.6.1

Any ideas how to diagnose this further?

---

### Post by ajgreeny on 2013-01-13
It is exactly the same in Lucid 10.04, both in Firefox and chromium.

The main google logo can however be downloaded using ```
wget http://www.google.co.uk/images/srpr/logo3w.png
``` I found that url from the page-source info in both browsers, but strangely it is not possible to right click on the image and choose view or copy.

Like you, I don't understand why, and was not even aware of this until a few minutes ago, on reading your post.  It does not really matter to me, but nevertheless it would be interesting to know what's going on; perhaps this behaviour is common, but we had simply not noticed it before.

---

### Post by paulnewall on 2013-01-13
I have a partial solution.
The logo is a "background image" not an "image"
You can print background images as follows:
Print...
select the printer
select the options tab
tick the print background images box
print

But the page still looks wrong (the menu and buttons are wrong)

---

### Post by ajgreeny on 2013-01-14
> **paulnewall said:**
> I have a partial solution.
The logo is a "background image" not an "image"
You can print background images as follows:
Print...
select the printer
select the options tab
tick the print background images box
print

But the page still looks wrong (the menu and buttons are wrong)
Thanks for that.

As I say, it is not that important to me, but it is still worth knowing, and quite a surprise that the Google logo is not a normal image but a background image.

No doubt there is a good reason why they do it that way!

---

