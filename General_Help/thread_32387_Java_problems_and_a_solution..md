---
title: "Java problems and a solution."
date: 2005-05-07
forum: General Help
---

### Post by packetcat on 2005-05-07
This is one of those it worked for me but may not for you topics. Hey if it works and the solution is harmless, try it. 

**To fix my Java I removed the Firefox Adblock extension.**

History below.

Ok so I was having funkiness  with Java after installing per this guide: 

[5.04 Starter Guide](http://www.ubuntuguide.org/#jre) 

Using Firefox I would get inconsistant results using the tests here:

[Test Java Virtual Machine (Sun)](http://www.java.com/en/download/help/testvm.xml) 

and here:

[java.com Hot Games, Cool Apps (Sun)](http://www.java.com/en/) 

What would happens is sometimes the applet would work and then going back in the same session it wouldn't or I would get 100% CPU usage and it stayed there, even  after closing Firefox, until I rebooted X or Firefox would just lock up and need a force quit. Sometimes the applet would work but take forever to load or only half work, like at the first link the text showed Java installed correctly but the little guy wouldn't dance. All in all it was just overall funkiness. A "I can't point a finger at it" problem. I tried everything I knew, clearing all caches including the java cache, made sure all modules were registered and in the right places, ran java-version, everything I knew and all checked out ok.

**What I did to fix it!**

[COLOR=Red]I removed the Adblock extension form Firefox.[/COLOR]

That's it, after that anytime I went to those tests they loaded fast and worked like a charm. I don't know why or how but it worked.

I didn't even have any filters active in Adblock to block anything, even with Adblock disabled there still was the problem. I had to uninstall it totally, which was easily done from the tools/extensions dialog in Firefox.

Thanks.

---

### Post by defkewl on 2005-05-07
Write this down in wiki please :)

---

### Post by Dogmeat on 2005-06-01
To everyone who can't see java applets in firefox: Check [this](http://www.ubuntuforums.org/showthread.php?p=195333#post195333) out too, it's another issue that may be prevening your applets from loading!

---

