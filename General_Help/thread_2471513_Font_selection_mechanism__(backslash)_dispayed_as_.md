---
title: "Font selection mechanism: \ (backslash) dispayed as ¥ (yen) in web page"
date: 2022-02-01
forum: General Help
---

### Post by dimitri-papadopoulos on 2022-02-01
This is probably a [Fontconfig]("https://www.freedesktop.org/wiki/Software/fontconfig/") question and I may file a bug upstream, but I thought I would ask here first.

On my Ubuntu 20.04 workstation, the web page of a Microsoft product displays **DOMAIN¥*login*** instead of **DOMAIN*\login***, both in Firefox and Google Chrome. I can reproduce this issue using the attached minimal HTML page [ATTACH]289934[/ATTACH]. It looks like the Japanese font "*Meiryo UI*" is selected, a font that displays ASCII character U+005C as ¥ (yen) instead of \ (backslash), and yet:
[LIST]
[*] the explicitly specified language of the HTML page is not Japanese (**"fr"**), 
[*]the explicitly specified content type of the HTML page has nothing to do with Japan (**"text/html;charset=UTF-8"**), 
[*]the system locale is not Japanese(**"fr_FR.UTF-8"**). 
[/LIST]
 As can be seen from [Bugzilla #]("https://bugzilla.mozilla.org/show_bug.cgi?id=1753007")[1753007]("https://bugzilla.mozilla.org/show_bug.cgi?id=1753007"), it's really a question of font selection, nothing the browser can fix. Unfortunately, it looks like there is no mechanism to inform Fontconfig that "*Meiryo UI*" is tailored for Japan and unable to display U+005C as a \ (backslash), as would be expected outside of countries such as Japan or Korea.

Now the details:

1. The Microsoft HTML page requests hardwired fonts, obviously I cannot change that page. Curiously, "*Segoe UI*" is missing from that list of hardwired fonts.```
font-family: "Segoe UI Webfont",-apple-system,"Helvetica Neue","Lucida Grande","Roboto","Ebrima","Nirmala UI","Gadugi","Segoe Xbox Symbol","Segoe UI Symbol","Meiryo UI", ...
```
2. I do have both Microsoft fonts "*Segoe UI*" and "*Meiryo UI*" installed in [FONT=courier new]/usr/local/share/fonts[/FONT]., but no "*Segoe UI Webfont*".
3. Note that "*Segoe UI Webfont*" is not in the list of Microsoft fonts, unlike "*Segoe UI*" or "*Segoe UI Symbol*" ([https://docs.microsoft.com/en-us/typography/font-list/#s](https://docs.microsoft.com/en-us/typography/font-list/#s)).
4. Because my system does have "*Segoe UI*" but not "*Segoe UI Webfont*", the next hardwired font "*Meiryo UI*" is selected instead.

I realize this is probably a bug in the Microsoft product: they should probably add "*Segoe UI*" in front of "*Segoe UI Webfont*" in the list of hardwired fonts requested by their HTML page. I realize I could simply delete Japanese (or Korean) fonts from my machine too, but I do view Japanese or Korean pages from time to time, so I would rather keep these fonts.

I'm just wondering. How does it work on Windows? Does Windows substitute "*Segoe UI*" for "*Segoe UI Webfont*"? If so, shouldn't Fontconfig perform the same substitution?

---

### Post by dimitri-papadopoulos on 2022-02-02
Thanks to the reviewer of [Bugzilla #]("https://bugzilla.mozilla.org/show_bug.cgi?id=1753007")[1753007]("https://bugzilla.mozilla.org/show_bug.cgi?id=1753007") for providing additional information: it turns out that even Windows does not perform any kind of substitution. What happens on Windows 10 is that "*Segoe UI Webfont*" is **not** selected, instead the next available font is selected, which is "*Ebrima*" in his case. Unfortunately, on my Linux machine, the next available font is "*Meiryo UI*", which is not suited to non-Japanese context.

This really is a bug in the server: the CSS style fails to specify "*Segoe UI*" and instead specifies "*Segoe UI* Webfont" although no font is provided by the server with [FONT=courier new]@font-face[/FONT]. Additionally, it goes on hardwiring a non-sensical list of fonts, including a Japanaese font which in my case is unfortunately the first available in the list.

---

### Post by Holger_Gehrke on 2022-02-02
Take a look at the documentation for fontconfig in '/usr/share/doc/fontconfig/'. You could set up a personal configuration file and have an alias for "Segoe UI Webfont". Running your browser from a terminal with FC_DEBUG set to a value of 2 (MATCHV) should tell you what font matching is done.

Holger

---

