---
title: "Lots of freezing in 14.04 LTS"
date: 2014-05-11
forum: General Help
---

### Post by josephellengar2 on 2014-05-11
I upgraded to 14.04 LTS today on my HP Envy touchsmart 17 (core i9-4900 processor, Nvidia graphics)

As soon as I did, my computer started freezing so much that I ultimately had to restore my backup from prior to the upgrade. It happened in multiple desktop environments, mostly when the computer had high CPU usage, and was very, very frequent.

I'm not sure why this would be-- mostly in the past when this happened after an upgrade it was due to the DE being faulty. My 13.10 installation is fine. I did install the Nvidia driver, but even when I changed 14.04 back to the nouveau driver it didn't work properly. Does anybody have any advice? I am concerned since with the shortened support schedule I only have a few months left on 13.10 to sort this out.

Thanks!

---

### Post by LastDino on 2014-05-11
Can you try doing fresh install? You've back up and everything, it's better to sort it out that way. Usually problem like this is related to GPU but you're saying that you installed non-free drivers for it, so I'm guessing something went wrong with update and it would be hard to pin point correctly what it is.

---

### Post by josephellengar2 on 2014-05-11
> **LastDino said:**
> Can you try doing fresh install? You've back up and everything, it's better to sort it out that way. Usually problem like this is related to GPU but you're saying that you installed non-free drivers for it, so I'm guessing something went wrong with update and it would be hard to pin point correctly what it is.

I could, but I'm not quite that desperate yet. I just have so much stuff that I closely customize on my systems and I would prefer not to do do that if there is any way around it. One thing that I haven't done yet that you just made me think of, though, is that I should probably go and use a live usb. I could try that both with and without the drivers and see if it freezes. I'll report back here as soon as I do that. Anything else that you think I should try while I'm in the live session?

Oh, I just thought of something else that I should try. Maybe I'll try re-updating and keeping "top" open in a terminal window. I might have enough luck to see something misbehaving.

---

### Post by monkeybrain20122 on 2014-05-12
> **josephellengar2 said:**
> I could, but I'm not quite that desperate yet. I just have so much stuff that I closely customize on my systems and I would prefer not to do do that if there is any way around it. 

See that is the problem. The more 'customized' your system is the more likely that 'upgrade' will break it because it expects a system without much modification. But if yu have a vanilla system there is no real incetive to 'upgrade' instead of a clean install,--upgrades take several hours and a clean install 15 minutes So either way you should do a clean install. 

You can do other things to save some of your customizations, for example, a separate /home and backup some key system config files and do a fresh install, it is a lot faster and safer. There is no way to keep all your 'customizations' from one release to another.

---

### Post by LastDino on 2014-05-12
> **josephellengar2 said:**
> I could, but I'm not quite that desperate yet. I just have so much stuff that I closely customize on my systems and I would prefer not to do do that if there is any way around it. One thing that I haven't done yet that you just made me think of, though, is that I should probably go and use a live usb. I could try that both with and without the drivers and see if it freezes. I'll report back here as soon as I do that. Anything else that you think I should try while I'm in the live session?  Oh, I just thought of something else that I should try. Maybe I'll try re-updating and keeping "top" open in a terminal window. I might have enough luck to see something misbehaving.    You do realize that most of your customizations with 13.10 wont work with 14.04 due to upgrade process, right?

---

### Post by josephellengar2 on 2014-05-12
> **LastDino said:**
> You do realize that most of your customizations with 13.10 wont work with 14.04 due to upgrade process, right?

They're mostly in linux-specific (as opposed to ubuntu-specific) system files. I'm sure that some stuff will break, but I think most stuff will be fine. And then there's just what I have installed, how specific programs are customized, and stuff like that. My home directory is on a separate partition.

---

