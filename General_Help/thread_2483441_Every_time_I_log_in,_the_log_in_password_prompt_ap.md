---
title: "Every time I log in, the log in password prompt appears on a different screen."
date: 2023-01-30
forum: General Help
---

### Post by patrickfeeney on 2023-01-30
Hello,
I installed Xubuntu a couple of days ago. It's working fine.
My question is why does the log in prompt appear on a different screen each time I log in? I have 3 screens.
I have set my center display as my main one already.

           `-/osyhddddhyso/-`              patrick@patrick-OptiPlex-7020 
        .+yddddddddddddddddddy+.           ----------------------------- 
      :yddddddddddddddddddddddddy:         OS: Xubuntu 22.04.1 LTS x86_64 
    -yddddddddddddddddddddhdddddddy-       Host: OptiPlex 7020 00 
   odddddddddddyshdddddddh`dddd+ydddo      Kernel: 5.15.0-58-generic 
 `yddddddhshdd-   ydddddd+`ddh.:dddddy`    Uptime: 30 mins 
 sddddddy   /d.   :dddddd-:dy`-ddddddds    Packages: 1980 (dpkg), 7 (snap) 
:ddddddds    /+   .dddddd`yy`:ddddddddd:   Shell: bash 5.1.16 
sdddddddd`    .    .-:/+ssdyodddddddddds   Resolution: 1280x1024, 1280x1024, 19 
ddddddddy                  `:ohddddddddd   DE: Xfce 4.16 
dddddddd.                      +dddddddd   WM: Xfwm4 
sddddddy                        ydddddds   WM Theme: Greybird 
:dddddd+                      .oddddddd:   Theme: Greybird [GTK2/3] 
 sdddddo                   ./ydddddddds    Icons: elementary-xfce-darker [GTK2/ 
 `yddddd.              `:ohddddddddddy`    Terminal: xfce4-terminal 
   oddddh/`      `.:+shdddddddddddddo      Terminal Font: Monospace 12 
    -ydddddhyssyhdddddddddddddddddy-       CPU: Intel i7-4790 (8) @ 4.000GHz 
      :yddddddddddddddddddddddddy:         GPU: NVIDIA GeForce GTX 1660 SUPER 
        .+yddddddddddddddddddy+.           Memory: 2152MiB / 15940MiB 
           `-/osyhddddhyso/-`
                                                                   
                                                                   
I hope I explained myself properly.
Thanks in advance,
Patrick

---

### Post by TheFu on 2023-01-30
[https://ubuntuforums.org/showthread.php?t=2409072](https://ubuntuforums.org/showthread.php?t=2409072) reads like the same issue.

---

### Post by patrickfeeney on 2023-01-31
Hello, thanks for your response. I'll give it a look and tell you if it works. Cheers

---

### Post by patrickfeeney on 2023-01-31
> **TheFu said:**
> [https://ubuntuforums.org/showthread.php?t=2409072](https://ubuntuforums.org/showthread.php?t=2409072) reads like the same issue.
Thanks. I'll give it a look.
Cheers.

---

### Post by patrickfeeney on 2023-01-31
> **TheFu said:**
> [https://ubuntuforums.org/showthread.php?t=2409072](https://ubuntuforums.org/showthread.php?t=2409072) reads like the same issue.
Hello, I tried to run the first command which is:

sudo cp ~/.config/monitors.xml ~gdm/.config/monitors.xmlAnd I got this output:
p: cannot stat '/home/patrick/.config/monitors.xml': No such file or directory

---

### Post by TheFu on 2023-01-31
> **patrickfeeney said:**
> Hello, I tried to run the first command which is:

sudo cp ~/.config/monitors.xml ~gdm/.config/monitors.xmlAnd I got this output:
p: cannot stat '/home/patrick/.config/monitors.xml': No such file or directory

But that isn't the first step. In the first step it says how to create that file using another tool.  Did you do that?
I don't have nvidia stuff on my systems anymore (as of about a month ago) and I don't have 22.04 with xubuntu either, so I can't try it myself.

---

### Post by #&amp;thj^% on 2023-01-31
> **TheFu said:**
> But that isn't the first step. In the first step it says how to create that file using another tool.  Did you do that?
I don't have nvidia stuff on my systems anymore (as of about a month ago) and I don't have 22.04 with xubuntu either, so I can't try it myself.
+1
The path needs to read like:
```
ls '/home/me/.config/monitors.xml' 
/home/me/.config/monitors.xml

```
Or
```
ls ~/.config/monitors.xml
```
Don't copy mine it will break yours:
```
cat '/home/me/.config/monitors.xml' 
<monitors version="2">
  <configuration>
    <logicalmonitor>
      <x>0</x>
      <y>0</y>
      <scale>1</scale>
      <primary>yes</primary>
      <monitor>
        <monitorspec>
          <connector>DP-2</connector>
          <vendor>BOE</vendor>
          <product>0x08e8</product>
          <serial>0x00000000</serial>
        </monitorspec>
        <mode>
          <width>1920</width>
          <height>1080</height>
          <rate>120.002</rate>
        </mode>
      </monitor>
    </logicalmonitor>
    <logicalmonitor>
      <x>1920</x>
      <y>0</y>
      <scale>1</scale>
      <monitor>
        <monitorspec>
          <connector>HDMI-0</connector>
          <vendor>SAM</vendor>
          <product>SAMSUNG</product>
          <serial>0x01000e00</serial>
        </monitorspec>
        <mode>
          <width>4096</width>
          <height>2160</height>
          <rate>59.940</rate>
        </mode>
      </monitor>
    </logicalmonitor>
  </configuration>
</monitors>


```
Sorry for the drive by, and you need to set your monitors first in "Settings" then copy it over,.... it looks like you just picked what you wanted, and did not follow it completely. All details matter.

---

