---
title: "Ubuntu 8.04 Seems to Stop Working after Login"
date: 2008-06-04
forum: General Help
---

### Post by JustinChuTw on 2008-06-04
[FONT="Book Antiqua"]Hello All ...

I am new to Ubuntu and hope that someone can help me with the following problem.

If I start Ubuntu 8.04 using Kernel 2.6.24-17-Generic, the computer stops functioning after the desktop and both the Panels at the top and bottom of the screen appear.  The "User Name" and the Clock which should appear on the right side of the top Panel next to the "Shut Down" icon is missing and nothing happens when clicking on "Applications", "Places", "System" or any of the other icons.  And the only way to shut down the computer is with the "Power On/Off" switch.

However, everything seems to work normally if I start Ubuntu 8.04 using Kernel 2.6.24-16-Generic.

I will appreciate if very much if someone can help me resolve the above problem.

Cheers,
Justin[/FONT]

---

### Post by cmnorton on 2008-06-04
Please post something about your hardware.

Also, boot with the kernel that does not freeze, and go back into your logs, /var/log/kern.log, /var/log/messages, /var/log/syslog, and the output of dmesg, to see if  there is any information back from when you booted with the newer kernel.

Did you install something new or configure your system in between kernel updates?

---

### Post by Fixman on 2008-06-04
Have you tried pressing alt+f2 and putting "gnome-panel" on the text box?

Else, have you rebuilt the kernel after updating?

---

### Post by cmnorton on 2008-06-04
This may or may not apply to you, but it might be worth a look.

[http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

---

### Post by JustinChuTw on 2008-06-11
[FONT="Book Antiqua"][SIZE="2"]Cmnorton/Fixman ...

Thank you very much for your responses.

Like I said in my original post, I am new to Ubuntu (having defected from Microsoft Windows Vista Ultimate).  Since I had just installed Ubuntu and have not done too much in terms of configurations, or anything else for that matter, I thought it might be a whole lot easier to simply re-install Ubuntu and run "Update Manager" to update the system.  It works fine now, and even though there is quite a bit of getting used to, I have been Ubuntu exclusively for the past few days and it has been an enjoyable experience.

Again, thank you for your assistance.

Cheers,
Justin[/SIZE][/FONT]

---

