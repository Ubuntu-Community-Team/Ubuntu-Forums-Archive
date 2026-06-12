---
title: "Synaptic Package Manager's stored data"
date: 2007-02-09
forum: General Help
---

### Post by BobSongs on 2007-02-09
Somewhat Technical: Synaptic Package Manger stores its data in text files somewhere and I'd like to know exactly where it does. Here's the 'why'.

A friend has no Internet connection. All his repositories are on 4 DVDs. Now I've noted that when a DVD is added to Synaptic as a source it requests a title for the disk. No hassles there. But when re-added it doesn't. So it's saying that it has a file with the list of repositores on it related to that DVD/CD.

An older set of DVDs given to him lacked repository files. So I downloaded a new set for him to use. However he says that many of the files are missing needed to compile some software.

I'd like to be able to tell him where Synaptic stores the files that keep a record of what is found on the DVDs to see if starting anew might help. However this is where my knowledge of Synaptic comes to an end.

So, if you know where this/these file(s) are, please let me know. The Synaptic documentation doesn't reveal this.

Bob

---

### Post by dagnabit dang doohickey on 2007-02-10
I think you might find what you're looking for in /var/lib/apt/lists/

---

### Post by BobSongs on 2007-02-10
That's it! Many thanks!!

---

