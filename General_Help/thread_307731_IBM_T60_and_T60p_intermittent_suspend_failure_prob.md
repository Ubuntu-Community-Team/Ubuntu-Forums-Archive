---
title: "IBM T60 and T60p intermittent suspend failure problem - Solved"
date: 2006-11-27
forum: General Help
---

### Post by Deus42 on 2006-11-27
I just thought I would throw this out there for anyone who is having problems suspending a t60 or t60p laptop.

The problem is when you try to suspend the laptop, sometimes it will work, and other times when the laptop is going into suspend mode, the moon light will just keep blinking.

It looks like the problem is with the processor frequency scaling, I got around the problem by shutting down the powernowd daemon before the system suspends, and then starting it again after the computer comes out of suspend.

---

### Post by rodik on 2006-12-25
I just got a T60, but haven't suspended it yet. Let me try it and i'll get back to you.

---

### Post by findik1 on 2007-01-14
can you describe it in detail, step by step please?

---

### Post by Deus42 on 2007-01-15
Sure:

First, try manually stopping the process before you suspend by typing:

sudo /etc/init.d/powernowd stop

This will turn off your frequency scaling, then suspend your thinkpad and it should work (although it takes up to 15 sec on mine).

If that works, you can stop, then start the service every time your computer suspends by following the below instructions:

in the console, edit /etc/acpi/suspend.d/10-thinkpad-standby-led.sh and add "/etc/init.d/powernowd stop" (without the quotes) to the bottom of the file.

Next, edit /etc/acpi/resume.d/90-thinkpad-unstandby-led.sh and add "/etc/init.d/powernowd start" (without the quotes) to the bottom of the file.

---

### Post by findik1 on 2007-01-17
I got the following error:

sudo edit /etc/acpi/suspend.d/10-thinkpad-standby-led.sh
Error: no "edit" mailcap rules found for type "application/x-sh"

---

### Post by Deus42 on 2007-01-17
Sorry, I was generically talking about editing a file. Let me take another crack at this:

In the console type: sudo nano -w /etc/acpi/suspend.d/10-thinkpad-standby-led.sh and add "/etc/init.d/powernowd stop" (without the quotes) to the bottom of the file. Then press <CTRL> W to save changes and exit.

Next type: sudo nano -w /etc/acpi/resume.d/90-thinkpad-unstandby-led.sh and add "/etc/init.d/powernowd start" (without the quotes) to the bottom of the file. Then press <CTRL> W to save changes and exit.

Sorry for the confusion! Did manually disabling powernowd before suspending work?

---

### Post by cb474 on 2007-02-25
> **Deus42 said:**
> I just thought I would throw this out there for anyone who is having problems suspending a t60 or t60p laptop.

The problem is when you try to suspend the laptop, sometimes it will work, and other times when the laptop is going into suspend mode, the moon light will just keep blinking.

It looks like the problem is with the processor frequency scaling, I got around the problem by shutting down the powernowd daemon before the system suspends, and then starting it again after the computer comes out of suspend.

This solution worked for me. But I also found that removing powernowd and using the cpu's built in frequency scaling works better. I followed this guide:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

After shifting the the cpu's own frequency scaling features I found that not only does suspend not have problems working but it also works much more quickly. (I'm on a IBM T60 with the core duo processor.)

---

