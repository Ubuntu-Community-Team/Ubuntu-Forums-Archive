---
title: "guidance power manager/powersaved not initializing properly"
date: 2007-04-05
forum: General Help
---

### Post by d3athp3nguin on 2007-04-05
I have noticed an odd quirk with guidance on my intel centrino duo laptop.  Ideally, when plugged/unplugged the lappy will scale its cpu accordingly.  However, regardless of whether or not the laptop is in battery mode, both cores stay at full throttle (or at least guidance says they do.)

I read up a bit on guidance and power management and checked to see what governors the program had available.  I typed
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors

And it only returned one mode: performance.  I checked for available frequencies with:
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
and it listed 1.8 Ghz, 1.33 Ghz, and 1 Ghz available.

I tried restarting the powersaved module with:
sudo /etc/init.d/powersaved restart

And suddenly my cpu is scaling properly, and detects four available governors when I check cpufreq in the console.

I found one workaround that involves going into powersaved and adding an extra delay between loading the cpufreq module and loading the governors so that they load in the proper order, but that doesn't seem to have any effect at all.  Only restarting powersaved within a session seems to work.

Any ideas or solutions?  Or, is there any way to at least make sure the "on-demand" governor is loaded instead of "performance?"  Thanks in advance for any advice.

---

### Post by d3athp3nguin on 2007-04-05
Nevermind- the proposed fix that I found actually DID work; I did not add the delay in the right place.

For those experiencing the same problem and are novices at modifying scripts, read this article:
[https://bugs.launchpad.net/ubuntu/+source/powersave/+bug/68423](https://bugs.launchpad.net/ubuntu/+source/powersave/+bug/68423)

The area they are talking about in /etc/init.d/powersaved looks something like this:

                > # -> load powersave,performance,userspace and ondemand governor
		load_governors
		# wait for modules to be loaded
		sleep .2
	fi
	###### load CPUFREQ modules############

Right before load_governors, add "sleep X", where X is how long in seconds you want it to delay to give cpufreq time to finish loading.  Half a second worked for me; your mileage may vary.

After the edit:
> 
                # -> load powersave,performance,userspace and ondemand governor
		sleep .5                          #added to delay loading governors
		load_governors
		# wait for modules to be loaded
		sleep .2
	fi
	###### load CPUFREQ modules############

Don't make the noobish mistake I made by changing the sleep AFTER the load_governors command.

---

