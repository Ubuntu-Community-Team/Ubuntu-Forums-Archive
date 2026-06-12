---
title: "Help - Simple Script for Monitoring Wireless Status"
date: 2016-03-28
forum: General Help
---

### Post by antoniog2 on 2016-03-28
Hi to all the community,):P

I want to create a script that monitors the status of the network (I do not know if there are any programs that already do what I want to do even better).

I'm only interested monitor the **signal strength **and the **bit rate** of a device connected to an access point and creates an output file for an example of this style:

[TABLE="width: 500"]
[TR]
[TD="align: center"]TIME (s)[/TD]
[TD="align: center"]SIGNAL STRENGTH (dBm)[/TD]
[TD="align: center"]BITRATE (Mbit/s)[/TD]
[/TR]
[TR]
[TD="align: center"]00[/TD]
[TD="align: center"]-53[/TD]
[TD="align: center"]54[/TD]
[/TR]
[TR]
[TD="align: center"]05[/TD]
[TD="align: center"]-50[/TD]
[TD="align: center"]300[/TD]
[/TR]
[TR]
[TD="align: center"]10[/TD]
[TD="align: center"]-55[/TD]
[TD="align: center"]54[/TD]
[/TR]
[TR]
[TD="align: center"]15[/TD]
[TD="align: center"]-60[/TD]
[TD="align: center"]36[/TD]
[/TR]
[TR]
[TD="align: center"]...[/TD]
[TD="align: center"]...[/TD]
[TD="align: center"]...[/TD]
[/TR]
[/TABLE]

This data can be obtained from the command:
```
$ iw dev wlan1 station dump[INDENT]Station 12:34:56:78:9a:bc (on wlan0)[/INDENT]
        inactive time:  304 ms
        rx bytes:       18816
        rx packets:     75
        tx bytes:       5386
        tx packets:     21
**        signal:         -29 dBm**
        **tx bitrate:     54.0 MBit/s**
```

Or the command:

```
$ iw dev wlan0 link[INDENT]Connected to 04:21:b0:e8:c8:8b (on wlan0)[/INDENT]
        SSID: attwifi
        freq: 2437
        RX: 2272 bytes (18 packets)
        TX: 232 bytes (3 packets)
**        signal: -57 dBm**
**        tx bitrate: 36.0 MBit/s**
```

I do not know if I have explained well, I want to get this data in any way and save them in a file (eg .txt)
The way to get the data not know what would, I know these data appear in these commands that I put below.

 Could anyone help me create a script to get what I want?, or give me some advice / tutorial?
Or failing that, could someone tell me some tool to do something?
Thank you very much in advance.


A greeting.:D
AntonioG2

---

### Post by papibe on 2016-03-28
Hi antoniog2. Welcome to the forum ):P

Take a look at 'awk'. There are several tutorials around the Internet.

Here's an example on what you can do with it:
```
$ iw dev wlan1 station dump | awk -F: '/signal/{printf $2}; /tx bitrate/{print $2}'
         -29 dBm     54.0 MBit/s

```
I hope that points you in the right direction. Let us know if you have more questions.
Regards.

---

### Post by antoniog2 on 2016-03-29
Hi papibe,

I'm trying to create a .sh script to do, for example for a minute, what I said you
I managed with awk create an output file, but when I try to write back to the same file, to write a line below, do not write. See, this is what I have for now:

file test.sh
```


#This should go a loop recursively do what I want and increase line in the file to write.

iw dev wlan0 station dump | awk -F: '/signal/{printf $2}; /rx bitrate/{print $2}' > out_file.txt # this in line i

#i++
#wait 0.5sec ie.
#return to loop
```

I've seen that to write in a line of a specific file you can be made easy with
```
sed "#i add text" out_file.txt
```

but I do not know how to add in the text field (add text) sed command the output of the awk command that returns me the values that I want (awk -F: '/signal/{printf $2}; /rx bitrate/{print $2}')

How could I do what I tell you?
Do you recommend me a .sh script?
Or what is the best way you can think?


Thank you very much for the help
A greeting.
AntonioG2

---

### Post by papibe on 2016-03-29
To both create the file the first time, and add lines on subsequent  calls use '>>' instead of '>'.

If you just to keep an eye on the current WiFi levels, you can open a terminal and just run the previous command under 'watch':
```
watch -e -n 1 "iw dev wlan1 station dump | awk -F\: '/signal/{printf \$2} /tx bitrate/{print \$2}' " 
```
I'd recommend a script if you want to keep the output file for later analysis.

This should point you in the right direction:
```
#!/bin/bash                                                                                                                             
                                                                                                                                        
while true                                                                                                                              
do                                                                                                                                      
    echo "current date is: $(date)" >> ./logfile                                                                                        
    sleep 1s                                                                                                                            
done 
```
Or this other one, in case you want to both see it on the terminal and log it into a file:
```
#!/bin/bash

while true
do
    echo "current date is: $(date)" | tee -a ./logfile
    sleep 1s
done

```
Hope it helps. Let us know how it goes.
Regards.

---

