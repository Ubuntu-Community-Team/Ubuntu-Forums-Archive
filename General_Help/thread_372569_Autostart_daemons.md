---
title: "Autostart daemons"
date: 2007-02-28
forum: General Help
---

### Post by Andesh on 2007-02-28
Hi

I'd like to autostart some applications as daemons; ventrilo, teamspeak and an eggdrop.
Let's start with the eggdrop.

I've got a script **start_eggdrop.sh** that I've put in the **/etc/init.d/** folder and the script contains:
```
#!/bin/bash
cd /opt/eggdrop/
./eggdrop simple.conf
```
Of course the executable is located in the /opt/eggdrop/ folder as well.

and when I execute it **manually **the eggdrop starts just as it should :)

I've run the command: **sudo update-rc.d start_eggdrop.sh defaults 99 01**
And I also got S99start_eggdrop.sh in rc2.d ->rc5.d and K01start_eggdrop in rc0.d and rc6.d
According to **who-r **I am in **runlevel 2**

What is the problem, why is it not auto-starting.
1. Is it the script? (I know it's ugly and does not kill the process at shutdown)
2. Is it the update-rc.d?
3. What do you think about this script-generator? [http://rob.pectol.com/content/view/17/33/](http://rob.pectol.com/content/view/17/33/)
Running Kubuntu-edgy btw.

---

### Post by filltr on 2007-11-17
> #!/bin/bash
cd /opt/eggdrop/
./eggdrop simple.conf

use sudo 

> #!/bin/bash
cd /opt/eggdrop/
sudo -u yourusername ./eggdrop simple.conf

---

