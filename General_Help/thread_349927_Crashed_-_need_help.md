---
title: "Crashed - need help"
date: 2007-01-30
forum: General Help
---

### Post by herbertbrubaker on 2007-01-30
I was performing some simple tasks in Terminal (tar, cp, mv) and suddenly I began getting some odd feedback. Upon trying a sudo command, I got the response to the effect that "UID 1000 was not in the database."

I closed out terminal and reopened. When it opened, the standard handle in front of the prompt $ was changed to something like "no name available". The font and size were also different. I rebooted immediately, but it now hangs in both regular boot and "recovery mode," leaving me an unresponsive prompt (just an underscore, sometime no character at all) on a black screen. In the regular boot, it hangs after the initial Ubuntu splash screen with the progress bar. In recovery mode, it hangs after "starting /scripts/user_init"

How do I go about diagnosing this problem? I have a dual-boot setup with windows, and could also boot into the live CD if that would help things. 

Thanks for any suggestions.

---

### Post by K.Mandla on 2007-01-30
It doesn't sound good. If I were you I'd seriously think about copying off anything that was on the drive (by mounting the drive from a live CD environment and copying to USB drive) before you go any further.

So your rescue mode prompt doesn't work at all? Do you get any error messages or error logs?

---

### Post by herbertbrubaker on 2007-01-31
No error messages appear - just the blank screen. 

Where do I find any logs that might have been created during the startup process?

Thanks for your response.

---

