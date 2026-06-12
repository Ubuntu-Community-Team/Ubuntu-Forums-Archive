---
title: "Firefox and Thunderbird not showing text"
date: 2015-03-15
forum: General Help
---

### Post by reef2dive on 2015-03-15
When opening certain web-pages, the web-page does not show any text. 
If clicking "Allow Pages to chose their own fonts, instead of my selections above" the webpage shows.
The same issue is in Thunderbiird when having emails with web-pages.
The problem with using that setting is that the text come out of place compared to the initial page. (This is valid for Ubuntu Forums page too.)

The Windows fonts from restricted-extras are installed.
The command 
```
sudo fc-cache -r
```
has been run.

Checking the raw HTML of a troubling webpage, no non-installed fonts are listed in the web-page data. 
Any tips on where to look to fix this without having to re-install the whole system.

---

### Post by buzzingrobot on 2015-03-15
Try "fc-cache -fv"?

Sites typically design their pages to use a range of specific fonts in specific sizes, etc.  Telling the browser to use fonts of your own selection can often break the page's display.

---

### Post by reef2dive on 2015-03-15
Thank you, but stll the same issue.

---

### Post by SeijiSensei on 2015-03-15
It's pretty much impossible to diagnose a problem like this without examples.  Please list a few URLs so we can test them out as well.

---

### Post by reef2dive on 2015-03-16
Thank you!
One site is [http://www.webhallen.com/se-sv/](http://www.webhallen.com/se-sv/)
Screenshot using Firefox. [ATTACH=CONFIG]260651[/ATTACH]

There are others but I do not have them on top of my head.

---

### Post by amanchesterman on 2015-03-16
I have Xubuntu and I use Firefox with 'Allow pages to use their own fonts' enabled, and as you say, the page (WebHallen) displays perfectly with that setting.
I don't really understand your post #1 when you say:
"The problem with using that setting is that the text come out of place  compared to the initial page. (This is valid for Ubuntu Forums page  too.)"
Can you explain what you mean by the text 'coming out of place compared to the initial page'? Can you give us a screenshot of how that looks?
I never have a problem with Firefox -- certainly not on the Ubuntu Forums page -- so I am puzzled.

---

### Post by SeijiSensei on 2015-03-16
I see all the text on that page using Firefox 37.0 on Kubuntu 14.04.

Try this.  Close Firefox, then open a terminal and type the following:
```

cd 
mv .mozilla .mozilla.old

```
Then open Firefox.  You'll be starting with a clean profile.  Any better?

Also, make sure you can open this page: [http://www.webhallen.com/css/css.php?1-1-1425545382](http://www.webhallen.com/css/css.php?1-1-1425545382)
It contains the style sheet for the site.

---

### Post by reef2dive on 2015-03-16
I have different profiiles, e.g. standard and test. The result is the same for those.

Attached example from a slightly more known page and using the setting "Allow pages to use...." .
This is the result using the standard profile
[ATTACH=CONFIG]260669[/ATTACH]
This is the result using the test profile
[ATTACH=CONFIG]260670[/ATTACH]

Moving the .mozilla dir to .mozilla-new and starting Firefox, open webpage, e.g. FB, still misses text.

Complete Removal and installation of Firefox does not make any difference.

---

### Post by reef2dive on 2015-04-15
Closed, fixed through reload of complete Xubuntu.

---

