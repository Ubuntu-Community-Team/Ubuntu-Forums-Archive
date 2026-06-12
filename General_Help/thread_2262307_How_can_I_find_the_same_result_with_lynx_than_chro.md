---
title: "How can I find the same result with lynx than chromium"
date: 2015-01-24
forum: General Help
---

### Post by CkDGTAT on 2015-01-24
Hi,

I need to find the exact same result I have with google-chrome with lynx. How can I find my user agent (which is wrong here)?

```
lynx -dump -useragent="Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/36.0.1985.125 Safari/537.36" link.com
```

Thank you

---

### Post by TheFu on 2015-01-24
Does lynx support javascript? Didn't think so. That will make it very hard (impossible) to get any data via Ajax calls.

---

### Post by vasa1 on 2015-01-24
I probably don't understand the question but [http://www.useragentstring.com/](http://www.useragentstring.com/) gives me the user agent string for the browser I use to visit the site.

---

### Post by Nutria on 2015-01-24
> **CkDGTAT said:**
> Hi,

I need to find the exact same result I have with google-chrome with lynx. How can I find my user agent (which is wrong here)?

```
lynx -dump -useragent="Mozilla/5.0 (X11; Linux i686) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/36.0.1985.125 Safari/537.36" link.com
```

links2 supports javascript.

---

### Post by CkDGTAT on 2015-01-30
With lynx (from [http://www.useragentstring.com/](http://www.useragentstring.com/)[COLOR=#000000] ), I find

[CODE]
[/COLOR]https://www.google.ch/search?q=%22foo%22&safe=off&hl=en&gbv=1&sei=k
https://www.facebook.com/foofighters
http://smarturl.it/FFSH
https://www.facebook.com/foofighters?fref=nf
http://smarturl.it/
https://twitter.com/foofighters
http://t.co/yzvFx0EpOv
http://t.co/Aam6igaYzy"
https://www.google.ch/webhp?tab=ww
https://www.google.ch/search?hl=en&safe=off&q="foo"&gws_rd=cr,ssl&um=1&ie=UTF-8&tbm=isch&source=og&sa=N&tab=wi
[\CODE]

and with google

[COLOR=#808080][FONT=arial]fr.wikipedia.org/wiki/Variable_métasyntaxique
[LIST]
[*]
[*]
[/LIST]


[/FONT][/COLOR]
[COLOR=#808080][FONT=arial][/FONT][/COLOR]
[COLOR=#545454][FONT=arial][/FONT][/COLOR][COLOR=#006621][FONT=arial]en.wikipedia.org/wiki/[/FONT][/COLOR][B]Foobar
[/B][COLOR=#006621][FONT=arial]fr.wiktionary.org/wiki/[/FONT][/COLOR][B]foo
[/B]...

---

### Post by Holger_Gehrke on 2015-01-30
Different Browser -> different Cookies by the search engine -> different search history and profile in the search engine -> different results. If you delete the Cookies in both browsers you should get -- more or less -- the same results.

---

### Post by CkDGTAT on 2015-02-10
How can I send the same cookies with lyxy?

---

