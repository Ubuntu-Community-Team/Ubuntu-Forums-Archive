---
title: "Grub2 no longer boots all oses"
date: 2018-05-03
forum: General Help
---

### Post by ardwarefreak on 2018-05-03
hd1 w7 and 16.04 
Hd2 w7 seperate install program only
Hd3. W7 from hd2 documents

Grub2 was on hd1 and would seamlessly could load all three oses. 

tried to use grub customizer to change grub background image and w7 on hd1 no longer functions. Load up to w7 logo then reboots or says startup repair failed. ubuntu and h2+3 w7 load fine

unplug all hdds except hd1 and grub can load w7 and Ubuntu  on hd1 no problem.

Would this be a grub issue or a w7 problem? And what to do?

---

### Post by flocculant on 2018-05-03
Given that what you did with grub customiser appears to have broken your grub then I'm not sure why you're blaming something else :)

What happens if you undo what you did to make it stop working?

---

### Post by ardwarefreak on 2018-05-03
although I understand the initial cause stemmed from the use of customizer, I don't understand what modification was made in simple image change that would lead to a grub2 breaking. Large fonts are known to break grub2, but that wasn't changed here. In addition I don't have a way of going back to the original config, since I have already removed the image modification but the issue persists.

---

### Post by monkeybrain20122 on 2018-05-03
I agree that you broke grub with customizer, Lesson is that dualboot with Windows is a fragile configuration, if you get it working just leave it alone. As I recall grub customizer is always kind of dangerous,--and adding Windows in the mix makes it even more risky,-- you don't want to fool around with grub unnecessarily and frankly i don't know why people would even care about the appearance of grub menu,  you don't have to look at it once you are booted up, if you have to stare at it for a long time something is wrong because of the slow boot. if it does the job, leave it.

---

