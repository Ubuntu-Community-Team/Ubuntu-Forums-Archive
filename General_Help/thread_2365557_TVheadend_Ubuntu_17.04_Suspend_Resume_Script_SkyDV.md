---
title: "TVheadend Ubuntu 17.04 Suspend Resume Script SkyDVB - Script Doesn't Run"
date: 2017-07-07
forum: General Help
---

### Post by dr-bond on 2017-07-07
[COLOR=#111111][FONT=Ubuntu]i have a suspend script which doesn't seem to be running. The script is located in ```
/lib/systemd/system-sleep
``` and also```
 /etc/pm/sleep.d
``` the script is named ```
99_htpc.sh
``` and has executable permissions with the owner as root.[/FONT][/COLOR]

```
#!/bin/bash

case "$1" in
suspend|hibernate)
service tvheadend stop
sleep 3
modprobe -v -r smipcie m88ds3103 dvb_core m88rs6000t
;;
resume|thaw)
modprobe smipcie m88ds3103 dvb_core m88rs6000t
sleep 3
service tvheadend start
;;
esac
```

[COLOR=#111111][FONT=Ubuntu]It's meant to stop TVheadend and restart it along with stopping and reloading my SkyDVB S952 modules because the DVB card doesn't work after suspend, so i'm trying to unload the modules and then reload them.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]After waking from suspend, TVheadend can't use the DVB card but if i run ```
service tvheadend stop modprobe -v -r smipcie m88ds3103 dvb_core m88rs6000t
``` then```
 modprobe smipcie m88ds3103 dvb_core m88rs6000t service tvheadend start
``` TVheadend restarts and so does the DVB card and it works fine.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]So i'm trying to work out why it doesn't work when i use it as a script, could anyone help me please?[/FONT][/COLOR]

---

