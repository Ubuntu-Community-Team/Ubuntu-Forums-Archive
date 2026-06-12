---
title: "Amarok freezes.."
date: 2008-03-04
forum: General Help
---

### Post by geo909 on 2008-03-04
Hello everybody,
I have a situation here:
Every time I boot up my computer and try to run amarok for the first time,
it freezes when I  try to play a song (in any way. Double click on a song in the now-playing list, press the 'play' button or do "amarok -p" on a terminal). The strange thing is that the second time I open amarok (after I kill the freezed first one) everything is normal, I can play any song, no freezes, no hangups no "force quit"..


Does anyone knows what happens?!

Here is the output if I open Amarok the first time from a terminal:

```
jorge@jorge-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098490 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8098490 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QColor::setRgb: RGB parameter(s) out of range
jorge@jorge-desktop:~$ kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
```

Then I try to play a song. On the same terminal:
```
amarok -p
```

As always, amarok freezes and here's what I get:
```
amarok -p
DCOP aborting call from 'anonymous-5626' to 'amarok'
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x2400021
jorge@jorge-desktop:~$ DCOP aborting call from 'kded' to 'klauncher'
kded: ERROR: : couldn't create slave : Cannot talk to klauncher


```

That's so frustrating! I even tried to reinstall amarok but the problem doesn't get fixed..
Please, any ideas?
Thank you in advance

---

### Post by geo909 on 2008-03-04
*bump*

---

### Post by geo909 on 2008-03-05
Nobody?

Anybody?!

---

### Post by cszikszoy on 2008-03-05
I have the same problem.  The only way I've been able to "fix" it is to kill -15 amarok's PID and then restart it :(

I would *LOVE* to get this fixed because it is quite annoying.

---

### Post by wayne040576 on 2008-03-05
I just started getting the same problem tonight. Not sure what's going on. I don't have time to look into it tonight so I will have to wait until tomorrow.

---

### Post by Crafty Kisses on 2008-03-05
> **geo909 said:**
> Nobody?

Anybody?!

Hmmm, lets see what you have running at the time of the freeze.
Post the following output:
```
top
```

---

### Post by wayne040576 on 2008-03-05
Well this is mine anyways:

```
 [7m  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND             [m (B [39;49m [K
 [m (B 7409 wayne     15   0  217m  90m  27m S    6  4.5   3:08.08 firefox-bin         [m (B [39;49m
 [m (B 7642 wayne     15   0 20280 7388 6476 S    4  0.4   0:04.22 amarok              [m (B [39;49m
 [m (B [m (B 7650 wayne     15   0  2488 1100  792 R    4  0.1   0:00.02 top                 [m (B [39;49m
 [m (B 2465 root      11  -5     0    0    0 S    2  0.0   0:00.67 scsi_eh_3           [m (B [39;49m
 [m (B    1 root      21   0  2948 1856  532 S    0  0.1   0:02.02 init                [m (B [39;49m
 [m (B    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd            [m (B [39;49m
 [m (B    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0         [m (B [39;49m
 [m (B    4 root      34  19     0    0    0 S    0  0.0   0:00.01 ksoftirqd/0         [m (B [39;49m
 [m (B    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0          [m (B [39;49m
 [m (B    6 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/1         [m (B [39;49m
 [m (B    7 root      34  19     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1         [m (B [39;49m
 [m (B    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1          [m (B [39;49m
 [m (B    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2         [m (B [39;49m
 [m (B   10 root      34  19     0    0    0 S    0  0.0   0:00.03 ksoftirqd/2         [m (B [39;49m
 [m (B   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2          [m (B [39;49m
 [m (B   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3         [m (B [39;49m
 [m (B   13 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3         [m (B [39;49m
```

---

### Post by wayne040576 on 2008-03-05
ok. For me it seems that the ipod-convienience package is not working properly. Amarok is freezing because it tries to run the ipod-touch-mount command and fails. 
The error given is 

ssh: : Name or service not known


Not sure what is up with my ssh.

---

### Post by cszikszoy on 2008-03-05
The ipod service causes your amarok to freeze when you try to play a song or when it starts up?

For me it amarok starts just fine, it just freezes when you try to play a file.

---

### Post by wayne040576 on 2008-03-06
> **cszikszoy said:**
> The ipod service causes your amarok to freeze when you try to play a song or when it starts up?

For me it amarok starts just fine, it just freezes when you try to play a file.

Yeah it seems that there is a bug in the scripts that are used to handle the ipod touch. It causes Amarok to freeze on startup. I didn't even get a chance to play a song. 

I ran an update yesterday it the ipod scripts were updated. I may just need to reconfigure them. Basically the ipod touch is mounted using ssh over a wifi connection and it looks like the update messed up my settings. I got amarok to start late last night but didn't have time to test playing files. I will test it later today.

---

### Post by geo909 on 2008-03-06
> **Codename said:**
> Hmmm, lets see what you have running at the time of the freeze.
Post the following output:
```
top
```

Ok, first of all thanks for taking the time to answer this!
Here's what's going on BEFORE the freeze:

```
jorge@jorge-desktop:~$ top

top - 16:36:04 up 3 min,  2 users,  load average: 0.34, 0.45, 0.20
Tasks: 110 total,   3 running, 107 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.3%us,  0.5%sy,  0.0%ni, 95.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1027200k total,   527092k used,   500108k free,    19104k buffers
Swap:   899600k total,        0k used,   899600k free,   268080k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5615 jorge     15   0  149m  50m  20m R    5  5.0   0:17.09 firefox-bin        
 5158 root      15   0  351m  22m 6392 R    4  2.2   0:07.26 Xorg               
 5571 jorge     15   0 10220 3780 3044 S    0  0.4   0:00.42 conky              
 5656 jorge     15   0 74032  20m  11m S    0  2.0   0:00.70 gnome-terminal     
    1 root      18   0  2948 1852  532 S    0  0.2   0:01.31 init               
    2 root      12  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      11  -5     0    0    0 S    0  0.0   0:00.00 khelper            
   31 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   32 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
```

Ok. Now I press 'play' and amarok freezes as always.
I get this now:
```
jorge@jorge-desktop:~$ top

top - 16:38:10 up 5 min,  2 users,  load average: 0.23, 0.36, 0.19
Tasks: 109 total,   1 running, 108 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.6%sy,  0.0%ni, 97.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1027200k total,   531184k used,   496016k free,    19376k buffers
Swap:   899600k total,        0k used,   899600k free,   270156k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5158 root      15   0  352m  23m 6672 S    2  2.3   0:11.22 Xorg                                                                                            
 5615 jorge     16   0  150m  51m  20m S    2  5.2   0:21.38 firefox-bin                                                                                     
 5448 jorge     15   0 18104  10m 7604 S    1  1.0   0:00.98 metacity                                                                                        
 5571 jorge     15   0 10220 3780 3044 S    1  0.4   0:00.65 conky                                                                                           
 5709 jorge     15   0  2364 1160  876 R    0  0.1   0:00.07 top                                                                                             
    1 root      17   0  2948 1852  532 S    0  0.2   0:01.31 init                                                                                            
    2 root      12  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                     
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                     
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                      
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0                                                                                        
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1                                                                                        
   11 root      11  -5     0    0    0 S    0  0.0   0:00.00 khelper                                                                                         
   31 root      16  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0                                                                                       
   32 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1                                                                                       
   33 root      12  -5     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                          
   34 root      13  -5     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                    
  126 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod                                                                                         
  151 root      16   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  152 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush                                                                                         
  153 root      13  -5     0    0    0 S    0  0.0   0:00.00 kswapd0                                                                                         
  204 root      13  -5     0    0    0 S    0  0.0   0:00.00 aio/0                                                                                           
  205 root      14  -5     0    0    0 S    0  0.0   0:00.00 aio/1                                                                                           
 2037 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd                                                                                   
 2038 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd                                                                                           
 2065 root      10  -5     0    0    0 S    0  0.0   0:00.00 ata/0                                                                                           
 2066 root      10  -5     0    0    0 S    0  0.0   0:00.01 ata/1                                                                                           
 2077 root      17  -5     0    0    0 S    0  0.0   0:00.00 ata_aux                                                                                         
 2198 root      10  -5     0    0    0 S    0  0.0   0:00.02 scsi_eh_0                                                                                       
 2199 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1                                                                                       
 2236 root      10  -5     0    0    0 S    0  0.0   0:00.03 scsi_eh_2                                                                                       
 2237 root      10  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_3                                                                                       
 2533 root      10  -5     0    0    0 S    0  0.0   0:00.01 kjournald                                                                                       
 2738 root      14  -4  3048 1396  408 S    0  0.1   0:00.34 udevd                                                                                           
 3743 root      16  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused                                                                                       
 4098 root      15   0  3784  956  572 S    0  0.1   0:00.00 mount.ntfs                                                                                      
 4101 root      15   0  3908 1156  588 S    0  0.1   0:00.46 mount.ntfs                                                                                      
 4340 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty                                                                                           
 4341 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty                                                                                           
 4343 root      18   0  1696  516  448 S    0  0.1   0:00.00 getty                                                                                           
 4345 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty                                                                                           
 4347 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty                                                                                           
 4348 root      18   0  1696  520  448 S    0  0.1   0:00.00 getty  
```


Any ideas?

---

### Post by geo909 on 2008-03-07
anybody?

---

### Post by geo909 on 2008-03-08
*Boom-dim-dilly BUMP*

---

### Post by geo909 on 2008-03-10
Nobody?
Any additional info needed?

---

### Post by NightwishFan on 2008-03-10
Perhaps get the latest amarok. Well the main page has a tar see if It is the same version as the one you have.

You can also try to completely remove it in synaptic and then install via command line.
sudo apt-get update
sudo apt-get install amarok

---

### Post by smilz247 on 2008-06-26
I have the same problem, but I don't own an ipod touch... just a 5th gen ipod nano. :???:

---

