---
title: "want to delete all the data."
date: 2013-02-13
forum: General Help
---

### Post by Akhj on 2013-02-13
Hello,

I have a faulty HDD which is under warranty and will be replaced by vendor. Earlier i had windows installed in it. So before replacing i installed Ubuntu in this disk. Will it erase all the data from it or service centre engineer can retrieve it ??
Please let me know.

---

### Post by schragge on 2013-02-13
Look at the packages [secure-delete]("http://manpages.ubuntu.com/manpages/precise/man1/srm.1.html"), [wipe]("http://manpages.ubuntu.com/manpages/precise/man1/wipe.1.html"), *nautilus-wipe*, [scrub]("http://manpages.ubuntu.com/manpages/precise/en/man1/scrub.1.html"), [dcfldd]("http://manpages.ubuntu.com/manpages/precise/en/man1/dcfldd.1.html").

---

### Post by Akhj on 2013-02-13
Thanks for your quick response but i am very new to Ubuntu, and i didn't get what you said.

---

### Post by mörgæs on 2013-02-13
Boot the computer with a USB stick / CD created with [http://www.dban.org/](http://www.dban.org/).

---

### Post by schragge on 2013-02-13
Search for said packages in *Software Center*, or install any of them from command line. I guess the *nautilus-wipe* extension should be the easiest for beginners, but I never used it.
To install all of them from command line, open the terminal window and put in
```

sudo apt-get install secure-delete scrub {nautilus-,}wipe dfldd

```

[color=blue]**Update.**[/color].
Sorry, ignore all I said. I didn't get that you don't have a working Ubuntu installation

---

### Post by Mark Phelps on 2013-02-13
Understand, that with a "faulty" HDD, none of the software solutions are likely to work.  I had a WD drive go bad and even tried using THEIR wiping program -- and it failed due to drive errors.

---

