---
title: "Autosuspend on Ubuntu server 22.04"
date: 2023-11-04
forum: General Help
---

### Post by Jeanke on 2023-11-04
Hi

I installed Ubuntu server 22.04 on an older desktop to use as a NAS using Samba.
It works perfectly for our needs, just a home NAS to store pictures and documents.

However, because we don't need access to it all the time I would like it to suspend when not in use.
I enabled wake-up on LAN to wake it up manually when we need it, which works fine.

Now I would like it to suspend automatically when no active samba connections are present.
Therefore I installed "autosuspend" and I'm trying to get it to work, with no luck so far.

The manpage for autosuspend provides following information on the "available activity check" to check if there are active samba connections:

[I]Smb: Any active Samba connection will block suspend.

Options:
smbstatus: executable needs to be present.[/I]

So I adjusted /etc/autosuspend.conf as follows:

```
          [general]
          interval = 10
          idle_time = 30
          suspend_cmd = /usr/bin/systemctl suspend

          [check.Smb]
          enabled = true
```

This does not work (interval time and idle_time are low for testing purposes).
Both the *suspend_cmd* and *smbstatus* run fine (only as root).

I suppose I have to do something with the option "smbstatus", but I'm not sure what, I tried already:

```
          [general]
          interval = 10
          idle_time = 30
          suspend_cmd = /usr/bin/systemctl suspend

          [check.Smb]
          enabled = true
          smbstatus = /bin/smbstatus
```

and

```
          [general]
          interval = 10
          idle_time = 30
          suspend_cmd = /usr/bin/systemctl suspend

          [check.Smb]
          enabled = true
          smbstatus = true
```

Both with no effect.
Is there an error in the config file or is something else wrong?
Thanks!

---

### Post by MAFoElffen on 2023-11-04
Just one method for this, but does this give you ideas? [https://danielpgross.github.io/friendly_neighbor/howto-sleep-wake-on-demand](https://danielpgross.github.io/friendly_neighbor/howto-sleep-wake-on-demand)

---

### Post by Jeanke on 2023-11-04
Thanks for the reply! 
Even though the method described in the link does not match our needs it did give me ideas on how to write a simple script to automatically suspend the NAS and ditch the autosuspend software all together.

---

