---
title: "Madcatz RAT 3 Mouse issues"
date: 2013-08-12
forum: General Help
---

### Post by niel2 on 2013-08-12
I'm having issues with configuring my Madcatz RAT 3 Mouse with Ubuntu 13.04. It's like the mouse is having issues with switching between windows. Movement works fine though.

I have added this to my xorg.conf but it still doesn't work:

```
Section "InputClass"
    Identifier      "Mouse Remap"
    MatchProduct    "Madcatz Mad Catz R.A.T.3 Mouse"
    MatchDevicePath "/dev/input/event*"
    Option      "ButtonMapping" "1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 0 0 0"
EndSection
```

Here is some more info.

From xinput list:

```
Madcatz Mad Catz R.A.T.3 Mouse              id=13   [slave  pointer  (2)]

```

More details:

```
niel@niel-VPCF13M1E:~$ xinput query-state 13
2 classes :
ButtonClass
    button[1]=up
    button[2]=up
    button[3]=up
    button[4]=up
    button[5]=up
    button[6]=up
    button[7]=up
    button[8]=up
    button[9]=up
    button[10]=down
    button[11]=up
    button[12]=up
    button[13]=up
    button[14]=up
    button[15]=up
    button[16]=up
    button[17]=up
    button[18]=up
ValuatorClass Mode=Relative Proximity=In
    valuator[0]=512
    valuator[1]=762
    valuator[2]=-7
```

cat /proc/bus/input/devices

```
I: Bus=0003 Vendor=0738 Product=1703 Version=0100
N: Name="Madcatz Mad Catz R.A.T.3 Mouse"
P: Phys=usb-0000:05:00.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/usb3/3-1/3-1:1.0/input/input18
U: Uniq=
H: Handlers=mouse3 event15 
B: PROP=0
B: EV=17
B: KEY=3ff0000 0 0 0 0
B: REL=103
B: MSC=10

```
Anyone knows how to fix this? Thanks!

---

### Post by niel2 on 2013-08-14
Bump.

---

### Post by samuel-taylor on 2013-08-21
I'm having this issue too.

Did you manage to solve it?

Thanks
Sam

---

### Post by niel2 on 2013-08-30
No, still waiting for someone to help me.

---

### Post by samuel-taylor on 2013-09-07
I managed to get the mouse working just fine with adding this section to my xorg.conf

```

Section "InputClass"    Identifier "Mouse Remap"
    MatchProduct "Madcatz Mad Catz R.A.T.3 Mouse"
    MatchDevicePath "/dev/input/event*"
    Option "ButtonMapping" "1 2 3 4 5 6 7 8 0 0 0 0 0 0 0 0 0 0 0"
EndSection

```

Hope it helps

Thanks
Sam

---

### Post by Starscrye on 2013-11-17
> **samuel-taylor said:**
> I managed to get the mouse working just fine with adding this section to my xorg.conf

```

Section "InputClass"    Identifier "Mouse Remap"
    MatchProduct "Madcatz Mad Catz R.A.T.3 Mouse"
    MatchDevicePath "/dev/input/event*"
    Option "ButtonMapping" "1 2 3 4 5 6 7 8 0 0 0 0 0 0 0 0 0 0 0"
EndSection

```

Hope it helps

Thanks
Sam

This worked perfectly for me, thanks for the post. Using Linux Mint 15 32-bit

---

### Post by vcf35 on 2014-02-07
> **samuel-taylor said:**
> I managed to get the mouse working just fine with adding this section to my xorg.conf

```

Section "InputClass"    Identifier "Mouse Remap"
    MatchProduct "Madcatz Mad Catz R.A.T.3 Mouse"
    MatchDevicePath "/dev/input/event*"
    Option "ButtonMapping" "1 2 3 4 5 6 7 8 0 0 0 0 0 0 0 0 0 0 0"
EndSection

```

Hope it helps

Thanks
Sam


Thank you so much ! My new Madcatz Mad Catz R.A.T.3 Mouse (for instance) works now.
Olivier.

---

