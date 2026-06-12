---
title: "I broke /usr/lib"
date: 2007-10-26
forum: General Help
---

### Post by camini on 2007-10-26
By moving the file **libstdc++-libc6.2-2.so.3** - received from my bank - in the /usr/lib I must have broken something as now firefox nor thunderbird will start..

I'm running gutsy and would like to restore this situation - any advice on what I can do?

What puzzles me is I don't think this file existed in /usr/lib in the first place..  Could somebody please check - I could have it sent to my mail if it existed...

your help is appreciated

Any other way to download libraries from a repo?

pm

---

### Post by thelocust on 2007-10-26
you can reinstall in synaptic

---

### Post by camini on 2007-10-26
..guess what..
synaptic doesn't start either..

can somebody show me the results of following command (in gutsy):

ls -l /usr/lib/*std*

thanks!

Is there a way to get the correct lib files from the installation CD?

---

### Post by Maestro23 on 2007-10-26
> **camini said:**
> ..guess what..
synaptic doesn't start either..

can somebody show me the results of following command (in gutsy):

ls -l /usr/lib/*std*

thanks!

Is there a way to get the correct lib files from the installation CD?

Here's mine. Gutsy 64-bit:

> lrwxrwxrwx 1 root root      33 2007-10-20 03:35 libgstdataprotocol-0.10.so.0 -> libgstdataprotocol-0.10.so.0.13.0
-rw-r--r-- 1 root root   16224 2007-10-05 14:07 libgstdataprotocol-0.10.so.0.13.0
lrwxrwxrwx 1 root root      18 2007-10-20 08:47 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r-- 1 root root  829360 2007-07-29 15:36 libstdc++.so.5.0.7
lrwxrwxrwx 1 root root      18 2007-10-20 03:35 libstdc++.so.6 -> libstdc++.so.6.0.9
-rw-r--r-- 1 root root 1014808 2007-09-28 19:51 libstdc++.so.6.0.9


---

### Post by camini on 2007-10-26
which is what I have also.

I can't believe I broke my install by just adding a new file in /usr/lib
i'm gonna be sick

---

### Post by camini on 2007-10-26
Fixed it by retrieving lib file from a Feisty install. phew..
thanks for the dumps etc..

---

