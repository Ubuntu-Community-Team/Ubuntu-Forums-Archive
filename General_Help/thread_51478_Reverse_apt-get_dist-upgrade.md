---
title: "Reverse apt-get dist-upgrade?"
date: 2005-07-24
forum: General Help
---

### Post by cam8001 on 2005-07-24
Hi there. I foolishly (but innocently!) ran apt-get dist upgrade, thinking it was the right  thing to do. Now I am running on a 2.6 kernel, meaning I can't do much in terms of installing drivers and the like (with me level of knowledge). Can I go back? Is there a command I can run or process I can take to go back to the standard kernel for Hoary?

Thought I'd post this to:

cam@funk:~$ uname -r
2.6.10-5-386

---

### Post by ubuntp on 2005-07-24
run boot-admin and select the 2.4 kernel as default

---

### Post by cam8001 on 2005-07-24
I'm not sure how to run boot-admin under Ubuntu...I had a look around and couldn't find a way to get it to go (google and forums). I also assume that this would mean the 2.4 kernel would be in my Grub list for this to be an option - it's not, I only have 2.6 and 2.6 recovery mode.

---

