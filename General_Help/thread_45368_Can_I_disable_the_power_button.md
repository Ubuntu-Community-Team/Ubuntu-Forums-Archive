---
title: "Can I disable the power button?"
date: 2005-06-29
forum: General Help
---

### Post by chaumurky on 2005-06-29
I have a 2 year old that just loves to press buttons - much to my dismay. In windows I can "disable" the power button. It looks like in Ubuntu I need to modify /etc/acpi/events/powerbtn to get the same effect. The question is, what should I put there? Perhaps just comment out 'action=/etc/acpi/powerbtn.sh'? Also is the co-responding file for the keyboard's sleep button '/etc/acpi/events/sleepbtn' ? I might do the same thing there...

---

### Post by dickohead on 2005-06-29
[QUOTE=chaumurky]I have a 2 year old that just loves to press buttons - much to my dismay. In windows I can "disable" the power button. It looks like in Ubuntu I need to modify /etc/acpi/events/powerbtn to get the same effect. The question is, what should I put there? Perhaps just comment out 'action=/etc/acpi/powerbtn.sh'? Also is the co-responding file for the keyboard's sleep button '/etc/acpi/events/sleepbtn' ? I might do the same thing there...[/QUOTE]
 I disabled mine by just changing the power management settings under the last Gnome menu, and under Admin(?)

---

### Post by chaumurky on 2005-06-29
[QUOTE=dickohead]I disabled mine by just changing the power management settings under the last Gnome menu, and under Admin(?)[/QUOTE]
 The only power settings I see in Gnome are in  System>Preferences>Screensaver>Advanced>Display Power Management and there is no setting for power button behaviour. Are you referring to somewhere else?

---

### Post by dickohead on 2005-06-29
[QUOTE=chaumurky]The only power settings I see in Gnome are in  System>Preferences>Screensaver>Advanced>Display Power Management and there is no setting for power button behaviour. Are you referring to somewhere else?[/QUOTE]
 ...... maybe i'm thinking of SuSE.... I'm at work right now, they use win98, so i'm not much good from here, but i do remember seeing a menu item regarding the power functions of a computer. I do have ubuntu on a laptop though, so it may be different packages?

---

### Post by Navin_Johnson on 2005-06-30
At the risk of sounding like a jerk (imagine that w/ my handle!  for those who might not know "Navin Johnson" is the main character in the movie "The Jerk"), I hope you will also fix the initial problem of your two-year old pushing the button.  It took a couple times of being firm with my own boys (now 3.5 and 1.5 yrs;  my 2 month old obviously is too young for this) but after the initial period of them testing -- and finding -- their boundaries we've never had a problem with button pushing.  

While the computer (and television) buttons were an annoyance, it was a learning opportunity that taught them to listen and do as they are told -- which is much more important when applied to things like power outlets, the road, etc.

Good luck, and in the meantime it would be good to know how to disable the power button.  Since no one has come up with a good software solution -- and I have none to offer -- have you considered a physical means (like some sort of cover?).

Again, sorry if I sound like a jerk, especially since I myself get annoyed by nagging parenting advice.  But I hope you'll take this in a constructive way from someone who had -- and solved -- a very similar problem.

Best,
Navin Johnson (eric)

---

### Post by nocturn on 2005-06-30
[QUOTE=chaumurky]I have a 2 year old that just loves to press buttons - much to my dismay. In windows I can "disable" the power button. It looks like in Ubuntu I need to modify /etc/acpi/events/powerbtn to get the same effect. The question is, what should I put there? Perhaps just comment out 'action=/etc/acpi/powerbtn.sh'? Also is the co-responding file for the keyboard's sleep button '/etc/acpi/events/sleepbtn' ? I might do the same thing there...[/QUOTE]

What if you just put:
action=/bin/true

I think that'll do it.

---

### Post by chaumurky on 2005-06-30
[QUOTE=Navin_Johnson]At the risk of sounding like a jerk (imagine that w/ my handle!  for those who might not know "Navin Johnson" is the main character in the movie "The Jerk"), I hope you will also fix the initial problem of your two-year old pushing the button.  It took a couple times of being firm with my own boys (now 3.5 and 1.5 yrs;  my 2 month old obviously is too young for this) but after the initial period of them testing -- and finding -- their boundaries we've never had a problem with button pushing.  

While the computer (and television) buttons were an annoyance, it was a learning opportunity that taught them to listen and do as they are told -- which is much more important when applied to things like power outlets, the road, etc.

Good luck, and in the meantime it would be good to know how to disable the power button.  Since no one has come up with a good software solution -- and I have none to offer -- have you considered a physical means (like some sort of cover?).

Again, sorry if I sound like a jerk, especially since I myself get annoyed by nagging parenting advice.  But I hope you'll take this in a constructive way from someone who had -- and solved -- a very similar problem.

Best,
Navin Johnson (eric)[/QUOTE]
 Yes, that was a risk. My son has autism spectrum disorder. Disabling the power button is more straightforward than discipline. Let's move on.

@nocturn, thanks. I'll look into it.

---

### Post by Navin_Johnson on 2005-06-30
My apologies  (dammit, I am a jerk).  Perhaps I can offer some better assistance and be less of a jerk this time.

Several possibilities I found elsewhere (and cannot vouch that they work):

1.  Several possibilities here:  [http://nixdoc.net/files/forum/post-198168.html](http://nixdoc.net/files/forum/post-198168.html)  in here sounds like the best bet when using ACPI. (I think is basically what nocturn is suggesting)

2.  [http://lists.debian.org/debian-user/1999/06/msg02443.html](http://lists.debian.org/debian-user/1999/06/msg02443.html)  Setting bios up with apmd so that the power button makes the system suspend rather than power off.

3.  [http://www.linuxforum.com/forums/index.php?showtopic=146402](http://www.linuxforum.com/forums/index.php?showtopic=146402)  This involves setting the bios.

Good luck.
Navin Johnson

---

### Post by chaumurky on 2005-07-03
[QUOTE=nocturn]What if you just put:
action=/bin/true

I think that'll do it.[/QUOTE]

Perfect. Thank you.  \\:D/

---

