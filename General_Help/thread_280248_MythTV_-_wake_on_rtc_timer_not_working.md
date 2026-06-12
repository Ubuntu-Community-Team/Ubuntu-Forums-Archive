---
title: "MythTV - wake on rtc timer not working"
date: 2006-10-19
forum: General Help
---

### Post by mal on 2006-10-19
For some weeks now I have been struggling to get my mythtv box to wake itself up automatically to record a scheduled TV program.  I am posting this summary of my attempts in the hope that someone else may be able offer some advice on solving this problem.

The mythtv box is based on an Asus p4p800s-x motherboard.  This board uses Intel 848P MCH / ICH5 chips which provide various wakeup facilities including wake-on-lan and wake-on-rtc (real time clock), both of which are useful for a mythtv box.

I can set the options in the BIOS for both of these and then shutdown the computer and it can be woken up by an appropriate lan magic packet or at the specified time.  However, if I let it boot to linux (Dapper) and shut it down again, it refuses to restart on either the lan or rtc options!!  Clearly, linux is doing something to disable these functions.

After much experimenting and forum searching, I found that I could re-enable the wake-on-lan function using the command: ```
$ sudo ethtool -s eth0 wol g
``` before halting the computer.  This seems to be a reliable solution to the wol problem.  I can now wake up my mythtv box from another machine.

The wake-on-rtc problem seems to be more difficult.  I have used two programs to set the alarm time and enable the wakeup function, nvram-wakeup and wakeup_clock.  Once it was properly configured, nvram-wakeup loads the required wake up time into the rtc cmos memory and supposedly enables the wake function.  Unfortunately, the machine refuses to wake up.  Using the wakeup_clock program, I have dumped the contents of cmos memory and, with the assistance of the Intel chipset documentation, I've found that bit 0x20 of the 11th byte of the cmos address range is an AIE bit (Alarm Interrupt Enable).  When I read this bit it returns a zero, indicating that the alarm interrupt is disabled.  I then modified the wakeup_clock program so that I could set the AIE bit to a one.  However, still no good the machine refuses to wake at the set time. :( 

At this point I've pretty well reached the end of my ability and perseverance.  Hence this call for help.

Any suggestions would be welcome.

Regards,

Mal

---

### Post by mal on 2006-11-26
If anyone comes across this thread and would like to know how to sort out this problem with the wake on timer function of some motherboards, [this post]("http://ubuntuforums.org/showthread.php?t=305751") by piec2 should help.

The solution was to get the motherboard to reboot before shutting down.  After setting this up, my mythtv box is happily waking itself up and recording scheduled shows and then shutting down to wait for the next scheduled recording.  :) 

Mal

---

