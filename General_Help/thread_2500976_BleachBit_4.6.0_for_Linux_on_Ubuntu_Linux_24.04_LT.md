---
title: "BleachBit 4.6.0 for Linux on Ubuntu Linux 24.04 LTS"
date: 2024-09-18
forum: General Help
---

### Post by la.khan on 2024-09-18
Hi,

I have Ubuntu Linux 24.04 LTS and wish to install BleachBit so that I can regularly clean my system. However, when I visit [https://www.bleachbit.org/download/linux](https://www.bleachbit.org/download/linux) website, I see no Bleachbit version for UL24.04. Bleachbit 4.6.0 is compatible with earlier version of UL but UL24.04 is not listed. Yet.

Can I install BleachBit for UL23.10 on UL24.04? How compatible are these? Will these work together? Any alternative tools to BleachBit?

---

### Post by Rubi1200 on 2024-09-18
I would ask what you want to clean that can't be done with the common built-in Linux commands?

For example:
```
sudo apt clean
sudo apt autoremove
sudo apt autoclean
```

You can create a simple bash script to run the commands or even create a cronjob to run at regular intervals.

Obviously, those are just a few examples.

You can also add other things like limiting the number of snap packages to be retained or setting limits for log file size or deleting logs older than a certain time period etc.

---

### Post by 1fallen on 2024-09-18
> **la.khan said:**
> Hi,

I have Ubuntu Linux 24.04 LTS and wish to install BleachBit so that I can regularly clean my system. However, when I visit [https://www.bleachbit.org/download/linux](https://www.bleachbit.org/download/linux) website, I see no Bleachbit version for UL24.04. Bleachbit 4.6.0 is compatible with earlier version of UL but UL24.04 is not listed. Yet.

Can I install BleachBit for UL23.10 on UL24.04? How compatible are these? Will these work together? Any alternative tools to BleachBit?

I'm not sure why your looking @outside sources for.
```
> apt search bleachbit
bleachbit/oracular 4.6.0-4 all
  delete unnecessary files from the system


```
```
apt policy bleachbit
bleachbit:
  Installed: (none)
  Candidate: 4.6.0-4
  Version table:
     4.6.0-4 500
        500 http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages

```

If you have never used it before then "Rubi1200" has a Kind Warning.

I've used it for many years with zero problems, but YMMV.

EDIT I see you have asked about other cleaning tools: [https://www.maketecheasier.com/best-linux-system-cleaning-tools/](https://www.maketecheasier.com/best-linux-system-cleaning-tools/)

---

### Post by Norm24 on 2024-09-18
If you know what Bleachbit does and how to use it then:

```
sudo apt update
```

```
sudo apt install bleachbit
```

Done.

---

### Post by la.khan on 2024-09-19
> **Rubi1200 said:**
> I would ask what you want to clean that can't be done with the common built-in Linux commands?

For example:
```
sudo apt clean
sudo apt autoremove
sudo apt autoclean
```

You can create a simple bash script to run the commands or even create a cronjob to run at regular intervals.

@Rubi1200: Thanks for your reply. I am aware of these Linux apt commands to clean up my system. These commands & others are part of a bash script I run every time my system is updated with a new Linux kernel. I reboot my machine and run the bash script. That way, all old kernel(s) are removed, save the current (latest) and one prior. I believe these commands also remove downloaded, installed and/or unsed packages. I use tools like these just to be doubly sure that my system is clean. 

I prefer to also use a tool like BleachBit at the end of each calendar month. These tools may not do anything more than what built-in Linux commands do. I do realize that these might be redundant. I used it with UL22.04 and now this is just a force of habit. 

> **1fallen2 said:**
> I'm not sure why your looking @outside sources for.
```
> apt search bleachbit
bleachbit/oracular 4.6.0-4 all
  delete unnecessary files from the system


```
EDIT I see you have asked about other cleaning tools: [https://www.maketecheasier.com/best-linux-system-cleaning-tools/](https://www.maketecheasier.com/best-linux-system-cleaning-tools/)
@1fallen2: I vaguely recollect using Ubuntu Software Centre to install BleachBit. This may have searched snap store. BleachBit may NOT be available as snap package. I ignored to look at Ubuntu repositories. apt escaped my notice. Actually, this solves my problem.

> **Norm24 said:**
> If you know what Bleachbit does and how to use it then:

```
sudo apt update
```

```
sudo apt install bleachbit
```

Done.
@Norm24: I am familiar with BleachBit and the above commands solved my problem. Thanks for the reply.O:)

---

