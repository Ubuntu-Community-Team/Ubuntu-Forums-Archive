---
title: "Wrong cpu frequencies"
date: 2018-02-10
forum: General Help
---

### Post by jacopastorius82 on 2018-02-10
I have a laptop with this CPU: Intel Core i7-4710HQ CPU @ 2.50GHz × 8 core. Cpufreq-info says that i have powersave governor which can decide frequencies in the range between 2.10 ghz and 2.10 ghz so my cpu is always @ 2.10 Ghz.
How can i fix this? It should be between 800 and 3.5 ghz.

After fixing that, i'd really like to set the frequencies lower than 800 and i'd really like to change the governor from powersave to ondemand depending on my needs. is it possible?

---

### Post by banceu_sergiu_ione on 2018-02-10
Hello jacopastorius82

Use cpupower in terminal. You may need to  install linux-tools-common & linux-tools-generic &  linux-cloud-tools-generic, if not yet installed, on way to have it work.

```
sudo apt install linux-tools-common
```
```
sudo apt install linux-tools-generic
```
```
sudo apt install linux-cloud-tools-generic
```

Check the cpufreq governors available with:

```
cpupower frequency-info
```

Set a new governor (this command will set the governor on type ondemand; you can chose whatever governor you have available):

```
sudo cpupower -c all frequency-set -g ondemand
```

Have a good day.

---

### Post by jacopastorius82 on 2018-02-10
thank you very much, i did what you suggested setting the governor to powersave (as i can choose just powersave and performance) but the frequency in idle remained high:

```
duccio@duccio-N551JM:~$ cpupower frequency-info
analyzing CPU 0:
  driver: intel_pstate
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency:  Cannot determine or is not supported.
  hardware limits: 800 MHz - 3.50 GHz
  available cpufreq governors: performance powersave
  current policy: frequency should be within 3.50 GHz and 3.50 GHz.
                  The governor "powersave" may decide which speed to use
                  within this range.
  current CPU frequency: Unable to call hardware
  current CPU frequency: 2.50 GHz (asserted by call to kernel)
  boost state support:
    Supported: yes
    Active: yes

```

---

### Post by banceu_sergiu_ione on 2018-02-10
This will set the minimum frequency at 800 MHz for the governor in use. If you need to change the minimum frequency to another governor, switch on it before running the fallowing code:

```
sudo cpupower -c all frequency-set -d 800MHz
```

---

### Post by jacopastorius82 on 2018-02-11
Thank you. I did that for powersave governor but at avery reboot the cpu in idle is @ 2500mhz and if i set at 800 it stays at 1200 in idle instead

---

### Post by banceu_sergiu_ione on 2018-02-11
Do you have cpufreqd installed?

If so, uninstall it as it interfere with cpupower settings: 
```
sudo apt --purge remove cpufreqd
```
and set back the frequency settings as you did before with cpupower.

---

### Post by banceu_sergiu_ione on 2018-02-11
To make it persistent at reboot you have 2 options, create a cron job or a service.

In this case i would suggest to go for a service.

Before you go for it, make sure that cpupower is found in /usr/bin : navigate from Files or use the terminal
```
locate cpupower
```

If cpupower is located in /usr/bin as it should be since you installed it, lets go to create a service for cpupower to run once at boot.

Open a terminal and run the code, you will be prompted to insert the needed code for the service:

```
cat << EOF | sudo tee /etc/systemd/cpupower.service
```

- now ( in edit mode ) you have to type in terminal the fallowing code
- you can not do a copy/past
- at the end of file after you type EOF press enter(only this enter will get you out from edit mode) and you will be asked for password

```

[Unit]
Description=CPU scaling minimum frequency

[Service]
Type=oneshot
ExecStart=/usr/bin/cpupower -c all frequency-set -d 800MHz

[Install]
WantedBy=multi-user.target

EOF

```

-press enter
-type password

- reload the systemd manager and enable the service at boot time:

```
sudo systemctl daemon-reload
```
```
sudo systemctl enable cpupower.service
```

The service will only run at boot as 1 time action and will not be active during the session.

You can disable it anytime by running 
```
sudo systemctl disable cpupower.service
```

---

