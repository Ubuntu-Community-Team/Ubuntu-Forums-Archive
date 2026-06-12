---
title: "Temperature Logger"
date: 2018-12-01
forum: General Help
---

### Post by Hasimir on 2018-12-01
Hi,
is there a way to have an app running in background that keeps constant logs of the system temperatures?
I've found references to **sensord** but it appears unavailable since Ubuntu 16, and I'm running 18.04.

I'm asking because almost every time I run a videogame, the computer shuts down automatically.
Nothing crazy... look at my hardware in the signature, and think about games like Kathy Rain, Technobabylon, Anachronox, etc. It just should not happen :(
Supposedly, it is due to overheating.
But at times the machine doesn't feel hot at all.
I want a way to KNOW if it is a temperature problem... so I thought that I need a log of the temperature just before the "crash" or "shutdown" or whatever this problematic behaviour is called :P

A note.
I have a Win10 partition and when I game on it the computer gets quite hot, but never shuts down.
If it is OK for Win10... then maybe it could be OK for Ubuntu too?
Maybe the system is being over-cautious? 
Maybe there is a way to prevent the laptop from abruptly powering off?

Thanks for any help :)

---

### Post by CatKiller on 2018-12-01
First of all, you'll need to start reading the temperatures. **lm-sensors** is the package that will do that. Then you'll need to run ```
sudo sensors-detect
``` to identify all the sensors on the motherboard. Hopefully that will find them: not all sensor chips are supported, since their output needs to be reverse-engineered.

Then you'll need something to display the temperatures, or log the temperatures, or both. I've generally used conky to show temperatures, but there are a whole bunch of widgets that can show the output of the *sensors* command. There are also tools to log the output, too.

---

### Post by Hasimir on 2018-12-02
Thanks CatKiller :)
This is the output from **sensor-detect**, with only one positive match out of all the probing done:
```

Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)


To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----




```


The output from the **sensors** command is then:
```

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +43.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +43.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +41.0°C  (high = +100.0°C, crit = +100.0°C)

```

Which tools can I then use to LOG my temperature readings?

---

### Post by CatKiller on 2018-12-02
It's good that your CPU temperature is shown by coretemp. You'll probably also find that ```
nvidia-smi --query-gpu=temperature.gpu --format=csv,noheader
``` will show you your GPU temperature.

As for logging, I normally just eyeball conky when I want to keep an eye on temps, so it's not something I've played with myself. The outputs are just text, so if you can't find a nice logging utility you could use something like ```
while true ; do sensors coretemp-isa-0000 >> coretemp.txt ; sleep 60 ; done
``` to check the temperature of your processor every 60 seconds and put the output at the end of a text file. You can probably pretty up that command to log both temperatures and tweak it to your liking. As that command stands, you'd need to keep the terminal window open to keep it logging. Ctrl-C would stop it. (Edit: As would a crash, of course, so the final temperature would be the one at the end)

---

### Post by meijer.o on 2018-12-02
There is a very simple graphical tool called psensor

```
sudo apt-get install psensor
```

Will install it.

If you cannot see the output, resize its window.

---

### Post by Hasimir on 2018-12-02
I need logs, not visualizations.
My computer WILL shutdown, and I want to know what the temperature was at that time.
Can I use psensor to see the temperatures from a previous session? from a specific date and time?

Also, I tried installing psensor before. It seems to have a problem on my system
```

psensor: error while loading shared libraries: libXNVCtrl.so.0: cannot open shared object file: No such file or directory

```

To install psensor I followed to the letter the instructions from at least 3 different guides, but none mention this lib file, nor give help on how to fix the problem ;(

---

### Post by Doug S on 2018-12-02
Based on your signature, you have a recent Intel processor. turbostat (linux-tools-common package) can do what you want. Example 1 (package temp (usually good enough for me)):

```
doug@s15:~$ sudo turbostat --Summary --quiet --show PkgTmp --interval 20
[sudo] password for doug:
PkgTmp
26
26
42
45
46
32
31
29
28

```Example 2 (Temp of each core and package or highest core, I don't know which):
```
doug@s15:~$ sudo turbostat --quiet --show CoreTmp --interval 20
CoreTmp
26
26
26
26
26
CoreTmp
26
26
26
26
26
CoreTmp
40
32
33
40
35
CoreTmp
43
35
36
43
37

```Example 3; (Just highest core, or package, I don't know which):
```
 sudo turbostat --Summary --quiet --show CoreTmp --interval 20
CoreTmp
51
37
35
33
32
31
30

```Just redirect the output for a log file:```
doug@s15:~/c$ sudo turbostat --Summary --quiet --show PkgTmp --interval 1 [COLOR="#FF0000"]> xcxcxc[/COLOR]
^Cdoug@s15:~/[COLOR="#FF0000"]cat xcxcxc[/COLOR]
PkgTmp
26
26
26
26
29
28
28
27
27
26

```Or use the write to a logfile option within turbostat (which I didn't know about):```
doug@s15:~/c$ sudo turbostat --Summary --quiet --show PkgTmp --interval 1 [COLOR="#FF0000"]--out xcxcxc[/COLOR]
^Cdoug@s15:~/c$
doug@s15:~/c$ [COLOR="#FF0000"]cat xcxcxc[/COLOR]
PkgTmp
26
26
26
26
26
26
26
25
26

```


By the way, it might be a good idea to look at the big spew of stuff that turbostat outputs during startup without the --quiet option. See also [here.]("https://ubuntuforums.org/showthread.php?t=2405766")

EDIT: This script will also monitor processor package temperature and CPU0 frequency (hardcoded at 4 seconds per sample (I don't recall why)):```
#! /bin/dash
#
# temp_mon4 Smythies 2018.07.24
#       try 0x19c as the temp MSR.
#       was 0x1b1
#
# temp_mon3 Smythies 2016.10.05
#       a simplified version of temp_mon2,
#       for monitoring temp.
#       Note: it is on purpose that -a is not used.
#       Also CPU0 frequency (1 is good enough, when all
#       are loaded).
#
# temp_mon2 Smythies 2016.09.29
#       Monitor Package temperatures.
#       Use clock modulation to control temps.
#       i.e. simulate the second to last level
#       of defense.
#       Use simple primatives.
#       run as sudo
#       hardcoded for my tcc of 98 degrees.
#
echo ... begin package temperature monitoring ...

#
# In case I forgot (which I often do)

modprobe msr

#
# first let the drastic effect of the sudo command decay
# Done later in temp_mon3.

#
# some stuff

COMMAND="rdmsr --bitfield 22:16 -u 0x19C"
COMMAND2="cat /sys/devices/system/cpu/cpufreq/policy0/scaling_cur_freq"

#
# then get on with it

while [ 1 ];do
  sleep 4
  TEMP_RAW=$(eval $COMMAND)
  CPU0_FREQ=$(eval $COMMAND2)
  TEMP_ACT=$((98-TEMP_RAW))
  echo "$TEMP_ACT   $CPU0_FREQ"
done

```

---

