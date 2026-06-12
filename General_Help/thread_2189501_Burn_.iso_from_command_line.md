---
title: "Burn .iso from command line"
date: 2013-11-22
forum: General Help
---

### Post by borgward on 2013-11-22
How do I burn .iso from the commandline? I downloaded it to Downloads

---

### Post by jCjQszKMO5JH on 2013-11-22
You can follow the instructions here to burn from the commandline:

[https://help.ubuntu.com/community/CdDvd/Burning#Burning_a_CD_on_the_Command_Line_with_wodim](https://help.ubuntu.com/community/CdDvd/Burning#Burning_a_CD_on_the_Command_Line_with_wodim)

---

### Post by borgward on 2013-11-22
wodim does not burn DVD, CD only?

I was able to use growisofs with succes. I am confused as I have notice wodim mentioned when I use K3b to burn a DVD.

---

### Post by borgward on 2013-11-23
I was able to run these commands, but got bad md5sums

I also used K3b to burn the .iso and got the correct md5sum


$ growisofs -Z /dev/dvdrw -R -J /linuxmint-16-cinnamon-dvd-64bit-rc.iso

bad md5sum

04aa64c442dc78daa55accfc15972497
232b8e3de36abccdaedc1dd904e2bded (should be)

$ growisofs -Z /dev/sr1 -R -J linuxmint-16-cinnamon-dvd-64bit-rc.iso

bad md5sum

c4e693f0d5cd5c909c2592b1533158e6
232b8e3de36abccdaedc1dd904e2bded (should be)

$ wodim -v -dao speed=4 dev=/dev/sg2 linuxmint-16-cinnamon-dvd-64bit-rc.iso

Bad md5sum
(
232b8e3de36abccdaedc1dd904e2bded (should be!)
d9c24692d966c55f560d958026bff83f

Burned w/K3b

$ dd if=/dev/sr1 bs=2k count=608400 | md5sum
608400+0 records in
608400+0 records out
1246003200 bytes (1.2 GB) copied, 109.918 s, 11.3 MB/s
232b8e3de36abccdaedc1dd904e2bded  -
232b8e3de36abccdaedc1dd904e2bded

---

### Post by VMC on 2013-11-23
I've seen this answer on several occasions:

```
[COLOR=#800000][FONT=Lucida Grande]growisofs -dvd-compat -Z /dev/sr0=/path/to/iso_file[/FONT][/COLOR]
```

---

