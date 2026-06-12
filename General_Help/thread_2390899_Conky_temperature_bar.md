---
title: "Conky temperature bar"
date: 2018-05-03
forum: General Help
---

### Post by micmir on 2018-05-03
Hi.
I want to add temperature bar for conky, exaclly like for cpu (bar from green to red).
 Can someone tell my what arguments I have to use in lua script?

---

### Post by NM5TF on 2018-05-03
Your question leaves a little open to interpretation....

such as...

what temp are you trying to read....CPU...MOBO....GPU  ???

what CPU bar are you referencing from red to green....

can you post the conkyrc file you are using.....

maybe this will help.....

```
 vumeter how to ;-)
    label         = name of the widget
    textColour    = colour of text
    pointerColour = colour of pointer
    numberColour  = colour of numbers
    colourStop    = {0,0.7,1}  table with colour stops
    startColour   = {red,0.9},
    midColour     = {brown,0.5},
    endColour     = {lime,0.3},
    unitToShow    = " Max: ${maxuv}", only this variable has variable expansion like in bash
                        the required variables are maxuv and moonState inclose them in ${}
    maxDivisor    = 1,  the widget has support to show 1 to 10 - is anything closer to 10
                        make this 1 or is like moon then 100
    vhstyle       = 'V', style vertical or horizontal

```

here is a sample of my code to generate a color-coded bar to display the UV data.....

```
local w = {}

w.vuData = {
    U = {
        label             = "UV",
        textColour        = {yellow,1},
        pointerColour     = {blue,1},
        numberColour      = {lime,0.8},
        colourStop        = {0,0.7,1},
        startColour       = {red,0.9},
        midColour         = {brown,0.5},
        endColour         = {lime,0.3},
        unitToShow        = " Max: ${maxuv}",
        maxDivisor        = 1,
        vhstyle           = 'V',
        showOriginalValue = 1,
    },

```

maybe it will help you get started...

tommy

---

### Post by micmir on 2018-05-03
Cpu temp.
I prepare a visualisation of what I want to do:

[https://imgur.com/a/axlgP4w](https://imgur.com/a/axlgP4w)

[IMG]https://imgur.com/a/axlgP4w[/IMG]
[IMG]https://imgur.com/a/axlgP4w[/IMG]
In lua file for load cpu bars script look like this,
>                                                     {            
            name="cpu",            
            arg="cpu0",            
            max=100,            
            alarm=80,            
            bg_colour={0x848E84,0.25},            
            fg_colour={0x00ff00,1},            
            alarm_colour={0xff0000,1},            
            x=110,y=223,            
            blocks=29,            
            height=8,width=9,             
            angle=90,            
            smooth=true,            
            cap="e",            
            space=1,            
            skew_y=-30,            
            mid_colour={{0.5,0xffff00,1}}            
            },            
        



and I want to do somthing like this:
> name=**"cputemp"**,arg=**"cpu0temp",**
max=100,
alarm=80,
bg_colour={0x848E84,0.25},
fg_colour={0x00ff00,1},
alarm_colour={0xff0000,1},
x=110,y=223,
blocks=3,
height=8,width=9, 
angle=90,
smooth=true,
cap="e", 
space=1,
skew_y=-30,
mid_colour={{0.5,0xffff00,1}} 
},



but I dont know what parameters i should type in arg section.

---

### Post by NM5TF on 2018-05-03
for the arg.......you might try something like this....don't know if it will work in lua

```
hwmon 1 temp 1 
hwmon 1 temp 2
hwmon 1 temp 3
```

temp1 is for CPU1
temp2 is for CPU2
temp3 is for CPU3

and so forth....

good luck

tommy

---

### Post by micmir on 2018-05-04
Thank you for help, hwmon with temp arg is working :)
I have seven sensors from 2 to 7 are for cpu's.
> {			name="hwmon",
			arg="temp 2",
			max=100,
			alarm=70,
			bg_colour={0x848E84,0.25},
			fg_colour={0x00ff00,1},
			alarm_colour={0xff0000,1},
			x=120,y=141,
			blocks=6,
			height=10,width=10,
			angle=90,
			smooth=true,
			cap="e",
			space=1,
			skew_y=0,
			mid_colour={{0.5,0xffff00,1}}
		},
Image:
[https://imgur.com/smhGR4c](https://imgur.com/smhGR4c)

AGAIN THX TOMMY :)

---

### Post by NM5TF on 2018-05-04
you are most welcome...it's what Linux is all about...people helping people

I would also like to commend your excellent English skills.....

if you go to THREAD TOOLS at top of post, you can mark this solved so other users can find & use it...

tommy

---

