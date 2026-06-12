---
title: "Ubuntu 14.04 gets stuck at shutdown"
date: 2015-11-08
forum: General Help
---

### Post by Denco1 on 2015-11-08
My girlfriend's laptop seems to have another problem with Ubuntu.  Apparently, it gets stuck at shutdown. It has never happend to me, when I  tried it. It happens just to her (but that is OK, computers are afraid  of me). It hangs on Ubuntu logo with those 3 dots below it. Are there  any logs, that could help me (and you) to find out, what is the problem?

One thing I tried. I removed "quiet splash" from GRUB config file, so I can see what is happening. And this is what happend.

[ATTACH=CONFIG]265436[/ATTACH]

And that really does not say anything (at lease I think). Thank you for your answers.

---

### Post by matt_symes on 2015-11-08
Hi

It looks like her laptop is halting and not powering down.

Let's try a test.

Start her laptop and login. Bring up a terminal and type

```
sudo shutdown -P now
```

That's a capital P above.

Does that power off the laptop ?

Kind regards

---

### Post by Denco1 on 2015-11-09
Problem is, that it does not happen everytime. Sometimes it powers down correctly. Anyway. I'll try it.

EDIT
If that command powers down the laptop everytime, what could be the solution? (so she does not have to power it down by terminal)

EDIT #2
Also it looks like it happens if the laptop has been powered on for longer time, like the all day. Let's say she works on it all day, it won't shutdown. But if she turns it on in the morning and shutdowns immediatelly, it will power down correctly.

---

### Post by matt_symes on 2015-11-09
Hi

> **Denco1 said:**
> Problem is, that it does not happen everytime. Sometimes it powers down correctly. Anyway. I'll try it.

EDIT
If that command powers down the laptop everytime, what could be the solution? (so she does not have to power it down by terminal)

EDIT #2
Also it looks like it happens if the laptop has been powered on for longer time, like the all day. Let's say she works on it all day, it won't shutdown. But if she turns it on in the morning and shutdowns immediatelly, it will power down correctly.

The above post is really unclear.

Does the shutdown -P command in post #2, _always_ poweroff the laptop ? If not then we may be barking up the wrong tree.

Anyway, can you post the output of this command please

```
cat /etc/default/halt
```

Kind regards

---

### Post by Denco1 on 2015-11-09
> **matt_symes said:**
> Does the shutdown -P command in post #2, _always_ poweroff the laptop ? If not then we may be barking up the wrong tree.
She hasn't tried it yet. As I said, laptop needs to be powered on for longer time to be sure, that the command really helps. I'll be back with result tomorrow.

This is the output of *cat /etc/default/halt*

```
# Default behaviour of shutdown -h / halt. Set to "halt" or "poweroff".
HALT=poweroff
```

---

### Post by Denco1 on 2015-11-09
New info

```
sudo shutdown -P now
```

Did not help. It got stuck anyway.

---

### Post by Dennis N on 2015-11-09
Does the computer shut down by itself if you wait 90 seconds?

Also, you should be able to view shut down messages if you press ESC when the shutdown splash screen is displayed. I don't think you need to remove quiet splash.

---

### Post by Denco1 on 2015-11-09
No, it does not shutdown by itself. It just stays on until she holds the power button for few seconds.

---

### Post by matt_symes on 2015-11-10
Hi

Does the magic key combination turn it off if, for the last key, you hit o instead of r ?

Hold Alt and PrtSc at the same time. Keep the depressed and then type b u s i e o.

Press press each key for 2-3 seconds.

Is her BIOS up to date ?

What's odd with the laptop is that it's not shutting down the laptop only after the laptop has been running for a while. I'm not sure what this would suggest.

Kind regards

---

### Post by Denco1 on 2015-11-10
> **matt_symes said:**
> Hi

Does the magic key combination turn it off if, for the last key, you hit o instead of r ?

Hold Alt and PrtSc at the same time. Keep the depressed and then type b u s i e o.

Press press each key for 2-3 seconds.
Not sure here. All three sentences belong to one action?
Should I try it with busieo and busier? Should I hit space bar after each key (except the last one)?

> **matt_symes said:**
> Is her BIOS up to date ?
I'll check that.

> **matt_symes said:**
> What's odd with the laptop is that it's not shutting down the laptop  only after the laptop has been running for a while. I'm not sure what  this would suggest.
Exactly. True, I'm little bit confused too. That's why I'm here.

---

### Post by matt_symes on 2015-11-10
Hi

To clarify...

> Hold Alt and PrtSc at the same time. Keep them depressed and then type b u s i e o.

Press press of the each keys (b u s i e o) for 2-3 seconds. 

EDIT:

We may be able to get more debug information when you shutdown.

Try adding

```
debug
```

to the grub command line and the running update-grub.

EDIT 2:

If the magic key combination works then you may be able to use it to get a list of running tasks when the system hangs on shutdown, as it's possible that a rouge process is stopping the system powering off.

That may also explain why the hang is intermittent as well.

Kind regards

---

### Post by Denco1 on 2015-11-10
I'm not with her the whole week, so we are doing this remotely. The magic combination did power off the laptop (but I guess immediately, like when you hold the power button). But it was in the moment, when the laptop would power off correctly anyway. So I'm not sure if that's useful or not.

Debug is in the grub command line. I told her to take a photo in case it gets stuck again.

> **matt_symes said:**
> 
If the magic key combination works then you may be able to use it to get a list of running tasks when the system hangs on shutdown, as it's possible that a rouge process is stopping the system powering off.
So the whole thing with Alt and PrtSc and busieo should do that or I don't get it right?

---

### Post by matt_symes on 2015-11-10
Hi

> **Denco1 said:**
> I'm not with her the whole week, so we are doing this remotely. The magic combination did power off the laptop (but I guess immediately, like when you hold the power button). But it was in the moment, when the laptop would power off correctly anyway. So I'm not sure if that's useful or not.

She should try the magic key combination when it is stuck and see if it powers down then. 

That'll be informative and she's had a practice run now :)

Kind regards

---

