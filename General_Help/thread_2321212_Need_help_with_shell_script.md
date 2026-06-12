---
title: "Need help with shell script"
date: 2016-04-21
forum: General Help
---

### Post by DanielVermeulen on 2016-04-21
Hi sorry if I'm posting this in the wrong section, I don't know where else to post this. In any way, I'm trying to perform a periodical speed test via a bash script but I can't seem to get it working. 

```

#!/bin/bash

i=1
while [$i le 24]
do
echo Hour: $i
exec ./speedtest_cli.py > speedtest.log
((i++))
sleep 3600
done
echo Speed test Completed!

```

The problem is that i can't get speedtest_cli.py to run from within a shell script, it works fine when i run it manually tho.
Any help would be greatly appreciated!

---

### Post by Habitual on 2016-04-21
could also use this
```
wget -O - [https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py](https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py) | python
```

or
and le should be -le

See [http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html) says
```
-le
is less than or equal to
if [ "$a" -le "$b" ]
```

---

### Post by sudodus on 2016-04-21
I suggest that you remove exec:

From
```
exec ./speedtest_cli.py > speedtest.log
```
to
```
./speedtest_cli.py > speedtest.log
```
and try again.

---

### Post by DanielVermeulen on 2016-04-21
Thanks man it works, but is there a way to suppress the wget commands console output, but not the python script?

Edit:
Never mind, I got it working, heres the script if anyone is interested:
 
```

#!/bin/bash

i=0
echo "Save output file name:"
read outputfile
echo "How many times would you like to test you're internet speed?"
read amount 
echo "Enter the amout of seconds to wait inbetween tests:"
read scnds
timew=Second/s 
timei=1
if [ $scnds -le 60 ]
    then
    timei=$scnds
    fi
if [ $scnds -gt 59 ]
    then
    timew="Minute/s"
    timei=$(($scnds / 60))
    fi
if [ $scnds -gt 3599 ]
    then
    timew="Hour/s"
    timei=$(($scnds / 3600))
     fi
while [ $i -le $amount ]
    do
    now=$(date +"%T")
    echo $timew": " $i "  Time: "$now
    echo $timew": " $i "  Time: "$now >> $outputfile
    wget -O - https://raw.github.com/sivel/speedtest-cli/master/speedtest_cli.py | python >> $outputfile
    now=$(date +"%T")
    echo "Test " $i " completed at " $now ", waiting " $timei " " $timew " until next text."
    echo "Test " $i " completed at " $now ", waiting " $timei " " $timew " until next text." >> $outputfile
    ((i++))
    sleep $scnds
    echo "---------------------------------------------------------------------" >> $outputfile
    echo "---------------------------------------------------------------------" >> $outputfile
    echo "---------------------------------------------------------------------" >> $outputfile
    echo "---------------------------------------------------------------------" >> $outputfile
    echo "---------------------------------------------------------------------" >> $outputfile
    echo "---------------------------------------------------------------------" >> $outputfile
    echo "---------------------------------------------------------------------" >> $outputfile
    echo "---------------------------------------------------------------------" >> $outputfile
    echo "---------------------------------------------------------------------" >> $outputfile
done
now=$(date +"%T")
echo "Speed test conmpeted!"
echo "Speed test conmpeted!" $now >> $outputfile

```

Output:
```

Hour/s:  0   Time: 17:21:54
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Internet Solutions (000.000.00.000)...
Selecting best server based on latency...
Hosted by Telkom SA (SAIX) (Cape Town) [32.47 km]: 10.622 ms
Testing download speed........................................
Download: 9.53 Mbit/s
Testing upload speed..................................................
Upload: 2.37 Mbit/s
Test  0  completed at  17:21:54 , waiting  1   Hour/s  until next text.

```

---

