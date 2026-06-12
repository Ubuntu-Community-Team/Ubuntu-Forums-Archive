---
title: "Dual Monitors separate X sessions?"
date: 2016-05-24
forum: General Help
---

### Post by pasjrwoctx-8 on 2016-05-24
Anyone here know how to create a separate X session in ubuntu 16.04 so that I can use one monitor to work on, and the other to watch something eles.  Without the second monitor changing virtual desktops while I change them on the first display?  I used to be able to do this in 12.04, but now the nvidia-settings control display is undefined and I have no clue how to us it.

Here is my hardware if you need it.
```
root@woctxphotog-Dell-XPS420:~# lshw -C video                                                                                                                                                    
  *-display                                                                                                                                                                                      
       description: VGA compatible controller                                                                                                                                                    
       product: G92 [GeForce 8800 GT]                                                                                                                                                            
       vendor: NVIDIA Corporation                                                                                                                                                                
       physical id: 0                                                                                                                                                                            
       bus info: pci@0000:01:00.0                                                                                                                                                                
       version: a2                                                                                                                                                                               
       width: 64 bits                                                                                                                                                                            
       clock: 33MHz                                                                                                                                                                              
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom                                                                                                                    
       configuration: driver=nouveau latency=0                                                                                                                                                   
       resources: irq:28 memory:fc000000-fcffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc80(size=128) memory:fde00000-fde1ffff 
```    
```
root@woctxphotog-Dell-XPS420:~# xrandr                                                                                                                                                                                                                                          
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192                                                                                                                                                                                                           
DVI-I-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm                                                                                                                                                                                
   1920x1080     60.00*+                                                                                                                                                                                                                                                        
   1680x1050     59.88                                                                                                                                                                                                                                                          
   1280x1024     60.02                                                                                                                                                                                                                                                          
   1440x900      59.90                                                                                                                                                                                                                                                          
   1280x800      59.91                                                                                                                                                                                                                                                          
   1152x864      75.00                                                                                                                                                                                                                                                          
   1280x720      60.00                                                                                                                                                                                                                                                          
   1024x768      70.07    60.00                                                                                                                                                                                                                                                 
   800x600       60.32    56.25                                                                                                                                                                                                                                                 
   640x480       66.67    60.00                                                                                                                                                                                                                                                 
   720x400       70.08                                                                                                                                                                                                                                                          
DVI-I-2 connected 1366x768+1920+312 (normal left inverted right x axis y axis) 410mm x 230mm                                                                                                                                                                                    
   1366x768      59.79*+                                                                                                                                                                                                                                                        
   1280x960      60.00                                                                                                                                                                                                                                                          
   1152x864      75.00                                                                                                                                                                                                                                                          
   1280x720      60.00                                                                                                                                                                                                                                                          
   1024x768      75.08    70.07    66.01    60.00                                                                                                                                                                                                                               
   832x624       74.55                                                                                                                                                                                                                                                          
   800x600       72.19    75.00    60.32    56.25                                                                                                                                                                                                                               
   640x480       75.00    72.81    66.67    60.00
```

---

### Post by yetimon_64 on 2016-05-24
> **pasjrwoctx-8 said:**
> Anyone here know how to create a separate X session in ubuntu 16.04 so that I can use one monitor to work on, and the other to watch something eles.  Without the second monitor changing virtual desktops while I change them on the first display?  I used to be able to do this in 12.04, but now **the nvidia-settings control display is undefined** and I have no clue how to us it.

Here is my hardware if you need it.
[FONT=monospace][COLOR=#000000]root@woctxphotog-Dell-XPS420:~# lshw -C video                                                                                                                                                    [/COLOR]
  *-display                                                                                                                                                                                      
       description: VGA compatible controller                                                                                                                                                    
       product: G92 [GeForce 8800 GT]                                                                                                                                                            
       vendor: NVIDIA Corporation                                                                                                                                                                
       physical id: 0                                                                                                                                                                            
       bus info: pci@0000:01:00.0                                                                                                                                                                
       version: a2                                                                                                                                                                               
       width: 64 bits                                                                                                                                                                            
       clock: 33MHz                                                                                                                                                                              
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom                                                                                                                    
       configuration: **driver=nouveau** latency=0                                                                                                                                                   
       resources: irq:28 memory:fc000000-fcffffff memory:d0000000-dfffffff memory:fa000000-fbffffff ioport:dc80(size=128) memory:fde00000-fde1ffff     
[/FONT][FONT=monospace][COLOR=#000000]root@woctxphotog-Dell-XPS420:~# xrandr                                                                                                                                                                                                                                          [/COLOR]
Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 8192 x 8192                                                                                                                                                                                                           
DVI-I-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 521mm x 293mm                                                                                                                                                                                
   1920x1080     60.00*+                                                                                                                                                                                                                                                        
   1680x1050     59.88                                                                                                                                                                                                                                                          
   1280x1024     60.02                                                                                                                                                                                                                                                          
   1440x900      59.90                                                                                                                                                                                                                                                          
   1280x800      59.91                                                                                                                                                                                                                                                          
   1152x864      75.00                                                                                                                                                                                                                                                          
   1280x720      60.00                                                                                                                                                                                                                                                          
   1024x768      70.07    60.00                                                                                                                                                                                                                                                 
   800x600       60.32    56.25                                                                                                                                                                                                                                                 
   640x480       66.67    60.00                                                                                                                                                                                                                                                 
   720x400       70.08                                                                                                                                                                                                                                                          
DVI-I-2 connected 1366x768+1920+312 (normal left inverted right x axis y axis) 410mm x 230mm                                                                                                                                                                                    
   1366x768      59.79*+                                                                                                                                                                                                                                                        
   1280x960      60.00                                                                                                                                                                                                                                                          
   1152x864      75.00                                                                                                                                                                                                                                                          
   1280x720      60.00                                                                                                                                                                                                                                                          
   1024x768      75.08    70.07    66.01    60.00                                                                                                                                                                                                                               
   832x624       74.55                                                                                                                                                                                                                                                          
   800x600       72.19    75.00    60.32    56.25                                                                                                                                                                                                                               
   640x480       75.00    72.81    66.67    60.00   
[/FONT]
Note what I have bolded in your output. You need to go to the Additional Drivers application in Dash and install the relevant Nvidia drivers for your card. You are currently running on the nouveau drivers by that output. Then you should get access to the nvidia settings you mention.

Ediit: sorry I just noticed you are on kubuntu, I was assuming Ubuntu when I answered. You still need to install the nvidia drivers though I don't know how that happens in kubuntu. Dash is in Ubuntu only as far as I understand it. Regards, yeti.

---

### Post by pasjrwoctx-8 on 2016-05-24
I tried adding the Relevant drivers.  Nvidia-settings is the same, it has no options.  Very different than it used to be.  That is why I am here asking for help.

---

### Post by yetimon_64 on 2016-05-24
> **pasjrwoctx-8 said:**
> I tried adding the Relevant drivers... 
Ah, I see. Then you have a different problem if you have already tried. How did you try to add them in Kubuntu ? 

Going by the output you originally posted you are still running the nouveau driver. 
Adding the nvidia drivers (from Additional drivers or its counterpart in kubuntu) would normally change that configuration line I bolded in my last post from [FONT=monospace]"driver=nouveau[/FONT]" to "driver=nvidia". Once you get the configuration line to change to nvidia, then the nvidia settings program should work.

Letting us know how you tried to add the drivers may possibly give some clues to what is happening.

---

### Post by pasjrwoctx-8 on 2016-05-25
Here is how I tried other drivers.  FYI They all provide the same deal for controlling Nvidia-settings [[IMG]http://woctxphotog.com/UbunutIssues/MyDesktop2.jpg[/IMG]]("http://woctxphotog.com/UbunutIssues/MyDesktop2.jpg")  this is what I always see when I try to use it [[IMG]http://woctxphotog.com/UbunutIssues/MyDesktop3.jpg[/IMG]]("http://woctxphotog.com/UbunutIssues/MyDesktop3.jpg")

---

