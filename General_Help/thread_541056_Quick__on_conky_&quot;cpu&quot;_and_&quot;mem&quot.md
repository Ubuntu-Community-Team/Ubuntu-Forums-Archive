---
title: "Quick ? on conky &quot;cpu&quot; and &quot;mem&quot; variables"
date: 2007-09-02
forum: General Help
---

### Post by timzak on 2007-09-02
What format are the results in?  Megabytes?  

For example:

```
${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}
${offset 240}${color lightgrey} ${top_mem name 5}${top_mem mem 5}
```

On my system, it reports the mem value for Firefox is 5.71 as I am currently typing.  This seems outrageously low if it is megabytes, maybe more in line with percent of memory used?  

What makes me doubt it is percent is there is a separate command for percent:  memperc.  Since conky reports that I have 1011MB (I have 1024 installed), then 5.71% of that would be almost 58 MB.  That actually seems a little too high.  So in the example above, is Firefox using 58 MB or 5.71 MB of memory?

Can anyone help with my curiosity?

Thanks.

---

### Post by timzak on 2007-09-02
*bump*

---

### Post by timzak on 2007-09-03
*bump*

Is there a better place to post a conky question?

Thanks.

---

### Post by merlyn on 2007-09-03
Try [this]("http://ubuntuforums.org/showthread.php?t=281865") thread, it has loads of conky.rc examples, screenshots and people more than willing to help others get Conky set up.

Cheers.

---

### Post by timzak on 2007-09-03
> **merlyn said:**
> Try [this]("http://ubuntuforums.org/showthread.php?t=281865") thread, it has loads of conky.rc examples, screenshots and people more than willing to help others get Conky set up.

Cheers.

I don't know if you read my first post or not, but I don't need help setting up conky--it's set up fine already.  I just want to know what format the results are displayed in.  Please read my opening topic.

Thanks.

edit--I went ahead and posted my question in the thread you posted.  Hopefully between the two threads I can get an answer.  Thanks.

---

### Post by merlyn on 2007-09-03
You also asked if there was another thread that could help with your question. ;)

The folks who post regularly on the thread I mentioned would be able to provide you with the answer that you seek.

Cheers.

---

### Post by timzak on 2007-09-04
No luck in the other thread...with nearly 600 posts, I think my question quickly got lost in the shuffle.  As an aside, I've had the worst luck getting questions answered lately.  I don't know if I'm not wording my questions clearly, they're all obscure questions with no answer, or perhaps I smell bad, but most of my recent queries on these forums have gone unanswered, despite bumping them periodically.

Oh well.  

Thanks for trying.

---

### Post by merlyn on 2007-09-05
> **timzak said:**
> No luck in the other thread...with nearly 600 posts, I think my question quickly got lost in the shuffle.  As an aside, I've had the worst luck getting questions answered lately.  I don't know if I'm not wording my questions clearly, they're all obscure questions with no answer, or perhaps I smell bad, but most of my recent queries on these forums have gone unanswered, despite bumping them periodically.

Oh well.  

Thanks for trying.

Sniff, sniff. . . .

and I thought that was my socks. ;)

Seriously though I'm sorry to hear that you haven't had any constructive answers to your posts, and also that I have been unable to provide you a direct answer myself.

I'm surprised that no one on the other thread offered an answer, as to the best of my knowledge it's one of the most in depth Conky related threads running.

Actually perhaps a copy of my conky.rc may help clear something up for you, note the lines that I use for displaying memory and CPU usage, as this method makes it quite clear what is actually being used as a percentage for example.

I'm clutching at straws here, and you most likely know how to display memory/cpu usage by the same method that I've used.

```
double_buffer yes
update_interval 1.0
background yes

own_window yes
own_window_transparent yes
own_window_type root
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

use_xft yes
override_utf8_locale no
xftfont Bitstream Vera Sans:size=9
xftalpha 0.8
draw_shades no
draw_outline no
draw_borders no
uppercase no
use_spacer no

border_margin 9
border_width 0

default_color white
default_outline_color black

alignment bottom_left
gap_x 9
gap_y 6

TEXT
${font :size=18:bold}${color #b8bec1}${time %A %B %e} ${time %H:%M}${font}
${stippled_hr}
${font :size=9}CPU ${cpu}% ${acpitemp}C${offset 50}Ram ${memperc}% ${mem}/${memmax}${offset 20}Swap ${swapperc}% ${swap}/${swapmax}${offset 55}Down ${downspeed eth0}Kb/s${offset 111}Up ${upspeed eth0}Kb/s${font}
${cpugraph 16,120 5e646a b8bec1} ${membar 16,180} ${swapbar 16,180} ${downspeedgraph eth0 16,180 5e646a b8bec1} ${upspeedgraph eth0 16,180 5e646a b8bec1}
```

I appreciate that this is not a direct answer to your specific question, but I'm not so sure what the "top" variable does, is it the same as using the command top in a terminal?

The only other possible option to getting the answer you need could be to join in on the conky irc channel mentioned on Conky's home page, which is [here]("http://conky.sourceforge.net/").

Sorry once again if I'm bringing up stuff you already know.

Cheers.

---

### Post by timzak on 2007-09-05
Hi Merlin,

The "top" variable shows the Xth highest consumer.  So "top_mem mem 1" displays the process name using the most memory at the moment, along with how much memory it is using.  "top_mem mem 2" shows the 2nd highest memory consumer and how much it is currently using.

Nowhere in the manual or Conky's website documentation could I find out what format this is in.  It APPEARS to be in percentage of total memory, but then why offer a separate variable for memperc?

Thanks again for your responses.

---

### Post by merlyn on 2007-09-05
> **timzak said:**
> Hi Merlin,

The "top" variable shows the Xth highest consumer.  So "top_mem mem 1" displays the process name using the most memory at the moment, along with how much memory it is using.  "top_mem mem 2" shows the 2nd highest memory consumer and how much it is currently using.

Nowhere in the manual or Conky's website documentation could I find out what format this is in.  It APPEARS to be in percentage of total memory, but then why offer a separate variable for memperc?

Thanks again for your responses.

So it is similar to the top command. I wonder what would happen if you changed one of your "top" entries to read as follows,```
top_mem memperc 1
```

I'm not sure if it would be a "legal" entry. If it did work however then you could be certain that the values displayed are in fact a percentage.

Also have you tried Conky's IRC channel?

Cheers.

---

### Post by timzak on 2007-09-06
I just tried subbing in "memperc" and where there should be a value in conky is blank, so you are right, it is an illegal entry.  It seem pretty obvious now that the value is in percent.

Thanks for your help, Merlin.

Best Regards.

---

### Post by merlyn on 2007-09-06
I'm really not sure if I was any help at all, and I'm glad that you've finally got a resolution.

Cheers mate.

Dave.

---

