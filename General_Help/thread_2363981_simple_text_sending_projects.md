---
title: "simple text sending projects"
date: 2017-06-17
forum: General Help
---

### Post by linuxprj on 2017-06-17
Can we build simple text sending machine from one desktop to another only two computer
with internet?

---

### Post by efflandt on 2017-06-17
Web search "python client server script", or substitute "perl" for "python" if more familiar with perl scripting. Or substitute "tutorial" in place of "script". Our question is, what do you want to do with that text once you receive it? That will determine what else you need to learn from there.

For example when I wanted to tell how long a battery pack would last for a Raspberry Pi (credit card size computer powered from microUSB running Linux) I was not sure if writing to its SD would corrupt the SD when power went down. So I wrote a python client script that would open a network connect to a server script on my desktop PC, send it date and uptime info, disconnect, sleep for 5 minutes, and repeat. The listening server script on my desktop PC would add what it received to a log file. In the end, from the last entry in the log, I could tell within 5 minutes (close enough) when the battery pack ran out.

---

### Post by linuxprj on 2017-06-19
hello,
i want to send and receive simple text message from one pc to another over internet nothing to do with it right now.

---

### Post by HermanAB on 2017-06-19
You can use netcat.

---

### Post by linuxprj on 2017-06-19
ok, can we talk like Ubuntu Linux to a window or only Ubuntu?
is there any other service needed other than internet?
and security can anyone open this message like in gmail/facebook

---

### Post by Habitual on 2017-06-19
> **linuxprj said:**
> hello,
i want to send and receive simple text message from one pc to another over internet nothing to do with it right now.

check out termbin.com

See [http://termbin.com/mhsa](http://termbin.com/mhsa) for examples.

---

