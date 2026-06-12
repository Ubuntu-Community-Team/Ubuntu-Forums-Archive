---
title: "Just installed &amp; can't log in."
date: 2008-05-14
forum: General Help
---

### Post by nickthebic on 2008-05-14
I've just completed installation of Ubuntu 8.04 and I can't seem to log in.

When I try to login, all of the login prompts & the logo goes away for about 5 seconds, before taking me directly back to the login screen as if nothing happened.

This also happened when I booted directly to the OS from the CD to test it out. I'm afraid maybe I'm missing something completely obvious.

This is my first time on any Linux computer, so I know basically nothing about them.

EDIT: Under the Options > Select Session menu, I selected Failsafe GNOME and I got in. If someone could explain this all to me it would be great. I'm not sure which option should be selected, really.

---

### Post by sweeneytodd on 2008-05-14
if you are logging in when using the live cd there is something else wrong because you shouldn't have to log in using the live cd, if this isn't the case and i read it wrong, are you sure you have your username right. can you instinctively remember when installing, the exact spelling of your username, but then again, if it doesn't tell you you have the wrong username, my suggestion would have to be a faulty image of hardy, might be better to use p2p progam to download it and even though lotz would disagree use th 32 bit version

---

### Post by nickthebic on 2008-05-14
Well, I'm pretty sure I've got the username and password right. When I logged in under the session "Failsafe GNOME" It seemed to work, but I still have the feeling I'm doing something wrong.

---

### Post by OzzyFrank on 2008-05-14
I was going to suggest [COLOR="Blue"]Failsafe Gnome[/COLOR], but see you had success with that. OK, as it would have told you, it starts up without scripts and stuff, so is not what you really want to pick for every log in. From experience I can tell you simply logging in once that way can often fix things. The default for every login is to use the last one, but if you log in under Failsafe, the next time it will (as far as I know) default to a standard Gnome session, not the Failsafe one.

If only it was that simple for all problems (I am just about to post about not being able to get into Gnome after Virtualbox install). But, as I said, quite a few times all I had to do was log in under Failsafe, then log back in under normal Gnome session.

Other times it is as simple as deleting the "session" file in /home/username/.gnome2/. If you can't get into Gnome even the Failsafe way, you need to get into the Failsafe Terminal and do it, or log into another desktop environment like KDE.

I strongly suggest to all to install another desktop environment into Ubuntu, as for times Gnome just isn't happening, you should still be able to log into KDE or whatever. From there you have a graphical environment to work in, rather than have to do everything at the command prompt. For those times I couldn't fix Gnome while in KDE, by editing this and that etc, I've still been able to do everything I need in KDE, including log into this forum to ask questions. The other beauty of this is that you might not be able to fix things coz what you really need is some updated Gnome packages... so while in KDE or Xfce your Update Manager will still get updates, which could fix things for you.

That has actually happened to me 3 or so times... couldn't fix the problem or find an answer here, but then the Update Manager grabs some hew Gnome packages and voila! next time I try to log into Gnome it works without issue.

So for those only with Gnome I suggest a backup DE like KDE (or Xfce, if you prefer a smaller download) which you can install through Synaptic or **[COLOR="Indigo"]sudo apt-get install kubuntu-desktop[/COLOR]**.

Now off to post about me not being able to get into Gnome, even the Failsafe way...

---

