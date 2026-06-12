---
title: "The file should be owned by root.root"
date: 2008-03-30
forum: General Help
---

### Post by Bernie01 on 2008-03-30
Hello,

Cany body please tell me what this means?

---

### Post by mcduck on 2008-03-30
Without getting any more information about what you are trying to do, all I can say that you have a file that has wrong owner and group. The file should be owned by root and group root, but it's not.

---

### Post by Bernie01 on 2008-03-30
Thanks mcduck. I have recently installed Frostwire and needed to download some updates to make it work properly. It was not accepting data input for searching and I found through this forum that I needed to instal java updates which I did. It was a few weeks ago so I am not sure which ones. I now have several updates available from the repositories and when I try to download them I get the following message:-

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

When I try to run 'dpkg --configure -a' in the terminal I get this message:-

"Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]"

Are you able to translate this into simple language?

---

### Post by pointone on 2008-03-30
[http://ubuntuforums.org/showthread.php?t=713234](http://ubuntuforums.org/showthread.php?t=713234)

---

### Post by Bernie01 on 2008-03-30
Thanks pointone. I will try this tonight when I get home.

---

