---
title: "Merge mbox files"
date: 2007-12-26
forum: General Help
---

### Post by GMWeezel on 2007-12-26
I have 2 mbox files both of which are copies of my inbox but at different times. Being as such, there are a lot of duplicate messages between them however one of them has emails I deleted later on. Is there a way I can merege two mbox files so that messages are not duplicated but it is still a combination of both of them? The only idea I have is to find a program (which I have been unable to do thus far) that will slice an mbox file into separate files for every email then compare the files to each other.

---

### Post by psusi on 2007-12-26
To combine the two mbox files, just use cat:

cat a b > c

If you use Thunderbird, there is a plugin you can get to find and remote duplicate messages.

---

### Post by jpkotta on 2007-12-26
How about diff or diff3?  There are many GUI tools that make it easy to use these.  Googling a bit, I see meld is pretty easy to use.

---

### Post by bobslaughter on 2008-01-03
Seems easy enough to merge the actual mbox files, but what about Evolution's index and meta-info files? For example, for a "linux" folder, I have:

linux.ibex.index.data
linux.ibex.index
linux.ev-summary
linux
linux.cmeta

If I merge another mbox file into 'linux' (and evolution isn't running), will these files simply get rebuilt when evolution starts up again, incorporating the changes? Or will I have created a Really Huge Mess (tm)?

---

### Post by tek1024 on 2008-02-25
I'm curious if you ever found an answer to this question. Please pardon the "bump" of an old thread.

---

### Post by HermanAB on 2008-02-25
AFAIK you can delete the meta files and Thunderbird or Evolution will then recreate them.

---

