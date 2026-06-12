---
title: "Kubuntu sound since upgrade"
date: 2005-10-17
forum: General Help
---

### Post by jimmystewpot on 2005-10-17
Hello,

I have recently upgraded from hoary to breezy, Since doing that upgrade my sound does not work. It appears as though the modules list and all the usual things are in place however no sound. Ive even checked the permissions.

Is there anywway that I can easily do a hardware recheck like that one which was done on the initial cd install of hoary. It detected all my sound ok without any issues. I would like to run that again from breezy or is that only avail in the cd install?

---

### Post by mcframe on 2005-10-21
Hi,
I had similar problems. It took me quite some time to find out a reason.I have installed alsmixer and played around with the controls. On a second konsole I tried playiing a wav file wih aplay. I turned out that a "Line Jack" button had to be muted and sound switched on right away. Hope it works for you too!
Make shure to permanently store the setting with ```
alsactl -f /etc/asound.names store
``` command.

cheers 
mcframe

---

