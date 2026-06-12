---
title: "Firefox 3.0 crashes and freezes"
date: 2008-04-24
forum: General Help
---

### Post by gardara on 2008-04-24
After I have been running the new firefox for some time it starts freezing when I click on links and open tabs...
And firefox does also close itself when I close tabs, both when I have been running it for a short time and for long time.

I tried to run it from terminal too se some output when it crashes.

```
gardar@glappi:~$ firefox-3.0 
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
Segmentation fault

```

---

### Post by KrisWillis on 2008-04-25
I'm having the same problem, there are a few suggestions in my thread, but none of them worked for me, they might for you - [http://ubuntuforums.org/showthread.php?p=4788401#post4788401](http://ubuntuforums.org/showthread.php?p=4788401#post4788401)

---

### Post by gardara on 2008-04-26
> **KrisWillis said:**
> I'm having the same problem, there are a few suggestions in my thread, but none of them worked for me, they might for you - [http://ubuntuforums.org/showthread.php?p=4788401#post4788401](http://ubuntuforums.org/showthread.php?p=4788401#post4788401)

Thanks for the tip, however this didn't help me.

I have noticed firefox only closes itself when I close gmail.... Pretty strange.

---

### Post by rshel on 2008-06-02
Anybody ever figure this out?  Same exact thing for me.  Firefox 3 crashes when I close a tab with gmail.  Why did ubuntu include such a flakey beta version with the latest release, anyway?

---

### Post by Cain67 on 2008-06-13
Have got the same problem whenever i try to get into my hotmail account...

so no fix then?

---

### Post by MariusSilverwolf on 2008-06-13
So it most happens with GMail, Hotmail, or other java-intensive sites?

Firefox 3.0 RC1 is available in the repositories now, so you can update from Beta 5 to that.  You can also add "deb [http://ppa.launchpad.net/fta/ubuntu](http://ppa.launchpad.net/fta/ubuntu) hardy main to your repositories and update to RC2 from there.

If either of those fail, double-check your Javascript settings and [your java installation]("http://www.java.com/en/download/help/testvm.xml?ff3").  You may need to update your JRE.

---

