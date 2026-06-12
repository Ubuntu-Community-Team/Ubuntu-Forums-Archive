---
title: "Russian font problem"
date: 2014-03-09
forum: General Help
---

### Post by Cudo29 on 2014-03-09
In my Firefox, the pages including cyrillic fonts such as Russian pages were displayed with too broad font like multibyte Japanese strings.
And I found a thread discussing the same problem.
[ubuntu] Russian font problem
[http://ubuntuforums.org/showthread.php?t=2071844](http://ubuntuforums.org/showthread.php?t=2071844)

But no solution was posted and it is already closed.
Then I tried some other solution by my own effort to solve it.

I describe the detail.

1. Open Firefox menu [Edit]-[Preferences] ([&#32232;&#38598;]-[&#35373;&#23450;] in Japanese) to open the "Firefox Preferences" (Firefox&#12398;&#35373;&#23450;) dialog.
2. Click [(A)dvanced...] &#65288;[&#35443;&#32048;&#35373;&#23450;(A)...]) in the [Fonts & Colors] ([&#12501;&#12457;&#12531;&#12488;&#12392;&#37197;&#33394;]) group of [Content] ([&#12467;&#12531;&#12486;&#12531;&#12484;]) tab to open "Fonts" dialog.
3. Select [?] (perhaps cyrillic or similar, in Japanese [&#12461;&#12522;&#12523;&#25991;&#23383;]) from the list in the [Select a language to add…] ([&#23550;&#35937;&#35328;&#35486;]).
4. Change the value of Serif (&#26126;&#26397;&#20307;) to another font which support cyrillic narrow font such as Arial.
5. Also change Sans-serif (&#12468;&#12471;&#12483;&#12463;&#20307;) as Serif.
6. Click [OK] button to close Fonts dialog.
7. Click [Close] to close Firefox Preferences dialog.

I checked the information above in following environment
Ubuntu 12.04 + Firefox 27.0.1

The following page also help the setting described above.
[URL="http://mzl.la/PBZPEY"]Settings for fonts, languages, pop-ups, images and JavaScript | Firefox Help
http://mzl.la/PBZPEY[/URL]

I hope it helps someone.

---

