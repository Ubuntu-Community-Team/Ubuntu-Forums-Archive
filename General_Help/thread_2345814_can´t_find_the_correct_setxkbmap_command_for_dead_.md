---
title: "can´t find the correct setxkbmap command for dead keys"
date: 2016-12-08
forum: General Help
---

### Post by saroele on 2016-12-08
Hi,

I´m trying to change the keyboard layout on my laptop to us international. I have two wishes: 
[LIST=1]
[*]using alt gr as the compose-key (for example alt-gr + 5 should produce €) 
[*]using rctrl as dead key (for example rctrl + ^ + e should produce ê). 
[/LIST]

I searched, googled and tried but I can´t obtain this behaviour.

The following command comes close but the dead keys don´t work.

```
setxkbmap -model pc105 -layout us -variant intl
```


Any suggestions on how to get the correct setxkbmap command?  I suppose once I know the right variant and options, I can just convert it to the right /etc/default/keyboard file (I'm on Xubuntu 14.04 lts).
Thanks,
roel

---

