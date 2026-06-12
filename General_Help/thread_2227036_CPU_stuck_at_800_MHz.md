---
title: "CPU stuck at 800 MHz"
date: 2014-05-30
forum: General Help
---

### Post by Unkins on 2014-05-30
I recently upgraded to 14.04 and Ubuntu somehow think my i7 4770k has a minimum CPU speed of 800 MHz and the maximum CPU speed is 800 MHz. I dual boot with Windows 7 and I have normal control over CPU speed and voltage there. I don't think I had this problem with 13.10, but I also haven't used it very much in the last few months so I can't be sure. I did some research but none of those solutions helped me. Playing with my CPU BIOS settings has no effect. I would really like to completely disable the CPU governor stuff and just use my BIOS settings. I'm using a desktop computer I built myself, not a laptop.

---

### Post by pqwoerituytrueiwoq on 2014-05-30
what does this script say your cpu speeds are?, you have 8 logical cores
[https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts/blob/master/cpu-freq-plugin](https://github.com/GM-Script-Writer-62850/xfce-genmon-scripts/blob/master/cpu-freq-plugin)
run it like this:
```
x=0;while [ $x -lt 8 ];do cpu-freq-plugin $x|grep Core | sed 's/<tool>//';x=$(($x+1));done;
```
you can save the script to [FONT=courier new]/usr/local/bin/cpu-freq-plugin[/FONT] or fill out the path in the above 1 line script
It will print out a snapshot for your 8 core speeds
be sure to run that when the system is under load, not idle

---

### Post by Unkins on 2014-05-31
Thanks for the reply and trying to help me. Unfortunately, I'm very inexperienced at the terminal/scripts so I get a "cpu-freq-plugin: command not found". I downloaded that script as a .txt file and moved it to /usr/local/bin then ran that 1 line script in the terminal. Maybe that wasn't what I was supposed to do? :???: I also tried to download xfce4-cpufreq-plugin ([http://pkgs.org/download/xfce4-cpufreq-plugin](http://pkgs.org/download/xfce4-cpufreq-plugin)) since it looked very similar to the script you wanted me to use, but couldn't figure out how to run it. It could be that I'm using Unity.

I ran the command "cpufreq-info" and here is the output (all other 7 cores were the basically the same as core 0 so I only showed 0. Also note that the CPU is set to 4.6 GHz and 1.38 volts in my BIOS): ```
cpufrequtils 008: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 801 MHz
  available frequency steps: 801 MHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 801 MHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 801 MHz.
  cpufreq stats: 801 MHz:74.59%, 800 MHz:25.41%  (1351)

```

---

### Post by DeMus on 2014-05-31
Go to the website which is mentioned and copy all the text from the script.
Open a terminal and type: cd ~
Then type <name of your texteditor> [COLOR=#000000][FONT=Ubuntu Mono]cpu-freq-plugin[/FONT][/COLOR].sh   ; <name of your texteditor>[COLOR=#000000][FONT=Ubuntu Mono] means the real name of your text editor, for example gedit, or nano, or kate depending on which one you use)[/FONT][/COLOR]
A new textfile ([COLOR=#000000][FONT=Ubuntu Mono]cpu-freq-plugin[/FONT][/COLOR].sh) is opened and you paste the copied lines from the website into this textfile.
Save and close it.
Type ls to see the file in the list of files on your homedirectory
Type: chmod +x [COLOR=#000000][FONT=Ubuntu Mono]cpu-freq-plugin[/FONT][/COLOR].sh
This will make the file executable.
Now type this:
x=0;while [ $x -lt 8 ];do ./cpu-freq-plugin.sh $x|grep Core | sed 's/<tool>//';x=$(($x+1));done;

It should give you the actual frequencies of all cores your CPU has onboard.


Success.

---

### Post by Unkins on 2014-05-31
Thank you for the directions. I actually understood what most of those commands did. The output I get at 100% CPU load is:
```
Core 0 is at 801 MHz
Core 1 is at 801 MHz
Core 2 is at 801 MHz
Core 3 is at 801 MHz
Core 4 is at 801 MHz
Core 5 is at 801 MHz
Core 6 is at 801 MHz
Core 7 is at 801 MHz



```

I should mention that the reason that this slow speed is a huge problem to me is that I want to run Folding At Home basically 24/7 on this machine and I want every FLOP the overclocked CPU is capable of producing. Also, Firefox freezes if I try to watch a flash video and the system is a little bit sluggish considering my hardware. I know it's something in Linux and not a hardware problem because Windows has absolutely no problems. I will make a new partition and see if a clean install fixes the problem when I have more time tomorrow.

---

### Post by q64ceo on 2014-05-31
Do you use a special bootloader like Chameleon or Clover EFI?

---

### Post by Unkins on 2014-05-31
No, just the default bootloader. I think it is GRUB 2.

---

### Post by q64ceo on 2014-05-31
Do you have P and C states enabled in your BIOS?

---

### Post by Unkins on 2014-05-31
I reset the BIOS and suddenly it started working. #-o I did go through the CPU options carefully and tried everything, but I must have missed something or had a bad combination of settings. I have a Asus Maximus vi Hero and it has pages and pages of settings and tweaks.  I will experiment tomorrow and try to find what exactly caused it. Thank you to everyone who tried to help me. I usually reset the BIOS first thing after I find a problem, but most of the other people who had the same problem said that the fix was the OS was stuck in a power saving mode.  

```
Core 0 is at 3.501 GHz
Core 1 is at 3.501 GHz
Core 2 is at 3.501 GHz
Core 3 is at 3.501 GHz
Core 4 is at 3.501 GHz
Core 5 is at 3.501 GHz
Core 6 is at 3.501 GHz
Core 7 is at 3.501 GHz



```

---

