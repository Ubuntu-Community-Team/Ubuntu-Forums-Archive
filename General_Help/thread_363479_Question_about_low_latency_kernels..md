---
title: "Question about low latency kernels."
date: 2007-02-17
forum: General Help
---

### Post by SoulinEther on 2007-02-17
Yeah... Can someone explain to me exactly what a low latency kernel does? Just wondering.

Maybe this should go into another forum.. hum, just wouldn't mind a decent explanation. Perhaps both simplistically and more detailed. Or some resource that I may visit to find more information, like a link.

Thanks!

---

### Post by junglebarry on 2007-02-19
Latency is the amount of delay between input and output. It is most noticeable for realtime applications like audio recording, where the input is usually from a music instrument, and the output is then played back to the musician. If latency is large, there will be a significant delay between playing the sound and hearing it, which can be offputting, but also makes it difficult to record tracks in parallel (since it is hard to get the sounds to line up).

Low latency kernels are designed to minimise the amount of delay in any input/output scenario. They are useful for realtime applications like audio recording.

I don't know the precise details, but there are a number of very low-level operations (like the way an OS allocates memory or CPU time to processes) that can impact upon latency. If you change the specific details of these operations, the OS (kernel) can be "tuned" to make realtime applications faster, at the expense of, say, running many programs at once. In general there is a trade-off between latency and other system characteristics, so default kernels are not tuned to low latency, preferring a balance that is better for everyday use.

There's a pretty lame snippet here:
[http://en.wikipedia.org/wiki/Low_latency](http://en.wikipedia.org/wiki/Low_latency)

HTH

---

