---
title: "&quot;Out of range&quot; error. It came and went, not sure why or where it's at."
date: 2007-02-18
forum: General Help
---

### Post by Roasted on 2007-02-18
Long story short. I got some updates from Ubuntu and my Nvidia driver was hosed. Tried to boot and it gives me some X Server errors and blah blah. Redid the Nvidia driver's from the terminal using a Beryl installation guide and only using the section where you installed the drivers (thanks to somebody in my other thread that helped). Anyway, okay no big deal.

Here's the kicker. I've had Linux running for the last 4 days. So when I rebooted for the first time and came back to Linux, I had the error again. I also got an "out of range" error, that also said something to the degree of "H - 65KHz V - 60Hz." It stuck on the screen for a bit, then phased away. I booted up, and my Nvidia driver was hosed.

As I said, I came in terminal and redid the Nvidia driver, rebooted, I got the "out of range" error again, however I could boot just fine into the GUI. To be safe, I rebooted again.

I booted up the third time, ready with a pen and paper to write down everything on the out of range error, and it didn't show up. I was confused, but like before, I booted into the GUI just fine.

Where did the error go?
Why did I have the error?
How can I change whatever it is the error found wrong?

---

### Post by dcstar on 2007-02-19
> **Roasted said:**
> Long story short. I got some updates from Ubuntu and my Nvidia driver was hosed. Tried to boot and it gives me some X Server errors and blah blah. Redid the Nvidia driver's from the terminal using a Beryl installation guide and only using the section where you installed the drivers (thanks to somebody in my other thread that helped). Anyway, okay no big deal.

Here's the kicker. I've had Linux running for the last 4 days. So when I rebooted for the first time and came back to Linux, I had the error again. I also got an "out of range" error, that also said something to the degree of "H - 65KHz V - 60Hz." It stuck on the screen for a bit, then phased away. I booted up, and my Nvidia driver was hosed.

As I said, I came in terminal and redid the Nvidia driver, rebooted, I got the "out of range" error again, however I could boot just fine into the GUI. To be safe, I rebooted again.

I booted up the third time, ready with a pen and paper to write down everything on the out of range error, and it didn't show up. I was confused, but like before, I booted into the GUI just fine.

Where did the error go?
Why did I have the error?
How can I change whatever it is the error found wrong?

The message is the system trying to set your monitor into a mode (resolution/refresh) that it cannot handle, so you saw that message.

It isn't supposed to happen, but if you had a broken video driver then it could well have got itself messed up enough to cause something like this.

Once your video driver got itself 100% sorted out, it looks like the problem is gone (as it should be), so don't worry about it (until the next time your video driver gets broken!).

---

