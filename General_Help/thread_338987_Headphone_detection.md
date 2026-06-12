---
title: "Headphone detection"
date: 2007-01-15
forum: General Help
---

### Post by samden on 2007-01-15
I would like to listen to music in the office on my iMac running Xubuntu dapper. However when I plug in the headphones, the main speakers do not mute. They keep playing as well, so both my main speakers and my headphones are making noise.

The Xubuntu sound control panel doesn't seem to do anything either - it just consists of a list of tick boxes saying whether to use certain extensions, it doesn't even have a volume control. 'Headphone detection' is on according to this.

This is not a hardware problem - I dual-boot with OSX and it works fine in OSX.

Any suggestions? Can I edit something in the terminal? Is there a better sound control panel I could use?

---

### Post by samden on 2007-01-15
I have added the "volume control" button to the panel. Whenever I open this, 'Headphone detection' is turned off. I can turn in on, but the headphones are still not detected. When I close the volume control window and turn it back on, 'Headphone detection' is always turned off again.

Can I edit this directly through the terminal to ensure headphone detection is on and check whether or not it works?

---

### Post by samden on 2007-01-18
Does anyone have any thoughts on this?

---

### Post by samden on 2007-01-29
Just one final bounce before I give up on this thread. If anyone has any thoughts I would be very very grateful for any suggestions, however slight. Thankyou.

---

### Post by Robin T Cox on 2007-01-29
Can you unplug your speakers and use headphones only?

Just a thought, as it's how I am running.

---

### Post by samden on 2007-01-30
Built-in speakers, so no luck there. I could theoretically delve deeper into the electronics and solder in an on-off switch, but I don't think it is worth going to that much effort!

I have now found that alsa sound may not work correctly on these iMac computers anyway, which is a shame but does explain my problems. Noone seems to know a workaround. 

I think I will just give up on this for now. Thanks for the suggestion though.

---

### Post by kutlu on 2007-02-03
I am using ubuntu.
for ubuntu;
if you write "alsamixer " to the command ine, you will see an interace in order to control audio input-output devces. you can use up-down, right left, and M (for mute/unmute)

in order to switch to headphe automatically, you should unmute "Headphone Jack sense"
you can also unmute inputs which are muted.

I hope it applies for Xubuntu, too

Edit: This is my first post to forum :D

---

### Post by samden on 2007-02-05
Thanks for putting your first post on my thread!

Unfortunately I have tried that, with no luck. It appears alsa does not work correctly on the particular computer I have, and others have complained about it too. But thanks for the suggestion.

I wish you a long and happy posting career!

---

### Post by eitan_a on 2007-03-03
one thing that worked on my laptop was to use install gnome alsa mixer and mute the "front" everytime i used headhpones.  It's a workaround, but no solution.

---

### Post by aaaantoine on 2007-09-13
I'm posting to say that I have the same problem with my sound system.  I sense this is a flaw in the ALSA drivers, as, for example, my headphone jack volume is assigned to the "Front" channel, and my internal speakers are assigned to the "Surround" (!?) channel.

As a workaround, I have to mute the Surround channel if I want to hear the headphones exclusively.  Hopefully, a future ALSA release will better support my sound (ALC883 I think).

---

