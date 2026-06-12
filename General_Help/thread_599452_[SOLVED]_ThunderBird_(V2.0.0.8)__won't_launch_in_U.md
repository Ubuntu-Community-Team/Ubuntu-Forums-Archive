---
title: "[SOLVED] ThunderBird (V2.0.0.8)  won't launch in Ubuntu 7.10 (Gutsy)"
date: 2007-11-01
forum: General Help
---

### Post by rmhodv on 2007-11-01
Finally I managed to install tbird 2, only to find that now when I click the icon to launch, the hour glass appear and just hangs for about 20-25 seconds and then that's it.

The thunderbird panel appears at the bottom of the screen when it's trying to launch (with the hour glass), but then disappears after 20-25 seconds.

see this post for a complete history  

[http://ubuntuforums.org/showthread.php?t=597424](http://ubuntuforums.org/showthread.php?t=597424)


If anyone can help me I'd be most grateful.

---

### Post by fdv1 on 2007-11-01
Can you open a command prompt, and start the application, and see if any errors are generated when you start *that* way?

---

### Post by rmhodv on 2007-11-01
> **fdv1 said:**
> Can you open a command prompt, and start the application, and see if any errors are generated when you start *that* way?

Hi I've only been using Linux for about a week now...How do I do that?

---

### Post by Maestro23 on 2007-11-01
> **rmhodv said:**
> Hi I've only been using Linux for about a week now...How do I do that?

Apps>>Accessories>>Terminal

At the prompt type:

> thunderbird

---

### Post by rmhodv on 2007-11-01
> **Maestro23 said:**
> Apps>>Accessories>>Terminal

At the prompt type:

Thank you. I'll give this a try. I'm in the UK (and at work ;)), but when I get home in about 1.5 hours time I'll do this and post my response.

---

### Post by rmhodv on 2007-11-01
OK, I have just typed Thunderbird into Terminal, and this what I get.

/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Hope this helps with a diagnosis.

---

### Post by Maestro23 on 2007-11-01
> **rmhodv said:**
> OK, I have just typed Thunderbird into Terminal, and this what I get.

/opt/thunderbird/thunderbird-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Hope this helps with a diagnosis.

You need: libstdc++5 - The GNU Standard C++ Library v3
or

libstdc++6 - The GNU Standard C++ Library v3

Search for them in Synaptic.  Mark for install and apply

---

### Post by rmhodv on 2007-11-01
> **Maestro23 said:**
> You need: libstdc++5 - The GNU Standard C++ Library v3
or

libstdc++6 - The GNU Standard C++ Library v3

Search for them in Synaptic.  Mark for install and apply


That looks like it has worked. Thank you very much. :cool: :grin:

---

### Post by stchman on 2007-11-01
> **rmhodv said:**
> Finally I managed to install tbird 2, only to find that now when I click the icon to launch, the hour glass appear and just hangs for about 20-25 seconds and then that's it.

The thunderbird panel appears at the bottom of the screen when it's trying to launch (with the hour glass), but then disappears after 20-25 seconds.

see this post for a complete history  

[http://ubuntuforums.org/showthread.php?t=597424](http://ubuntuforums.org/showthread.php?t=597424)


If anyone can help me I'd be most grateful.

I was not aware that Mozilla released Tbird 2.0.0.8.  If you go to their website they talk about 2.0.0.6.

---

### Post by Maestro23 on 2007-11-01
> **rmhodv said:**
> That looks like it has worked. Thank you very much. :cool: :grin:

Good deal man.  Don't forget to mark this SOLVED using Thread Tools.

Thanks.:)

---

