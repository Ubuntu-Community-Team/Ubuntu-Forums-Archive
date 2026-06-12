---
title: "Speed test package"
date: 2014-04-09
forum: General Help
---

### Post by satimis on 2014-04-09
Hi all,

Ubuntu 12.04 desktop 64bit

What is the equivalent package of "speedtest-cli" for up/down speed of Fibre Optic Broadband broadband.  "speedtest-cli" is NOT on repo.  I have to download it on [https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py](https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py)

Install the python script/broad band test
[http://askubuntu.com/questions/104755/how-to-check-internet-speed-via-terminal](http://askubuntu.com/questions/104755/how-to-check-internet-speed-via-terminal)

The package will be installed on the host of Oracle Virtual box.  I expect keeping it clean as possible.

Thanks

Rgds
satimis

---

### Post by Kirboosy on 2014-04-09
I don't think there are really any alternatives to the "speedtest-cli" script. 

Using the "python-pip" package you could install the script to the computer.

```
sudo pip install speedtest-cli
```

Then you can just run the command from the commandline at anytime.

Hope that helps!
~Caboose

---

### Post by satimis on 2014-04-09
> **Caboose885 said:**
> I don't think there are really any alternatives to the "speedtest-cli" script. 

Using the "python-pip" package you could install the script to the computer.

```
sudo pip install speedtest-cli
```

Then you can just run the command from the commandline at anytime.

Thanks for your advice.

I suppose I have to download speedtest-cli manually as the article mentioned?  Can I uninstall it completely if I don't need it?  Because this is the Host.

satimis

---

### Post by Kirboosy on 2014-04-09
If you use the script as the article mentions it doesn't install anything. You are simply running a python script.

~Caboose

---

