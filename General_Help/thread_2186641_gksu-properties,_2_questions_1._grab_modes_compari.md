---
title: "gksu-properties, 2 questions: 1. grab modes comparison; 2. su/sudo mode buggy or what"
date: 2013-11-08
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2013-11-08
2 questions about the gksu-properties dialogue:

1. What exactly are the grab modes? The only thing close to documentation is the somewhat vague tooltip that pops up. "man gksu-properties" is useless. An -h or --help switch is ignored. It defaults to "enabled" which I assume means that the gksu password dialogue will grab the keyboard and not let anything else see the password you type into it. IF that is the case what is the difference with "force enabled"? Does that mean the gksu password dialogue INSISTS on having exclusive sight of the password and won't work until it gets it whereas with plain enabled it meekly says "Well, Mr. Malware, I don't want to let you see the password but if your're gonna be pushy about it I'll let you."? Or am I misunderstanding this altogether? It sure sounds like "force" is the more secure option.

2.The other question is about the su/sudo mode setting. Is the su mode supposed to be a graphical equivalent to "sudo su" or to "su"?  I've got an Openbox, sans Lubuntu, sans LXDE, system working pretty well under Raring and now I'm building one up under Precise. I ran into a problem with none of my "gksu whatever" menu entries working. They'd pop up the right graphical password dialogue but they insisted I was giving the wrong password, which I wasn't. In searching for solutions I saw changes in the su/sudo mode in gksu-properties suggested for similar problems. That kinda could make sense. If it was a graphical "su" rather than a "sudo su" or "sudo" it would want the nonexistent root password. Seems kind of weird that would be an option in an OS where su is officially a dirty word. I always assumed gksu was a graphical "sudo su". Anyway, it was already set to "sudo" so that wasn't the problem. I toggled it a few times and it didn't seem to make any difference to anything as far as I could see. But the proecess got me to wondering. So I did the forbidden magic and enabled the root account. Then the "gksu whatever" entries all started working. So, does that mean gksu-properties is broken in Precise, at least on that system, or maybe buggy period? And that gksu is equivalent to "su" no matter how I set it? Is it supposed to be? Ever? That doesn't make sense to me. What good is "su" (as distinct from "sudo su") without a root account? Pragmaticly, my problem is solved with the forbidden measures we won't discuss, but I'd like to understand this.

---

