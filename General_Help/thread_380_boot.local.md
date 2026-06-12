---
title: "boot.local?"
date: 2004-10-13
forum: General Help
---

### Post by rupert on 2004-10-13
Hi,
how can I add the loading of modules and parameters at boot?
I need to set my DVD Burner into dma mode and i compiled a kernel module.
There is no boot.local, so how can i add these things @boot time?

thx

btw.
my logfile gets flooded by this message 

```
Oct 13 10&#58;29&#58;26 localhost kernel&#58; atkbd.c&#58; Unknown key pressed &#40;translated set 2, code 0x0 on isa0060/serio0&#41;.
Oct 13 10&#58;29&#58;26 localhost kernel&#58; atkbd.c&#58; Use 'setkeycodes 00 &lt;keycode&gt;' to make it known.
Oct 13 10&#58;29&#58;26 localhost kernel&#58; atkbd.c&#58; Unknown key pressed &#40;translated set 2, code 0x0 on isa0060/serio0&#41;.
Oct 13 10&#58;29&#58;26 localhost kernel&#58; atkbd.c&#58; Use 'setkeycodes 00 &lt;keycode&gt;' to make it known.
Oct 13 10&#58;29&#58;29 localhost kernel&#58; atkbd.c&#58; Unknown key pressed &#40;translated set 2, code 0x0 on isa0060/serio0&#41;.
Oct 13 10&#58;29&#58;29 localhost kernel&#58; atkbd.c&#58; Use 'setkeycodes 00 &lt;keycode&gt;' to make it known.
```

---

### Post by triad169 on 2004-10-13
hdparm boot pararmeters can be configured in 

/etc/hdparm.conf 

They explain alot in this file on howto setup.  In a nut shell I just added:

```

/dev/hdc &#123;
	dma = on
&#125;

/dev/hdd &#123;
	dma = on
&#125;
```

at the end of the file for my 2 CDROM drives.  

Triad

---

