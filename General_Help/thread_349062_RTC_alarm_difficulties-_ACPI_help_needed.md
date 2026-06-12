---
title: "RTC alarm difficulties- ACPI help needed"
date: 2007-01-29
forum: General Help
---

### Post by majoridiot on 2007-01-29
since the local electric company decided to double their rates, it's now prudent to get my
mythbackend shutting itself down and waking itself up for recordings.  as the mobo i run seems
(from reports on the net) to have issues with nvram-wakeup, i've settled on wake from bios
using the RTC alarm wakeup.

i have enabled ACPI functions and RTC in bios, ACPID is up and running (Edgy 2.6.17) and seems
to be working properly.  a quick check shows:

```
# powersave -S
ACPI
```

which means the ACPI functions are ok, according to info i have.  however, when i try to write a
wakeup time to /proc/acpi/alarm i get:

```
 # sudo echo "2007-01-29 15:10:00" > /proc/acpi/alarm
-bash: /proc/acpi/alarm: Permission denied
```

which contradicts the information i'm relying on- it should write the new time to the RTC alarm.

i can manually edit /proc/acpi/alarm with nano, etc. and change it, but it doesn't seem to
be written to bios as it should.... i modded /etc/init.d/hwclock.sh with the following, to write
the value back out, in case the mobo gets finicky about linux changing the RTC after the
alarm was set (a reported problem on different mobos, so i did it to be safe, **bolds** were added):

```
hwclocksh()
{
    [ ! -x /sbin/hwclock ] && return 0
    . /etc/default/rcS

    . /lib/lsb/init-functions

    [ "$GMT" = "-u" ] && UTC="yes"
    case "$UTC" in
       no|"")	GMT="--localtime"
		UTC=""
		;;
       yes)	GMT="--utc"
		UTC="--utc"
		;;
       *)	return 1 ;;
    esac

    case "$BADYEAR" in
       no|"")	BADYEAR="" ;;
       yes)	BADYEAR="--badyear" ;;
       *)	return 1 ;;
    esac

    case "$1" in
	start)
	    if [ ! -f /etc/adjtime ] && [ ! -e /etc/adjtime ]; then
		echo "0.0 0 0.0" > /etc/adjtime
	    fi

            if [ "$HWCLOCKACCESS" != no ]; then
                # Copies Hardware Clock time to System Clock using the correct
                # timezone for hardware clocks in local time, and sets kernel
                # timezone. DO NOT REMOVE.
                /sbin/hwclock --hctosys $GMT $HWCLOCKPARS $BADYEAR

                if /sbin/hwclock --show $GMT $HWCLOCKPARS $BADYEAR 2>&1 > /dev/null |
                    grep -q '^The Hardware Clock registers contain values that are either invalid'; then
                        echo "Invalid system date -- setting to 1/1/2002"
                        /sbin/hwclock --set --date '1/1/2002 00:00:00' $GMT $HWCLOCKPARS $BADYEAR
                fi
            fi
            ;;
        stop|restart|reload|force-reload)
            #
            # Updates the Hardware Clock with the System Clock time.
            # This will *override* any changes made to the Hardware Clock.
            #
            # WARNING: If you disable this, any changes to the system
            #          clock will not be carried across reboots.
            #
**ACPITIME=`cat /proc/acpi/alarm`**
            if [ "$HWCLOCKACCESS" != no ]; then
                if [ "$GMT" = "-u" ]; then
                    GMT="--utc"
                fi
                /sbin/hwclock --systohc $GMT $HWCLOCKPARS $BADYEAR
            fi
            ;;
        show)
            if [ "$HWCLOCKACCESS" != no ]; then
                /sbin/hwclock --show $GMT $HWCLOCKPARS $BADYEAR
            fi
            ;;
        *)
**echo "$ACPITIME" > /proc/acpi/alarm**

            log_success_msg "Usage: hwclock.sh {start|stop|reload|force-reload|show}"
            log_success_msg "       start sets kernel (system) clock from hardware (RTC) clock"
            log_success_msg "       stop and reload set hardware (RTC) clock from kernel (system) clock"
            return 1
            ;;
    esac
}

hwclocksh "$@" &
```

checking the modules shows:

```
#  sudo dmesg|grep -i acpi

[17179569.184000]  BIOS-e820: 000000003bfc0000 - 000000003bfce000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000003bfce000 - 000000003bff0000 (ACPI NVS)
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9240
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x02000614 MSFT 0x00000097) @ 0x3bfc0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x02000614 MSFT 0x00000097) @ 0x3bfc0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x02000614 MSFT 0x00000097) @ 0x3bfc0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x02000614 MSFT 0x00000097) @ 0x3bfc03f0
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x02000614 MSFT 0x00000097) @ 0x3bfce040
[17179569.184000] ACPI: DSDT (v001  761GX 761GX964 0x00000000 INTL 0x02002026) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[17179569.184000] ACPI: IRQ0 used by override.
[17179569.184000] ACPI: IRQ2 used by override.
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179573.448000] ACPI: Core revision 20060707
[17179573.448000] ACPI: Looking for DSDT ... not found!
[17179573.592000] ACPI: bus type pci registered
[17179573.600000] ACPI: Interpreter enabled
[17179573.600000] ACPI: Using IOAPIC for interrupt routing
[17179573.600000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.608000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.628000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179573.628000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179573.628000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179573.628000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179573.628000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179573.628000] ACPI: PCI Interrupt Link [LNKF] (IRQs *3 4 5 7 10 11 12 14 15)
[17179573.628000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179573.628000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179573.628000] pnp: PnP ACPI init
[17179573.636000] pnp: PnP ACPI: found 14 devices
[17179573.636000] PnPBIOS: Disabled by ACPI PNP
[17179573.636000] PCI: Using ACPI for IRQ routing
[17179574.064000] ACPI: (supports S0 S1 S3 S4 S5)
[17179575.268000] ACPI: Processor [CPU1] (supports 8 throttling states)
[17179575.268000] ACPI: Thermal Zone [THRM] (-269 C)
[17179577.972000] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 169
[17179578.680000] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 177
[17179578.808000] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 185
[17179579.228000] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 193
[17179579.404000] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 201
[17179579.580000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 18 (level, low) -> IRQ 209
[17179589.332000] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179590.124000] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179594.880000] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 209
[17179613.864000] ACPI: Power Button (FF) [PWRF]
[17179613.864000] ACPI: Power Button (CM) [PWRB]
[17179614.000000] ibm_acpi: ec object not found
[17179614.036000] pcc_acpi: loading...
```

also:

```
#  find /proc/acpi
/proc/acpi
/proc/acpi/video
/proc/acpi/wmi
/proc/acpi/sony
/proc/acpi/hotkey
/proc/acpi/hotkey/info
/proc/acpi/hotkey/action
/proc/acpi/hotkey/poll_config
/proc/acpi/hotkey/event_config
/proc/acpi/button
/proc/acpi/button/power
/proc/acpi/button/power/PWRB
/proc/acpi/button/power/PWRB/info
/proc/acpi/button/power/PWRF
/proc/acpi/button/power/PWRF/info
/proc/acpi/battery
/proc/acpi/ac_adapter
/proc/acpi/thermal_zone
/proc/acpi/thermal_zone/THRM
/proc/acpi/thermal_zone/THRM/polling_frequency
/proc/acpi/thermal_zone/THRM/cooling_mode
/proc/acpi/thermal_zone/THRM/trip_points
/proc/acpi/thermal_zone/THRM/temperature
/proc/acpi/thermal_zone/THRM/state
/proc/acpi/processor
/proc/acpi/processor/CPU1
/proc/acpi/processor/CPU1/power
/proc/acpi/processor/CPU1/limit
/proc/acpi/processor/CPU1/throttling
/proc/acpi/processor/CPU1/info
/proc/acpi/fan
/proc/acpi/wakeup
/proc/acpi/alarm
/proc/acpi/sleep
/proc/acpi/event
/proc/acpi/fadt
/proc/acpi/dsdt
/proc/acpi/info
/proc/acpi/power_resource
/proc/acpi/embedded_controller
```

i'm hoping someone can point me in a good direction to take with this, as it is imperative 
i get this box waking up and shutting down by itself.  if i'm missing or misunderstanding
something, please let me know.  again, nvram-wakeup is **not** and option.  i need the
rtc alarm wakeup.

---

### Post by majoridiot on 2007-01-31
nobody out there is using RTC alarm wakeup?  i find that hard to believe... :confused:

---

### Post by majoridiot on 2007-02-06
maybe if we pare it down and start simpler...?

anyone have a clue why i get the Permission denied when i try the sudo echo command?  it
spits that error out immediately and without prompting for the password.

i've worn google out on this one... nothing mobo specific i can find  :confused:

---

### Post by mahoneyr on 2007-02-11
If you're not prompted for the password it's probably because you've already used sudo and have entered it already...

As for the permission denied error - you're doing a sudo on the echo command, but not the file writing.

Try this
sudo sh -c 'echo "2006-07-01 22:47:01" > /proc/acpi/alarm' 

I got stuck with the same problem for ages too :-)

---

### Post by majoridiot on 2007-02-11
> **mahoneyr said:**
> If you're not prompted for the password it's probably because you've already used sudo and have entered it already...

As for the permission denied error - you're doing a sudo on the echo command, but not the file writing.

Try this
sudo sh -c 'echo "2006-07-01 22:47:01" > /proc/acpi/alarm' 

I got stuck with the same problem for ages too :-)

baby... yer the greatest! LOL :D

i thought about posting more info about the sudo failure... actually it had nothing to do with
having previously used sudo or not.  for some reason, it just failed.

the command you provided now works... mostly.  it does not echo the day, which is probably
an idiosyncracy of the mobo.  but, THIS IS PROGRESS! :D

the sudo problem is interesting, and for those of you keeping track at home, i did the
research and the difference between this (which fails):

```
# sudo echo "2007-01-29 15:10:00" > /proc/acpi/alarm
```

and this (which works):

```
# sudo sh -c 'echo "2006-07-01 22:47:01" > /proc/acpi/alarm' 
```

is, as mahoney pointed out, that the first applies root priviliges to the echo command *only*,
where the second launches a shell *process* (the **sh** part, which performs **both**
the echo **and** the redirect of the echo to the file (**>/proc/acpi/alarm**) as root.

it's a *very* subtle but important difference... and one i missed entirely, assuming that
the sudo applies to everything in the command string, when in fact it doesn't always.  great
knowledge to file away for future use.

this gives me a direction to proceed with, thanks again mahoney!

i'll continue to post progress as it (hopefully) occurs...

---

### Post by mahoneyr on 2007-02-11
> **majoridiot said:**
> 

the command you provided now works... mostly.  it does not echo the day, which is probably
an idiosyncracy of the mobo.  but, THIS IS PROGRESS! :D



Does the day get written out at all?
I've got a problem on my server that I can alter the contents of /proc/acpi/alarm to include a date and time. when I check the contents straight away they're correct. When I power off the system doesn't restart when it should - when I look at /proc/acpi/alarm again the year, month and time are set, but the day is just 00. 
It works fine on my laptop though.

---

### Post by majoridiot on 2007-02-11
> **mahoneyr said:**
> Does the day get written out at all?
I've got a problem on my server that I can alter the contents of /proc/acpi/alarm to include a date and time. when I check the contents straight away they're correct. When I power off the system doesn't restart when it should - when I look at /proc/acpi/alarm again the year, month and time are set, but the day is just 00. 
It works fine on my laptop though.

still working on it... on my system, only the day is set, as the mobo assumes that a day date less
than the current date is a setting for the following month, i guess.  i suggest checking your bios 
settings to try and gain some insight into how your mobo wakeup works.  for mine, the wakeup 
can be set to every day with a time or by specific day with a time and no month setting.

at this point, i have managed only to wake by manually setting the wake time by hand... but
it will wake at the correct time, so more progress has been made!  i needed to update my
bios, which fixed the power management settings that were buggered.

something you might also consider is some mobos need to reboot **fully** before the wake 
time is fixated in cmos... mine was one of those.  i found that if i manually set the time, 
saved the changes to bios, let it reboot, hit the reset switch as soon as the grub screen
appeared and *then* shut it off that the time was correctly fixated in cmos and it would
wake. 

the things i need to get working, in order of appearance, are:

the correct time is not currently being written to cmos on ubuntu exit

my mobo clock is set to UTC, not local time

i need to install the "shutdown kernel", which is a fake kernel that reboots immediately, 
thus satisfying the need to reboot to fixate the wake time in cmos.

need the correct scripts to get myth to use it all.

i have a diretion to take on each of these, and will continue updates as things work.  when 
all is done, i'll probably post a how-to or a how-i-got-it-working-in-my-situaton to help
guide the way.  problem is that each mobo is different... but knowing what works for others is
always a help, no?  i know it always is for this idiot. :D

**EDIT:** ok... i can set /proc/acpi/alarm and verify it is set correctly and the mobo will wake up
if i  set the waketime in bios by hand, but /proc/acpi/alarm is not being copied over to cmos
on exit from some reason... it remains set to the last hand-set value.

i'm taking a break... if there's any input on what's happening, or in this case not happening,
please holla.  otherwise, it's back to google.

---

### Post by majoridiot on 2007-02-12
> **majoridiot said:**
> i'm taking a break... 

HA!  that lasted about 10 minutes and then i was back at it until now... but hey, what's another
five or six hours when you're obsessed with solving a problem? ;)

at this point, i'm beginning to wonder if this mobo will work from RTC wake alarm  or not. i've
got things traced down, and i've got no idea where things are going wrong.

i've focused on the hwclock.sh shutdown from the first post... and that was incorrect from bad
info- (probably based on the script for dapper or another debian release and this is on an 
edgy backend).  i've since moved on to troubleshooting it and the correct wake time exists
at /proc/acpi/alarm as it should when i set it with a script. this holds true both before and
after hwclock.sh writes system time back to the RTC before shutting down, but  it seems 
the info doesn't get written out to bios.  as that portion of hwclock.sh stands:

```
ACPITIME=`cat /proc/acpi/alarm`

...

	    # Updates the Hardware Clock with the System Clock time.
	    # This will *override* any changes made to the Hardware Clock.
	    #
	    # WARNING: If you disable this, any changes to the system
	    #          clock will not be carried across reboots.
	    #

	    if [ "$HWCLOCKACCESS" != no ]; then
		if [ "$GMT" = "-u" ]; then
		    GMT="--utc"
		fi
		
		echo "$ACPITIME" > /home/test/acpiecho  **## test what will be echoed**
		cat /proc/acpi/alarm > /home/test/before  **## show alarm time before RTC is written back out**	
	
	/sbin/hwclock --systohc $GMT $HWCLOCKPARS $BADYEAR  **## writes system time back to RTC**

		echo "$ACPITIME" > /proc/acpi/alarm && sleep 1 && echo "$ACPITIME" > /proc/acpi/alarm  **## tried writing it twice, as some mobos need it**
		cat /proc/acpi/alarm > /home/test/after **## test that it was in fact written**
   
		fi
```

upon reboot: *acpiecho, before* and *after* all reflect the wake time my script sets, but /proc/acpi/alarm
still retains the test value (2007-**-12 15:15:15) i set by hand in bios setup.  kinda says to
me that even though /proc/acpi/alarm is set correctly and the hwclock.sh script is configured
correctly, that linux itself is failing to write to bios.  delightful. :confused: 

i've had it for this round... twelve hours is more than enough.  i'll be back on it tomorrow...
if all else fails, i suppose i can setup the bios by hand to wake at the same time every day, 
and then script it out to figure the offset between that time and the time myth needs to 
wake... and then set the RTC to that bogus time on shutdown, so it *thinks* it's waking up 
on time.

but that, is the next to the last resort.

the last resort being nvram-wakeup, which i know has problems with ECS mobos... and is 
just a dangerous idea to begin with, what with all the mucking about in nvram and "guessing"
it does.

---

### Post by mahoneyr on 2007-02-12
This is the only page I've come across that has proved useful:
[http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)
Though I guess if you've googled for /proc/acpi/alarm you've probably seen it.

In my case it sounds like my bios isn't up to it - there aren't many ACPI options in there - the manual claims that it supports wakeup with the RTC though

---

### Post by majoridiot on 2007-02-12
> **mahoneyr said:**
> This is the only page I've come across that has proved useful:
[http://www.mythtv.org/wiki/index.php/ACPI_Wakeup](http://www.mythtv.org/wiki/index.php/ACPI_Wakeup)
Though I guess if you've googled for /proc/acpi/alarm you've probably seen it.

In my case it sounds like my bios isn't up to it - there aren't many ACPI options in there - the manual claims that it supports wakeup with the RTC though

hehe... that was the first page i pulled up when i started this adventure.

which mobo do you have?  mine is an ECS 761GX-M754... lots for sale but not much info.

---

### Post by mahoneyr on 2007-02-12
Intel D865GSA - one of the reasons I bought it was because it claimed it had wakeup support!

I wonder what's wiping out the day value in proc/acpi/alarm though - that must have something to do with it not working

---

### Post by majoridiot on 2007-02-12
> **mahoneyr said:**
> I wonder what's wiping out the day value in proc/acpi/alarm though - that must have something to do with it not working

are you sure it's the *day* that's wiped, and not the month?  seems a lot of mobos ignore
the month value, as previously noted.

as far as the adventure on this end, there has been some interesting developments.  i still am
unable to get the time in /proc/api/alarm written back to cmos on exit- it just doesn't make it.
kinda odd, since it gets read ok. i thought maybe it's something to so with incorrect usage 
of write registers on my mobo or something... except-

i yanked the sata drive from that box, stuck in a spare 3.5GB HD and installed a dapper
server to see if maybe this problem was edgy-related.  turns out dapper acts exactly the
same way.  while i had a junk drive in and was in no danger of data corruption, i decided to
play around and see what, if anything i could get working...

now the interesting thing is that the board has absolutely no problem waking up from a suspend
to disk, based on the alarm time.  if i do:

```
sudo sh -c 'echo "+00-00-00 00:03:30" > /proc/acpi/alarm'
```

the alarm sets to wake 3.5 minutes in the future and

```
sudo sh -c 'echo 4 > /proc/acpi/sleep'
```

suspends the system to disk, and powers down...  3.5 minutes later, IT WAKES UP!!!

this causes a real "hmmmm..." moment, as it writes out fine, suspends and wakes as it should.
the test values i echo back out from the hwclock.sh script match the time it wakes exactly-
as it also  it does when i try it with a shutdown... which, to me, means that *somewhere*
in the shutdown the alarm write is choking and failing.

on the plus side, the S4 development gives an option instead of a complete shutdown and
satisfies the need to conserve power.  on the negative, the firewire drivers *do not* survive 
the wake process and choke on use.  not a good thing, as firewire is the primary tuner and 
mythbackend freaks out when it can't find a firewire tuner.

pressing on...

---

### Post by majoridiot on 2007-02-12
ok, likely the last post in this thread, since i'm mostly talking to myself...

 ;) @ mahoneyr

it looks like the S4 suspend to disk will be a viable workaround to the problem.  the firewire
modules snafu can be worked around by unloading them from the kernel before suspend
and reloading after wake:

```
sudo modprobe -r dv1394      ## gotta unload it first, as it ties up--
sudo modprobe -r ohci1394    ## this module, which is the culprit

....

sudo modprobe ohci1394  ## load it again after resume
sudo modprobe dv1394    ## dunno if i need it, but it's normally loaded, so hey.
```

there's still quite a bit of scripting to be done to coordinate all of this and the firewire seems
***exceedingly*** testy on resume, which means i need to do a fair amount of tweaking
to the firewire priming util i use (available at the community wiki mythtv hardware pages).

unless something else develops in this thread, i'm going to concentrate on getting this wrapped
up in the next few days.  i will post a complete "how-i-did-it-and-good-luck-to-you" with wakeup
and shutdown scripts for mythtv and the modified firewire_tester util in another thread once
it's all good to go.

**EDIT:** I neglected to mention that the resume buggers the splash screen on resume.  not
a major problem, as it only affects the resume terminal, and not the system or other processes, 
as far as i can tell.  i can live with this if i have to, as that backend is headless 99% of the time
anyway... although there maybe be fixes already available.  worth mentioning, tho.

***another edit*** because upon review of the logs, the resume apparently kills the usb module and it
is unable to restart after resume. again, doesn't affect me, but needs mentioning.  might be able to
work around it unloading/loading the usb modules at the same time as the firewire.  we'll see.

***IMPORTANT EDIT--***

the method described above wound up being unstable and possibly damaging if i would have
continued to use it!!  before i got too far into the finishing scripts, i kept working with it, stressing
the system after sleeping and waking and found that it was **VERY** unstable after a couple
of suspends and a little stress- a lot of segfaults, kernel panics and core dumps.  

so be **careful** if you are considering messing with this!

i abandoned it immediately and went back to a different tack at the original problem...

---

### Post by majoridiot on 2007-02-13
***TOTAL SUCCESS!!!***

are you ready for this? **everything** once again turned out to be a convoluted mixture of
what available information was stating.  it was confusing as hell in the long run, but turned out
to be quite simple in a bizarro-world kinda way.

for my mobo, if you want it to resume from a *hand-set* time in bios, you must enable
ACPI aware OS, power management and resume on RTC alarm.  the setting can be daily 
or by date, with a time attached to either.  to successfully resume from this method, you 
*must* complete a reboot cycle completely through POST and *then* shut down.

to resume from a time set in linux, you again enable ACPI aware OS and power management
in BIOS but you *disable* resume from RTC alarm!

now here's the rub... to successfully resume from a time set in /proc/acpi/alarm, the exact
opposite is true again for the need to boot through post.  assuming that it needed to- since
info on the net said some boards need to and mine did for a hand-set BIOS waketime- i got
a fake kernel that just did a poweroff and monkeyed with grub.  everything worked fine 
except the actual waking up part.  following the bizarro-world logic again, i just did a 
shutdown command and let ACPI shut it down normally.

and **then** it woke itself up!

one interesting thing to note, mahoneyr... when i was doing the reboot with the poweroff kernel
to shut down (and failing), when i turned it back on and looked at /proc/acpi/alarm to see
if the time didn't get set correctly, i noticed that the days were zeroed out.  this is similar
to what you are describing on your board, no?  you might be able to get yours working
with some combinations of the settings i'm describing...

if anyone is still reading this and didn't read the edit to my previous post that i'm about to 
add- **DO IT** before playing with S4 suspend!!

**THANKS LOADS**, mahoneyr!  your single reply to this thread helped solve the problem in 
long run!!

---

### Post by mahoneyr on 2007-02-17
It now works for me as well!

My problem was simply down to my unfamiliarity with shell scripts - I'd put one line in the wrong place!

Thanks to the script you posted earlier which showed me how to write out from the script into files I was able to figure out that my call to write the value of $ACPITIME was never getting called.

I think the day getting wiped out was a symptom of the hardware clock being modified after the RTC value was set. Who knows, but at least it's now working.

So despite a complete lack of options to do with this in the bios the Intel D865GSA  works perfectly with ACPI wakeup once you edit hwclock.sh

---

### Post by majoridiot on 2007-02-17
EXCELLENT, mahanoeyr!  i'm glad you got it working!

the ironic thing is i just yesterday changed that mobo out of my backend box and now i need 
to complete this process for the new one...

---

### Post by mahoneyr on 2007-02-17
You should be an expert on it now tho :-)

I even managed to top it off by getting wake on LAN to work too!

---

### Post by majoridiot on 2007-02-17
then your box is set and ready for anything... 

i probably won't get to setting up the new mobo until tomorrow or the next day, but it should
be interesting to see what that board wants to happily WOL and wake on RTC.

both subjects will be written up for the ubuntu mythtv guide in the near future, so others can
get their boxes working to their full potential.

glad you got it all sussed. :D

---

### Post by pairajacks on 2007-02-18
I also have the problem described by mahoneyr where the date is zero'd after reboot. The commands from [www.mythtv.org/wiki/index.php/ACPI_Wakeup](www.mythtv.org/wiki/index.php/ACPI_Wakeup) work pretty much straight away; I can set the RTC and using cat /proc/acpi/alarm, it spits back the time I used in the echo command. 

root@mythtv:/usr/bin# echo "2007-02-25 11:51:04" >/proc/acpi/alarm
root@mythtv:/usr/bin# cat /proc/acpi/alarm
2007-02-25 11:51:04

I was even able to see make the PC wake up using the relative time setting
# echo "+00-00-00 00:05:00" >/proc/acpi/alarm

But if I set the alarm for 11:51:04 (like above), after reboot, cat /proc/acpi/alarm replaces the day with zeros.
007-02-00   11:51:04

You guys have seen this "zero' condition. What "combinations" do you need to have to make it wake up?

I also thought that maybe my bios was limited. I noticed that my Bios (AMI 1001), under power management, there's an RTC Alarm Date [25], but no RTC Alarm hour, minute or second. There's also a system time which doesn't make much sense (maybe not used except in windows?) 12:30:00.  I noticed that my PC did turn on after leaving overnight, so I was thinking maybe my bios was limited to just turning on based on date, not hour, min, or second

---

### Post by mahoneyr on 2007-02-19
When you say after reboot do you mean you restart after setting /proc/acpi/alarm?

Even when the server wakes up correctly the day is zeroed out which suggests that something is resetting the day following a reboot. Perhaps that's happening for you as well i.e. you have to set /proc/acpi/alarm before every shutdown.

I have zero settings in my bios that relate to the RTC alarm - it does work though.

---

### Post by majoridiot on 2007-02-19
> **mahoneyr said:**
> Perhaps that's happening for you as well i.e. you have to set /proc/acpi/alarm before every shutdown...

because of the idiosyncracies of various mobos and BIOSes, it's a good idea to set /proc/acpi/alarm
on every shutdown.  in my case, the correct wake times survive through the shutdown/wake
process, but obviously that cannot be relied on in every case.

---

### Post by majoridiot on 2007-02-20
put a new mobo in my backend box... 

add the ASUS K8N-E to the list of mobos that need wake on RTC set to **disable** to wake properly.

but it wakes up and shuts down like a dream. :D  i'll try to post a semi-decent "try this" with all
the appropriate scripts in a few days.

/me gives the electric company the finger

---

### Post by pelago on 2007-02-23
Hi, I've been playing with Wake on RTC too, also with a view to myth. My motherboard, Asus P4C800-E Deluxe, also requires Wake on RTC to be disabled in BIOS. I agree this seems counterintuitive at first, but the way I read it is that if it is enabled in the BIOS then it will only accept the date/time set in the BIOS. If it is disabled in BIOS it lets you set your own date/time in the operating system.

I had to modify hwclock.sh to save ACPITIME and reset it afterwards as well. Does anyone know how to communicate this with Ubuntu devs to get it fixed at source? Also, does anyone know when hwclockfirst.sh is used, as that might need fixing too?

My motherboard also has the issue where the day gets zeroed out after a reboot. I think this might be quite common. I haven't experimented fully to see whether it's a problem or not in reality.

---

### Post by majoridiot on 2007-02-23
> **pelago said:**
> I had to modify hwclock.sh to save ACPITIME and reset it afterwards as well. Does anyone know how to communicate this with Ubuntu devs to get it fixed at source? Also, does anyone know when hwclockfirst.sh is used, as that might need fixing too?

i don't believe this is a "bug" or something the the devs need to "fix", as it seems to be an idiosyncracy
of some boards, but not all... so "fixing" it for some night very well break it for others.  plus, it's
just bad practice.  also, i don't know if the system ever writes /proc/acpi/alarm back out on exit or
sleep... it didn't seem to when i was playing with it.  i *believe* it's left that way so as to not interfere 
with user apps/scripts.

i think hwclock.sh is called primarily on startup and exit, but perhaps also on restore
from sleep, etc... to synchronize BIOS with the system time, which is likely more accurate due
to ntp, etc.

---

### Post by culliard on 2007-04-03
Hi Guys

Maybe someone will be able to help me..

I been playing around with the RTC alarm and it is working to an extent. I have the Asus M2nPV-VM mobo. By the way, I am a complete beginner at linux but I built a system to learn how to use it. Eventaully it will be used as a MythTV/Multimedia centre. I just want to get things working for now!

In the Bios there are settings for Day, Hour, minute second, but I have disabled RTC alarm in Bios to get this to work.

I have modified the hwclock.sh script as specified in this thread.

```
cat /proc/acpi/alarm
```

reveals time format e.g. 2007-04-03 18:00:00

**Main Issue**
If I edit the file to set the time to say 2007-04-03 18:05:00, then shutdown. The RTC alarm will wakeup at the correct time. However looking in /proc/acpi/alarm again reveals that both the Month and Day have returned to 00, which means that my system wakes up EVERY day at the time in the alarm file, which is a bit annoying. I hae followed this post to the letter but no joy. Any ideas whats wrong?

**Secondary Issue**
If I do
```
sudo sh -c 'echo "+00-00-00 00:05:00" > /proc/acpi/alarm'
```

```
cat /proc/acpi/alarm
```

shows 0007-04-03 21:07:38 - notice that the year is wrong. If I power down, the RTC wakeup does work but I noticed that the system clock gets corrupted and returns to something like 2000-01-01 00:00:00

If I manually edit /proc/acpi/alarm to fix the year before shutting down everything is OK.
(I figures out that the time in this file should be in GMT not British summer time)

As a last resort I could try using nvram wakeup instead but I have read that it can mess up the bios - not good!

---

### Post by majoridiot on 2007-04-03
i'm not sure what your application is, but this thread resulted in an ACPI guide for mythtv that goes into
much greater detail of the procedure:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

you might check that out for more info.

i have had great luck with asus boards and acpi wake functions, though not that board in particular.  you
might check to see how old your BIOS is, as i had to update at least one boards BIOS to get it working
correctly.

also, some boards reportedly ignore the month setting out of hand (mine do) and others ignore both 
the month and day for some reason.

---

