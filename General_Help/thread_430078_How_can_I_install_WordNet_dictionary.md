---
title: "How can I install WordNet dictionary?"
date: 2007-05-01
forum: General Help
---

### Post by kwilliam on 2007-05-01
I often look up words with Kdict, KDE's dictionary application.  It uses dict.org by default, but I don't want to be tied to the Internet for a dictionary, and dict.org lists far more sources than I want to look through.

In Dapper, there was a dict-wn package that I could install, and by pointing Kdict to "localhost" it would use that.  *In Feisty, there isn't a dict-wn package*!  There is a "wordnet" package but it didn't install the dict server.  Many of the other dict packages are there, such as dict-gcide, dict-foldoc and dict-jargon, but not the one I happen to want.  How can I install the WordNet dictionary for dict?  Can I compile it from somewhere?

(If you don't know what I'm talking about, take a look at [this article](http://blogs.pcworld.co.nz/pcworld/tux-love/2007/04/hidden_linux_the_dict_differen.html).)

---

### Post by kenos on 2007-05-15
I ran into this same problem trying to install the Ichthux desktop. To get around this I downloaded the dict-wn deb from the hoary repository.  It required several dependencies - dict-server & dict-gcide both of which I could install via apt from Feisty sources.  After those were installed I dpkg'd the dict-wn deb and all is working well now.

---

### Post by kwilliam on 2007-05-16
I have had success! I googled "dict-wn" and downloaded the .deb from the Debian repository.  ([http://packages.debian.org/oldstable/text/dict-wn)](http://packages.debian.org/oldstable/text/dict-wn)).  I wasn't sure if it would work, but it did.  Didn't have any dependency problems either!  And now I come back to report my success to see that somebody beat me to it by 23 hours. ;-)

Now I can get my dictionary faster, and offline.  Now to try the same thing with Kdar...

I wonder how I can contact the MOTU team and tell them to copy the Debian package into the Feisty repository. ??

---

### Post by olskar on 2007-05-17
How am I able to browse the swe-eng dict dictionary offline with the bulitin dictionaryapplication in ubuntu?

---

### Post by kwilliam on 2007-05-19
> **olskar said:**
> How am I able to browse the swe-eng dict dictionary offline with the bulitin dictionary application in ubuntu?

Install dictd and dict-freedict-swe-eng.  You can install them using the graphical Synaptic Package Manager, or simply paste
```
sudo apt-get install dictd dict-freedict-swe-eng
```
in a terminal and hit ENTER.

(This next part is taken from [http://ubuntuforums.org/showthread.php?t=145949](http://ubuntuforums.org/showthread.php?t=145949). Since I don't use Gnome, II haven't actually tested it.)

Then change the preferences in gnome-dictionary.
-- Applications > Dictionary opens gnome-dictionary
-- Edit > Preferences
-- change server to localhost
-- change the Database to "search all databases"

Hope that helps!  (Note that this switches the dictionary application to be offline all the time.)

---

