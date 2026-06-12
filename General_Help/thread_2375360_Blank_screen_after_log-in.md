---
title: "Blank screen after log-in"
date: 2017-10-24
forum: General Help
---

### Post by EowynCarter on 2017-10-24
Having the same here.
To explain the long story. 

The day before yesterday, I'm happily playing cities skylines. Everything works. 

Yesterday, I start the computer to play. Login screen is at the wrong resolution. Trying to log in fail. It display a message too quickly to read, and back to login screen. Why? Guess an update was pushed I didn't see. 

Not this crap again, I though. I've been dealing with issues like this frequently since 16.04. I've reached the point where I went from 'annoyed' to 'seriously pissed off' over this issue. 

So, recovery mode. 

apt-get remove - - purge nvidia*

Reboot. That gets the gui working. 

I update to 17.10, hoping the new version fixes the issue. 

Reboot. Gui works partly. Network not working. (again!) 

Fix network. 

apt-get install nvidia-current 

Reboot. 

Login 

Black screen. 

**Goes off to bed, enough of this crap**. 

So, now I've slept a bit. Any clue on getting stuff to work again ? 
What can I do to make sure this don't happen again? 
What happened to canonical QA? Ubuntu used to be stable. Now it's problems after problems.

And I forgot, in case it matters. Card is GT950.
Secure boot is OFF.

---

### Post by QIII on 2017-10-24
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2375327](https://ubuntuforums.org/showthread.php?t=2375327)

Hello!

Please do not hijack the threads of other users.  They and you deserve individual attention.  Your problem may be the result of an entirely different cause.

---

### Post by mastablasta on 2017-10-24
> **EowynCarter said:**
>  
What happened to canonical QA? Ubuntu used to be stable. Now it's problems after problems.


you mean "what happened to nVidia QA?", because they are the ones that provide the drivers that are causing you issues.


> 
And I forgot, in case it matters. Card is GT950.
Secure boot is OFF.


nvidia has procedure to resolve issues. i didn't manage to resolve them, but i know you are supposed to run some troubleshooting program and then post the output to their support team or on their forums.

you can also check your own logs to see what is going on. if you have another output you could try adding a screen there to see if the GPU is not outputting to wrong screen. this is what happens on one of my PCs when i run linux live session on it. it also hapens on windows. nVidia GPU card simply throws the output to some other external screen rather than the one that is plugged in.

---

### Post by EowynCarter on 2017-10-24
But then, canonical is in change in integrating them into ubuntu. 

Maybe I should look on nvidia broad. Didn't thought about it, but...
Where would the log be ?

And nice idea about the wrong output.

---

### Post by dino99 on 2017-10-24
wayland+nvidia are known to fail working; so login on a xorg session instead, or use 'nouveau'

---

### Post by EowynCarter on 2017-10-24
Tanks. I'll try xorg session. Nouveau probably isn't an option with steam.

---

### Post by mastablasta on 2017-10-24
> **EowynCarter said:**
> 
Maybe I should look on nvidia broad. Didn't thought about it, but...
Where would the log be ?


logs are in /var/log

but also there should be a log viewer installed (forgot what it's called in Ubuntu), which will load and show up all important logs.

---

### Post by EowynCarter on 2017-10-24
Oh, the obvious place then.

The end of the story in case someone with similar issue read this.

At login , i see "ubuntu xorg" and "unity", but ubuntu xorg is selected. Not sure what mode it was on yesterday.
It start, but graphic performance is abysmal.

I look with synaptic, nvidia curent points to version 304. That's what installed. 
Ok, let try the last version.

remove nvidia-current
add nvidia-384.
reboot
enjoy working computer.

And maybe I should have a look at my repository list.

Edit : nope, nothing wrong there. Though 304 is the legacy driver. Not good for my rather new graphic card.

Tanks both for your help :)

---

