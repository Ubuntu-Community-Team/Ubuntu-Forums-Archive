---
title: "System crashes about once a day"
date: 2006-12-22
forum: General Help
---

### Post by pickarooney on 2006-12-22
And I have no idea why. Since about two weeks ago, about the time I got internet and a TV tuner, the system locks up completely at seemingly random moments. The only indicator I can find at all is /var/log/messages, but I'm not sure how helpful that is.

Where do I begin trying to solve this?

*edit: just noticed this bit, a gap of six minutes after I shutdown a program and a forced restart. Not so useful, eh?*

```

Dec 22 22:06:44 marklar -- MARK --
Dec 22 22:26:45 marklar -- MARK --
Dec 22 22:46:45 marklar -- MARK --
Dec 22 23:06:45 marklar -- MARK --
Dec 22 23:20:39 marklar kernel: [ 7038.878749] btdownloadgui[6112]: segfault at 0000000000ec80
80 rip 0000000000ec8080 rsp 00007fff700cb6b8 error 15
Dec 22 23:26:42 marklar syslogd 1.4.1#18ubuntu6: restart.
Dec 22 23:26:43 marklar kernel: Inspecting /boot/System.map-2.6.17-10-generic
Dec 22 23:26:43 marklar kernel: Loaded 23625 symbols from /boot/System.map-2.6.17-10-generic.
Dec 22 23:26:43 marklar kernel: Symbols match kernel version 2.6.17.

```

Another weird thing: every so often my display goes wonky, as though images were displaying in 256 colours, andI have to reset X for it to work again.

---

### Post by jimbob on 2006-12-22
What release are you using?  

I have this problem with Edgy.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by pickarooney on 2006-12-22
Kubuntu Edgy 64-bit.

---

