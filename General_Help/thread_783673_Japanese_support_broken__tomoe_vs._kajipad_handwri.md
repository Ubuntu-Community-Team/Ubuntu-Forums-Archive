---
title: "Japanese support broken:  tomoe vs. kajipad handwriting recognition"
date: 2008-05-05
forum: General Help
---

### Post by TokyoYank on 2008-05-05
the [_Japanese HowTo for 7.10_]("https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_7.10_using_SCIM#head-227d86f63341994c48cc5bf37d4ff832bfacf45f") does not fully work for Hardy 8.04.  In particular, most/many things seem to work by simply System > Administration > Language Support.  (Though, it seems some people have problems with [_only English being offered as an option_]("http://ubuntuforums.org/showthread.php?t=684469&page=3").)  I got SCIM, the language picker, working with no fuss.  However, the handwriting recognition pad for writing in chinese characters (kanji) is not working. 

The package that used to exist is called scim-tomoe, and it adds an option in the language picker SCIM to use handwriting recognition.  When I use synaptic to search for "tomoe", I get no hits.  Search "scim" and get lots of hits, but nothing related to handwriting.  

Searching "handwriting" I found the package kanjipad.  It installs, however there is no menu icon.  There is no integration with the SCIM chooser.  Launching it manually from the command prompt works.  If no other option presents itself, I'll manually add a menu or panel launcher.

Googling tomoe and hardy, I see lists of source packages.. but why is there no actual package in the repos?  Did I do something wrong, or is it as broken as it seems?  

Thanks

---

### Post by fusebokme on 2008-06-01
Hi Everyone,
yeah, this is an issue, is there anyone who knows how to fix this. For people who use the Japanese IME a lot this is quite an important function and current Ubuntu documentation (see link in previous post) is not correct.
Thanks,
Futzl

---

### Post by TokyoYank on 2008-06-01
It appears that the behavior of ubuntu is greatly dependent on which repository you have set up.  Tomoe is listed in the repository indicated on a related thread:

[http://ubuntuforums.org/showthread.php?t=812552](http://ubuntuforums.org/showthread.php?t=812552)

Personally, I prefer to manually edit as few configuration files as possible, so I'm looking in to a way to add / modify the repository via GUI.  If I get it working I'll post instructions here

---

