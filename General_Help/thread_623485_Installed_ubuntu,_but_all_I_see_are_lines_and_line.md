---
title: "Installed ubuntu, but all I see are lines and lines of text"
date: 2007-11-25
forum: General Help
---

### Post by flippykid on 2007-11-25
Alright first of all I installed ubuntu on a CD, but it didnt seem to work, so i looked around and saw that you didnt need a cd, and infact that there was a program so that you didnt need a cd, Well I did everything it said and at the last step where it asked me if i wanted to add any other programs since i only had the base installation i didnt click anything, and well i see this now, i lost my windows xp because i wanted to have a whole drive just for ubuntu, and Im currently on my brothers computer, i have no idea what to do now, i cant go back now that i lost windows xp, i can log in and everything but it always asks me to put in texts, there is no graphical interface, if there is some way of getting ubuntu to run properly please tell me, i have no money so i cant go and rebuy anything, please I need some help on this, and quick. A short way of saying it is that I lost windows xp, all i see now is text instead of any interface, and i can log on, but thats about it, i really need my computer back, and i need it for school too, so please if someone can help me, help.

---

### Post by Seti on 2007-11-25
I think you're going to need to give a more detailed description of what you did (link?) if you want someone to give you meaningful advice on a solution.
Did you format the whole drive and install linux?
What distro are you using? Ubuntu? How did you perform the install?

---

### Post by flippykid on 2007-11-25
I reformated the drive so i could use ubuntu, and yes i used ubuntu 7.10, there was a program that restarted your computer and installed ubuntu, all you needed to do was follow the steps, and Ièm guessing when it asked me if i wanted to install other programs ( ubuntu destop being one of them) i skiped it by acident. please someone help

---

### Post by flippykid on 2007-11-25
Sorry about the double post, but getting ubuntu to run is something i have to do, so please can someone help me, someone, anyone, just please.

---

### Post by PeterJS on 2007-11-26
I'd like to help, but I've yet to make heads or tails of what's going on exactly. Sounds like you installed Ubuntu using Wubi, and then used the entire disk (wiping out windows) when installing, which I didn't think wubi would let you do, but I've never used it. And now your system boots but your graphics card isn't configured right.

Well let's try to get X working, ok. Can you login in and run lspci and post the output here?

---

### Post by flippykid on 2007-11-26
> **PeterJS said:**
> I'd like to help, but I've yet to make heads or tails of what's going on exactly. Sounds like you installed Ubuntu using Wubi, and then used the entire disk (wiping out windows) when installing, which I didn't think wubi would let you do, but I've never used it. And now your system boots but your graphics card isn't configured right.

Well let's try to get X working, ok. Can you login in and run lpsic and post the output here?

How Do I do that.. Is it a command. Alright I tried the command lpsic, but it said that its not a command.

---

### Post by petersjm on 2007-11-26
When you get to the prompt after starting up, can you tell us what the last few lines of text say? Is it an error? Is it warning you of something?

---

### Post by PeterJS on 2007-11-26
Wow, sorry about that, that's quite possibly the worst typo, that was supposed to be
```

lspci

```
which it short for list pci, which lists the devices attached to the machine

---

### Post by flippykid on 2007-11-26
Alright I give up, I just asked for the free version of ubuntu to get shipped to me in 4 to 6 weeks, I guess I will have to reinstall with that cd, but the weird part is that no matter what cd i put into the computer, it never reads it, ever, I dont know why, it looks almost as if Im going to need a whole new rig -_-.

---

### Post by Xavieran on 2007-11-26
Try this command after you've logged in in text:sudo apt-get install ubuntu-desktop
Then restart...

P.s. You'll need a working internet connection...

---

### Post by rnh on 2007-11-26
Hi, I'm having the same exact problem, and I just wanted to know, where do we need to put the text in?

---

### Post by Xavieran on 2007-11-26
Step 1: it says User Name:You type it in
           it says Password:You type that in too
Step 2: Type sudo apt-get install ubuntu-desktop
P.S. you'll need an internet connection for this
Step 3: Restart your machine and hopefully it will take you to a Graphical Login Screen...

---

### Post by petersjm on 2007-11-27
> **Xavieran said:**
> Step 2: Type sudo apt-get install ubuntu-desktop


Step 2A: It'll ask you for your password again, so type it at the prompt.

Also, if it spits back at you that you already have ubuntu-desktop installed, then it's some other reason you can't get to the GUI. If it says you have it, try typing

```
startx
```

and see if it lets you in. If it doesn't, tell us the error it gives.

Does it say anything about a missing screen (or "unable to find screen" or something like that)? If so, you could try typing (or copying and pasting to avoid typos):

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

It might ask you a few questions, although I'm not sure. If it does, defaults are usually acceptable.

In any event, if you still can't get a GUI login up and running after trying everything suggested in the last few posts, please tell us whatever errors you get on the screen so we can narrow it down a bit.

---

### Post by flippykid on 2007-11-27
OMG I love you with the passion, Its currently downloading the files after i did step 2, I sure hope this works perfectly. I will edit after it finnishes to see if it worked. Once again, I love you with the passion.. BTW.. how long is this going to take...

---

### Post by flippykid on 2007-11-27
guess who is texting this from ubuntu :D, thanks guys for all your help. I´m super  new to linux.... hmmm why can´t I type ¨´ by pressing it once... O.o

---

