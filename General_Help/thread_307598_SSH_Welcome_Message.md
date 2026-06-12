---
title: "SSH Welcome Message"
date: 2006-11-26
forum: General Help
---

### Post by krisrmgua on 2006-11-26
Any idea why i can edit the welcome message for ssh  here /etc/motd
and it work the message is changed. But as soon as i reboot it converts back to the default message?

---

### Post by krisrmgua on 2006-11-26
Any ideas?

---

### Post by kjacks on 2006-12-07
Same problem here.  Can anybody help?

---

### Post by Mithrilhall on 2006-12-07
Did you remember to restart ssh?

```

sudo /etc/init.d/./ssh restart

```

---

### Post by kjacks on 2006-12-07
Yeah I tried that.  Still changes back when the system reboots.  ](*,)

---

### Post by aetherh4cker on 2007-11-18
> **krisrmgua said:**
> Any idea why i can edit the welcome message for ssh  here /etc/motd
and it work the message is changed. But as soon as i reboot it converts back to the default message?

I hate to revive a year old post, but, I'm having this problem as well.

As far as I can tell, it was never resolved.

I use "sudo nano /etc/motd" and edit the motd file as normal.  It works, the message is changed and shows up when I re-login through SSH, but after I restart the computer it goes back to the default.

I'm on Ubuntu 7.04.

---

### Post by ab_au on 2007-11-18
The motd file is overwritten at boot. to make your change permanent you'll have to update /etc/motd.tail

---

