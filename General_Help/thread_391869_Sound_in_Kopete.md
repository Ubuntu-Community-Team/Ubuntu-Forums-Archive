---
title: "Sound in Kopete"
date: 2007-03-23
forum: General Help
---

### Post by iXneonXi on 2007-03-23
I use Xubuntu 6.06 and I have Kopete Messenger.
I need Kopete for MSN Video.
Whenever in a webcam I cannot hear audio. I also haven't been able to hear any sounds in kopete.
How do I fix this?

---

### Post by martin_legion on 2007-04-29
Same problem here....

---

### Post by flowerdealer on 2007-06-14
Same thing here (using Feisty Fawn Ubuntu whith gnome).

---

### Post by nrwilk on 2007-06-16
same here.  Amarok works, other KDE related sounds work, but there is no sound in Kopete at all.  And I get weird sound artifacts throught the speakers every few minutes.

Using Feisty on KDE, everything is up to date as of today.

---

### Post by mucho_maze on 2007-08-22
Same thing here... no sound i Kopete after I've updated to 7.04. I cannot even find the audio settings in Kopete....

Would be nice if somebody could help... thanks!

---

### Post by nrwilk on 2007-08-23
Well, it seems to come and go.  For a while, I had sound again and I thought that an update may have fixed the issue.  But, a little later it happened again, and since then it has been off-and-on.  I usually have sound in Kopete, but every once in a while, it decides that it wants to be silent.  When it is being silent, I still get those audible artifacts that I mentioned in my post above.

[COLOR="Red"]EDIT:[/COLOR]
Also, it seems that it happens on my desktop, but not my laptop.  Both run Kubuntu Feisty, and both are up-to-date.

---

### Post by Sutekh on 2007-09-19
> **mucho_maze said:**
> Same thing here... no sound i Kopete after I've updated to 7.04. I cannot even find the audio settings in Kopete....

Would be nice if somebody could help... thanks!

I never used Fiesty, but in Gutsy (Kopete is v0.12.5) the sound notifications are configured in **Settings** -> **Configure Notifications**.

I noticed that by default most events did not have sound files associated with them, including events for when new messages and mail arrive.

---

### Post by philinux on 2007-09-19
Got kopete set up correctly, webcam works out the box. But no sounds - test sounds dont work either?

---

### Post by DapperDrakeNewbieDR on 2007-10-28
Same problem here.

---

### Post by philinux on 2007-10-30
Gutsy still no sound :confused:

---

### Post by javierfh on 2007-11-05
> **philinux said:**
> Gutsy still no sound :confused:

I replied in some other thread you had...
maybe you can try to install kcontrol, launch it from terminal...and there check where it says notifications, check that you have alsa or your sound system properly configured.

Let me know if it helps.

Javi

---

### Post by raphinou on 2007-12-14
I corrected this problem in kcontrol > Sound & Multimedia:
At the bottom right of this window, you have a button "Player Setting". Click it and it opens a window to configure sound output.
It was set on no sound input. Choosing the KDE sound system didn't work either. I then set the external player "play" (you could have to install it, it is part of the sox package:
sudo apt-get install sox )

HTH

Raph

---

### Post by fk4n on 2008-01-16
In KDE, i tried turn on the system sound in System Settings->System Sound->Enable the sound system. And it solved my problem.

---

### Post by javierfh on 2008-01-16
The way it worked for me it is the following.
Install Kcontrol
launch it then with the terminal by invoking kcontrol
after that, go to sound & multimedia ->system notifications
there in the upper part where it says event source, select kopete messenger and there under player settings click where it says use the kde sound system

Please let me know if that works.
And if it works maybe you can put it to solved, i guess we will need to use it everytime you do fresh instalation and need to re install kopete.

Javi

---

### Post by valke on 2008-03-07
sadly nothing seems to work for me. some sounds work, others do not. it is most irritating, and i've gone back to pidgin.

---

### Post by marcosvega1 on 2008-03-27
> **javierfh said:**
> The way it worked for me it is the following.
Install Kcontrol
launch it then with the terminal by invoking kcontrol
after that, go to sound & multimedia ->system notifications
there in the upper part where it says event source, select kopete messenger and there under player settings click where it says use the kde sound system

Please let me know if that works.
And if it works maybe you can put it to solved, i guess we will need to use it everytime you do fresh instalation and need to re install kopete.

Javi

This solve my problem, but you forgot to say that you have to restart kopete to finally solve the problem :3 thank you:)

---

### Post by kjkrum on 2008-05-05
> **javierfh said:**
> Install Kcontrol
launch it then with the terminal by invoking kcontrol
after that, go to sound & multimedia ->system notifications
there in the upper part where it says event source, select kopete messenger and there under player settings click where it says use the kde sound system


kcontrol is included in a default installation of kubuntu 8.04.  Kopete was already set to use the KDE sound system, and it has sounds configured for its events.  The test button plays the sounds.  But there is still no sound whatsoever from Kopete.

Garbage software.  Going back to Pidgin, too.

---

