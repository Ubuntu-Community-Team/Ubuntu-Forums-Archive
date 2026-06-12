---
title: "Sudo"
date: 2004-11-04
forum: General Help
---

### Post by Burgundavia on 2004-11-04
I am just asking a question regarding sudo. I find that when I have any program that is sudoed, opening any other program that requires sudo does not require my password. I view this is as a fairly major hole. Am I correct in this? Is this just a problem with gksudo or is it sudo itself?

Corey

---

### Post by diebels on 2004-11-04
Only a 15 minutes hole / time limit. See ```
man sudo
```

---

### Post by Burgundavia on 2004-11-04
15 minutes is an age in computer time. Could this not be one ticket that get used up when a program is run.

Corey

---

### Post by Burgundavia on 2004-11-04
Found an option timestamp_timeout, that if set to 0 always prompts for the password

Corey

---

### Post by diebels on 2004-11-05
> 15 minutes is an age in computer time.Sure, but it's for your own convenience. Adjust it to 0 if you'd like:
```
export ME=$USER
sudo -s
echo "Defaults:$ME timestamp_timeout=0" >> etc/sudoers
```

---

### Post by HungSquirrel on 2004-11-05
If you're paranoid that your kid brother/roommate/girlfriend/local law enforcement might hop on your machine for a few minutes of fun with root, tell XScreenSaver to come on after a few minutes and to lock the screen when it starts.

---

