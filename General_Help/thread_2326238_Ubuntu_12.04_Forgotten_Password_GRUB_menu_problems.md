---
title: "Ubuntu 12.04 Forgotten Password GRUB menu problems"
date: 2016-05-30
forum: General Help
---

### Post by jospph on 2016-05-30
I have forgotten my password.  I have attempted to open GRUB menu at boot but all that shows up is a black screen :confused:.  
I have tried holding shift as well as just pressing shift.  I've even tried using esc.  Any thoughts?

---

### Post by DuckHook on 2016-05-30
Use the following guide to reset a forgotten password.

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

You must hold <shift> down as soon as the POST process starts. Keep holding until GRUB shows.

There are other ways to change your password including chrooting into your install using a LiveUSB, but they are more convoluted and to be avoided if simpler solutions will work. If you absolutely cannot get to GRUB, then change your BIOS to boot from DVD/USB and use the following instructions:

[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

As a general observation, most new users, especially from Windows, forget their password because they opt for automatic login (a really bad, pernicious Windows habit) and then one day reactivate login authentication only to find that they can't remember the password they used. Not saying that you did this, but others read these posts too, and the lesson must be stated: get used to using your password with every login. It is one of the most effective security tools you have and a part of the good habits that make Linux more secure than Windows (it is about your habits, you know, not some magic security app).

---

### Post by RobGoss on 2016-05-30
> **jospph said:**
> I have forgotten my password.  I have attempted to open GRUB menu at boot but all that shows up is a black screen :confused:.  
I have tried holding shift as well as just pressing shift.  I've even tried using esc.  Any thoughts?


Hello and welcome, Here's is good YouTube video will show you in detail how to access your desktop if you've forgotten your password you cab them reset it to gain access again
[https://www.youtube.com/watch?v=c7TTD_UUUjQ](https://www.youtube.com/watch?v=c7TTD_UUUjQ) you should always right your passwords down some were for safe keeping. 

Best of luck

---

### Post by DuckHook on 2016-05-30
> **RobGoss said:**
> ...YouTube video...a rather lengthy video that doesn't add anything to what I already linked to, but no harm, no foul, I suppose> you should always right your passwords down some were for safe keeping....however, this is just bad advice and you shouldn't be giving it. The first and most important rule of passwords is: ***don't write them down***. What is effectively kept in your head cannot be stolen ***or*** forgotten. The key to the password conundrum is to come up with lengthier phrases that are relatively easy to remember, but impossible to guess and next to impossible to brute force. A good strategy is embodied in the following link:

[http://world.std.com/~reinhold/diceware.html](http://world.std.com/~reinhold/diceware.html)

There are many other good strategies. Almost all involve some form of mnemonics that work *with* our natural proclivities rather than against them, and yet are surpassingly difficult for anyone else to reproduce except the originator.

---

### Post by RobGoss on 2016-05-30
> [COLOR=#000000]however, this is just bad advice and you shouldn't be giving it. The first and most important rule of passwords is: [/COLOR]***don't write them down**. *

if this were true then we would remember our password  correct? but not everyone can do this that's why I recommend writing them down and keeping them in a safe place. I have **85** password for my online accounts and it's impossible for me to remember them all


>  [COLOR=#000000]a rather lengthy video that doesn't add anything to what I already linked to, but no harm, no foul, I suppose[/COLOR]


2:19 seconds not long at all and very detailed sometimes a visual picture to some may give them a better understanding

Hey but I understand what your saying hard to remember hard to access. I get it

---

### Post by DuckHook on 2016-05-30
@RobGoss

We are in danger of hijacking the OP's thread.

@jospph

If you have any interest in discussing the pros and cons of differing password strategies, please start separate thread in Security forum.

If any of the above methods work for your problem, *then please mark thread **solved** using *Thread Tools* in the top toolbar for the benefit of others searching for solutions*.

---

