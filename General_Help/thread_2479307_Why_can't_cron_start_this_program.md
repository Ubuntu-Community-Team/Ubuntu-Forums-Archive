---
title: "Why can't cron start this program?"
date: 2022-09-20
forum: General Help
---

### Post by Rocket J Squirrel on 2022-09-20
Here's the path to the target program:

[FONT=fixedsys]/home/kpov-staff/Desktop/StereoTool/StereoTool_FM/stereo_tool_gui_64_FM[/FONT]

It is executable:

[FONT=fixedsys]-rwxrwxr-x 1 kpov-staff kpov-staff 34554056 Sep  2 16:56 /home/kpov-staff/Desktop/StereoTool/StereoTool_FM/stereo_tool_gui_64_FM[/FONT]

If I open Terminal and run it as shown, it launches. 

But the same line in cron, such as:

[FONT=fixedsys]@reboot /home/kpov-staff/Desktop/StereoTool/StereoTool_FM/stereo_tool_gui_64_FM[/FONT]

Does nothing. After reboot, dmesg reports:

[FONT=fixedsys]$ sudo dmesg | grep stereo[/FONT]
[FONT=fixedsys][sudo] password for kpov-staff: [/FONT]
[FONT=fixedsys][    4.334626] process 'Desktop/StereoTool/StereoTool_FM/stereo_tool_gui_64_FM' started with executable stack[/FONT]


In case something needs to complete before the program can launch I've tried 

[FONT=fixedsys]@reboot sleep 120; /home/kpov-staff/Desktop/StereoTool/StereoTool_FM/stereo_tool_gui_64_FM[/FONT]

But either way, the program does not load. 

[FONT=fixedsys]$ ps -aux | grep stereo[/FONT]
[FONT=fixedsys]kpov-st+    2937  0.0  0.0  17732  2380 pts/0    S+   09:06   0:00 grep --color=auto stereo[/FONT]

What the heck?

---

### Post by ian-weisser on 2022-09-20
@reboot runs before you login. So there is no GUI yet and no $DISPLAY environment variable.

It might be more reliable to create a .desktop file for your application, and place (or link) that .desktop file in ~/.config/autostart so it runs every time you login.

---

### Post by Rocket J Squirrel on 2022-09-20
EDIT: NEVER MIND, IT WAS THE "X-GNOME-Autostart-enabled=false" LINE IN THE .DESKTOP THAT WAS CAUSING THE PROBLEM.

Ah, excellent, I didn't know that @reboot ran too early for gui programs. Very well -- the reason I posted this question is that I was unable to get this program to launch from a .desktop file, either. 

So here is what I have.

In ~/.config/autostart I have a file "StereoTool.desktop"

It contains:

[FONT=fixedsys][Desktop Entry][/FONT]
[FONT=fixedsys]Name=StereoTool[/FONT]
[FONT=fixedsys]Comment=Stereo_Tool[/FONT]
[FONT=fixedsys]Exec=/home/kpov-staff/Desktop/StereoTool/StereoTool_FM/stereo_tool_gui_64_FM[/FONT]
[FONT=fixedsys]Icon=/usr/share/icons/butt_icon_scalable.svg[/FONT]
[FONT=fixedsys]Terminal=false[/FONT]
[FONT=fixedsys]Type=Application[/FONT]
[FONT=fixedsys]Categories=Audio[/FONT]
[FONT=fixedsys]X-GNOME-Autostart-enabled=false[/FONT]

It is executable:

[FONT=fixedsys]$ ls -l[/FONT]
[FONT=fixedsys]total 12[/FONT]
[FONT=fixedsys]-rw-rw-r-- 1 kpov-staff kpov-staff 179 Sep  3 09:43 butt.desktop[/FONT]
[FONT=fixedsys]-rw-rw-r-- 1 kpov-staff kpov-staff 112 Sep  1 06:55 ignore-lid-switch-tweak.desktop[/FONT]
[FONT=fixedsys]-rw-rw-r-- 1 kpov-staff kpov-staff 255 Sep 20 07:25 StereoTool.desktop[/FONT]

The other two .desktops here do launch after I log in, no problem. "butt.desktop" launches a gui program, the other is just a utility. But "StereoTool.desktop" does not launch when I log in. So, the goal here is to find some darn way to get that program to autostart! There's gotta be a way!!!!

Thank you!

---

### Post by TheFu on 2022-09-20
Don't expect any GUI program to work from cron.  

Please use the "thread tools" link/button at the top of the page and mark this thread as SOLVED so people don't waste time reading about already SOVLED threads, unless they seek a solution.  Thank you for helping out!

---

