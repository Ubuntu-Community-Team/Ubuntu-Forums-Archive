---
title: "search in text from ... untill ...."
date: 2008-04-22
forum: General Help
---

### Post by p.becks on 2008-04-22
Hello,

I use grep/sed/cut/paste a lot to ¨take¨ info out off a text/log. grep work great if you are looking for a unique ¨word¨. But now i have a text in which the searchterm isn unique. (searchterm = slot: , see sample text below). I only need to grep the lines which are in the section:  ¨*-memory¨

How do i tell grep that it has to search for ¨slot:¨ ONLY in the section that starts with ¨*-memory¨ and ends with ¨*-display:0 UNCLAIMED¨ ??



sample text:

*-cache:1
	       description: L2 cache
	       physical id: 13
	       slot: CPU Internal
	       size: 2MiB
	       capacity: 2MiB
	       clock: 1GHz (1.0ns)
	       capabilities: internal write-back unified
	  *-memory
	       description: System Memory
	       physical id: 81
	       slot: System board or motherboard
	       size: 2GiB
	     *-bank:0
		  description: SODIMM Synchronous 667 MHz (1.5 ns)
		  product: M4 70T2953EZ3-CE6
		  vendor: CE00
		  physical id: 0
		  serial: 442E1434
		  slot: DIMM 0
		  size: 1GiB
		  width: 64 bits
		  clock: 667MHz (1.5ns)
	     *-bank:1
		  description: SODIMM Synchronous 667 MHz (1.5 ns)
		  product: M4 70T2953EZ3-CE6
		  vendor: CE00
		  physical id: 1
		  serial: 442E1368
		  slot: DIMM 1
		  size: 1GiB
		  width: 64 bits
		  clock: 667MHz (1.5ns)
*-display:0 UNCLAIMED

---

### Post by tjajab on 2008-04-22
If you know the numbers of rows after the *-memory section, you could always do a grep -A{numberOfRows} which tells grep to output numberOfRows rows after the actual row, and then pipe it to the slot grep. In the example below:

grep -A25 "*-memory" some.txt | grep "slot:"

---

### Post by p.becks on 2008-04-23
Hallo.

Eventually, i did it like this:(not pretty but it works).

#!bin/bash
sudo lshw -C memory -C network -C display -C multimedia > /home/patrick/scripts/HARDWARE/collect.txt
#memory
grep -C1 slot..DIMM /home/patrick/scripts/HARDWARE/collect.txt >  /home/patrick/scripts/HARDWARE/mem1.txt
sed '/--/d' /home/patrick/scripts/HARDWARE/mem1.txt > /home/patrick/scripts/HARDWARE/mem2.txt
sed '/serial:/d' /home/patrick/scripts/HARDWARE/mem2.txt > /home/patrick/scripts/HARDWARE/mem3.txt
sed  's/          //g' /home/patrick/scripts/HARDWARE/mem3.txt > /home/patrick/scripts/HARDWARE/mem4.txt
#video
grep -C2 *-display:0 /home/patrick/scripts/HARDWARE/collect.txt >  /home/patrick/scripts/HARDWARE/video1.txt
grep product /home/patrick/scripts/HARDWARE/video1.txt > /home/patrick/scripts/HARDWARE/video2.txt
sed 's/product://g' /home/patrick/scripts/HARDWARE/video2.txt > /home/patrick/scripts/HARDWARE/video3.txt
sed 's/        //g' /home/patrick/scripts/HARDWARE/video3.txt > /home/patrick/scripts/HARDWARE/video4.txt
#ethernet
grep [Nn]etwork /home/patrick/scripts/HARDWARE/collect.txt > /home/patrick/scripts/HARDWARE/net1.txt
sed '/\*-network/d' /home/patrick/scripts/HARDWARE/net1.txt > /home/patrick/scripts/HARDWARE/net2.txt
sed 's/product://g' /home/patrick/scripts/HARDWARE/net2.txt > /home/patrick/scripts/HARDWARE/net3.txt
sed '/description:/d' /home/patrick/scripts/HARDWARE/net3.txt > /home/patrick/scripts/HARDWARE/net4.txt
sed 's/        //g' /home/patrick/scripts/HARDWARE/net4.txt > /home/patrick/scripts/HARDWARE/net5.txt
#audio
grep -C1 "Audio device" /home/patrick/scripts/HARDWARE/collect.txt >  /home/patrick/scripts/HARDWARE/audio1.txt
grep product /home/patrick/scripts/HARDWARE/audio1.txt > /home/patrick/scripts/HARDWARE/audio2.txt
sed 's/product://g' /home/patrick/scripts/HARDWARE/audio2.txt > /home/patrick/scripts/HARDWARE/audio3.txt
sed 's/        //g' /home/patrick/scripts/HARDWARE/audio3.txt > /home/patrick/scripts/HARDWARE/audio4.txt
exit

output of the files mem4.txt video4.txt net5.txt audio4.txt:

slot: DIMM 0
size: 1GiB
slot: DIMM 1
size: 1GiB

Mobile GM965/GL960 Integrated Graphics Controller

82566MC Gigabit Network Connection
PRO/Wireless 4965 AG or AGN Network Connection

82801H (ICH8 Family) HD Audio Controller

---

### Post by justleen on 2008-04-23
you can do an inline replace with sed
```
 sed -i 's/text1/text2/'  test.txt 
```

that way you dont need to ouput to another file, just dump it straight back to the orginal file..

edit: ohw, you can also chain sed
```

sed -i -e 's/1stsub/xx/'  -e 's/2ndsub/yy/' -e 's/3thsub/zz/'

```
so you dont need to reread every  substitutue from a new file

something like this :
```

cat /home/patrick/scripts/HARDWARE/collect.tx | grep [Nn]etwork t | sed -e  '/\*-network/d' -e 's/product://g' -e   '/description:/d' -e 's/ //g' > /home/patrick/scripts/HARDWARE/net.txt

```

---

### Post by p.becks on 2008-04-23
THNX!!

Changed the script into:

#!bin/bash
sudo lshw -C memory -C network -C display -C multimedia > /home/patrick/scripts/HARDWARE/collect.txt
#memory
cat /home/patrick/scripts/HARDWARE/collect.txt | grep -C1 slot..DIMM | sed -e '/--/d' -e '/serial:/d' -e 's/  //g'> /home/patrick/scripts/HARDWARE/mem4.txt
#video
cat /home/patrick/scripts/HARDWARE/collect.txt | grep -C2 *-display:0 | grep product | sed -e 's/product://g' -e 's/  //g'> /home/patrick/scripts/HARDWARE/video4.txt
#ethernet
cat /home/patrick/scripts/HARDWARE/collect.txt | grep [Nn]etwork | sed -e  '/\*-network/d' -e 's/product://g' -e '/description:/d' -e 's/  //g' > /home/patrick/scripts/HARDWARE/net5.txt
#audio
cat /home/patrick/scripts/HARDWARE/collect.txt | grep -C1 "Audio device" | grep product | sed -e 's/product://g' -e 's/  //g' > /home/patrick/scripts/HARDWARE/audio4.txt
exit

---

### Post by justleen on 2008-04-23
just for readabilty:

#!bin/bash
OUTDIR="/home/patrick/scripts/HARDWARE"
OUTPUT=`sudo lshw -C memory -C network -C display -C multimedia` 

#memory
cat $OUTPUT | grep -C1 slot..DIMM | sed -e '/--/d' -e '/serial:/d' -e 's/ //g'> $OUTDIR/mem4.txt
#video
cat $OUTPUT | grep -C2 *-display:0 | grep product | sed -e 's/product://g' -e 's/ //g'> $OUTDIR/video4.txt
#ethernet
cat $OUTPUT | grep [Nn]etwork | sed -e '/\*-network/d' -e 's/product://g' -e '/description:/d' -e 's/ //g' > $OUTDIR/net5.txt
#audio
cat $OUTPUT | grep -C1 "Audio device" | grep product | sed -e 's/product://g' -e 's/ //g' > $OUTDIR/audio4.txt
exit

---

