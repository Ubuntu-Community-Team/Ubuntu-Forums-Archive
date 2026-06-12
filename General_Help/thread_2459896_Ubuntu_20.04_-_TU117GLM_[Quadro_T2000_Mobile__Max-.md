---
title: "Ubuntu 20.04 - TU117GLM [Quadro T2000 Mobile / Max-Q] Unable to install &amp; enable grap"
date: 2021-03-29
forum: General Help
---

### Post by blokh on 2021-03-29
[COLOR=#333333][FONT=DIN-Web-Pro]Greetings,
I’ve purchased a new thinkpad ( 20ST003AIV - LENOVO p15 i9-10885H vPRO|32G|1T|T2000| )

The laptop icludes 2 different graphic cards -[/FONT][/COLOR]

[LIST=1]
[*]NVIDIA - TU117GLM [Quadro T2000 Mobile / Max-Q]
[*]Mesa Intel® UHD Graphics (CML GT2).
[/LIST]
[COLOR=#333333][FONT=DIN-Web-Pro]Unfortunately, No matter what I do, Ubuntu does not recognizes the nvidia driver.

when running: nvidia-smi
it returns:
NVIDIA-SMI has failed because it couldn’t communicate with the NVIDIA driver. Make sure that the latest NVIDIA driver is installed and running.

[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]I’ve tried installing all available drivers. re-installing ubuntu, updating kernel. downgrading kernel. installing all drivers from 440 - 460.[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]Nothing changes the current state.[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]I am very lost and I am unable to find a solution to this issue.[/FONT][/COLOR]
[COLOR=#333333][FONT=DIN-Web-Pro]
Could anyone help?[/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-03-29
Welcome.

Disable Secure Boot and try again.

---

### Post by blokh on 2021-03-29
holly hell! it worked like magic!!!
Thank you very much @CelticWarrior.

I thought it was disabled by default.

---

### Post by ActionParsnip on 2021-03-29
Please mark as solved if the issue is no longer present

---

