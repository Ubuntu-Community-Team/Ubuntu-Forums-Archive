---
title: "How can I easilly check cpu temp"
date: 2021-07-22
forum: General Help
---

### Post by juntjoo2 on 2021-07-22
I'm working with an old laptop who's fan died so until a new one arrives I'm sandwiching it between ice packs and laptop fans.

So in this meantime and for future use I'd like to be able to monitor the cpu temp. How so? And what Temps arenhaelthy/dangerous? Thanks

I'm currently running the live DVD of 16.0.4(till I'm able to upgrade, working on it)

---

### Post by grahammechanical on 2021-07-22
Install psensor. It is in the Ubuntu software store. It puts an icon in the top panel that will give a drop down menu showing motherboard, CPU, disk driver temperatures as well as fan speeds.

A similar utility is lm-sensors

[https://github.com/lm-sensors/lm-sensors](https://github.com/lm-sensors/lm-sensors)

There is also a command line utility called htop that can be installed.

[https://htop.dev/](https://htop.dev/)

The software store also has sensor-unity.

Regards

---

### Post by juntjoo2 on 2021-07-22
Thanks! And do you happen to know what's a bad temp?

---

### Post by ActionParsnip on 2021-07-22
> **juntjoo2 said:**
> Thanks! And do you happen to know what's a bad temp?

Depends on the CPU. Check manufacturers documentation as well as the cooling you are using. There is no single value here

---

### Post by juntjoo2 on 2021-07-22
Like this?

"./configure; make; sudo make install"

I tried this from htop. Dev but it returned:

"no such file or directory" 

My "Ubuntu software" app isn't even connecting to the internet. I AM connected though

---

### Post by juntjoo2 on 2021-07-22
never mind, I got it, thanks.

---

### Post by ActionParsnip on 2021-07-22
Please mark as solved if the issue is resolved, or ask a question / provide additional information

---

### Post by sudodus on 2021-07-22
I have hardinfo (which came with Lubuntu), and the package has the same name as the program.

```

sudo apt update
sudo apt install hardinfo

```

Hardinfo is a graphical tool, that shows a lot of information about the comuter's hardware, also temperature of the processors.

I use the text mode tool hddtemp to check the temperature of the SATA drives and nvme to check for it on nvme drives.
```

sudo apt update
sudo apt install hddtemp nvme-cli

sudo hddtemp /dev/sda
sudo nvme smart-log /dev/nvme0n1

```

My version of Disks (gnome-disks) in 18.04 LTS can also see temperature of the HDDs and SATA SSDs, but not nvme drives. It might work better in newer versions.

---

### Post by Impavidus on 2021-07-22
I'm not sure what you mean by "I got it".

psensor, lm-sensors, htop can all be installed from the repositories, either using the GUI tool or from command line:```
sudo apt install psensor
```et cetera.

On a live dvd, changes aren't saved when you reboot, so you have to install them each time again. On a live usb with persistence the software will still be there after a reboot.

And on 16.04 the repositories may no longer be online, making installation a bit harder. You could change software sources to old-releases.

Laptop hardware is designed to be able to run quite hot, mostly because it has rather poor cooling. The CPU in my 10 year old laptop can reach 80&#8304;C. When you start smelling hot plastic, you're close to the limit. CPUs are designed to trottle down when they get too hot, but I don't want to rely on that. I've experienced heat-induced memory corruption before the CPU trottled down. No hardware failure though.

Keep in mind that the temperatures reported by the mentioned tools sometimes suffer from calibration errors.

---

