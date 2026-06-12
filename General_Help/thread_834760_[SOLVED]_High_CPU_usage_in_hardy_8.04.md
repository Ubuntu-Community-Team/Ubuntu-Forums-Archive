---
title: "[SOLVED] High CPU usage in hardy 8.04"
date: 2008-06-19
forum: General Help
---

### Post by hellzkeeper1216 on 2008-06-19
Currently running ubuntu on a Toshiba Satellite P205-6347. Everything seems to run smoothly except my CPU runs at 50-60% at all times. I'm running an Intel duo core proccessor with 3.6 GHZ. Both processors are currently at 56%. Any thing to help would be great. thank you.

---

### Post by werries on 2008-06-19
what programs do you run in the background? mine stays at like 10-30%. and i only have a 2.5GHz, with pidgin/screenlets running.

your graphics card may not be powerful enough to handle compiz so the processor takes the load? maybe?

---

### Post by hellzkeeper1216 on 2008-06-19
Mobile GM965/GL960 Integrated Graphics Controller off of a laptop. it is possible. although compiz runs smooth.

---

### Post by hellzkeeper1216 on 2008-06-19
I never really run anything in the background. The most i ever really have up is Pidgin and a system monitor on one of the desktops. other than that i don't really run anything else.

---

### Post by hellzkeeper1216 on 2008-06-24
*Bump*

anyone have any ideas?

---

### Post by sco01 on 2008-06-24
As a starting point, try running the command "top" from a console to figure out what process(es) that uses the CPU the most. Then try to locate the log for that process to see if there is something funny going on.

//S

---

### Post by mahuyar on 2008-06-24
Open up your system monitor.  List your applications by their cpu usage.  See what's eating the most of your cpu.

---

### Post by NilsHG on 2008-06-24
if it is a new installation of hardy it might be tracker indexing your files.

i do not quite understand what kind of a system you are running. a desktop or a notebook? i have neither heard of anyone using a notebook graphic adapter in a desktop nor of anyone running a notebook cpu at 3.6ghz... what do i not understand?

---

### Post by jimv on 2008-06-24
> **NilsHG said:**
> if it is a new installation of hardy it might be tracker indexing your files.

i do not quite understand what kind of a system you are running. a desktop or a notebook? i have neither heard of anyone using a notebook graphic adapter in a desktop nor of anyone running a notebook cpu at 3.6ghz... what do i not understand?

He says he's got a Toshiba Satellite P205-6347, which is a laptop.  Googled it and it says 1.6 ghz processor.  Probably just a typo.

---

### Post by sdennie on 2008-06-24
Do you have the system monitor open full screen on another desktop?  If so, the system monitor itself is probably what is taking all the CPU (this is a known bug).  Close it and instead use htop in a terminal:

```

sudo apt-get install htop

```

Then:

```

htop

```

---

### Post by hellzkeeper1216 on 2008-06-24
I'm sorry for the typo, it is a notebook and it is a 1.67Ghz duo core. installed the htop app. and it is saying that my CPU is only about 29% per core. which i think is good for linux right?

---

### Post by hellzkeeper1216 on 2008-07-02
i gave it a week or two to see how it would fair out and the system monitor was using a good amount. htop works great, i can keep it opened and it doesn't take up 
CPU. marking as solved.

---

### Post by themadhatter on 2008-10-18
I am seeing system slowdowns that are really bad. Running 3 instances of Firefox 3, my Hardy system (which is up to date on patches) slows to a crawl. 

This is shown in TOP, which has recorded XOrg at up to 75% CPU usage. Any suggestions?

---

### Post by Potters Son on 2008-11-14
Could it be a graphics card issue? I talked to a guy about why Scribus seemed to lag, and he discovered that XOrg is running on my computer at 15-20% of the CPU. The problem? My computer isn't using my Intel GM965/GL960 graphics card! (still trying to get drivers for it - been trying stuff for a week). My computer shouldn't be slow - 64 bit Intel Centrino, 4 gig RAM.

See if your computer's graphics card isn't configured correctly - run "lshw -C display" in a terminal. Does any entry say "UNCLAIMED"?

---

### Post by Murflaw on 2008-11-19
When I type that command in I get this...

  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
so I see it reads my graphics card but what does "UNCLAIMED" mean?

also how do you open system monitor?

---

