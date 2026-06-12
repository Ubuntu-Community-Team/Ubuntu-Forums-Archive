---
title: "sluggishness &amp; nvidia-settings"
date: 2008-02-02
forum: General Help
---

### Post by atorch on 2008-02-02
Hi everyone,

I'm having a problem with sluggishness.

I've attached a screenshot of my system monitor; please take a look at it *before reading what follows.*

A: I click once on a document on my desktop, simply to select it. Then I press the arrow keys to quickly select others. I'll pick one up and drag it around. All of this happens with a noticeable delay between action & effect (it takes a noticeable amount of time for an icon I've clicked on to become highlighted), and my CPU usage spikes up noticeably. If I check the "Processes" tab (while selecting icons on my desktop), I see that almost all running processes are at 0% CPU; sometimes one of them will climb to 2 or 3%, but never higher. This is strange -- you'd think the parts (0+0+...+0+2) would add up to the whole (sometimes up to 90% CPU usage at the peaks), but they don't.

B: I run nvidia-settings OR sudo nvidia-settings; CPU usage spikes as I change my display's resolution and refresh rate. More on this later.

C: I am doing the *exact* same thing as in A, but CPU usage is now constant at 1~3%, as expected.

B is a solution to the problem in A (since C is where I want to be), but *every time I restart my computer*, I'm back at A.

Now, more detail on what's happening at B:

I run either nvidia-settings or sudo nvidia-settings and then, under the "X Server Display Configuration Tab," I change the Resolution / Refresh Rate combination.

The Resolution / Refresh Rate combination can be one of three things:

Auto and Auto
1280x800 and Auto
1280x800 and 60Hz

No matter what the Resolution / Refresh Rate is, I change it to something else, and click apply. After a few moments of my CPU spiking to 100% (you can see this in the graph), I click OK. After that I click "Save to X Configuration File." If I am running sudo nvidia-settings, the save works without any error and I'm done. If I am running nvidia-settings without sudo, I get an error message about rewriting or saving to the X Config Backup File, probably because I don't have permission.

Whether or not I ran nvidia-settings as sudo, step B solves the problem *temporarily* -- that is, until I restart.

Now here's the strange part:
If I ran nvidia-settings with sudo, and restart my computer, the Resolution / Refresh Rate combination that I chose will be remembered by nvidia-settings. However, I still get lag -- to fix it, I again have to change to something else.

But if I ran nvidia-settings without sudo (and restart my comptuer), the Resolution / Refresh rate combination will *not* be remembered by nvidia-settings; instead, it defaults back to the most recent combination that was saved with sudo.

This is strange because it allows any member of the set of Resolution / Refresh Rate combinations to be either a solution to or a cause of the problem. Neither combination is always best or always worst -- all that matters is that, every time I restart my computer, I *change* the Resolution / Refresh Rate from whatever if was before. It does not matter *what* I change it to or what I change it from; all that matters is that it change. And that fixes the problem -- temporarily, until I restart my computer, at which point I have to change it again.

I might be shooting a dead horse at this point, but let me just give an example:

When I first noticed the lag, I ran nvidia-settings without sudo and changed from Auto-Auto to 1280x800-60Hz. The lag is gone.

I restart the computer. It's lagging again; and because I changed the settings without sudo, they've defaulted back to Auto-Auto. This time I run *with* sudo and change from Auto-Auto to 1280x800-60Hz. The lag is gone.

I restart the computer. It's lagging again; but this time the settings are 1280x800-60Hz. So I run settings with sudo and change back to Auto-Auto. The lag is gone.

I restart the computer. It's lagging again; the settings are Auto-Auto. I sudo change them to 1280x800-Auto. The lag is gone.

I restart. Lagging again; the settings are 1280x800-Auto. I sudo change them. The lag is gone.

I restart. Ad infinitum.

Phew. Sorry for such a long post to explain something so simple, but I find the problem very strange and I wanted to give a thorough explanation.

So: Any suggestions? Lag is annoying; so is running nvidia-settings every time I restart. I'd appreciate any help you can offer.

Thanks,
--Adrian

---

### Post by nemilar on 2008-02-02
Please run 

```
top
```

In a terminal, and when your computer lags, notice the processes at the top of the list, and how much CPU % they are using; then post them here.

---

### Post by atorch on 2008-02-03
Xorg runs with 10~100% CPU when the computer is lagging (the percentage climbs the most when I'm selecting icons on my desktop, dragging them around, et cetera.)

After step B, Xorg's CPU percentage falls to 0~1%.

---

### Post by atorch on 2008-02-04
Turning off desktop effects makes the lag go away.  So this is Xorg / Compiz / Graphics related, or so my linux-newbie intuition tells me.

---

