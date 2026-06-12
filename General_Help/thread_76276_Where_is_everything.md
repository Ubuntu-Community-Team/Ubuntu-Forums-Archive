---
title: "Where is everything??"
date: 2005-10-14
forum: General Help
---

### Post by kudu on 2005-10-14
No anjuta, clamav, firestarter, etc. etc. etc. Oh yeah, and how do I restore "Open Terminal" in the right-click menu options ?? Very useful and sorely missed.

None of the extra repositories seem to be up and running yet. Will they be available anytime soon ? I really need a lot of stuff I had in Hoary back up and running. Thanks!

kudu

---

### Post by DJ_Max on 2005-10-14
Did you do a clean install, or upgrade? Also, post your sources.list. The only repo's not up (which makes sense) are the backports.

---

### Post by dbott67 on 2005-10-14
[QUOTE=kudu]No anjuta, clamav, firestarter, etc. etc. etc. Oh yeah, and how do I restore "Open Terminal" in the right-click menu options ?? Very useful and sorely missed.

None of the extra repositories seem to be up and running yet. Will they be available anytime soon ? I really need a lot of stuff I had in Hoary back up and running. Thanks!

kudu[/QUOTE]

To enable the repositories change your sources.list file as noted in the [following thread]("http://www.ubuntuforums.org/showthread.php?p=411974#post411974").

After that, to get the "Open Terminal" back in the context menu:
```
sudo apt-get install nautilus-open-terminal
```

-Dave

---

### Post by kudu on 2005-10-14
I did a clean install.  Wait while I do a quick check...

Ah! Yes that was it. I had un-commented out ALL the extra repositories including backports and that caused synaptic to choke and put the kybosh on all the following repsitories in the file. Thanks, you fixed it. :)

kudu

---

### Post by kudu on 2005-10-14
dbott67...THANK YOU!!

regards,
kudu

---

### Post by dbott67 on 2005-10-14
You're welcome!

---

