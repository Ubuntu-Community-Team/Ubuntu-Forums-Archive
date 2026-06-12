---
title: "help! i killed libxau6 and nothing works"
date: 2007-11-03
forum: General Help
---

### Post by anstosa on 2007-11-03
im relatively new to ubuntu. and as i was going about trying to get my nvidia card to show my dual screen setup correctly it somehow got into my head that i needed to replace 'libxau6' with an older version, i guess it didnt occur to me that it would be bad to just get rid of it. so i did. i hit the remove button on the package manager and it removed. everything went dowbhill after that. i couldnt get anything (including internet connection or terminal to work) all i could do is reboot and i ended up in text only. it wont load the gui. i tried

       sudo apt-get install libxau6

to see if i could reverse the damage and it was all going good for 3 lines of code when i got

       Package libxau6 is not available, but is referred to by another package,
       This may mean that the package is missing, has been obsoleted, or
       is only available from another cource
       E: Package has no installation candidate 

any help getting that package back would be amazing

---

### Post by Maestro23 on 2007-11-03
**libxau6** is in the repositories.  Make sure you have Universe/Multiverse enabled.

---

