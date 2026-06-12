---
title: "Wireless network slow in Ubuntu"
date: 2005-07-28
forum: General Help
---

### Post by diffuser78 on 2005-07-28
Hi,

I have an observation that wireless network (in my ubuntu) at my home works much slower as compared to WLAN on windows XP.

Could somebody explain and tell some tips to overcome this issue.

Dan

---

### Post by strikeforce on 2005-07-28
Its probably running ipv6 or trying to where as in winxp doesn't.

In your modules or modprobe.conf file add this.

```

alias net-pf-10 off
alias ipv6 off

```

I'm coming from a RH background so I'm assuming its /etc/modules someone who has more experience with debian based distro's please advise if I'm not correct.

---

### Post by diffuser78 on 2005-07-29
[QUOTE=strikeforce]Its probably running ipv6 or trying to where as in winxp doesn't.

In your modules or modprobe.conf file add this.

```

alias net-pf-10 off
alias ipv6 off

```

I'm coming from a RH background so I'm assuming its /etc/modules someone who has more experience with debian based distro's please advise if I'm not correct.[/QUOTE]


I couldnt find this file modprobe.conf. Can somebody tell any suggestions for the above mentioned problems,

Dan

---

### Post by SFN on 2005-07-29
Try ```
sudo nano /etc/modprobe.d/aliases
```

---

