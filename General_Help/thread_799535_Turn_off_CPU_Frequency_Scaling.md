---
title: "Turn off CPU Frequency Scaling"
date: 2008-05-19
forum: General Help
---

### Post by AcidHawk on 2008-05-19
Previously when I used Kubuntu I could right click on an applett which I added to the panel and change the CPU scaling from Dynamic to Performance.

I have since moved to Ubuntu and cannot find where to switch Dynamic scaling off.

I have tried adding the CPU Frequency Scaling Monitor to the panel but there is no option to set the scaling as Not Dynamic.

---

### Post by m83 on 2008-05-19
See [this page]("http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/").

---

### Post by sdennie on 2008-05-19
I'm not sure that "performance" will gain you much over "ondemand".  The CPU can change P-States very quickly and, anything that is CPU bound isn't likely to run noticeably faster with the "performance" governor.

---

### Post by jespdj on 2008-05-19
I agree with vor, there is really no reason why you would want to disable CPU frequency scaling.

If you start any program that needs the CPU, then it jumps up to full speed immediately. Letting the CPU run at full speed when it's idle is useless, and only wastes energy and drains your battery faster (if it's on a laptop).

---

### Post by jdong on 2008-05-19
The main reason for wanting it off is because some games, virtualization suites, etc react very badly to the clock jumping around. Other than that, Ubuntu only enables scaling for CPUs that do it very fast, and there should be no noticeable performance difference with it on or off.

---

### Post by AcidHawk on 2008-05-21
Thanks folks.  As always this forum is a wealth of info.

I'll not worry about it then.

---

### Post by jdong on 2008-05-21
> **AcidHawk said:**
> Thanks folks.  As always this forum is a wealth of info.

I'll not worry about it then.


For posterity, if you go to gconf-editor (Alt-F2, type that in), then look under apps/gnome-power-manager, under one of those sub-folders you'll find the option to make CPU frequency scaling options available.

After activating that option, the preferences for gnome-power-manager will have CPU frequency scaling options...

As said before, this will likely not yield any noticeable increase in performance; it's primarily for people who have buggy drivers or games that cannot deal with a changing CPU frequency... Symptoms you'll typically see include:

A game suddenly running 5x faster time than normal
In VMWare, the cursor in the VM blinks at a CRAZY fast rate
X drops mouse packets (mouse cursor movement jerky) -- this happens on some Dells with PS/2 touchpads!


EDIT: Note that locking the CPU into "powersave" actually does not save power either. Ondemand is really the optimum setting.

---

### Post by chewearn on 2008-05-21
If you are running [folding@home]("http://folding.stanford.edu/"), the easiest way to run at constant full tilt (maximize your folding) is to change the gconf field:
apps > gnome-power-manager > cpufreq > policy_ac
change to performance

Note:
The default ondemand will run the CPU at the lowest frequency while folding.
Of course, you should monitor the temperature while doing this.

.

---

### Post by sdennie on 2008-05-21
> **AstalaVista said:**
> 
Note:
The default ondemand will run the CPU at the lowest frequency while folding.
Of course, you should monitor the temperature while doing this.


No, it won't.  Something as benign as "ls" in a terminal will push the CPU to maximum frequency.  I don't know how nice levels and CPU P-States interact but, unless an application tries really hard to keep the CPU in a low P-State, the CPU will jump to full frequency in a few milliseconds and stay there until it becomes idle.

---

### Post by chewearn on 2008-05-21
> **vor said:**
> No, it won't.  Something as benign as "ls" in a terminal will push the CPU to maximum frequency.  I don't know how nice levels and CPU P-States interact but, unless an application tries really hard to keep the CPU in a low P-State, the CPU will jump to full frequency in a few milliseconds and stay there until it becomes idle.

Alright, rephrase.

Note:
The default ondemand will run the CPU at the lowest frequency while folding* and idle*.


.

---

### Post by sdennie on 2008-05-21
> **AstalaVista said:**
> Alright, rephrase.

Note:
The default ondemand will run the CPU at the lowest frequency while folding* and idle*.


.

That's interesting.  Can you run powertop while folding with the ondemand governor with something like:

```

sudo powertop -d -t 300

```

I'd be interested to know if using the ondemand governor ever lets the P-State drop below the highest frequency.

---

### Post by chewearn on 2008-05-21
Here you go:
```

PowerTOP 1.9    (C) 2007 Intel Corporation 

Collecting data for 300 seconds 
< Detailed C-state information is only available on Mobile CPUs (laptops) >
P-states (frequencies)
  2.00 Ghz    15.3%
  1.80 Ghz    12.8%
  1000 Mhz    71.9%
Wakeups-from-idle per second : 507.8    interval: 300.0s
no ACPI power usage estimate available
Top causes for wakeups:
  25.3% (132.4)       <interrupt> : nvidia 
  21.0% (109.6)       <interrupt> : eth0 
  15.8% ( 82.4)      <kernel IPI> : Rescheduling interrupts 
  13.3% ( 69.5)       <interrupt> : PS/2 keyboard/mouse/touchpad 
   4.3% ( 22.3)           firefox : futex_wait (hrtimer_wakeup) 
   4.0% ( 21.1)    FahCore_a1.exe : sk_reset_timer (tcp_delack_timer) 
   3.1% ( 16.0)       <interrupt> : ehci_hcd:usb2 
   2.6% ( 13.7)    FahCore_a1.exe : sk_reset_timer (tcp_write_timer) 
   2.1% ( 11.2)       compiz.real : schedule_timeout (process_timeout) 
   1.9% ( 10.0)   USB device  2-7 : USB Reader ( ) 
   1.2% (  6.1)             artsd : schedule_timeout (process_timeout) 
   0.9% (  4.8)    sensors-applet : schedule_timeout (process_timeout) 
   0.4% (  2.3)   multiload-apple : schedule_timeout (process_timeout) 
   0.4% (  2.0)              fah6 : do_nanosleep (hrtimer_wakeup) 
   0.4% (  1.9)   hald-addon-stor : schedule_timeout (process_timeout) 
   0.2% (  1.2)              Xorg : schedule_timeout (process_timeout) 
   0.2% (  1.2)       <interrupt> : libata 
   0.2% (  1.1)         nm-applet : schedule_timeout (process_timeout) 
   0.2% (  1.0)    cpufreq-applet : schedule_timeout (process_timeout) 
   0.2% (  1.0)             artsd : do_setitimer (it_real_fn) 
   0.2% (  1.0)              ntpd : do_setitimer (it_real_fn) 
   0.2% (  1.0)            dhcdbd : schedule_timeout (process_timeout) 
   0.2% (  1.0)              Xorg : nv_start_rc_timer (nv_kern_rc_timer) 
   0.2% (  1.0)     <kernel core> : ehci_work (ehci_watchdog) 
   0.2% (  1.0)   hald-addon-stor : blk_plug_device (blk_unplug_timeout) 
   0.2% (  0.8)    FahCore_a1.exe : do_nanosleep (hrtimer_wakeup) 
   0.1% (  0.7)       gnome-panel : schedule_timeout (process_timeout) 
   0.1% (  0.6)      <kernel IPI> : TLB shootdowns 
   0.1% (  0.5)        pulseaudio : schedule_timeout (process_timeout) 
   0.1% (  0.4)           firefox : schedule_timeout (process_timeout) 
   0.1% (  0.4)           firefox : sk_reset_timer (tcp_write_timer) 
   0.1% (  0.4)     <kernel core> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.1% (  0.4)         evolution : schedule_timeout (process_timeout) 
   0.1% (  0.4)   gnome-screensav : schedule_timeout (process_timeout) 
   0.1% (  0.3)              Xorg : do_setitimer (it_real_fn) 
   0.1% (  0.3)          nautilus : schedule_timeout (process_timeout) 
   0.0% (  0.2)   update-notifier : schedule_timeout (process_timeout) 
   0.0% (  0.2)   <kernel module> : neigh_table_init_no_netlink (neigh_periodic_timer) 
   0.0% (  0.2)              Xorg : sk_reset_timer (tcp_delack_timer) 
   0.0% (  0.2)     <kernel core> : page_writeback_init (wb_timer_fn) 
   0.0% (  0.2)    NetworkManager : __netdev_watchdog_up (dev_watchdog) 
   0.0% (  0.1)    sensors-applet : inet_twsk_schedule (inet_twdr_hangman) 
   0.0% (  0.1)   gnome-power-man : schedule_timeout (process_timeout) 
   0.0% (  0.1)    NetworkManager : nv_open (nv_do_stats_poll) 
   0.0% (  0.1)             touch : start_this_handle (commit_timeout) 
   0.0% (  0.1)   gnome-volume-ma : schedule_timeout (process_timeout) 
   0.0% (  0.1)           firefox : sk_reset_timer (tcp_delack_timer) 
   0.0% (  0.1)    gnome-terminal : schedule_timeout (process_timeout) 
   0.0% (  0.1)                ip : __dst_free (delayed_work_timer_fn) 
   0.0% (  0.1)          gconfd-2 : schedule_timeout (process_timeout) 

Suggestion: increase the VM dirty writeback time from 5.00 to 15 seconds with:
  echo 1500 > /proc/sys/vm/dirty_writeback_centisecs 
This wakes the disk up less frequenty for background VM activity

Suggestion: Disable 'hal' from polling your cdrom with:  
hal-disable-polling --device /dev/cdrom 'hal' is the component that auto-opens a
window if you plug in a CD but disables SATA power saving from kicking in.

```

---

### Post by sdennie on 2008-05-21
Wow, AstalaVista that's actually really interesting.  I would imagine that the folding app (presumably the Fah* processes in that display) is set to a "super nice level" so as to not interrupt other apps.  I'm actually really surprised it's not forcing the CPU to max frequency at all times.  Maybe there is some sort of interaction between nice levels and the CPU governor.  Something to investigate at the very least.

Saludos.

---

### Post by chewearn on 2008-05-21
Yeah, the FahCore processes is set to nice=19; it take only the spare CPU cycles.

.

---

### Post by jdong on 2008-05-21
> **vor said:**
> Wow, AstalaVista that's actually really interesting.  I would imagine that the folding app (presumably the Fah* processes in that display) is set to a "super nice level" so as to not interrupt other apps.  I'm actually really surprised it's not forcing the CPU to max frequency at all times.  Maybe there is some sort of interaction between nice levels and the CPU governor.  Something to investigate at the very least.

Saludos.



By default ondemand ignores niced processes in load calculation... Folding runs under the lowest priority.

---

### Post by sdennie on 2008-05-27
Thanks, jdong.  I hadn't realized that and it explains several things I've seen.

---

### Post by russlar on 2008-06-19
Good thread with lots of info, but I want to do the opposite. I've got an Intel T7100 CPU (1.8 GHz) in a ThinkPad T61, and the default scaling setting is "OnDemand". I know this is the best option for maximum battery life, but I want it to peg at 1.2 GHz at startup (this is an option in the CPU scaling monitor applet in Gutsy). Anybody got a fairly straightforward way to achieve this?

---

### Post by sdennie on 2008-06-19
I'm not sure why you would want to do this but, it can be done easily with cpufrequtils:

```

sudo apt-get install cpufrequtils
sudo cpufreq-selector -g userspace -f 1200000

```

To test that it's working;

```

cpufreq-info

```

---

### Post by russlar on 2008-06-19
> **vor said:**
> I'm not sure why you would want to do this but, it can be done easily with cpufrequtils:

```

sudo apt-get install cpufrequtils
sudo cpufreq-selector -g userspace -f 1200000

```

To test that it's working;

```

cpufreq-info

```

thanks. will this alter the default settings that are loaded at boot?

---

### Post by sdennie on 2008-06-19
No.  You'd have to add the cpufreq-selector command to /etc/rc.local.

---

### Post by russlar on 2008-06-19
> **vor said:**
> No.  You'd have to add the cpufreq-selector command to /etc/rc.local.

ahhh... thanks!

---

### Post by Dave-CC on 2009-11-28
I have tried using ;
sudo cpufreq-selector -g userspace -f 1330000

as my CPU can handle 1 GhZ 133 and 186 however my CPU's speed is NOT changing. i have the system setup to auto goto Performance as its default governor however after approx. 3 minutes of running @ 1.86 Ghz the controls will goto 1 Ggz and not allow for change until i restart the syste, any idea's why this is happening? i need to disable CPU Freq. also as it's causing a game i play to drop to near 5 Frames per sec

---

### Post by dewdrop_world on 2010-12-30
> **jespdj said:**
> I agree with vor, there is really no reason why you would want to disable CPU frequency scaling.

I know this is an old thread, but I just have to say, it annoys me somewhat when people say things like this.

There IS a reason -- CPU-intensive real-time applications that demand the lowest possible latency (like professional audio). "Don't disable it" is absolutely right if someone is just browsing the web, writing word processor documents etc. But not everybody is using their machines only for that.

I guess it would annoy me less if it were a question -- "what are you doing with the machine that would need no scaling?" -- instead of a flat assumption.

James

---

### Post by Yellow Pasque on 2010-12-30
```
cpufreq-set -g performance
```

> I know this is an old thread, but I just have to say, it annoys me somewhat when people say things like this.
People say things like that because of ignorant people that don't gain anything from running their CPU 100% all of the time and basically say, "I don't care about saving power. More MHz! Where's the Turbo switch? Nuke the whales!.. etc." Those people are pretty annoying too.

---

