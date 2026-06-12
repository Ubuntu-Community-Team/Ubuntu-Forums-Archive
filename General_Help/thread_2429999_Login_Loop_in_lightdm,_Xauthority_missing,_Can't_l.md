---
title: "Login Loop in lightdm, Xauthority missing, Can't login after Backup restore"
date: 2019-10-26
forum: General Help
---

### Post by giant-paw on 2019-10-26
Hi
It's better if I described this story from the beginning.

I repartitioned my drive completely to GPT and full UEFI with Secure Boot on, installed Windows 8.1 then Ubuntu 18.04, and moved backup of old Ubuntu using _cp -a_ on /root, /usr, /etc, and whole /home. I used rdiff-backup for backup. On my old ubuntu, I had NVidia driver on (without any optimus).
It wasn't booting normally until I replaced entries in /etc/fstab with new UUID. After that it booted only to TTY. I couldn't boot into Gnome or gdm3 as usual and screen was flickering/blinking so I installed lightdm, had chosen it as default and Finally graphics of lightdm showed up.
But now it's stuck in the login loop.

When ubuntu boots it says ```
"Couldn't get size 0x800000000000000e"
```.
Command xauth returns something like "timeout waiting too much for file".
I have only ICEauthority file in /home and .xinputrc.
Also for some reason TTY shows msg ```
No home directory, logging in with HOME=/
``` I have /home/user directory though.

I hope it makes sense, and some bigger picture, and what's wrong? And why doesn't it login.
If you wish to spend some time on the forums, reading something curious, and writing, of course.

---

