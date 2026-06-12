---
title: "getting an error when I run speedtest-cli on Terminal"
date: 2021-04-08
forum: General Help
---

### Post by ardouronerous on 2021-04-08
I'm running Xubuntu 20.04. I'm getting this error when I ran speedtest-cli on the Terminal:

```
speedtest-cli
Retrieving speedtest.net configuration...
Traceback (most recent call last):
  File "/usr/bin/speedtest-cli", line 11, in <module>
    load_entry_point('speedtest-cli==2.1.2', 'console_scripts', 'speedtest-cli')()
  File "/usr/lib/python3/dist-packages/speedtest.py", line 1986, in main
    shell()
  File "/usr/lib/python3/dist-packages/speedtest.py", line 1872, in shell
    speedtest = Speedtest(
  File "/usr/lib/python3/dist-packages/speedtest.py", line 1091, in __init__
    self.get_config()
  File "/usr/lib/python3/dist-packages/speedtest.py", line 1173, in get_config
    ignore_servers = list(
ValueError: invalid literal for int() with base 10: ''
```

I installed speedtest-cli from the repos:

```
sudo apt-get install speedtest-cli
```

---

### Post by Xian on 2021-04-09
Python incapability issue! Lovely.

Let's install this application a different way. 

First uninstall speedtest-cli using APT
$ sudo apt-get remove speedtest-cli

Next install python3-pip
$ sudo apt-get install python3-pip

Then finally install speedtest-cli using PIP
$ sudo pip install speedtest-cli

Now run the program again
$ speedtest-cli

---

### Post by ardouronerous on 2021-04-09
Thank you that worked.

---

