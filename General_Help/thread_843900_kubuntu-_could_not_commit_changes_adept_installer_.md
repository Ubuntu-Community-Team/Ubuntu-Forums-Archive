---
title: "kubuntu- could not commit changes adept installer help"
date: 2008-06-28
forum: General Help
---

### Post by rawlwear on 2008-06-28
I'm running wubi kubuntu v8.04.1 & i can't install apps, I keep getting the same message in the adept installer, 

It says, there was an error commiting changes, possibly there was a problem downloading some of the packages or the commit would break packages. 

Any suggestions on how to fix this

---

### Post by ago on 2008-06-30
I do not think this is strictly wubi or kubuntu related, you might have to do some clean up in your installation

---

### Post by rawlwear on 2008-06-30
I dunno i've tried it about 5 times and it keeps doing it, what do you mean by clean up? how do i do that?

---

### Post by abn91c on 2008-07-01
did you do in a konsole sudo apt-get check or sudo apt-get clean
also try dpkg --configure -a

---

### Post by rawlwear on 2008-07-01
> **abn91c said:**
> did you do in a konsole sudo apt-get check or sudo apt-get clean
also try dpkg --configure -a

first two didn't work but when i go to try the last one it says this

dpkg: requested operation requires superuser privilege

any ideas?

---

### Post by ago on 2008-07-02
prepend"sudo " to all commands

sudo apt-get check
sudo apt-get update
sudo apt-get upgrade
sudo dpkg --configure -a

---

### Post by STPitcher on 2008-07-02
Hi.  I've been having the same problem.  Thanks... The command

[INDENT]sudo dpkg --configure -a [/INDENT]

told me there was something wrong.. It seemed to be in the middle of installing sun-java6-doc... Indeed, I'd attempted to install this the other day, and apparently it didn't work... or didn't finish.

I wasn't sure how to clear this, so I used ADEPT, located sun-java6-doc... it said it was installed... I told it to remove it, and I beleive things are now better.

Great help... I appreciate it!

- stp

---

### Post by rawlwear on 2008-07-04
is there anyway to fix this

dpkg: requested operation requires superuser privile says that when i tried sudo dpkg --configure -a

---

