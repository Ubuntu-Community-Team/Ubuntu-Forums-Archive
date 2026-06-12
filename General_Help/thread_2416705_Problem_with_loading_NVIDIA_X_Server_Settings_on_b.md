---
title: "Problem with loading NVIDIA X Server Settings on boot"
date: 2019-04-13
forum: General Help
---

### Post by thatdoku on 2019-04-13
Hello, I am new to ubuntu and linux in general. I have a problem with loading my NVIDIA X Server Settings (Gamma/ Brightness) on boot. I am using ubuntu 18.10 with NVIDIA X driver version 390.116.
 I have in Startup Application Preferences Startup Program with command "sh -c '/usr/bin/nvidia-settings --load-config-only'" but ubuntu never loads it on boot. To get It to work I have to manually run the command in terminal or run the NVIDIA X Server application and It's starting to get a bit annoying.

---

### Post by pqwoerituytrueiwoq on 2019-04-13
if by boot you mean after login
try putting this as a startup option
```
sh -c 'sleep 3 && /usr/bin/nvidia-settings --load-config-only'
```
this will delay it 3 seconds, you may need more or less than 3 depending on the hardware

---

### Post by thatdoku on 2019-04-14
Tried many different values ranging from 1s to 10s. Still nothing. I think the problem is that GNOME always overrides it. I see the correct brightness and gamma get set during the boot sequence but when I log in It's back to default.

---

### Post by him610 on 2019-04-14
I don't know if this will work or not, but it may.
Have you tried adjusting the Gamma/Brightness to the desired settings then going back to the 'X Server Display Configuration' page followed by clicking *Save to X Configuration File* at the bottom of the page?

---

### Post by thatdoku on 2019-04-15
Yes, I have saved it that way. When I run the application the correct values are applied. The problem is with applying them at login...

---

### Post by him610 on 2019-04-15
Okay, I played with this a little bit. In post #4, I suggested saving the configuration to file. It gets saved as [I].nvidia-settings-rc
[/I] in the directory of your choice. (By the way, there is a  *.nvidia-settings-rc* located in the home directory.) In my case, I chose *~/tmp*. See if you can use this command-plus-option, modified to use your chosen save directory.
```
 /usr/bin/nvidia-settings --config=~/tmp/.nvidia-settings-rc
 
```

Here is an extract from [I]man /usr/bin/nvidia-settings
[/I]
```

nvidia-settings(1)  
...
--config=CONFIG
              Use the configuration file CONFIG rather than the default ~/.nvidia-settings-rc
...
-l, --load-config-only
              Load  the  configuration  file, send the values specified therein to the X server, and exit.
              This mode of operation is useful to place in your xinitrc file, for example.

```
Did you modify your  *xinitrc* file?

---

