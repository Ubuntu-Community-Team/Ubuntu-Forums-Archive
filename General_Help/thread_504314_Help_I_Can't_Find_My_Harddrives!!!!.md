---
title: "Help I Can't Find My Harddrives!!!!"
date: 2007-07-19
forum: General Help
---

### Post by jayde_drag0n on 2007-07-19
i had 2 internal harddrives Armada and Dib... they were read only and i needed them to be read write (please keep in mind i'm a newbie) so in my searching i found "ntfs-config" installed it and tried to enable the read write option... well then it unmounted the drives and told me i no longer had permissions to mount them... so i figurewd out how to log in as administrator.. and there they said they couldn't be mounted because the log file was not good.. and i needed to either boot into windows and properly reboot (i don't have wondow) or try ntfsfix.... welll noone would help me do that and the only help i got was to uninstall and reinstall ntfs-config... and now my drives are not there at all... they are still listed under /media.. but they list as empty... but the space is incorrect... even if i did lose all my data they should be at 80g apiece.. but theyre not.. they're listed as empty and at 30g a piece... please please please.. help... AIM: the jayde drag0n YIM: jayde_drag0n MSN: [email]jayde_drag0n@hotmail.com[/email]

---

### Post by TheExplorer on 2007-07-19
Install the following packages with Synaptic:

libfuse2
fuse-utils
libntfs-3g
ntfs-3g
ntfs-config

Then go to Applications -> System Tools -> NTFS Configuration

P.S. A little trick with the Windows partition: assign a tick, input Windows and then click anywhere inside the list of available partitions. Apply and then put two ticks on the other message dialogue.

It works for me like a charm automatically mounting all my hdds at boot time.

---

