---
title: "Help: ATI TV Wonder 200, TV Time, CX2388X"
date: 2007-01-06
forum: General Help
---

### Post by phossal on 2007-01-06
I have an ATI TV Wonder 200, which, in response to lspci, is being reported as:

> Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

I'm not sure where to begin using the hardware. I downloaded TVTime, but I get errors at the command prompt when I try using it:


**[COLOR="#248"]tvtime fails:[/COLOR]**
> bash 3.1 $: tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/phossal/.tvtime/tvtime.xml
videoinput: Can't get tuner info: Invalid argument


**[COLOR="#248"]xawtv fails:[/COLOR]**
> bash 3.1 $: xawtv
This is xawtv-3.95, running on Linux/i686 (2.6.17-10-generic)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  136 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  65
  Current serial number in output stream:  65


Issuing: sudo modprobe bttv and then dmesg produces:
> [17181332.376000] bttv: driver version 0.9.16 loaded
[17181332.376000] bttv: using 8 buffers with 2080k (520 pages) each for capture
***[COLOR="DimGray"][17181526.068000] tuner 0-0060: tuner type not set[/COLOR]***


Any input would be appreciated.

---

### Post by phossal on 2007-01-06
**[COLOR="#248"]Resolution[/COLOR]**

```
cd /etc/modprobe.d/
sudo echo "options cx88xx card=4 tuner=44" > cx88xx
modprobe -r cx8800
modprobe cx8800
```

The ATI TV Wonder Pro 200 isn't properly recognized. I was able to immediately run TVTime after executing these commands.

---

