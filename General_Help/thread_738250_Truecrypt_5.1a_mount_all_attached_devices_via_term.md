---
title: "Truecrypt 5.1a mount all attached devices via terminal"
date: 2008-03-28
forum: General Help
---

### Post by co0lingFir3 on 2008-03-28
Hi folks!
I recently updated to newest Truecrypt and was quite satisfied with the new GUI but was totally disappointed by the documentation (there's no). Also the doc on the net isnt really Linux-specific.
So here's my problem: I want to "auto-mount devices" (all attached truecrypt devices) via terminal. in windows there's the "/a devices" parameter. So there has to be some kinda parameter in linux too also because it's possible to auto-mount devices via GUI.

greetings,
co0lingFir3

---

### Post by co0lingFir3 on 2008-04-02
So due to some help i managed to change the bash file like this:
```
#!/bin/bash
truecrypt -t --auto-mount=devices -k /path/to/keyfile -p ""
```
however truecrypt needs to be run as sudo. if i just leave the -t parameter (for textmode) out, it asks me to confirm the keyfile and then determines wheter it is necessary to enter the sudo password or not and eventually comes up with a prompt.
with the -t parameter (textmode -> no prompts/windows/gui) it doesnt ask me for a password even if it needs to be run as sudo. if i recently (not more than 15min ago i think) worked as sudo, the script works like a charm otherwise it doesnt. in order to fix this i modified it like this:
```
#!/bin/bash
gksu -m "Enter pw" truecrypt -t --auto-mount=devices -k /path/to/keyfile -p ""
```
if i exectue this script i have to enter my password but then nothing happens at all, as if the script and truecrypt wouldnt run as sudo and therefore be interrupted.

[SIZE="2"]am i doing anything wrong? is there another way than gksu?[/SIZE]

greets and thx for your help,
cF

---

