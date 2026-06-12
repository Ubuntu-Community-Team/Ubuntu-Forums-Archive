---
title: "Quamachi / Hamachi help needed"
date: 2007-05-19
forum: General Help
---

### Post by GadgetsGuy on 2007-05-19
I have one computer running Feisty Fawn, and another running XP that I am not having the best of luck keeping networked using the conventional route of Samba ...

I am familiar with Hamachi in a windows environment, as I use it to connect to my work PC while I am on the road.

I would like to use Hamachi as a fail-safe way to network my machines, as well as being to access the linux box while travelling ...

I did manage to successfully install both hamachi and the Quamachi GUI, and I did get Hamachi to configure and start using the console ... but I cannot figure out where/how to start the GUI, and then how to have it start each time Ubuntu starts?  :confused:

I have tried typing "quamachi" from console, and it does nothing, and I do not have any Quamachi icon in my applications menu.

Any help would be greatly appreciated.

---

### Post by Hairy_Palms on 2007-05-20
did you install it from source? if so have a look in /usr/local/bin and /usr/bin and see if theres an executable with the name your looking for,
when you find it, to make it start with ubuntu open System->Preferances->Session and add it as a new startup program

---

### Post by stalker145 on 2007-08-05
> **GadgetsGuy said:**
> I did manage to successfully install both hamachi and the Quamachi GUI, and I did get Hamachi to configure and start using the console ... but I cannot figure out where/how to start the GUI, and then how to have it start each time Ubuntu starts?  :confused:

I have tried typing "quamachi" from console, and it does nothing, and I do not have any Quamachi icon in my applications menu.

Any help would be greatly appreciated.

I don't know if you've found your answer yet, but I do have some input... well, and a question.

The executable for Quamachi is ```
Quamachi.pyw
```

Now the question: I recently did a reinstall and for some reason Quamachi refuses to run as anything but root (I have to sudo Quamachi.pyw to get it to run). I installed from a deb file downloaded from [KDE-Apps]("http://www.kde-apps.org/content/show.php/Quamachi?content=55089"). Now, before I reinstalled, Quamachi ran just fine from my user account.

Does anyone know how to "unsudo" this app by chance?

I really need to start writing this stuff down ;)

---

### Post by wyth on 2007-08-05
Stalker145, did you try chowning Quamachi?  I'm not clear on the exact syntax, but it sounds like it's owned by root, and you want it owned by you.

---

### Post by stalker145 on 2007-08-09
> **wyth said:**
> Stalker145, did you try chowning Quamachi?  I'm not clear on the exact syntax, but it sounds like it's owned by root, and you want it owned by you.

wyth, Thanks for the response and my apologies for not getting back - I've been out doing some training haven't had the energy to get on and deal with this.

Well, I gave it a shot chown'ing the Quamachi.pyw file itself. That didn't work as I still need to sudo the command to get it running properly. I was tempted to chown everything in the Quamachi folder within /usr/share but I didn't think that a really great idea... just thought I'd mention that if someone's done it and it's OK.

Thinking about my post and what's going on, I realized that I could have given more info before. I've attached a screen capture of the exact problem. Funny thing is that the install file has no good info on how to fix this problem. 

So far, I've tried chown'ing Quamachi.pyw, and adding /sbin/tuncfg to my user's path as suggested [here]("http://www.linuxquestions.org/questions/showthread.php?t=575141"), but it wasn't in my path after a restart (back to researching that one :tongue:). And looking at the path on my laptop that Quamachi runs fine on, I just realized tuncfg isn't in my path there, anyway...

If anyone else has any suggestions, I would greatly appreciate the input. Thanks.

---

