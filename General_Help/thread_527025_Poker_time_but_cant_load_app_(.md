---
title: "Poker time but cant load app :("
date: 2007-08-16
forum: General Help
---

### Post by RobertQQ on 2007-08-16
Hi All!! I am trying to run ultimatebet but i cant get it to load. I installed wine and IE6 and that got me to the point of being able to install ultimatebet but when I try and open it......it starts to load then shuts off. Can anyone help me get this up and running thanks.

---

### Post by Happy_Man on 2007-08-16
Try running it from a Terminal (Applications --> Accessories --> Terminal) and see what you get:

```
wine "/path/to/ultimatebet.exe"
```

---

### Post by RobertQQ on 2007-08-16
I found instructions through google on how to install but now when i get to the point of installing it stops on the first thing it tries to install which is a txt file and says i dont have permission. It also tells me to make sure my diak is not full which its not, then it tells me to make sure i have permission to the dierectory. Im not sure what all this means or if i am doing something stupid or not but any help will be greatly appreciated. Thanks!!

---

### Post by RobertQQ on 2007-08-16
oh 1 last thing im doing using the instructions from this site [http://www.linux.com/articles/51603](http://www.linux.com/articles/51603) Thanks again!

---

### Post by Happy_Man on 2007-08-16
Oh, then use ```
sudo wine "path/to/ultimatebet.exe
```

---

### Post by RobertQQ on 2007-08-16
Thanks for the help Happy_Man!! adding sudo helped...but now when i get past the license agreement it says i need at least IE4 to install but I do have IE6 installed. Do I need to save it in a different directory besides tmp?? Thanks again for the help!!

---

### Post by RobertQQ on 2007-08-16
i tried changing the directory to under the windows temp file but same problem ...need IE4 to install. I do have IE6 so im not sure what im doing wrong?! Thanks again for the help!!

---

### Post by Happy_Man on 2007-08-16
> **RobertQQ said:**
> i tried changing the directory to under the windows temp file but same problem ...need IE4 to install. I do have IE6 so im not sure what im doing wrong?! Thanks again for the help!!
I'm.... not sure. More than likely this is just another quirk of the application. Sorry, but I can't help more than that.

---

