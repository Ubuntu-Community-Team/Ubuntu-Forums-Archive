---
title: "Ubuntu just keeps reseting."
date: 2007-04-29
forum: General Help
---

### Post by Zellio on 2007-04-29
I enter my username, it starts up, then it asks for my username again...

---

### Post by solar george on 2007-04-29
I'm assuming that you mean at the graphical login,

Your username, don't press enter, use the menu in the bottom left corner to choose session, select failsafe gnome,  click OK,  finish logging in.

---

### Post by Zellio on 2007-04-30
It keeps doing this since I switched to my default sound card.

What do I enter to change it?

---

### Post by Zellio on 2007-04-30
I can't get into safe gnome, it resets on there too.

I selected my built in sound card as the main sound card, and now the system just resets.

If only I could get in and reset that :( 

It's like the system is laughing at me...

I kinda need to know what to enter into safe terminal to reset my sound card info...  or to set the sound card default to chaintech av710...

I've tried going as far as diabling built in sound in bios, it plays the beginning sound, then no other sounds, and still resets.

---

### Post by Zellio on 2007-04-30
bump?

---

### Post by solar george on 2007-04-30
Switch to a text terminal (ctrl+alt+f1)

Login as your self,

Type 
```
sudo adduser test 
```

The first password it asks you for will be your own password (for sudo) then it will ask you to enter a new password (for the new user) enter what ever you like.

Go back to the graphical login (ctrl+alt+f7) and try to login as test, see what happens and post back.




P.S. Please don't 'bump' after only two hours everyone isn't online at the same time.

---

### Post by Zellio on 2007-04-30
I can enter on test just fine...

But how do I save my main account...  It still resets...

---

### Post by chrisccoulson on 2007-04-30
Are there any errors in the bottom of /var/log/syslog or /var/log/messages? Just after you have attempted to log in via GDM and it crashes back out, switch to a terminal, log in and do:

```
tail /var/log/syslog
tail /var/log/messages
```

What do they say?

Also, is there anything in ~/.xsession-errors?

---

### Post by Zellio on 2007-04-30
I can't really do anything with that, because that sends logs to my dead account.  I dunno yet how to retreive the logs or even post them since they are on the dead account.

Is there anyway of reseting the sound card from the other account, or just erasing that accoutn and starting over? :-(

Okay, something is odd about my ubuntu...  I may have found the problem... If I can fix it, I may be able to ressurect my account.

Sounds show no sound card.

This problem started when I switched to main sound engine.

Coincindence?  I think not.

Anyone got any ideas?  It's a Nvidia Nforce built in and a chaintech av710.  When the chaintech runs everythng is okay, but I switched to nvidia stupidly and now...

And update manager is broken too, and I can't fix it...  ****

Damnit, I give up.  Reinstall.  Thanks anyway.

---

### Post by solar george on 2007-04-30
> Damnit, I give up. Reinstall. Thanks anyway.

That would have been my advice.

---

