---
title: "updater stuck on mscorefonts"
date: 2012-12-20
forum: General Help
---

### Post by tdubb on 2012-12-20
Hi everyone, 
I've been trying to update my system for a few days now and every time the software updater gets to the point where it reads: preparing installation of ttf-mscorefonts-installer

I've cancelled the update a each time because it won't get past this point.  I've tried to find an answer on what to do, but the instructions are a bit difficult for _me_ to follow.  Does any one have an easy way to fix this?  or very detailed instrucions.  

Also i've tried to download the unofficial netflix app, and everything seems to go fine until a microsoft agreement pops up with a an "ok" at the bottome that i cannot click or hit enter... anyone else have this issue?  :popcorn::p):P

Thanks a lot!!!

---

### Post by steeldriver on 2012-12-20
if it's the screen I think it is, you should be able to highlight the OK 'button' by using the TAB key - and then 'press' it using spacebar or (iirc) enter

---

### Post by tdubb on 2012-12-20
ok I got netflix installed, and honestly I thought that I was having trouble because of the font update not updating... either way I'm happy I have netlflix but I'm still stuck on the update.  Is there anyway to skip over the msfont update so I can still update the updates that work. but thanks for the tab suggestion,  I feel pretty dumb not trying that haha.

---

### Post by tdubb on 2012-12-20
well this is kind of funny,  netflix is running, as soon as i went to play something, it said it could not play... i checked why and it is because i am missing fonts.  So in the end I do need the font update.

---

### Post by howefield on 2012-12-20
What is it that you are stuck on ?

Use the tab key to highlight the ok button as mentioned above, then press enter, you might then need to use the arrow key to highlight the yes button and again press enter.

---

### Post by tdubb on 2012-12-20
netflix is installed.  the thing i'm stuck on is mscorefonts update.  when I open up the system updater, It starts to update, then gets stuck on the font update.  I'm not sure what to do.

---

### Post by howefield on 2012-12-20
> **tdubb said:**
> netflix is installed.  the thing i'm stuck on is mscorefonts update.  when I open up the system updater, It starts to update, then gets stuck on the font update.  I'm not sure what to do.

Try opening a terminal and type the following two commands..

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Does it give you an error ?

---

### Post by tdubb on 2012-12-23
HI,  I'm sorry to take so long to reply.... I haven't been at my ubuntu machine.  Either way,  I went to do the update so I could tell you the error, but all the updates went through fine.  Thanks anyway for your help.:p

---

