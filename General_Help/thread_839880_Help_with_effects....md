---
title: "Help with effects..."
date: 2008-06-24
forum: General Help
---

### Post by Szat on 2008-06-24
Here is another first time Ubuntu user needing help with the visual effects.  I tried to figure it out on my own and by using the forum; but everything I tried didn't get me closer to solving my problem.  When I go to turn on the visual effects, I get an error message saying that they could not be enabled. I am using Hardy Heron on my laptop (Pentium M 2.0 ghz, 1 gig RAM, 70 gig HD, Nvidia GeForce Go 6800). Sorry for having to post another one of these, but I know someone will help. Thanks!

---

### Post by overdrank on 2008-06-24
> **Szat said:**
> Here is another first time Ubuntu user needing help with the visual effects.  I tried to figure it out on my own and by using the forum; but everything I tried didn't get me closer to solving my problem.  When I go to turn on the visual effects, I get an error message saying that they could not be enabled. I am using Hardy Heron on my laptop (Pentium M 2.0 ghz, 1 gig RAM, 70 gig HD, Nvidia GeForce Go 6800). Sorry for having to post another one of these, but I know someone will help. Thanks!

HI and welcome, have you looked at the FAQ in the sticky at the top of this forum :)
[http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)
Post back if you still have issues.

---

### Post by Szat on 2008-06-24
Yes, I've looked at the FAQ and I still haven't gotten it working. I typed the code in the terminal to get compfiz (assuming I don't have it), but it says E: Couldn't find package compizconfig-settings-manager. What should I do?

---

### Post by overdrank on 2008-06-24
> **Szat said:**
> Yes, I've looked at the FAQ and I still haven't gotten it working. I typed the code in the terminal to get compfiz (assuming I don't have it), but it says E: Couldn't find package compizconfig-settings-manager. What should I do?

HI and I would suggest starting with compiz check.
[http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)
 What it the  model of the graphics card. You can use the command ```
lspci
``` int the terminal located under applications,accessories. Look for VGA

---

### Post by Szat on 2008-06-24
I have a Nvidia Geforce Go 6800. I tried using that Compiz-check script, but I don't know what to run it on. I tried the terminal, but it just give me error messages.

---

### Post by overdrank on 2008-06-24
> **Szat said:**
> I have a Nvidia Geforce Go 6800. I tried using that Compiz-check script, but I don't know what to run it on. I tried the terminal, but it just give me error messages.

Ok I am off to work but have you installed the drivers for you nvidia card. I am using a 6800 also and under system, administration, hardware drivers. You can enable the restricted drivers for you graphics. If compiz check gives you errors then post the errors and someone maybe able to help. :)

---

### Post by steveneddy on 2008-06-24
> **Szat said:**
> Yes, I've looked at the FAQ and I still haven't gotten it working. I typed the code in the terminal to get compfiz (assuming I don't have it), but it says E: Couldn't find package compizconfig-settings-manager. What should I do?

In a terminal type in

```
sudo apt-get install compizconfig-settings-manager
```

Easy peasy.

---

### Post by Forlong on 2008-06-25
> **Szat said:**
> I have a Nvidia Geforce Go 6800. I tried using that Compiz-check script, but I don't know what to run it on. I tried the terminal, but it just give me error messages.
Can you please post those error messages?

---

### Post by Szat on 2008-06-25
> **steveneddy said:**
> In a terminal type in

```
sudo apt-get install compizconfig-settings-manager
```

Easy peasy.
 
I did that but all it said was E: Couldn't find package compizconfig-settings-manager.

Also, when I put in the compiz check into the terminal it just seems to keep copying itself and then giving me a new command line. The OS also won't let me see my Device Manager...

---

### Post by saratchandra on 2008-06-26
> **Szat said:**
> I did that but all it said was E: Couldn't find package compizconfig-settings-manager.

Also, when I put in the compiz check into the terminal it just seems to keep copying itself and then giving me a new command line. The OS also won't let me see my Device Manager...

Did you enable restricted and third party software in your sources?

---

### Post by Szat on 2008-06-26
I have no idea. I went to the restricted drivers option but it was blank. I have to go to bed. I have work in a few hours, but I'll be back to check replies later tomorrow. Also, does anyone suggest a good beginner Linux book?

---

