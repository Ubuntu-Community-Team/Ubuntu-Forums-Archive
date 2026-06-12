---
title: "Installing JAVA... for Azureus"
date: 2007-02-14
forum: General Help
---

### Post by WinterWeaver on 2007-02-14
Hi there!

I have always had a problem with Azureus, in that the program eats most of my CPU, leaving my system crippled while it's downloading. I read on the Azureus wiki that I need to have the latest Java installed for it to run smoothly without eating all the resources.
> Note: Using an old Java version, or having more than one installed, may cause severe problems like 100% CPU usage! If you have installed Azureus but it is behaving strangely (eg. no windows display after the program launches) you probably need to upgrade your Java.

Can someone please enlighten me as to which packages I need to install to get the right version etc.?

Thanks! ^_^

WW

---

### Post by fenian on 2007-02-14
I use sun java5-jre (from synaptic) and Azureus works fine though it's a bit of resource hog.

---

### Post by taurus on 2007-02-14
What version do you have right now?

Applications -> Accessories -> Terminal
```
java -version
```

Otherwise, try this guide.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by WinterWeaver on 2007-02-14
```
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

I'm looking at the guide now. Thank for the quick replies :)

---

### Post by WinterWeaver on 2007-02-14
OH WOW... That worked brilliantly!!

I installed SUN Java, and now Azureus doesn't eat my processor, AND my download speeds are soooo much higher !!

Thanks guys!   (hehe... hope I'm not speaking to soon... will keep an eye on it ;)  )

WW ^_^

---

### Post by Maestro23 on 2007-02-14
> **WinterWeaver said:**
> OH WOW... That worked brilliantly!!

I installed SUN Java, and now Azureus doesn't eat my processor, AND my download speeds are soooo much higher !!

Thanks guys!   (hehe... hope I'm not speaking to soon... will keep an eye on it ;)  )

WW ^_^

Glad it worked man. Remember, that Azureus is a resource hog by nature anyway though.

---

