---
title: "set sound volume command"
date: 2013-05-29
forum: General Help
---

### Post by spiritech on 2013-05-29
i am using this command to try and set my sound volume.

```
pactl set-sink-volume 0 20%
```

it worked on 12.10. i have 13.04 installed now, and the command no longer works.

spiritech

---

### Post by Juniorr on 2013-05-29
Hi.

If I may ask here: Does this command allow you to hear your own microphone?

---

### Post by spiritech on 2013-05-29
> **Juniorr said:**
> Hi.

If I may ask here: Does this command allow you to hear your own microphone?

no.

---

### Post by spiritech on 2013-05-30
suppose i better throw a question in here. 

how do i set the main volume through the command line?

---

### Post by CaptainMark on 2013-05-31
I use ```
amixer -c 0 -- set Master 20%
```

---

### Post by spiritech on 2013-05-31
> **CaptainMark said:**
> I use ```
amixer -c 0 -- set Master 20%
```


i have tried this, aswell as the other numerous amixer options i have found around the net. i have luanched the amixer interface in the terminal and still no joy. maybe i need a pulse-audio option. 

also is there a reason why the original command i posted no longer works, as it worked on my previous install. maybe the device number is wrong, how can i check this?

---

### Post by spiritech on 2013-05-31
solved, the device was wrong should have been 1 not 0.

```
pactl -- set-sink-volume 1 20%
```

thank you for your help anyway.

---

### Post by pqwoerituytrueiwoq on 2013-05-31
use this to get part of the next command
```
pacmd dump | grep set-sink-volume | awk '{print $2}'
```
```
pactl set-sink-volume $SINK_NAME_FROM_ABOVE 0x5b19
```

you can try this script
[http://pastebin.com/DxDL7Ldn](http://pastebin.com/DxDL7Ldn)

---

