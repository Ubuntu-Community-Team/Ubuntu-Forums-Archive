---
title: "Firefox and wwwoffle"
date: 2008-06-10
forum: General Help
---

### Post by editrix on 2008-06-10
Just installed K/Ubuntu Hardy, and when I tried to use FF with wwwoffle, FF froze completely. Nor will it reload. Had to delete my .mozilla directory, but after a couple of times of doing that, FF seems completely destroyed. If I try to launch it, nothing happens for the longest time, then it finally loads, but only the top frame of the window shows up and I have to kill it.

I'm on dialup, so reluctant to download anything as huge as FF2, which seems to be the only solution to everyone else's FF problems.

---

### Post by y-lee on 2008-06-10
Strangle problem and I'm not sure But could you open a terminal and start firefox with a terminal command and post all error messages here.

```
firefox
```

---

### Post by editrix on 2008-06-10
Hi y-lee:

Since FF was completely frozen, I had to delete the .mozilla folder. Since then, FF loads--sort of--but very, very slowly. In fact, I entered firefox on the command line about 45 seconds ago and I'm still waiting for it to load. (twiddle thumbs, dah-dum, dah-dum)

Still not loading ...

Yikes! I see no feedback at all in the terminal. Was there something else I should have done? Pipe it to a file or something?

Anyway, it was frozen so I had to kill it. I never put wwwoffle in the new profile, so I don't know what's going on.

I'm using Kubuntu, if that makes any difference.

---

### Post by y-lee on 2008-06-10
Have you tried a new profile?

```
firefox -P
```

or safe mode?

```

firefox -safe-mode
```

If safe mode spits out any errors post them here please?


If none of that works have you tried uninstalling (purging might be the best idea) and then reinstalling?

> Was there something else I should have done? Pipe it to a file or something?

Shouldn't matter actually.


> I'm using Kubuntu, if that makes any difference.

No that shouldn't make much difference either.

---

### Post by editrix on 2008-06-10
> **y-lee said:**
> Have you tried a new profile?

```
firefox -P
```

I deleted the .mozilla folder and tried it:

firefox:19339): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(firefox:19339): atk-bridge-WARNING **: IOR not set.

(firefox:19339): atk-bridge-WARNING **: Could not locate registry

(firefox:19339): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(firefox:19339): atk-bridge-WARNING **: IOR not set.

(firefox:19339): atk-bridge-WARNING **: Could not locate registry

and I got the Welcome to Kubuntu screen but it's frozen. Nothing will click.

> or safe mode?

```
firefox -safe-mode
```

I deleted .mozilla once again and tried it:

(firefox:19257): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(firefox:19257): atk-bridge-WARNING **: IOR not set.

(firefox:19257): atk-bridge-WARNING **: Could not locate registry
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)  [ad nauseam]

Then it loaded, but said it couldn't go anywhere because it was offline. So was I (I'm on dialup).

Looks like it's an FF problem (or a Hardy problem) rather than wwwoffle.

> If none of that works have you tried uninstalling (purging might be the best idea) and then reinstalling?

Well, that will be my last resort, since I've read on these forums that some people are having problems even after doing that.

But, I assume you're running FF with wwwoffle? Has anything changed that I should know about? IIRC, the only thing you have to do is install wwwoffle and tell FF to use the proxy on port 8080.

Oh boy, it just loaded again while I was typing the above. I manage to type something in the Google box but then it froze. I'll be it was offline, too. I wonder if that isn't what's causing the problem: I have to remember to put it online before I do anything else?--If I can do anything with it once it loads.

Ack! Ten minutes doing something else, and all of a sudden I get the page I'd typed into the Google box!

---

