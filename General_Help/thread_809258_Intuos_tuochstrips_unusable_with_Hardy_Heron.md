---
title: "Intuos tuochstrips unusable with Hardy Heron"
date: 2008-05-27
forum: General Help
---

### Post by mallow on 2008-05-27
Under Ubuntu 7.10 my Intuos tablet worked great. Since upgrade to Hardy Heron using it is a pain. At first all the tablet`s express keys didn`t work. Thanks to [this tip]("http://ubuntuforums.org/showpost.php?p=4784464&postcount=2") express keys do work, but only until I use a touchstrip. Then the expresskeys deamon is killed. If running in terminal, it gives: "Segmentation fault". I`ve upgraded to latest linux wacom driver following [this tutorial]("http://ubuntuforums.org/showthread.php?t=765915&highlight=wacom+hardy"), but it still doesn`t work.
Please help. I really need this tablet working. I wouldn`t like to downgrade to Gutsy Gibbon or worse - install Windows :(

---

### Post by ProhetOfDoom on 2008-06-15
Yes indeed. I upgraded from gutsy to hardy this weekend and have exactly the same problem.

The tip Mallow found also suggests we need the xlibs-dev package which isn't in the repositories anymore. Perhaps that's the issue. Any ideas anyone?

---

