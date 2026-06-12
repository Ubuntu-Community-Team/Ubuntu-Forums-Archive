---
title: "ua-parser-js on Ubuntu?"
date: 2021-10-23
forum: General Help
---

### Post by UBUminJ on 2021-10-23
Having read on heise.de about the hacked javascript library UAParser, I wonder if it is on my Ubuntu.
How can I find out?

Hacked packages: 0.7.29, 0.8.0 and 1.0.0

They seem to contain malware, cryptominer.

---

### Post by Holger_Gehrke on 2021-10-23
That really depends ... Are you using node.js (a system for using JavaScript outside of a browser, either on the desktop or on a server) ? If not, than the probability of the module being on your system is very low. If you're using node and got the package 'node-ua-parser-js' for it from the Ubuntu repositories, then again the probability is low since the newest version in the repositories is 0.7.24 (in Ubuntu 21.10, older releases get even older versions). So you are only likely to have a problematic version of this library if you use node.js and installed the library using npm (nodes own package manager).

If you think you might have this module on your system (it really only makes sense if you're running a web-server written in JavaScript, the purpose of the lib is parsing a received UserAgent-String that a server gets from a browser), you could run "find / -name 'ua-parser.*'" (which would scan all mounted file systems for a file with a name starting with 'ua-parser.'; this obviously can take a while).

Holger

---

### Post by UBUminJ on 2021-10-23
Thanks Holger,
I don't know if any of the programs on my Ubuntu use Javascript outside the browser - that is the problem. Personally, I don't.
Running your advice "sudo find / -name 'ua-parser.*'", doesn't find anything. Good news.
Thanks again.

---

