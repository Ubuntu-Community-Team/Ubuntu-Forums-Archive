---
title: "Shell script &amp; &quot;nvidia-smi&quot; - needs right command/flag!"
date: 2015-06-19
forum: General Help
---

### Post by danhansendenmark on 2015-06-19
Hi friends,


I've got a problem regarding a shell-script and the "nvidia-smi" command!

I've made a script that as protection against CPU overheating on my Ubuntu Server 14.04.2. The scripts works nicely but I need to make it work on my 4 GPU's as well. 
I'm pretty green when it comes to bash scripts so I've been looking for commands which would make it easy for me to edit the script. I found and tested a lot of them, but none seems to give me the output I need! I'll show you the commands and the output below. And the scripts as well. 

What I need is a command which lists the GPU's the same way the "sensors" command from "lm-sensors" does. So that I can use "grep" to select a GPU and set the variable "newstring" (the temp. two digits). I've been trying for a couple of days, but have had no luck. Mostly because the command "nvidia-smi -lso" and/or "nvidia-smi -lsa" doesn't exist anymore. Think it was an experimental command.

Here's the commands I found and tested & the output:

This command shows GPU socket number which I could put into the string "str" but the problem is that the temp. is on the next line. I've been fiddling with the flag "A 1" but haven't been able to put it into the script:
```

# nvidia-smi -q -d temperature | grep GPU
Attached GPUs                       : 4
GPU 0000:01:00.0
        GPU Current Temp            : 57 C
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
GPU 0000:02:00.0
        GPU Current Temp            : 47 C
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
GPU 0000:03:00.0
        GPU Current Temp            : 47 C
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
GPU 0000:04:00.0
        GPU Current Temp            : 48 C
        GPU Shutdown Temp           : N/A
        GPU Slowdown Temp           : N/A
```
[/CODE]

This command shows the temp in the first line, but there's no GPU number!?
```

# nvidia-smi -q -d temperature | grep "GPU Current Temp"
        GPU Current Temp            : 58 C
        GPU Current Temp            : 47 C
        GPU Current Temp            : 47 C
        GPU Current Temp            : 48 C

```

This command shows the GPU number you select, but there's still no output showing the GPU numer/socket/ID!?
```

# nvidia-smi -q --gpu=0 | grep "GPU Current Temp"
GPU Current Temp            : 59 C

```

And this commands shows the GPU number and the results in the same row!! But, no temperature!!
```

# nvidia-smi -L
GPU 0: GeForce GTX 750 Ti (UUID: GPU-9785c7c7-732f-1f51-..........)
GPU 1: GeForce GTX 750 (UUID: GPU-b2b1a4a-4dca-0c7f-..........)
GPU 2: GeForce GTX 750 (UUID: GPU-5e6b8efd-7531-777c-..........)
GPU 3: GeForce GTX 750 Ti (UUID: GPU-5b2b1a2f-3635-2a1c-..........)

```

And a command which shows all 4 GPU's temp. without anything else. But still I need the GPU number/socket/ID!?
```
# nvidia-smi --query-gpu=temperature.gpu --format=csv,noheader
58
47
47
48

```


What I'm wishing for! If I could get a command which made a output like this I would be the happiest guy around:
```

GPU 0: GeForce GTX 750 Ti   GPU Current Temp            : 58 C
GPU 1: GeForce GTX 750   GPU Current Temp            : 47 C
GPU 2: GeForce GTX 750   GPU Current Temp            : 47 C
GPU 3: GeForce GTX 750 Ti   GPU Current Temp            : 48 C

```

Here's the output that "sensors" from "lm-sensors". As you can see the unit info and the temp is in the same line:
```

# -----------------------------------------------------------
# coretemp-isa-0000
# Adapter: ISA adapter
# Physical id 0:  +56.0°C  (high = +80.0°C, crit = +100.0°C)
# Core 0:         +56.0°C  (high = +80.0°C, crit = +100.0°C)
# Core 1:         +54.0°C  (high = +80.0°C, crit = +100.0°C)
# Core 2:         +54.0°C  (high = +80.0°C, crit = +100.0°C)
# Core 3:         +52.0°C  (high = +80.0°C, crit = +100.0°C)
# -----------------------------------------------------------

```

Here's the part of the script that needs changing. As mentioned in the top, this works using the command "sensors" from the application "lm-sensors". "lm-sensors" doesn't show GPU temp. when running CUDA and the driver attached, so we need another command to get the GPU's listed and the temp. shown. You may know another way to fix my problem, if please don't hesitate to show me.:
```

[...]
echo "JOB RUN AT $(date)"
echo "======================================="

echo ''
echo 'CPU Warning Limit set to => '$1
echo 'CPU Shutdown Limit set to => '$2
echo ''
echo ''

sensors

echo ''
echo ''

for i in 0 1 2 3
do

  str=$(sensors | grep "Core $i:")
  newstr=${str:17:2}

  if [ ${newstr} -ge $1 ]
  then
    echo '===================================================================='         >>/home/root/logs/watchdogcputemp.log
    echo $(date)                                                                        >>/home/root/logs/watchdogcputemp.log
    echo ''                                                                             >>/home/root/logs/watchdogcputemp.log
    echo ' STATUS WARNING - NOTIFYING : TEMPERATURE CORE' $i 'EXCEEDED' $1 '=>' $newstr >>/home/root/logs/watchdogcputemp.log
    echo ' ACTION : EMAIL SENT'                                                         >>/home/root/logs/watchdogcputemp.log
    echo ''                                                                             >>/home/root/logs/watchdogcputemp.log
    echo '===================================================================='         >>/home/root/logs/watchdogcputemp.log

# Status Warning Email Sending Code 
# WatchdogCpuTemp Alert! Status Warning - Notifying!"

/usr/bin/msmtp -d --read-recipients </home/......../shellscripts/messages/watchdogcputempwarning.txt

    echo 'Email Sent.....'
  fi
[...]

```



I hope there's a bash-script guru out there, ready to solve this issue ;)
Have a nice weekend!

Kind Regards,
Dan Hansen
Denmark

.

---

### Post by efflandt on 2015-06-19
With GTX 750's and Ti's I wonder why you would even need to monitor temperatures. GTX 750 models including Ti are chip limited to 60 watts max power. Although, I am not sure how hot single fan units get, especially if you actually have 4 of them in one PC.

I have an MSI Twin Frozr Gaming GTX 750 Ti OC and at 25°C ambient temperature it peaks at 60°C running Unigine Valley Benchmark 1080p with the gpu bumped up +220 MHz from its factory overclock and fans auto bumping up to less than 40% I think (38% when I exit the benchmark).

You might want to look at **psensor**. You can set temperature alarms and even remotely monitor if you run **psensor-daemon**. You need to run hdtemp (as root or sudo) if you want to monitor hard drive temperatures. It can log too, which apparently starts by listing the sensors and then a comma separated list of sensors readings. Each line begins with seconds since psensor started logging and then the comma list of only readings that changed. For example my hd temperature is only listed once because that had not changed. But I ran glxgears just to get the other things to change. It would just require something a bit more complicated than grep to parse.```
I,1434766892,0.8.0.3
S,lmsensor coretemp-isa-0000 Core 0,101
S,lmsensor coretemp-isa-0000 Core 2,101
S,hdd /dev/sda,6001
S,nvidia GPU0,10201
S,cpu usage,8004
0,32.0,32.0,38.0,32.0,1.2
300,31.0,33.0,,,0.2
600,45.0,46.0,,37.0,37.2
900,51.0,53.0,,41.0,37.6
```

---

### Post by danhansendenmark on 2015-11-13
Hi Efflandt,


Sorry for late reply. 

> With GTX 750's and Ti's I wonder why you would even need to monitor temperatures.

As you can see, the system is a 4 GPU box and these GPU's are all installed in a very "compact" 2U rack-case. This means very little replaced air, which results in hot air getting hotter. This is why I've installed new chassis-fans, the 4 original is replaced with a Papst 80x80mm industrial fan. 

[IMG]http://cdn.overclock.net/3/3b/900x900px-LL-3b14ca86_HeadlessLinuxBoincServer75b2.jpeg[/IMG]


I know these cards can handle temperatures up to 95 degrees Celsius or more. The first model I tested could too. This was AsusGT640 which was able to handle at least temperatures above 95 degrees. 2 of these cards crashed. I don't like the system to run that close to the limits, so I've been working to find a solution. I found it, all scripts are running and system will shutdown if it gets to hot.

If anybody is interested in the ToDo and/or these scripts, please don't hesitate to let me know.


This is the solution to my question btw:

```
 ( nvidia-smi -L
   nvidia-smi -q -d temperature | grep GPU
 ) |
 awk '
 /^GPU [0-9]:/     { gpu=0+$2; split($0,x,"("); gputype[gpu]=x[1]; }
 /^GPU 00/         { split($2,x,":"); gpu=x[2]-1; }
 /GPU Current Temp/{ temperature[gpu] = $5 " " $6; }
 END               { for(gpu=0;gpu<99;gpu++)
                     if(gputype[gpu]!="")
                      printf "%-30s GPU Current Temp: %s\n",gputype[gpu],temperature[gpu]
                   }'
```

The list using that command. Nicely sorted with GPU socket number, "GPU Temp" to grep and Temperature listed the right way. Using this code-block I was able to finish my script and its running perfectly. (Thank you meuh for your ideas btw):

```

GPU 0: GeForce GTX 750 Ti      GPU Current Temp: 49 C
GPU 1: GeForce GTX 750         GPU Current Temp: 41 C
GPU 2: GeForce GTX 750         GPU Current Temp: 44 C
GPU 3: GeForce GTX 750 Ti      GPU Current Temp: 48 C

```



Kind Regards,
Dan

---

