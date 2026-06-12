---
title: "Crossover Linux help installing"
date: 2007-01-15
forum: General Help
---

### Post by lyceum on 2007-01-15
I wanted to try installing crossover Linux, I downloaded the program, followed the "how to" but when I pasted the command into terminal, it told me that the file did not exist. I tried sudo, but the same happened. I sent them an e-mail, but no response. It is suppose to be easy to install, what am I doing wrong?

Thanks!

---

### Post by taurus on 2007-01-15
Sounds like you are in the wrong directory when you run the installer!  Where did you download it to, ~/Desktop perhaps?

---

### Post by lyceum on 2007-01-15
> **taurus said:**
> Sounds like you are in the wrong directory when you run the installer!  Where did you download it to, ~/Desktop perhaps?

Yes, I downloaded it to the desktop. I thought I might have it in the wrong place. Where should it be?

---

### Post by taurus on 2007-01-15
It's not in ~/Desktop!

```
ls -la ~/Desktop
```
Otherwise, look in your $HOME directory.

```
ls -l ~
```

---

### Post by lyceum on 2007-01-15
not knowing a lot about terminal codes, and not being with my laptop where I can install it (I was not expecting to get a response this soon) I can see the file on my desktop, I am guessing that is your ~/Desktop. So to look for it do i type your command, inserting the file name? Sorry for all the questions, again, I am still new at terminal. I normally just cut and paste what someone else has giving me.

---

### Post by taurus on 2007-01-15
Just cut and paste these two commands to a terminal.

```
cd ~/Desktop
ls -l
```

---

### Post by lyceum on 2007-01-15
Great, Thanks!

---

### Post by lyceum on 2007-01-15
Your code worked like a charm! Thanks again!!!

---

