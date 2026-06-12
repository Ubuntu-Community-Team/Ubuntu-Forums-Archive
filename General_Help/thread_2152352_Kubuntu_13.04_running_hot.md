---
title: "Kubuntu 13.04 running hot"
date: 2013-06-07
forum: General Help
---

### Post by cessanfrancisco on 2013-06-07
I'm a first time Linux user and just installed Kubuntu 13.04 (replaced Windows 7) on an Asus UL80JT (all stock with the exception of an Intel wireless card).  I noticed Kubuntu runs the CPU considerably hotter than Windows.  After digging around the internet I found the TLP-thing and installed that via a command line.  So far, there isn't much difference in temp.

Does anyone have any other input?

Thanks.

---

### Post by darekch on 2013-06-08
Check if cpufreqd works well and lowers CPU frequency if it's possible. Turn of unneeded applications, firefox, thunderbird, skype... and run
```

sudo apt-get install cpufrequtils
sleep 5
cpufreq-info | grep 'current policy' -A 3
```
This gives similar output:
```

  current policy: frequency should be within 800 MHz and 2.70 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
```
This tells me that cpufreqd(aemon) works well as it changes speed of my cpu between 800 MHz and 2,7 GHz and right now my CPU works at 800 MHz speed (so as low as possible) what in turn gives me low temperature. You can set ondemand governor like that: sudo cpufreq-set -g ondemand. Analyze cpufreq-info output if all your cores are managed by governors that you want.

You can run some youtube video in your browser and you will see that above command will give you various CPU speed.

More over please note that temperature levels read by OS can differ between Linux and Windows.

At last note that Kubuntu is bloated environment which will usually need more CPU power and causing temperature increase. You can try some live cd (xubuntu or lubuntu) and check temperatures there.

Also run top comand to see if there's some process that it's eating CPU too much. Maybe it hanged and you can kill it...

---

