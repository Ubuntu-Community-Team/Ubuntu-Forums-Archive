---
title: "lynx web browser with java ?"
date: 2013-04-07
forum: General Help
---

### Post by goof on 2013-04-07
hi im using lynx web browser and am liking it but lots of web pages have text missing and the message "please enable javascript" obioulsy there arint any addons for this browser that i can find does anyone know of a way to install java for lynx? i already have java jre+jde installed on ubuntu 12.04 thanks.

---

### Post by cbraxton on 2013-04-07
You might try elinks instead, it has some limited javascript support.

---

### Post by schragge on 2013-04-07
To begin with, [JavaScript is not Java]("http://kb.mozillazine.org/JavaScript_is_not_Java"). As to JavaScript in text browsers, try [elinks]("http://manpages.ubuntu.com/manpages/precise/en/man1/elinks.1.html"), [links2]("http://manpages.ubuntu.com/manpages/precise/en/man1/links2.1.html"), or [w3m]("http://manpages.ubuntu.com/manpages/precise/en/man1/w3m.1.html"). At least, *elinks* should [partially support]("http://elinks.or.cz/documentation/manual.html#ecmascript") JavaScript (support is disabled in recent Debian/Ubuntu packages, recompile the package from source to enable). Early versions of links2 also supported JavaScript, but support was dropped from later releases. w3m doesn't support it out of the box, but there's an extension, [w3m-js]("http://en.sourceforge.jp/projects/w3m-js/"). There is a text browser in Ubuntu repositories with JavaScript support enabled (using the same [Mozilla SpiderMonkey]("https://developer.mozilla.org/en-US/docs/SpiderMonkey") library as elinks), but a very peculiar one. It's [edbrowse]("http://manpages.ubuntu.com/manpages/precise/en/man1/edbrowse.1.html"). If you ever used the [ed]("http://manpages.ubuntu.com/manpages/lucid/en/man1/ed.1posix.html") editor, you may like it. Otherwise, I very doubt you'll find it usable. It's mainly interesting for blind users and for scripting.

---

