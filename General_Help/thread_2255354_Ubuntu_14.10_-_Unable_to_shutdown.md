---
title: "Ubuntu 14.10 - Unable to shutdown"
date: 2014-12-04
forum: General Help
---

### Post by raptir on 2014-12-04
Hoping you can help. I had been having trouble on and off with my laptop not shutting down. It would get to the shutdown splash screen and then freeze with the first "dot" illuminated. I updated my system fully and after a couple shutdowns still freezing I was able to shutdown successfully for about a week. Then, a few days ago, without having installed any new software or updates, the issue returned but will now *consistently* freeze every time. I did some research on how to disable the splash screen (removing "quiet splash" from the grub config). The majority of the shutdowns do not display any output to the terminal. The terminal comes back up but only shows the same text as from startup. Just once I've received output, and it ends with:

```
Deactivating swap...
Will now halt
[1070.500833] reboot: Power down
```

It freezes there and does not turn off. When it freezes, I can only shut down the laptop by holding the power button. Trying to switch to tty1, etc... does nothing.

Does anyone have any suggestions of things I could try to resolve the issue, or any additional info I can provide?

---

### Post by raptir on 2014-12-16
Just wondering if anyone had any thoughts on this.

---

### Post by shadytv on 2014-12-16
How are you shutting down the system? are you using the GUI?

try doing a sudo poweroff or sudo init 0 from the command line.

does using these commands make a difference?

---

### Post by spiffymoo on 2014-12-17
[B][FONT=Open Sans][COLOR=#444444]try updating grub[/COLOR][/FONT]
[FONT=Open Sans][COLOR=#444444]Open the Terminal[/COLOR][/FONT][COLOR=#444444][FONT=Open Sans] by clicking on Application > Accessories > Terminal[/FONT][/COLOR]
[COLOR=#444444][FONT=Open Sans]Type:
[/FONT][/COLOR]```

[B]sudo update-grub
[/B]
```[B]
Press [B]Enter
Type your [B]password and press [B]Enter
Once the update is done, [B]Restart your computer.

[/B][/B][/B][/B][/B][/B]

---

### Post by Bucky Ball on 2014-12-17
As in post #3. You could also try:

```
sudo reboot -h now
```

... and see if that kills it completely and reboots. Take note of any errors if they are different from the original.

---

### Post by raptir on 2014-12-17
Thanks for the tips. I was trying it from the GUI in both Unity and Xfce. I will see what happens from the command line when I get home tonight and report back.

Edit: Also, rebooting works fine, it's only shutting down that hangs.

---

### Post by raptir on 2014-12-22
I haven't been able to reproduce the issue consistently lately. It's only occurred a few times since I posted last. It did not happen any time I tried sudo poweroff, sudo init 0, or sudo reboot -h now. I did not yet try updating GRUB because I was hoping to be able to get some more information on this...

I don't want to mark this as solved yet, since it is still occurring occasionally, but I'm not sure of any next steps. Is there anything I can do to get more information after this issue occurs the next time?

---

### Post by schragge on 2014-12-23
It would be useful to test if you could perform shutdown by sending a signal to ConsoleKit over D-Bus like described [here]("https://stackoverflow.com/questions/13774312"). This is basically what GUI shutdown buttons do behind the scenes.
That scary-looking D-Bus command can be written in one line, too:
```

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop

```
And I don't think updating GRUB will change anything unless you also change grub configuration in */etc/default/grub*.

---

### Post by raptir on 2014-12-25
> **schragge said:**
> It would be useful to test if you could perform shutdown by sending a signal to ConsoleKit over D-Bus like described [here]("https://stackoverflow.com/questions/13774312"). This is basically what GUI shutdown buttons do behind the scenes.
That scary-looking D-Bus command can be written in one line, too:
```

dbus-send --system --print-reply --dest=org.freedesktop.ConsoleKit /org/freedesktop/ConsoleKit/Manager org.freedesktop.ConsoleKit.Manager.Stop

```
And I don't think updating GRUB will change anything unless you also change grub configuration in */etc/default/grub*.

Well, I was able to shutdown but unfortunately the issue is now very much intermittent. Between yesterday and today I've shutdown my laptop six times, once using the dbus method above. 4 out of the 6 times it shutdown fine, twice it hung on the line in the first post. I'm not really sure how to diagnose it when it is so intermittent.

---

### Post by Bucky Ball on 2014-12-25
When it hangs, can you hit control+alt+F1, login and type 'dmesg'. The last output there might give a clue about what's holding things up.

---

### Post by raptir on 2014-12-26
> **Bucky Ball said:**
> When it hangs, can you hit control+alt+F1, login and type 'dmesg'. The last output there might give a clue about what's holding things up.

Nope, it's fully frozen.

---

### Post by raptir on 2015-01-13
So, I played around with a few different kernel versions (and even jumped between distributions to try to troubleshoot this). Here's what I've learned...

**3.13 (tested in 14.04):**

Early versions of the kernel work fine, through about 3.13.0.37. The later versions than that freeze up on shutdown intermittently.

**3.16:**

Early versions (3.16.0.23-26) freeze frequently, nearly every time. 3.16.0.28 and 29 freeze often, but not nearly as frequently as the earlier builds. However, I will still sometimes get into a run where it freezes almost every time.

**3.17 (tested in Fedora):**

I can't find a pattern between different subversions. The system rarely freezes, but when it does freeze it seems to go into a string of freezing for a time, then works fine for a while.


Would it be worth trying one of the mainline kernels ([http://kernel.ubuntu.com/~kernel-ppa/mainline/)?](http://kernel.ubuntu.com/~kernel-ppa/mainline/)?) Or does that tend to introduce more problems since they are not ubuntu-patched?

---

