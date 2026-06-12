---
title: "Slow startup due to snaps programs"
date: 2019-03-28
forum: General Help
---

### Post by phcrepaldi on 2019-03-28
I have installed several snaps programs on my Ubuntu 18.10 and it's taking almost 4 minutes to the computer to startup. I noticed those /loop/dev... that appears at startup and found out that those are the snaps programs loading. I never knew that, if I knew it I would never installed them as snaps. I think there are a lot of people who also do not know about it. Is there any way I could fix this? Several of those programs are already set up and running just right and I did not want to have to reinstall them. Does the only way is to reinstall them as flatpak or through repository? Any suggestion of what kind of package should i use so i don't have anymore unpleasant surprises like that?

---

### Post by Bashing-om on 2019-03-28
phcrepaldi; Hello - Welcome to the forum.

Yeah, known issue and some means to help:
Snap startup time improvements -> [https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)

The developers do welcome  "feedback or suggestions on this topic, please join our forum for a discussion.".

[INDENT]my bit to try and help
[/INDENT]

---

### Post by raleigh3 on 2019-03-28
> **phcrepaldi said:**
> I have installed several snaps programs on my Ubuntu 18.10 and it's taking almost 4 minutes to the computer to startup. I noticed those /loop/dev... that appears at startup and found out that those are the snaps programs loading. I never knew that, if I knew it I would never installed them as snaps. I think there are a lot of people who also do not know about it. Is there any way I could fix this? Several of those programs are already set up and running just right and I did not want to have to reinstall them. Does the only way is to reinstall them as flatpak or through repository? Any suggestion of what kind of package should i use so i don't have anymore unpleasant surprises like that?

I had a problem with a Gimp snap package and had to remove it and use re-install using Synpatic.

I would recommend only using flatpaks or Synaptic.

---

