---
title: "Java java.lang.ArrayIndexOutOfBoundsException randomly popping up?"
date: 2007-11-07
forum: General Help
---

### Post by Lemons on 2007-11-07
It is the weirdest thing. Yesturday, I was running a program, that worked the previous night just fine. Now, I get this exception. I havnt modified code, but the only thing I can think is some modificiation with the Ubuntu update last night (I didnt read it, stupid me. Are there logs for this sorta thing?).

Heres the stack trace
```

Exception in thread "Thread-2" java.lang.ArrayIndexOutOfBoundsException: 65533
	at Class30_Sub2_Sub1_Sub4.method385(Class30_Sub2_Sub1_Sub4.java:152)
	at client.method18(client.java:332)
	at client.method102(client.java:7875)
	at client.method9(client.java:8711)
	at Applet_Sub1.run(Applet_Sub1.java:122)
	at client.run(client.java:4543)
	at java.lang.Thread.run(Thread.java:619)

```

Now, I have changed no code in the program, but this just suddenly pops up. I tried it with different java versions, using backed up code, and such. All this with no luck, im thinking of just formating my computer, cause its that frustrating. Anyone know whats up with this?

Thanks, Kris.

---

### Post by wieman01 on 2007-11-07
What sort of program is that? Have you programmed that on your own?

---

### Post by Lemons on 2007-11-07
I have not. Its a runescape client, and I tried it on a windows machine (Moms work computer), works fine. But on me and my sisters computers (Ubuntu 7.10), get the same error :S

---

### Post by wieman01 on 2007-11-07
Ok, what Java Runtime Environment have you installed? Sun's or the GNU one? Can you check that through Synaptic?

---

### Post by Lemons on 2007-11-07
Heres the list of the java VMs I tried:

_Java 6.0.0.3:_
/usr/lib/jvm/java-6-sun/jre/bin/java

_GNU Java:_
/usr/lib/jvm/java-gcj/jre/bin/java

_Java 5.?.?.?_
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java

GNU wont even load, cause it has an AWT exception thrown. I have no idea whats wrong :S

---

### Post by wieman01 on 2007-11-07
You could uninstall all VMs and try the one from Sun's website. Or possibly an earlier version.

---

### Post by Lemons on 2007-11-07
I tired reinstalling them, but ill get the ones off the site and try those as well. Thanks for the suggestion.

EDIT: Tried it, didnt work :S

---

### Post by wieman01 on 2007-11-07
If you have the chance please also post a bug report on Launchpad.

---

