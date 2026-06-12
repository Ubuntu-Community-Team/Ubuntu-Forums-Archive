---
title: "Detect Palm on a Ubuntu Lenovo ThinkPad Lenovo Laptop with a Synaptics touchpad"
date: 2016-09-25
forum: General Help
---

### Post by Salil_Surendran on 2016-09-25
Hello,
   I am unable to enable Palm Detection on my Ubuntu Lenovo ThinkPad Lenovo Laptop with a Synaptics touchpad. I have tried the following commands:


1. xinput list
2. xinput list-props "{id}"
3. xinput set-prop "{id}" "Synaptics Palm Dimensions" 5, 5
4. xinput set-prop {id} "Synaptics Palm Detection" 1


I tested my palm against the touchpad and the cursor still moved. I also tried this 'synclient PalmDetect=1 PalmMinWidth=xx PalmMinZ=yy' but this also didn't work.


What am I missing? Are the commands incorrect and what would be the right values? I am setting these values on a terminal and then testing against my touchpad. That should work right? Or do I have to restart my system each time for it to take effect? I have set these values on startup also

---

