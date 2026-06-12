---
title: "What's that &quot;Mysterious&quot; Python Process Using My Network?"
date: 2013-02-27
forum: General Help
---

### Post by navneeth on 2013-02-27
Occasionally I notice a lot of data being downloaded without any of my input whatsoever and when I check nethogs, it simply says /usr/bin/python.

Ubuntu updates are **not** set to download automatically. And there are no other applications that I run which require downloads like this. (Well, there's BOINC, which can access the network only during certain hours, but it's not that either.)

I've noticed this only a few times, so even if there's a reason or pattern to it, I haven't noticed it yet. So, my question is: how I can find out more about what's using the network?

---

### Post by dino99 on 2013-02-27
the system itself do some push/pull communications (sync time, update-notifier, zeitgeits,...), and some widgets too via javascripts,...

---

### Post by navneeth on 2013-02-27
> **dino99 said:**
> the system itself do some push/pull communications (sync time, update-notifier, zeitgeits,...), and some widgets too via javascripts,...

Hi dino; thanks for the reply. The amount being downloaded was too much for sync-time or things of that sort. Anyway, do you know how one can find out with more accuracy (than /usr/bin/python) what's happening?

---

### Post by jwbrase on 2013-02-27
If the process doing the network activity is still running, open up system monitor, go to Edit -> Preferences, go to the "Processes" tab and check "Command Line" under "Information Fields". This will cause system monitor to display the full command line of each process.

Alternatively, you can open a terminal and run:

```
ps -Awf
```

or, to filter for all instances of python

```
ps -Awf | grep python
```

"ps" gives a list of processes, the -A option causes it to display all processes on the system instead of just those on the current terminal, -w prevents ps from truncating output lines that are longer than the width of your terminal, -f causes the full command line of each process to be listed. "grep python" filters out all lines that do not contain the string "python".

---

### Post by navneeth on 2013-02-27
Thanks for the reply, jwbrase. It's not running right now, and when it does it lasts for no more than about 10-20 seconds. I'll try this the next time I notice it.

---

### Post by Impavidus on 2013-02-27
10-20 seconds? How much data would that be on your connection?

---

### Post by navneeth on 2013-02-28
> **Impavidus said:**
> 10-20 seconds? How much data would that be on your connection?

A few MB at most. The maximum I get is around 220KB/s.

---

