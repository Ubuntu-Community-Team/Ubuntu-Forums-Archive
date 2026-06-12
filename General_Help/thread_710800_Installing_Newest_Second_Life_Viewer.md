---
title: "Installing Newest Second Life Viewer"
date: 2008-02-28
forum: General Help
---

### Post by Angelbeast on 2008-02-28
Hi. I need some help with installing the new Second Life viewer just released today. It.s a tar.bz2 archive. I still don't quite understand how to install things from those. Could someone walk me through it? Please? Thank you...

---

### Post by taurus on 2008-02-28
```
cd ~/Desktop
tar xvjf filename.tar.bz2
cd filename
cat INSTALL
-or-
cat README
```
But if you can provide the exact link where you downloaded it, then I can have a look and tell you more precise steps.

---

### Post by Angelbeast on 2008-02-28
> **taurus said:**
> ```
cd ~/Desktop
tar xvjf filename.tar.bz2
cd filename
cat INSTALL
-or-
cat README
```
But if you can provide the exact link where you downloaded it, then I can have a look and tell you more precise steps.

I downloaded it through the client..I didn't see any install file and the readme says it runs right out of the unpacked folder...

---

### Post by Angelbeast on 2008-02-28
> **taurus said:**
> ```
cd ~/Desktop
tar xvjf filename.tar.bz2
cd filename
cat INSTALL
-or-
cat README
```
But if you can provide the exact link where you downloaded it, then I can have a look and tell you more precise steps.

Here's a link though

[http://secondlife.com/community/linux-alpha.php](http://secondlife.com/community/linux-alpha.php)

---

### Post by taurus on 2008-02-28
Assuming you've downloaded it to your ~/Desktop, open a terminal and run

```
cd ~/Desktop
tar xvjf tar xvjf SecondLife_i686_1_19_0_4.tar.bz2
cd SecondLife_i686_1_19_0_4
./secondlife
```

---

### Post by Angelbeast on 2008-02-28
> **taurus said:**
> Assuming you've downloaded it to your ~/Desktop, open a terminal and run

```
cd ~/Desktop
tar xvjf tar xvjf SecondLife_i686_1_19_0_4.tar.bz2
cd SecondLife_i686_1_19_0_4
./secondlife
```

thi method does not seem to be working

---

### Post by Angelbeast on 2008-02-28
> **taurus said:**
> Assuming you've downloaded it to your ~/Desktop, open a terminal and run

```
cd ~/Desktop
tar xvjf tar xvjf SecondLife_i686_1_19_0_4.tar.bz2
cd SecondLife_i686_1_19_0_4
./secondlife
```

When i go to run it from the start menu the old version runs

---

### Post by Angelbeast on 2008-02-28
Anyone know how to make the shortcuts work? Can i do a fresh install with this?

---

### Post by Angelbeast on 2008-02-29
Help? Someone? *LOL*

---

### Post by Angelbeast on 2008-02-29
*bump*

---

### Post by jdunn on 2008-02-29
I'm using Kubuntu with KDE.  I can't tell you how to edit your gnome "start menu".  However, I can tell you how to install and run SL from the console.  If you want to put the game in /usr/local/games, do this:

After downloading the SecondLife_i686_1_19_0_5.tar.bz2 file, go to the console and type:
'sudo cp SecondLife_i686_1_19_0_5.tar.bz2 /usr/local/games'
cd to /usr/local/games and type:
'sudo tar xvfj SecondLife_i686_1_19_0_5.tar.bz2'
That's it.  To run SL, cd to /usr/local/games/SecondLife_i686_1_19_0_5 and type:  './secondlife'

I downloaded and installed the new SL version today.  It works fine for me.

---

