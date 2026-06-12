---
title: "Installing application."
date: 2014-11-30
forum: General Help
---

### Post by Furycd001 on 2014-11-30
HI

If I want to download and compile an app. Is there any way of finding out what dependencies I need to install...


Many thanks.

---

### Post by mcduck on 2014-11-30
The website where you downloaded the source code should also tell you the requirements (although you might have to figure out the actual package names yourself). Or, the downloaded code should come with a readme file with such information.

In worst case you'll just have to try compiling it, and the install dependencies based on the error messages. Although if the developer didn't bother writing any documentation at all, you might want to consider if he's work is really worth installing in the first place... :D

---

### Post by HermanAB on 2014-11-30
After downloading, inside the tar ball, there should be two files called README and INSTALL.  Read them.

---

### Post by oldos2er on 2014-11-30
We have a [forum]("http://ubuntuforums.org/forumdisplay.php?f=44") that's dedicated to compiling software, although it doesn't see much traffic. If you need further help please consider posting there.

---

### Post by Impavidus on 2014-11-30
There are no rules for finding the dependencies. With a bit of luck, there is a list of all dependencies in the documentation of your download. Else, use your instinct.

When you figured out which libraries you need, you must install the development versions of these libraries (like **libfoo-dev** to install the foo library). These include the header files. The easiest way is using synaptic.

---

### Post by Furycd001 on 2014-12-05
Thank you guys for all the help :-) To sort out my problem I ended up contacting the developer.

---

