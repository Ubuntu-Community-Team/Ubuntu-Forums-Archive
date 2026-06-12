---
title: "aMule:  WHERE are the downloaded files?"
date: 2012-12-08
forum: General Help
---

### Post by catmontecatini on 2012-12-08
I, like many others, cannot find where my files are downloaded in AMULE 2.2.6.  I've followed suggestions from various blogs and have searched absolutely everywhere (with finder and in all library folders in Mac OS 10.8.2) for aMules's so called hidden file folder.  *...Niente!  *

Please and thank you!

---

### Post by Vaphell on 2012-12-08
default location in ubuntu is $HOME/.aMule (ctrl+h in file browser to unhide)
no idea about macos

---

### Post by catmontecatini on 2012-12-08
But I've tried this!

---

### Post by Vaphell on 2012-12-08
can't you open amule and right click on the downloaded files? there should be a local path listen among the file properties
also in amule preferences you can see its default directories and even change them to whatever you want.

---

### Post by cmcanulty on 2012-12-08
make sure you have view hidden files checked. The downloads are in /home/yourname/.amule/incoming

---

### Post by catmontecatini on 2012-12-08
I've done this too.  In preferences, there is a button *Directories*.  Therein was the default location for  *Incoming (which was Incoming/xxx/xxx and I changed to /Users/cat/Desktop) *and *Temporary* (/Users/cat/Library/Application Support/aMule/Temp). But I can't find these either.

I thank you for your patience.

---

### Post by Vaphell on 2012-12-08
i hope you don't expect us to know the layout of MacOS directories, do you? we are pretty much in the dark here.
can you look at properties of any downloaded file and tell us what path is there?

i think that change of the dir affects only future downloads, not the ones already completed.

---

### Post by catmontecatini on 2012-12-09
Vaphell,

Thank you for your assistance and no, I do not expect you to know about Mac directories.  We are both in the dark here.

I understand that my change in the directory only should affect only future downloads but there are files I seek from the previous setting.  Please tell me how I can view the properties of previously downloaded files as I don't understand this.   In aMule, I have no previous files as yet located/opened.

Cat

---

### Post by Vaphell on 2012-12-09
open terminal and try using *find*

```
find *<dir>* -iname '*incoming*' -type d
```
find in <dir> and its subdirs (name matching *incoming*, directory)

if you want to scan your $HOME, use ~
if you want to scan whole computer use / (will take a while)
i don't know anything about the mac config, if you suspect some other dir put its name right after *find*.

---

### Post by catmontecatini on 2012-12-09
> **Vaphell said:**
> open terminal and try using *find*

```
find *<dir>* -iname '*incoming*' -type d
```find in <dir> and its subdirs (name matching *incoming*, directory)

if you want to scan your $HOME, use ~
if you want to scan whole computer use / (will take a while)
i don't know anything about the mac config, if you suspect some other dir put its name right after *find*.

I am sorry but I opened the terminal and tried all of the above.  But I didn't get anywhere.  What exactly do I write in the terminal?

---

### Post by Vaphell on 2012-12-09
ask in this forum for apple users, i suspect you'll get your answer much faster there.
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

---

### Post by catmontecatini on 2012-12-11
Caro Vaphell,

I have put a note in a Mac forum.  I've located the files but they come up gray.  I've started again from scratch and we'llsee what happens.  Otherwise, I am going to let it go.

Enough!  THANK YOU!

Cat

---

