---
title: "Trying to get snapfish script to work"
date: 2008-05-16
forum: General Help
---

### Post by AdrianStrays on 2008-05-16
[http://ubuntuforums.org/showthread.php?t=481366&highlight=snapfish](http://ubuntuforums.org/showthread.php?t=481366&highlight=snapfish)

I've followed this How To perfectly, and yet the option of SendToSnapFish doesn't exist.  I really have no idea how to fix this, and I'd appreciate any help.

---

### Post by AdrianStrays on 2008-05-28
Bump

---

### Post by prshah on 2008-05-29
> **AdrianStrays said:**
> 
I've followed this How To perfectly, and yet the option of SendToSnapFish doesn't exist.  I really have no idea how to fix this, and I'd appreciate any help.

Can you open a terminal (Applications-Accessories-Terminal), then give the following command and show what output is given?```
ls -l .gnome2/nautilus-scripts/
```

Guessing it's probably a execute permissions (+x) issue.. simple to resolve, if given the above output.

---

### Post by AdrianStrays on 2008-05-30
adrian@Alpha-60-Workstation:~$ ls -l .gnome2/nautilus-scripts/
total 0
adrian@Alpha-60-Workstation:~$

---

### Post by unutbu on 2008-05-30
The command below should have put a file called SendToSnapfish in your nautilus-scripts directory.

> 12) Copy it to the Nautilus Scripts directory and rename it.
Code:
cp ./2gmail.txt ~/.gnome2/nautilus-scripts/SendToSnapfish

---

### Post by prshah on 2008-05-30
> **AdrianStrays said:**
> adrian@Alpha-60-Workstation:~$ ls -l .gnome2/nautilus-scripts/
total 0
adrian@Alpha-60-Workstation:~$

You've missed a step. Try the following from a terminal:```

cd
wget http://ceitl.zanestate.edu/blog/wp-content/uploads/2007/05/2gmail.txt
cp 2gmail.txt ~/.gnome2/nautilus-scripts/SendToSnapFish
chmod u+x ~/.gnome2/nautilus-scripts/SendToSnapFish

```

Don't forget step 13 & 14:> 
13) Open the script file:
Code:
gedit ~/.gnome2/nautilus-scripts/SendToSnapfish

14) Make the following change:
a) Change to="you@work.com" to to="save@snapfish.com"


Save, then restart X and check; has the option appeared?

---

### Post by AdrianStrays on 2008-05-30
LOL



Okay, this was a really stupid mistake.  I did not miss the file.  I installing that script on ANOTHER computer, but ran the terminal command on my personal computer.

I will run it on the correct computer when I get home.

---

### Post by AdrianStrays on 2008-06-07
johnny@Portable-1:~$ ls -l .gnome2/nautilus-scripts/
total 8
-rw-r--r-- 1 johnny johnny 555 2008-05-10 21:17 SendToSnapfish
-rw-r--r-- 1 johnny johnny 550 2008-05-10 21:17 SendToSnapfish~
johnny@Portable-1:~$

---

### Post by AdrianStrays on 2008-06-08
bump

---

### Post by unutbu on 2008-06-08
Please show us terminal output of what you have tried and what is going wrong. Particularly useful are error messages.

---

### Post by AdrianStrays on 2008-06-08
> Please show us terminal output of what you have tried

I've tried what I been told to try, and I've put the output.

What is going wrong is there is no script.

There are no error messages.

---

### Post by unutbu on 2008-06-08
Make the script executable
```
chmod 755 ~/.gnome2/nautilus-scripts/SendToSnapfish
```

Then according to [http://g-scripts.sourceforge.net/faq.php](http://g-scripts.sourceforge.net/faq.php),
> You first must visit the scripts directory with Nautilus (which can be done using the last option in the scripts menu.) Once the directory is visited, Nautilus will know about which scripts you have, and you will be able to use them.

---

### Post by prshah on 2008-06-10
> **AdrianStrays said:**
> johnny@Portable-1:~$ ls -l .gnome2/nautilus-scripts/
total 8
-rw-r--r-- 1 johnny johnny 555 2008-05-10 21:17 SendToSnapfish
-rw-r--r-- 1 johnny johnny 550 2008-05-10 21:17 SendToSnapfish~
johnny@Portable-1:~$

You've missed a step in the last batch of instructions;
> ```

chmod u+x ~/.gnome2/nautilus-scripts/SendToSnapFish
```

---

