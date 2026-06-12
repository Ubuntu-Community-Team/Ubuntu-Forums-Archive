---
title: "Java problems in Opera on Breezy"
date: 2005-10-23
forum: General Help
---

### Post by Wrosmo on 2005-10-23
I have installed opera-static 8.50-20050916.1 on ubuntu 5.10.

It worked fine. But then I installed java (jre-1_5_0_05-linux-i586.bin) after these instructions:  [http://www.ubuntuforums.org/showthread.php?t=76702&page=2](http://www.ubuntuforums.org/showthread.php?t=76702&page=2) (comradevik's post)

Java works fine in Firefox. In Opera I choose the rigth path to the java plugin (Tools -> Preferences -> Advanced -> Content -> Java Options), and validate the path. Opera replies: 'The Java path seems to specify a valid directory.'

But when I enter a webpage with java content, Opera just quits.

Any ideas?

PS. I have tried installing the opera package (8.50-20050916.5)(shared-qt) from 'http://deb.opera.com/opera/ stable non-free' via Synaptic but it depended on libqt3c102-mt and this is not available for breezy.

PPS. I also tried installing from the unstable repository (8.50-20050916.6) which is soppused to work with breezy, but when I try to start it I get 'segmentation fault' as response in the termnal. I read in some forum, that it was impossible to install the unstable version after having installed the stable version. Can this be true?

---

### Post by Z0l on 2005-10-26
Check out the the [wiki]("https://wiki.ubuntu.com/OperaBrowser"), solution is there.

---

### Post by Wrosmo on 2005-10-26
Thank you.
I'll try that rigth away.

---

### Post by Wrosmo on 2005-10-28
It worked. Thank you a lot.

---

