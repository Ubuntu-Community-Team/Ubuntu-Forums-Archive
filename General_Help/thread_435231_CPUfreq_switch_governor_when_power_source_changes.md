---
title: "CPUfreq switch governor when power source changes?"
date: 2007-05-06
forum: General Help
---

### Post by ryodoan on 2007-05-06
I installed CPUfreq and it works great, right now when I start up my computer the governor is always set to "ondemand" this is nice when I am going between classes and I want to save my battery.

But when I plug into a power outlet it would be nice if there was a way to automatically change the governor to "performance"

I realize it is pretty simple to just open up a terminal and type out the command, and I have even made an alias for it to make it even simpler, but it would just be nice for my laptop to be able to say, "Hey, I am plugged into a wall, lets switch to full speed!" and then when I unplug for it to go back to on-demand.

Is this possible? is there some script I can write?

I was thinking about writing a script, something I am not very familiar with, but as I was thinking about it I encountered several issues.

1. Is there some kind of option to run a script on an event? Or do I have to be constantly checking for the status of the power source?
1b. If I was constantly checking the power source, wouldnt this in itself be draining my battery because it would be using up CPU time checking the battery?
2. Changing the governor is a super user action, how would it request a password?

And finally, I hope I filed this in the correct forum, if not please either move it for me, or tell me where i should go with this.

Thanks in advance.

---

### Post by bodycoach2 on 2007-05-06
[This is what I used]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features"), and it works perfectly. Ubuntu now gets better battery life than Windows XP ever did.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features")

This is for Feisty, though. There are instructions for Dapper and Edgy if you need.

---

### Post by ryodoan on 2007-05-06
Thanks for the reply, I have Feisty installed on my laptop.

That guide is what I used to install CPUfreq, and it shows you how to set it up so that the CPU governor is set to a specific mode when your computer is turned on.

What I am looking for is a way to take it a step further, as in it will change the CPU governor when you plug into an outlet to give you full performance from your CPU then will switch back to a power saving governor when the laptop goes to battery power.

---

### Post by nubutu on 2007-05-10
Hi

I believe that what you're looking for should be implemented in the laptop-mode-tools package, which you probably have installed. If I'm not wrong, whenever the power state of your machine changes, the acpi daemon acknowledges this event and different cpu scalings can be set accordingly based on it. I can't tell you more now, as I only found this thread to see whether somebody has experienced any problem with the laptop-mode settings and the use of the libata driver...long story.

I'll report back whenever I set up my system--unless you do it before me, which I would appreciate :)

PS. I suppose that anything you have running on your system represents a power sink, but since checking, at some reasonable intervals, some system log is a very inexpensive task, you really want to have this enabled. The difference between having your cpu and drives running at their utmost and tuning their performance clearly outweight whatever power consumption you may be incurring by running a background daemon.

---

### Post by ryodoan on 2007-05-10
Thanks for the reply.

I checked my installed packages, and its installed, however I do not know how to use it.

I did some googling and I ended up at the packages homepage. From their I gathered enough information to find out that its not enabled on my laptop.

I am not sure if I am doing it correctly, but I typed, "sudo laptop_mode" and got the following errors:

> /usr/sbin/laptop_mode: line 597: [: ==: unary operator expected
/usr/sbin/laptop_mode: line 600: [: ==: unary operator expected
Laptop mode disabled, not active.


I am going to do a search of the forums now to see what I can turn up.

---

### Post by ryodoan on 2007-05-10
Ok, figured out my last problem after a forum search, put in the typed out: sudo laptop_mode start and it started up.

Now I just have to look into configuring it.

Thanks for the direction though.

---

### Post by nubutu on 2007-05-11
Glad to hear you're all set up. I actually did my part yesterday night, and it all seems right as well, only that it doesn't seem to be starting at booting, I have to call it as you did. Well, nothing that can't be solved by adding that line to the start up programs, but I believe something is missing here, for I made the laptop-mode daemon to start by using sysv-rc-conf, although to no avail.

As for the settings, the laptop-mode.conf file is quite self-explanatory. Just something I did you might not be aware of: to check which cpu frequencies and governors you've got available, do some cat of the corresponding /proc files (look for them, I'm really bad at remembering random strings). Also notice that ondemand is not the same as conservative, the former scales your cpu frequency as soon as some load is detected, whereas the latter waits a little before actually revving the processor up.

---

### Post by ryodoan on 2007-05-11
I am actually having the same problem now, the laptop mode is not enabled when my laptop starts.

I am pretty new to Linux, how did you add the laptop_mode to start up with the computer.  I know how to add a general program to the start-up program list, but the problem I see is that laptop_mode requires the sudo command.

---

### Post by nubutu on 2007-05-11
OK, I found what was missing. I did add the laptop-mode daemon to the startup scripts, as I said, using sysv-rc-conf (give it a go, it´s quite useful, but be careful with it), and, as we both noticed, laptop-mode-tools wouldn't start automatically on boot. I found this:

[https://bugs.launchpad.net/ubuntu/+source/laptop-mode/+bug/80979](https://bugs.launchpad.net/ubuntu/+source/laptop-mode/+bug/80979)

and it worked perfectly--it seems--for me. To avoid some potential problems with some systems the developers opted for not enabling laptop-mode automatically, so you will have to change the last line of /etc/default/acpi-support. The part about updating the startup scripts seemed to be unnecessary for me, but it won't hurt either.

I assume that you already know how to check whether laptop-mode-tools is up and running, but just in case:

cat /proc/sys/vm/laptop_mode  should give a number different to 0,
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq  to check the current cpu frequency, and
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  to check the currently used governor

While looking for the cause of the problem I found some related sites you may want to have a look at:

[http://forums.gentoo.org/viewtopic.php?t=80077](http://forums.gentoo.org/viewtopic.php?t=80077)
[http://www.gentoo.org/doc/en/power-management-guide.xml](http://www.gentoo.org/doc/en/power-management-guide.xml)

In the first one somebody posted a unified script for the acpi events, and in the second one you will find an overview of power management in linux.  

Have a lot of fun

---

### Post by ryodoan on 2007-05-12
Dude, you are certifiably awesome.

I plug in my laptop, and I am running at full 1.86 Ghz, unplug my laptop and it auto-switches to conservative.

Works flawlessly, thanks a ton.  I never would have figured this out on my own.

---

### Post by ramjet_1953 on 2007-05-13
It's great that you got what you are after, but I am still trying to work out the logic behind it!

In on-demand mode, when the CPU is not under heavy load it throttles down and will only go to full speed when it is required. 

You should not notice any performance difference when it is operating in on-demand mode.

Also, don't forget that laptops are hot little suckers and running the CPU flat-out all of the time could reduce its' life. 

Also the cooling fan will probably be working hard and its' life will be shortened, also.

With all of this extra heat, causing your system's life to be reduced for no real gain seems a bit pointless to me.

Regards,
Roger :cool:

---

