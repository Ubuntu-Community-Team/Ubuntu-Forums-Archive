---
title: "ntfs partition - global locale option?"
date: 2007-07-11
forum: General Help
---

### Post by Klaxmar on 2007-07-11
Hello,
I have a troublesome ntfs external hard drive.
I have many files with different sets of non-western characters.
I did not see my files whose names had these non-western characters (exmaple: German or Russian characters).

I saw these threads:
[http://ubuntuforums.org/showthread.php?t=492093](http://ubuntuforums.org/showthread.php?t=492093)
[http://ubuntuforums.org/showthread.php?t=428145](http://ubuntuforums.org/showthread.php?t=428145)
[http://ubuntuforums.org/showthread.php?t=373332](http://ubuntuforums.org/showthread.php?t=373332)

I learned that I need to change my locale option to see them.

I have the problem though that my files are of many different locales.
I am still left with these questions:
Is there a way to provide a global locale option?
Can I provide multiple locale options?
How do I know which locale options I need?
Can I capture some list of which files were not displain because of locale settings?

Any help is greatly appreciated!!!

---

### Post by kroiz on 2007-07-11
I think that you do not have many locals because windows use only UTF16 and the local that you need to define for your mount, is the local you are using, in other worlds the local you want the UTF16 files to be converted to. which in most cases is utf8.
did you try putting there utf8?

---

### Post by kroiz on 2007-07-11
reading the other posts you attached I see that there is some token before the utf8 I don't know what it is for. maybe I was all wrong before.

---

