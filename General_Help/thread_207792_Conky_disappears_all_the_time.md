---
title: "Conky disappears all the time"
date: 2006-07-02
forum: General Help
---

### Post by saax on 2006-07-02
I'm running kde and I recently installed conky. When I am looking at my desktop conky is there for like 10 seconds and then it totally disappears for a couple of seconds and then comes back again. Whats up with that?

I change "double_buffer no" instead of "double_buffer yes"

Im using this script
[http://conky.sourceforge.net/conkyrc-vert]("http://conky.sourceforge.net/conkyrc-vert")

I would also like to use it on right top corner ,but dont now how


Please help me

---

### Post by taurus on 2006-07-02
Try replacing "own_window" from no to yes in ~/.conkyrc.
```

own_window yes

```
And if you want it to start at top right corner, then you need to tell it in ~/.conkyrc.  Right now, you have it at "alignment top_left" so comment that out by placing a # in fron of it and remove the # sign in from of "alignment top_right" the next line...
```

#alignment top_left
alignment top_right

```
Don't forget to restart conky so the next chances will be in effect!!!

---

### Post by saax on 2006-07-02
It doesnt help ,when i enable own_window it dissapear in its own window and still blinking.And when i make to start alignment top_right it shows at near left and when i change back to left it shows in the middle of desktop.Something is really wrong,i also hear the same problem from other on gentoo forum,but the problem wasnt solved. :confused:

---

### Post by taurus on 2006-07-02
For the alignment, you also need to look at 
```

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 5 
gap_y 1 
alignment top_right
#alignment bottom_left
#alignment bottom_right

```

---

### Post by peschkaj on 2006-07-12
I encounter the same problem, but I'm using GNOME, and it occurs on both of my ubuntu boxes (3.6 GHz hp desktop and 1GHz dell laptop).

It occurs when I'm opening a graphical application, like Eye of Gnome.  Sometimes conky will flicker when I open a new tab in firefox.

When I run ps -ef | grep -i conky, it's still running, just not drawing itself.

> **saax said:**
> I'm running kde and I recently installed conky. When I am looking at my desktop conky is there for like 10 seconds and then it totally disappears for a couple of seconds and then comes back again. Whats up with that?

I change "double_buffer no" instead of "double_buffer yes"

Im using this script
[http://conky.sourceforge.net/conkyrc-vert]("http://conky.sourceforge.net/conkyrc-vert")

I would also like to use it on right top corner ,but dont now how


Please help me

---

### Post by peschkaj on 2006-07-12
I managed to get conky to work, for now it seems, by putting the following in my .conkyrc:
```

own_window 1
own_window_type override
own_window_transparent 1

```

---

### Post by maddbaron on 2006-07-12
does anyone know if i entered the double_buffer yes thing right and the other part correctly? In my kubuntu it just wont work anymore...

here is what is supposed to show on the screen is it correct?
> # Gap between borders of screen and text
gap_x 10
gap_y 10

# double_buffer yes

# own_window 1
# own_window_type override
# own_window_transparent 1

#alignment bottom_right
alignment bottom_right

# stuff after 'TEXT' will be formatted on screen

TEXT
$nodename $sysname $kernel on $machine
$color$stippled_hr
CPU: ${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph}$color

NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}
$color$stippled_hr
RAM:        $memperc%       ${membar 6}$color
Swap:       $swapperc%       ${swapbar 6}$color

Root:       ${fs_free_perc /}%        ${fs_bar 6 /}$color 
hda1:       ${fs_free_perc /media/hda1}%        ${fs_bar 6 /media/hda1}$color 
$color$stippled_hr
IP: ${addr eth1} Total: ${totaldown eth1} Down ${totalup eth1} Up

Down: ${downspeed eth1} k/s ${offset 110}Up: ${upspeed eth1} k/s
${downspeedgraph eth1 32,200} ${upspeedgraph eth1 32,200}

${execi 12 netstat -e -p -t | grep ESTABLISHED | cut -c45-68,80-86,102-140}
$color$stippled_hr
SYSTEM LOG TAIL
${execi 30 tail -n3 /var/log/messages | fold -w67}
$color$stippled_h
${execi 300 fortune -s | fold -w67}

---

### Post by peschkaj on 2006-07-13
I have the following in my .conkyrc file:

```

double_buffer 1
update_interval 1

own_window 1
own_window_type override
own_window_transparent 1


```

I'd start by commenting out everything above your TEXT section and uncommenting one line at a time until you hit the option that is causing it not to launch.

---

### Post by MrMojoRising on 2006-07-13
Easy (kinda) answer to get rid of any and all flickering/dissapearing problems.. Use FluxBox!

FluxBox + Conky = Harmony

---

### Post by PapaWiskas on 2006-07-13
> **MrMojoRising said:**
> Easy (kinda) answer to get rid of any and all flickering/dissapearing problems.. Use FluxBox!

FluxBox + Conky = Harmony

OpenBox + Conky = Tranquility  :)

---

### Post by taurus on 2006-07-13
XFce4 + Conky = Peace on Earth!!!  8)

---

### Post by improper on 2007-01-05
Hey all,

I scoured the web for a solution to this but couldn't find a complete document that helped, so I thought I'd write my own. Hopefully this helps the Linux community!

I pieced this together partially from these websites:

[http://ubuntuos.com/?p=224](http://ubuntuos.com/?p=224)
[http://www.linuxforums.org/forum/linux-newbie/67003-how-run-sh-files.html](http://www.linuxforums.org/forum/linux-newbie/67003-how-run-sh-files.html)

Thanks for writing them or contributing to them.

-------------------------------------------------------------------------------------------------

Open a file for editing in gedit: (sudo gedit conky_startup.sh)

Copy this into the window and save:
#!/bin/bash
sleep 10;
exec conky -d

Make script executable:
sudo chmod +x conky_startup.sh

Edit .bashrc file: (sudo gedit .bashrc)
Add this line to the bottom of the file:
export PATH=$PATH:/home/USERNAME/scripts/
*NOTE: This might not be necessary, but once I edited this file it seemed to work.

Open the System -> Preference -> Sessions program: (through Ubuntu menu at top)
Click the Startup Programs tab
Click add
Browse to your conky_startup.sh script and select it.

Now restart X (Ctrl + Alt + Bkspace)

Let me know if this helps!!

---

### Post by dr_d12 on 2007-01-29
> **improper said:**
> Hey all,

I scoured the web for a solution to this but couldn't find a complete document that helped, so I thought I'd write my own. Hopefully this helps the Linux community!

I pieced this together partially from these websites:
...
Let me know if this helps!!

This worked for me on Dapper.
Thanks,
DD

---

### Post by knlgSeekr on 2007-01-29
> **improper said:**
> Hey all,

I scoured the web for a solution to this but couldn't find a complete document that helped, so I thought I'd write my own. Hopefully this helps the Linux community!

I pieced this together partially from these websites:

.....
thanks man!=D> that worked like a charm.. my conky was dissappearing as soon as the background loaded up but that fixed it..:guitar:

---

