---
title: "Is it possible to run hardware accelerated applications in multiple x servers?"
date: 2014-11-16
forum: General Help
---

### Post by Kimm on 2014-11-16
Pretty much ett what the title says, can I run two X servers with hardware acceleration?

What i want to do is to run my desktop environment and all of my every day applications in one server and have games (World of watercraft to be exact) running on a dedicated X server. I can actually get WoW running on its own server, but it crashes as soon as I click on anything inside the window, throwing a "BadWindow" error, which I assume had something to do with it not getting proper hardware acceleration.

Does anyone have any experience with something like this?

---

### Post by TheFu on 2014-11-16
X-servers are tied to the GPU.  So, if you have 2 GPUs, then you can run a different X/Server on each.  If you have 1 GPU, no you cannot.

I've had 2 GPUs, run separate X/Servers, and connected to separate monitors. There are hassles with this - normal select/paste doesn't work across X/Servers, for example.  You won't be able to drag windows between them either.

---

### Post by matt_symes on 2014-11-16
Hi

Just to clarify, it is possible to have multi X servers on 1 GPU but you can only have 1 running at a time. The other X servers have to be suspended. 

I regularly have multiple X servers on different consoles and switch between them. It wakes up the suspended X server that I'm switching to and suspends the one I'm switching away from.

If you want to be able to access 2 or more X servers at the same time then, as stated by theFu, you need 2 or more GPUs.

I know it's not your original question but it may be of interest to others reading this thread.

Kind regards

---

