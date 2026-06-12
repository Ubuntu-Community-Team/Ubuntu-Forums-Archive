---
title: "Throttling problems"
date: 2006-09-30
forum: General Help
---

### Post by E21Craze on 2006-09-30
Greetings.

I'm a newbie here, running Hoary for less than a year. Trying to get things up and running, and doing fine... 'till now. I stumled when trying to get cpu  frequency scaling working: I followed all the how-to's and managed something.

However, when trying the "ondemand" governor, the frequency starts with the lowest setting (800 Mhz, I have a 1.8 GHz Turion), then goes to the highest (1.8 Ghz) when needed. Then it only throttles back to 1.6 Ghz and never reaches the lowest setting again.

Any clues? I'm using a 2.6.12-386 kernel and cpufreqd installed from the repositories.

Kind regards, 

Paulo

---

### Post by E21Craze on 2006-09-30
Another weird problem I just noticed: the governor switches itself between performance, ondemand and powersave. :confused:

---

