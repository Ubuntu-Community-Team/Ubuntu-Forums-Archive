---
title: "problem with resuming system from suspend"
date: 2008-04-11
forum: General Help
---

### Post by 65daysofstatic on 2008-04-11
hi,

my problem is that when i suspend the computer i cannot recover from it and i have to reboot the system, im using ubuntu 7.10 with all the updates installed, my video card is an nvidia with the driver downloaded and installed using envy
the system log says that "Resuming failed"...
does anyone know a solution for this?

thanks

---

### Post by ibuclaw on 2008-04-11
This is an old one.

Unfortunately there is not generic or universal way to solve this. There have been many bug reports at Launchpad about the issue, with an equally amount of apparent fixes, but with little avail.
 
Though, you could give uswsusp a try.

I don't think that it is installed by default. So apt-get it.
```
 sudo apt-get install uswsusp 
```
Then save all files and close all programs. As first we are going to test it to see if it works on your system.
```
 sudo s2disk 
```
**If it worked**.
Sorry let me rephrase that
**IF IT WORKED**, hurrah! Now, to make this the default way to hibernate/suspend the computer (including the logout dialog, and GNOME Power Manager) involves some hackery but it&#8217;s not too bad, and it&#8217;s not likely to cause any problems.

Run this from the terminal
```

sudo updatedb
locate hal-system-power-hibernate-linux

```
It should be in the** /usr/lib/hal/scripts/linux/ folder.** Though change the below command accordingly.

So! Now.
Download these two files:
[hal-system-power-hibernate-linux]("http://www.paulbetts.org/projects/hal-system-power-hibernate-linux")
[hal-system-power-suspend-linux]("http://www.paulbetts.org/projects/hal-system-power-suspend-linux")

And run this in the terminal
```

sudo cp hal-system-* /usr/lib/hal/scripts/linux/ -R
sudo chmod 755 /usr/lib/hal/scripts/linux/* -R

```

And enjoy a working suspend.

Regards
Iain.

[EDIT]
65daysofstatic are a wicked band!
Have you heard of an Icelandic band called "Mum"?
Also, I recommend "SeaFood" and "Porcupine Tree" if you're into that sort of stuff!
And dig for a "Hope of the States" EP. ie: Winter Riot Dusk Rackets. 
They do much better prog than on their pop glistened albums!

---

### Post by 65daysofstatic on 2008-04-11
ok..
Im gonna try that solution
thank you tinivole


ps.. what do you mean with  a wicked band ?? (my english isnt very good, hehe)
I will give a try to the bands you posted

---

### Post by ibuclaw on 2008-04-12
When I say wicked. I mean:
awesome; brilliant; fantastic; awe-inspiring.

I just presumed you were a fan of 65daysofstatic. As I doubt that you chose to name yourself that at random. :popcorn:

---

### Post by 65daysofstatic on 2008-04-12
the suspend seems that's working now,
thank you man

btw I'm a fan of the band i just didn't know what meant wicked on that context, hehe :)

---

