---
title: "Did I run an untrusted/unsupported package for Timeshift?"
date: 2018-12-16
forum: General Help
---

### Post by G0at1 on 2018-12-16
Hello there! I watched a youtube video on Timeshift and they said to the run the following command, which I did but now I'm wondering if the first command was a legitimate command? I googled it and one website says it's untrusted/unsupported. What should I do? The PPA is now also showing up in my Sofware & Updates. [Also, how do you post terminal codes in here? They all go on one line. I'm a n00b :( ]    sudo apt-add-repository -y ppa:teejee2008/ppa     sudo apt install timeshift

---

### Post by oldos2er on 2018-12-16
What command did you run? You can copy and paste from the terminal into a post here. See also how to use code tags [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

> one website says it's untrusted/unsupported. Every PPA carries that warning, it's up to each use to decide if they want to enable it.

---

### Post by G0at1 on 2018-12-16
I ran these two (the teejee bothers me): 
```

sudo apt-add-repository -y ppa:teejee2008/ppa   
sudo apt install timeshift 
```

---

### Post by oldos2er on 2018-12-16
You posted the command just fine. You can also copy/paste all the command's output, which can be very useful for those helping you.

After you add a PPA (or any repo) you need to refresh your sources by running ```
sudo apt update
``` Then try the install command again.

---

### Post by G0at1 on 2018-12-16
Thank you, I'll post the output next time. I installed Timeshift a couple of days ago so the output is gone. So it looks like I have nothing to worry about with the teejee command. I just ran sudo apt update too. Thank you!

---

