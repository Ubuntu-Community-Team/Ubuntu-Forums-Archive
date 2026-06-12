---
title: "intentionally slow machine"
date: 2007-05-03
forum: General Help
---

### Post by pjkoczan on 2007-05-03
This may sound like a strange topic, but I'd like to see if anyone has had experience with something like this.

At work I'm removing a bunch of old machines since they're getting harder and harder to support. However, my fellow co-workers and I still have at least one "need" for an old machine, punishment for bad users. For instance, one user was tying up a LOT of bandwidth on our main web server, so we made an invisible proxy/redirect to a slow (~1 GHz) machine, to show that was a difference without that user, to lessen the load on the main web server, and to try and slow down the slew of traffic. There has been quite a noticeable different. Plus, we could make fileservers, databases, and other things run on bad machines for bad users.

My question is this: Is there any way you know of to predictably slow down a machine (i.e. make a 3 GHz machine perform like a 1 GHz machine)?

I know there are some common suggestions people will have. However, we probably won't do them, and here's why:
- Running windows - A sure way of reducing performance, but we simply don't support windows servers. We have neither the need for any services it could provide nor the desire for that level of pain.
- Running it under a VM/emulator - Due to our network structure and file services, we can't reliably run under a VM or emulator and still access everything we need to.
- nice'ing the processes - Adds too much complexity for essentially an edge case.

Rather, what I'm looking for is some way to either tie up the CPU or force it to idle for a long time.

Any ideas?

---

### Post by rich.bradshaw on 2007-05-03
nice is surely the way to go... just make that user's processes the least priority. When no one else is using it it will be fine, otherwise they will be throttled.

What's the point of not using the CPU cycles when someone could be using it?

nice is the way to go.

---

