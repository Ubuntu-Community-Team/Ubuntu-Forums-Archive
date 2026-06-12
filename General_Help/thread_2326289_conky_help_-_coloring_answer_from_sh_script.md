---
title: "conky help - coloring answer from sh script"
date: 2016-05-30
forum: General Help
---

### Post by Chen78 on 2016-05-30
hi all 
im a noob to conky and kinda stuck on this one
i have this line in my conkyrc file

Internet:$alignr${execi 10 ~/.pingtest.sh 8.8.8.8}

this line gets one out of 2 answer :  Up or Down

is it possible to color the answer ? using if or another answer check?

---

### Post by QDR06VV9 on 2016-05-30
I usally use this sort of definitions for colors at the top where the text begins.

```
## My colors (suit yourself)
#
color0 White            #FFFFFF
color1 Ivory            #FFFFF0
color2 Ivory2           #EEEEE0
color3 yellow           #CDCDC1
color4 Tan1             #FFA54F
color5 cyan             #EE9A49
color6 Gray             #7E7E7E
color7 AntiqueWhite4    #8B8378
color8 DimGray          #696969
color9 Tomato           #FF6347
# colorX OrangeRed        #FF4500
```

And after I find the shade or color i want I use it something like this.
This just an example
```
${if_existing /proc/net/route tun0}
${color1}Up:${color} ${color3}${upspeed tun0}${color}${alignr}${color1}Down:${color} ${color3}${downspeed tun0}${color}
${upspeedgraph tun0 50,120 FF8800 FF8800}${alignr}${downspeedgraph tun0 50,120 FF8800 FF8800}
${color1}Sent:${color} ${color2}${totalup tun0}${color}${alignr}${color1}Received:${color} ${color2}${totaldown tun0}${color} 
```
Regards

---

### Post by Chen78 on 2016-05-31
thank you i will try that way

---

