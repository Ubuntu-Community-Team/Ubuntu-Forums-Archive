---
title: "Ubuntu 20.04 (NICE DCV) mic audio quality very inconsistent"
date: 2024-06-27
forum: General Help
---

### Post by charlieh512 on 2024-06-27
[COLOR=#0C0D0E][FONT=-apple-system]So I have this EC2 g4dn.xlarge instance set with NICE DCV and Ubuntu 20.04(it uses uses custom Intel Cascade Lake CPUs and NVIDIA T4 GPUs), I'm running Minecraft on it with a simple voice chat plugin. The audio through the mic is fine most of the time, but around 5% of the time, it just goes all muffled, sounds like talking through a wall and is very unclear. And there are some crackling occasionally as well. I made sure this is not simple voice chat or Minecraft's problem as I also set up OBS to record my mic input, and the quality is still dropping a lot at some point(it becomes normal after a while).[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]Anyway, I did a lot of searching myself, first I thought this was the CPU usage problem because Minecraft is a very CPU-consuming game, so I tweaked Minecraft to use as little CPU as possible(mods and reducing rendering distance, etc) and I set very high priority for PulseAudio (as some suggested, nice to -20 and real-time priority to like 90), I also tried tweaking the settings in /etc/pulse/daemon.conf in various ways but none of the above attempts help completely eliminate this problem.[/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system]So I'm wondering if any of you have gotten the same problem before and how you fixed it? Is this really a Ubuntu issue, or could this be a Nice dcv issue (they use a virtual sound card, and I couldn't find any post related to the NICE dcv audio issue)? I'd really appreciate any help at this moment, thanks.[/FONT][/COLOR]

---

