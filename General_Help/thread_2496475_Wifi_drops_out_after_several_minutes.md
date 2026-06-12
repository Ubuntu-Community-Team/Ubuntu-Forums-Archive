---
title: "Wifi drops out after several minutes"
date: 2024-03-30
forum: General Help
---

### Post by k20shores on 2024-03-30
I installed Ubuntu 22.04.4 two days ago. After installation, the wifi would work for some time and then drop out. To fix this, I've tried setting the wifi.powersave = 2 and updated my bios. This system has 2 NVME drives, one 2TB drive that windows is installed on, and a 1TB drive that Ubuntu is installed on. This wifi failure **does not** happen with windows, only Ubuntu, so I bet it's a software configuration.


[LIST]
[*]Here's a pastebin of several system stats when the wifi works: [https://pastebin.com/GLXT7J9s](https://pastebin.com/GLXT7J9s)
[*]Here's one for when it fails: [https://pastebin.com/5tZkHdny](https://pastebin.com/5tZkHdny)
[*]And a log of dmesg when it fails, notice that this happens when trying to send a STATISTICS_CMD, around line 1605: [https://pastebin.com/4uUNAnsm](https://pastebin.com/4uUNAnsm)
[/LIST]

When the wifi fails, `[FONT=var(--ff-mono)]sudo lshw -class network` shows that the wireless device is disconnected. I've tried restarting network manager (`sudo systemctl restart NetworkManager`), and bringing the interface up (`sudo [/FONT][FONT=var(--ff-mono)]fconfig [/FONT][FONT=var(--ff-mono)]wlp9s0[/FONT][FONT=var(--ff-mono)] up`). Neither work.

What other logs can I look at to find more information, or how might I fix this?[/FONT][/COLOR]

---

### Post by TheFu on 2024-03-30
I have a wifi AP that automatically reduces output power when traffic isn't flowing.  It doesn't reduce the power so much that it isn't still "connected", but it can take about 5 seconds for the power to be turned up again.  I've never researched if this is on the AP or the client or both sides.  I think it is part of the wifi-6  and later standards.

Wifi chip makers don't really test with Linux. That's part of the issue.

Probably unrelated, but having an SSID with spaces or punctuation in the name could be causing issues.  There are lots of little scripts involved in dealing with networking. If all of them aren't 100% safe when unusual characters are involved, bad things can happen.  In theory, it shouldn't matter, but it is a trivial thing to change the SSID.

---

### Post by k20shores on 2024-03-30
According to [this thread]([https://www.reddit.com/r/voidlinux/comments/rapmhh/comment/hnkn7pr/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button](https://www.reddit.com/r/voidlinux/comments/rapmhh/comment/hnkn7pr/?utm_source=share&utm_medium=web3x&utm_name=web3xcss&utm_term=1&utm_content=share_button)) wpa_supplicant and NetworkManager can interfere with each other. I [disabled wpa_supplicant]([https://stackoverflow.com/a/66000039/5217293](https://stackoverflow.com/a/66000039/5217293)) and thought it was fine, but then the wifi died again...

It only works on a restart. The dmesg logs indicate that `iwlwifi` can't get access to the wifi card after a certain point and I cannot identify why.

---

### Post by jeremy31 on 2024-03-30
Has the hybrid shutdown been disabled in Windows?

---

### Post by k20shores on 2024-03-30
I do not know. I have not ever explicitly messed with that setting; I'll have to check. But I don't see how it's related; Linux is on it's own drive entirely separate from Windows.

---

### Post by TheFu on 2024-03-30
> **k20shores said:**
> I do not know. I have not ever explicitly messed with that setting; I'll have to check. But I don't see how it's related; Linux is on it's own drive entirely separate from Windows.

There are sometimes interactions with how the hardware was left after booting MS-Windows.  

Sometimes the drivers in Windows do things that the vendor's driver team for Linux didn't do.  They aren't always the same people.

When it comes to networking and Linux, you should read and try what  jeremy31 says.

---

### Post by k20shores on 2024-04-01
I have disabled the hybrid shutdown in windows. Additionally, I provided two wireless info dumps in the original post.

---

### Post by k20shores on 2024-04-01
But, here are two new ones from when things

- [worked]([https://pastebin.com/imwrncMd](https://pastebin.com/imwrncMd))
- [and failed]([https://pastebin.com/Rn8GUBA5](https://pastebin.com/Rn8GUBA5))

after disabling hybrid shutdown

---

### Post by k20shores on 2024-04-01
Hmm. I did a full shutdown and things seem to be stable so far? currently at an uptime of 1 hour and 45 minutes and that's the longest yet. Here's hoping

---

### Post by k20shores on 2024-04-02
disabling windows hybrid shutdown may have worked? It was up for 2 hours last night without issue. This morning it died, but I had gone from Windows to Ubuntu through a restart, not a complete shutdown. So maybe if I always go to Ubuntu from a shutdown it works?

---

### Post by k20shores on 2024-04-02
*sigh* nope. Not 5 minutes after that, another wifi crash

---

