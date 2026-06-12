---
title: "Simple question regarding running from terminal"
date: 2006-10-05
forum: General Help
---

### Post by PigCorpse on 2006-10-05
Okay, I have a seemingly simple question.

Let's say I type "kwrite" in the terminal. It'll open up kwrite. Now, if I close the terminal that I ran kwrite in, kwrite will close. Can someone basically explain the basics as to why this happens? I'm not saying it's stupid or that it shouldn't happen. I'm just curious as to how it works.

Thanks!

---

### Post by mitch.c on 2006-10-05
> **PigCorpse said:**
> Okay, I have a seemingly simple question.

Let's say I type "kwrite" in the terminal. It'll open up kwrite. Now, if I close the terminal that I ran kwrite in, kwrite will close. Can someone basically explain the basics as to why this happens? I'm not saying it's stupid or that it shouldn't happen. I'm just curious as to how it works.

Thanks!
That happens because you are telling the terminal to run kwrite in the foreground, so when you close the terminal, it ends the child process running kwrite. What you want to do is start kwrite in the background. All you have to do is add the '&' character after the command like this:
```
kwrite &
```
It's that simple.

---

### Post by pete on 2006-10-05
Just to clarify, though, running the process in the background by appending the "&" symbol does not change the behavior PigCorpse described.  

Closing the originating terminal session still kills the process.  However, you can at least do other stuff in the same terminal session in the meantime.

---

### Post by Ramses de Norre on 2006-10-05
```
nohup command &
```
Will run the app in the background and independent from the terminal (closing the terminal wont close the app).
All output is redirected to ~/nhup.out.

---

### Post by mitch.c on 2006-10-05
> **pete said:**
> Just to clarify, though, running the process in the background by appending the "&" symbol does not change the behavior PigCorpse described.  

Closing the originating terminal session still kills the process.  However, you can at least do other stuff in the same terminal session in the meantime.
Ummm. OK, I guess the difference is, I don't 'close' the terminal, instead I do something like this:
```
gedit &
exit
```
Which closes the terminal, but leaves gedit running. Seems to me exit is cleaner, so I never noticed the behavior you describe.

---

