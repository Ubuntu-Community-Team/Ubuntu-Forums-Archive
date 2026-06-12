---
title: "Junk Filters in Evolution"
date: 2007-11-11
forum: General Help
---

### Post by HowlingAtTheMoon on 2007-11-11
I have installed Ubuntu a week ago and am still working through all the possibilities and problems.  In Evolution Preferences, Junk filter tab there are 2 options to use Spamassassin - for which a plugin is not available, please check whether package is installed and Bogofilter - plugin available & binary is installed.

I can't find any info anywhere on either junk filter, how they work and therefore which would suit me better.  What does it mean that Bogofilter will convert all to binary?  Where does one find the plugins, such as spamassassin?

Help.:confused:
Thanks

---

### Post by scourge on 2007-11-11
You can install SpamAssassin from Synaptic or by typing "sudo apt-get install spamassassin". It usually does a better job of detecting spam than Bogofilter. The remote tests apparently make it more effective, but they can also make retrieving mail slow, sometimes slower than deleting the spam manually.

Where does it say that Bogofilter converts anything to binary?

---

### Post by HowlingAtTheMoon on 2007-11-12
Thanks for your help, I love how easy it is to do things, it just means thinking a little differently, particularly after a decade on Windows!  Regarding binary, I confused unicode and binary.  Spamassassin is installed and it reads, plugin is available and the binary is installed.  Further down under Bogofilter it reads, convert mail text to Unicode.  This is where I got it wrong, sorry.

Thanks again for the help.:redface:

---

### Post by scourge on 2007-11-12
You're welcome.

> Further down under Bogofilter it reads, convert mail text to Unicode. This is where I got it wrong, sorry.

Unicode is the universal character encoding system that Ubuntu uses by default. A lot of your incoming mail will probably have a different encoding (e.g. Western Europe), so it's a good idea to let Bogofiler convert the text.

---

