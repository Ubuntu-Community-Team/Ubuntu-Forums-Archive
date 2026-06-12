---
title: "Ubuntu 14.04 Sound Not Working"
date: 2016-07-19
forum: General Help
---

### Post by khan3 on 2016-07-19
Hey,

My sound is not working. 

After running [COLOR=#333333][FONT=UbuntuMono]

lspci -v | grep -A7 -i "audio" 

[/FONT][/COLOR]Nothing is being displayed, it seems to be my sound card is not present / or being recognized.

I have a Realtek 2 Channel High Definition Audio sound card in my laptop.

I'm not sure what else i can do. Can someone help me narrow this problem i want to know If its the actual hardware sound card if so then ill put in a request for RMA.

thanks.

---

### Post by khan3 on 2016-07-19
Bump - I added some more information.

---

### Post by khan3 on 2016-07-28
Hey i could still do with some help on this.

---

### Post by QDR06VV9 on 2016-07-28
Hey we could use some more information in order to help you.;)
Lets start with this, return the output of this
```
inxi -Fxz
```

---

### Post by howefield on 2016-07-28
What's the output of ... 

```
sudo aplay -l
```

---

