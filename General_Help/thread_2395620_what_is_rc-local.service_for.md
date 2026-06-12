---
title: "what is rc-local.service for?"
date: 2018-07-04
forum: General Help
---

### Post by arapaho on 2018-07-04
It slows my system start:
```
[FONT=monospace][COLOR=#000000]systemd-analyze critical-chain                 [/COLOR]
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @2.228s
&#9492;&#9472;multi-user.target @2.228s
  &#9492;&#9472;getty.target @2.207s
    &#9492;&#9472;getty@tty1.service @2.207s
      &#9492;&#9472;[COLOR=#FF5454]**rc-local.service @2.031s +175ms**[/COLOR][COLOR=#000000][/COLOR]
        &#9492;&#9472;network-online.target @2.009s
          &#9492;&#9472;network.target @2.009s

[/FONT]
```

```
[FONT=monospace][COLOR=#000000]cat /etc/rc.local                                                                       [/COLOR]
#!/bin/sh -e                                                                                                      
#                                                                                                
# rc.local       
#                                                                                                                  
# This script is executed at the end of each multiuser runlevel.                               
# Make sure that the script will "exit 0" on success or any other 
# value on error.                                                                        
#                                                                                                                  
# In order to enable or disable this script just change the execution 
# bits. 
#           
# By default this script does nothing.                                                                             
**echo 1 > /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.1/remove**
exit 0

[/FONT]
```
I have no idea what is this line for. Can I hash it or remove?

---

### Post by Holger_Gehrke on 2018-07-04
The only hit I got when searching for this line on duckduckgo said it's for disabling hdmi sound output, but also said that the path was specific to the machine; so the only thing I can say for sure about this line is that it's meant to disable some device connected by pci to the rest of the system.

Holger

---

### Post by arapaho on 2018-07-04
Ok. Thank you. Now I remember. I did it to remove nvidia entries in sound menu:
[https://www.kubuntuforums.net/showthread.php/60791-TIP-How-to-remove-Nvidia-HDMI-Audio?highlight=remove+nvidia+hdmi](https://www.kubuntuforums.net/showthread.php/60791-TIP-How-to-remove-Nvidia-HDMI-Audio?highlight=remove+nvidia+hdmi)

I also found how to stop it:
[https://ubuntuforums.org/showthread.php?t=1671041](https://ubuntuforums.org/showthread.php?t=1671041)

---

### Post by SeijiSensei on 2018-07-04
Next time you might consider adding a comment line, especially for obscure commands like that one.

---

### Post by Holger_Gehrke on 2018-07-04
> **SeijiSensei said:**
> Next time you might consider adding a comment line, especially for obscure commands like that one.

And it's a good idea to put some constant text -- I use my initials -- and the date in the comment. That way you can just grep the files in /etc for that text to find all the ones you changed manually (which will be useful when prepararing for a backup before a new installation or upgrade).

Holger

---

