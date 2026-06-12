---
title: "Ubuntu near freezing... slowing to a crawl at best!"
date: 2007-06-20
forum: General Help
---

### Post by John CCC on 2007-06-20
I am new to Ubuntu and really enjoying it.  Through the help of these forums, I have managed to get a USB modem running, get sound where there was none, and figure out how to get a few other issues resolved.  So, thanks a ton!
I don't know where to start with this.  It just seems as if all of a sudden everthing slows down to an incredibly slow speed.  THe mouse still works but it jumps from place to place as if it takes the pointer (literally) two seconds to reach to where I had pointed the mouse.  If I wait patiently I can navigate the pointer enough to close programs and even reboot but it takes an amazingly long time to do anything ie: 4-5 min to shut down. But then it restarts just fine.

It seems to be triggered by random things.. I had it happen when trying to play a cd.  When messing with skype, but also when I was using picassa 2.  

I am using an AMD athlon, processor.  With 256 ram.  does anyone have any ideas???
cheers.

---

### Post by llamakc on 2007-06-20
Purchase more RAM or use something lighter like XFCE to save on resources.

---

### Post by John CCC on 2007-06-23
Hello, 
I put another 128mb of ram in, and will do more later, but I'm not convinced that it's just the ram issue.  It just happened again, and I was looking at system resources at the time.  I was using around 150mb with only the system monitor running.  I'm wondering if I have other unwanted programs running automatically needlessly.  Any advice on dealing with that?
Also, here is the system log from just when the computer slowed up: Problem happened just around 18:40 or so
```
Jun 23 17:32:22 niamh -- MARK --
Jun 23 17:52:23 niamh -- MARK --
Jun 23 18:12:23 niamh -- MARK --
Jun 23 18:24:23 niamh kernel: [ 4373.244666]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Jun 23 18:24:23 niamh kernel: [ 4373.244684]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
Jun 23 18:24:23 niamh kernel: [ 4373.244694]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Jun 23 18:24:23 niamh kernel: [ 4373.244702]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
Jun 23 18:24:23 niamh kernel: [ 4373.244710]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Jun 23 18:24:23 niamh kernel: [ 4373.244719]  [math_state_restore+26/80] math_state_restore+0x1a/0x50
Jun 23 18:24:23 niamh kernel: [ 4373.244725]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun 23 18:24:23 niamh kernel: [ 4373.244742]  =======================
Jun 23 18:52:23 niamh -- MARK --
Jun 23 19:12:24 niamh -- MARK --
Jun 23 19:32:24 niamh -- MARK --
Jun 23 19:52:24 niamh -- MARK --
Jun 23 20:12:25 niamh -- MARK --
Jun 23 20:32:26 niamh -- MARK --
Jun 23 20:39:52 niamh gconfd (root-17897): starting (version 2.18.0.1), pid 17897 user 'root'
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 23 20:39:58 niamh kernel: [12497.187314]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Jun 23 20:39:58 niamh kernel: [12497.187333]  [__switch_to+198/496] __switch_to+0xc6/0x1f0
Jun 23 20:39:58 niamh kernel: [12497.187341]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
Jun 23 20:39:58 niamh kernel: [12497.187351]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Jun 23 20:39:58 niamh kernel: [12497.187359]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
Jun 23 20:39:58 niamh kernel: [12497.187366]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Jun 23 20:39:58 niamh kernel: [12497.187376]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun 23 20:39:58 niamh kernel: [12497.187382]  [default_idle+0/96] default_idle+0x0/0x60
```

Also, The system monitor said that I was using 100% of the system resources.  I really want to figure out how to stop this if possible..

---

### Post by sloggerkhan on 2007-06-23
You most likely have a bad process.
Add a system monitor applet to your gnome bar and make sure is displays RAM and swap usage. The second things start slowing down or you see all your RAM getting consumed, click on it. This should open up the gnome system monitor. List processes by memory. Most likely one process will be hogging all of it. Kill that process.
Then look for a bug report on launchpad about it. The report will most likely have a workaround attached to it.

The 2 things I have seen sometimes behave this way are gs and beagle.

---

### Post by Crafty Kisses on 2007-06-23
> **John CCC said:**
> Hello, 
I put another 128mb of ram in, and will do more later, but I'm not convinced that it's just the ram issue.  It just happened again, and I was looking at system resources at the time.  I was using around 150mb with only the system monitor running.  I'm wondering if I have other unwanted programs running automatically needlessly.  Any advice on dealing with that?
Also, here is the system log from just when the computer slowed up: Problem happened just around 18:40 or so
```
Jun 23 17:32:22 niamh -- MARK --
Jun 23 17:52:23 niamh -- MARK --
Jun 23 18:12:23 niamh -- MARK --
Jun 23 18:24:23 niamh kernel: [ 4373.244666]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Jun 23 18:24:23 niamh kernel: [ 4373.244684]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
Jun 23 18:24:23 niamh kernel: [ 4373.244694]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Jun 23 18:24:23 niamh kernel: [ 4373.244702]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
Jun 23 18:24:23 niamh kernel: [ 4373.244710]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Jun 23 18:24:23 niamh kernel: [ 4373.244719]  [math_state_restore+26/80] math_state_restore+0x1a/0x50
Jun 23 18:24:23 niamh kernel: [ 4373.244725]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun 23 18:24:23 niamh kernel: [ 4373.244742]  =======================
Jun 23 18:52:23 niamh -- MARK --
Jun 23 19:12:24 niamh -- MARK --
Jun 23 19:32:24 niamh -- MARK --
Jun 23 19:52:24 niamh -- MARK --
Jun 23 20:12:25 niamh -- MARK --
Jun 23 20:32:26 niamh -- MARK --
Jun 23 20:39:52 niamh gconfd (root-17897): starting (version 2.18.0.1), pid 17897 user 'root'
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Jun 23 20:39:52 niamh gconfd (root-17897): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Jun 23 20:39:58 niamh kernel: [12497.187314]  [__report_bad_irq+36/128] __report_bad_irq+0x24/0x80
Jun 23 20:39:58 niamh kernel: [12497.187333]  [__switch_to+198/496] __switch_to+0xc6/0x1f0
Jun 23 20:39:58 niamh kernel: [12497.187341]  [note_interrupt+606/656] note_interrupt+0x25e/0x290
Jun 23 20:39:58 niamh kernel: [12497.187351]  [handle_IRQ_event+48/96] handle_IRQ_event+0x30/0x60
Jun 23 20:39:58 niamh kernel: [12497.187359]  [handle_fasteoi_irq+193/240] handle_fasteoi_irq+0xc1/0xf0
Jun 23 20:39:58 niamh kernel: [12497.187366]  [do_IRQ+64/128] do_IRQ+0x40/0x80
Jun 23 20:39:58 niamh kernel: [12497.187376]  [common_interrupt+35/48] common_interrupt+0x23/0x30
Jun 23 20:39:58 niamh kernel: [12497.187382]  [default_idle+0/96] default_idle+0x0/0x60
```

Also, The system monitor said that I was using 100% of the system resources.  I really want to figure out how to stop this if possible..

For sure you need more RAM, you could try closing more processes too, you can do that by going into terminal and entering:
```
top
```
You can see what processes you don't need then you can end them by typing:
```
kill *process name*
```
Hope this helps. :p

---

### Post by John CCC on 2007-06-23
Sweet.. Systems monitors in my Gnome bar!  Well wadda ya know?

I do like it and I'll be waiting for the next attack.. Till then, I was noticing that the monitor says I'm using about 30-40% of the RAM on programs (sounds about right) and 55% on Cache (is that high?).  It shows practically no free memory at all.  
And, is there a way that I can make sure that the Swap memory is configured correctly? Could that cause such an issue?

---

### Post by Crafty Kisses on 2007-06-23
> **John CCC said:**
> Sweet.. Systems monitors in my Gnome bar!  Well wadda ya know?

I do like it and I'll be waiting for the next attack.. Till then, I was noticing that the monitor says I'm using about 30-40% of the RAM on programs (sounds about right) and 55% on Cache (is that high?).  It shows practically no free memory at all.  
And, is there a way that I can make sure that the Swap memory is configured correctly? Could that cause such an issue?

Yeah, that's kinda high, if you want a all-out system monitor you might want to install this program:
```
sudo apt-get install gkrellm
```
That monitors your CPU every second. :p

---

### Post by John CCC on 2007-06-23
Here is what happens when I run top in the terminal:

```
top - 21:44:04 up 52 min,  2 users,  load average: 0.19, 0.27, 0.28
Tasks:  89 total,   2 running,  87 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  2.0%sy,  0.0%ni, 96.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    385936k total,   368440k used,    17496k free,    14588k buffers
Swap:   746980k total,        0k used,   746980k free,   208684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5354 john      22   0 23612  13m 7440 S  0.7  3.7   0:05.92 python             
 4770 root      15   0  169m  18m 8260 S  0.3  5.0   1:17.27 Xorg               
    1 root      18   0  2908 1840  524 S  0.0  0.5   0:01.31 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    7 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   91 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  116 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  117 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush            
  118 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kswapd0            
  119 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0    
```     
I don't know what *any* of those programs do!  I installed a bunch of updates (around 60) after the first install.  Now, I'm wondering if I didn't include a bunch that weren't necessary that are using system resources.

---

### Post by Crafty Kisses on 2007-06-23
> **John CCC said:**
> Here is what happens when I run top in the terminal:

```
top - 21:44:04 up 52 min,  2 users,  load average: 0.19, 0.27, 0.28
Tasks:  89 total,   2 running,  87 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  2.0%sy,  0.0%ni, 96.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    385936k total,   368440k used,    17496k free,    14588k buffers
Swap:   746980k total,        0k used,   746980k free,   208684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5354 john      22   0 23612  13m 7440 S  0.7  3.7   0:05.92 python             
 4770 root      15   0  169m  18m 8260 S  0.3  5.0   1:17.27 Xorg               
    1 root      18   0  2908 1840  524 S  0.0  0.5   0:01.31 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.05 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper            
    7 root      11  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0          
   31 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid             
   32 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify       
   91 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod            
  116 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush            
  117 root      15   0     0    0    0 S  0.0  0.0   0:00.01 pdflush            
  118 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kswapd0            
  119 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0    
```     
I don't know what *any* of those programs do!  I installed a bunch of updates (around 60) after the first install.  Now, I'm wondering if I didn't include a bunch that weren't necessary that are using system resources.

Don't worry, most of the programs you installed are probably in sleep mode. ;)

---

### Post by John CCC on 2007-06-23
Ok... I've found the culprit..
It just happened as I was messin around in the terminal.  I was going to try and adjust the swap settings to allow for more use of the harddrive if I run too low on ram. But, before I could, wham, the system moves to 100%.  I managed to run    top in the terminal and found what was eating all the resources.  The top line of top looked like this: 
```

PID    User    PR      NI    VIRT   RES   SHR     S   %CPU   %Mem   Command
5        Root    20      -5     0         0       0         R    99%             0%    events/0
 
```
So, do you know what events/0 is? I didn't want to kill it incase it was something really integral.  I just restarted and waited the 10 mins that it takes when you have no sys. resources.

---

### Post by John CCC on 2007-06-23
Well.. I learned a little about events/0.  Doesn't sound friendly or hopeful.   [Linuxquestions]("http://www.linuxquestions.org/questions/showthread.php?t=441837") defined events/0 this way.
> In a 2.6 kernel, events/cpu_number is a mechanism (it replaces the old keventd) for handling low-level requests that need to run asynchronously. All sorts of notifications run through there ... it's very ad hoc. So if you're seeing this "pegging the meter," all it's really telling you is that there's a loop somewhere.
THat's fine, but is there an easier way to determine where the loop is, then unplugging all the hardware piece by piece?  Or, what if it's a program.. there must be some way to tell.

Anyway, there is a wireless card in this machine that I don't use, I read something about turning hardware off in BIOS.. anyone know how I might do that?

---

### Post by sloggerkhan on 2007-06-23
It's fine to have a fair amount of cache memory. It tends to help things respond a bit speedier.

---

### Post by John CCC on 2007-06-24
Thanks for the tip... I won't worry about the cache. But, I need to get this system resources thing sorted out.  
Does anyone know any way of tracking what would be hogging the system resources within "events/0"?  Some sort of advanced system log or something that I could run for couple days.

---

### Post by manobes on 2007-06-24
For what it's worth, I'm getting the same problem.  

events/0 is maxing out the CPU, and I basically can't do anything.

I knew I shouldn't have bothered upgrading.

Does anybody have a suggestion on how to fix this?

---

### Post by vexorian on 2007-06-24
It is most likely another program using asynchronous stuff in a wrong way thus all the blame goest to events/0

It looks like the usual suspect in this case are LAN drivers. But could also be the drivers you just installed according to your first post, I would try disabling some of them and checking if it works all right, also if grub kept the older version of the kernel try booting on it.

---

### Post by manobes on 2007-06-24
Problem appears to be the driver for my wireless card.  The module is rt2500.  

Does anybody have any suggestions or is the computer unusable if I want to have wireless?

---

### Post by s_h_a_d_o_w_s on 2007-06-24
Did you install the wireless driver and then upgrade?

---

### Post by vexorian on 2007-06-25
perhaps a good read: [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3667&postdays=0&postorder=asc&start=0](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3667&postdays=0&postorder=asc&start=0)

---

### Post by John CCC on 2007-07-01
I haven't been able to work on this in a while, but I need to get it fixed as it's driving me nuts.
Anyway, (please bear with me, I'm a nu-bee here), I'm wondering if it's not the wireless drivers on this machine. only thing is... I'm not 100% sure that there is a wireless card in it.  
If I go to the hardware device manager, one of the items listed there is: 
RT2500 802.11g Cardbus/mini-pci
and then under that:
WLAN interface
and Platform Device (eisa.0)

So, I'm assuming it's either in there somewhere, and i don't see it, or it's erroneously listed there (which I doubt).  Can I just disable it somehow and then figure out if the problem starts?

---

### Post by John CCC on 2007-07-01
Ok... I'm a numpty (Scottish word for fool), I found the wireless card and pulled it, so we'll see if the problem occurs again.  I had no way to intentionally set it off, so I'll just have to wait and see.  Ideally, I would like to have the ability to use the card though.  [The serialmonkey thread]("http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=3667&start=45&postdays=0&postorder=asc&highlight=&sid=0f5a019a8469a23748ccedef02332462") referred to above seemed to have a working patch.  Only problem is that it's not exactly a step by step kind of thing.  I'm not exactly sure what to do with the patch..

---

