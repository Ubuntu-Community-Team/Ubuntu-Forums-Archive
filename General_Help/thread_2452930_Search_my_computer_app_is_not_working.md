---
title: "Search my computer app is not working"
date: 2020-10-30
forum: General Help
---

### Post by SUPERFITTER on 2020-10-30
Search my computer app is not working in Ubuntu 2020.  
Nothing shows up when I activated the app.  
Is there anything that I can run in terminal to fix this?

Thank You

---

### Post by CelticWarrior on 2020-10-30
Which app?

---

### Post by SUPERFITTER on 2020-10-30
The Search my computer app, in the top left corner of desktop.

---

### Post by CelticWarrior on 2020-10-30
Not an app...

What exactly doesn't work?
Please describe the issue in an understandable manner. We can't see what you're seeing.

---

### Post by SUPERFITTER on 2020-10-31
I should have said Icon in the top left corner of desktop. 
				I cannot search for anything in my computer. 
Nothing shows up in the field after I type in what i am looking for and hit search or the enter key?

---

### Post by deadflowr on 2020-10-31
Icon at top sounds like unity, but to be clear what does
```
env | grep Current
```
show?

---

### Post by CelticWarrior on 2020-10-31
Whatever you type in that field - after clicking on it, no enter, nothing, just type - should show installed software that matches the typed letter. As an example, if you type "f" it should show, among others, "Firefox". Perhaps what you're looking for isn't installed?

---

### Post by SUPERFITTER on 2020-10-31
deadflowr: you are right, it is  unity

dennis@dennis1:~$ env | grep Current
dennis@dennis1:~$ 


CelticWarrior:

When I type in Firefox that I use, I get:  Sorry, there is nothing that matches your search.  I have typed a few other things with the same results.

---

### Post by deadflowr on 2020-11-01
Check that the lens packages are installed or just try installing them
```
sudo apt install unity-lens-files unity-lens-applications unity-lens-video unity-lens-photos unity-lens-music
```
Might also check to see if the unity-scope-home package is installed.

---

### Post by SUPERFITTER on 2020-11-01
[B]deadflower
That did it, lens packages were missing.  I wonder why?  

Thank You
Very Much!
[/B]

---

