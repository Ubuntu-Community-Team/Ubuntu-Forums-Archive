---
title: "Crash after resuming from suspend, lirc related"
date: 2008-04-26
forum: General Help
---

### Post by mronkko on 2008-04-26
I am running Mythbuntu and have updated to the most recent version. After replacing motherboard, the system does not resume from sleep. The old mother board was Asus A7N8X-E Deluxe and the currently installed is Asus A7V880. 

When I try to resume from sleep, I get these messages on the screen:

pci_set_power_state(): 000:00:00:00.0: state=3, current state=5
BUG: soft lockup - CPU#0 stuck for 11s!: [lircd:3923]
BUG: soft lockup - CPU#0 stuck for 11s!: [lircd:3923]

The last message is repeated until I turn the computer of. Based on the error message, I assume that this is caused by lirc. Unplugging my windows media center remote receiver will make this problem go away. 

Now, the question is, how is it possible that this problem did not occurs only after I changed the motherboard? 

Mikko

---

### Post by Cue2 on 2008-04-26
A wild guess heere but it may have something to do with your Bios and APM. It must still have power and expect the CPU to still be running maybe so it freaks out. I'm new so be gentle if this is utter rubbish. :)

How is the WMC remote reciever plugged in to your MB.

---

### Post by mronkko on 2008-04-27
I did a workaround and to stop lirc before suspend and restart it when the system resumes from sleep. 

To do this, I added 

```
RestartServices lirc
```

at the end of /etc/hibernate/common.conf

Now I have a follow up problem of MythTV not listening ot my remote anymore. But I will post this issue to mythtv mailing list.

Mikko

---

