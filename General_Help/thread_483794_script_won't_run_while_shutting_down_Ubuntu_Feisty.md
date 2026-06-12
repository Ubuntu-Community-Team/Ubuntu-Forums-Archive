---
title: "script won't run while shutting down Ubuntu Feisty"
date: 2007-06-25
forum: General Help
---

### Post by slagermvd on 2007-06-25
I use Unison to synch the homeDir of my laptops with my server. This process is scripeted and is running perfectly whil booting my Ubuntu laptops. I also want to synch the laptop with the server while shutting down, so that the server always contains the latest updates.

I cannot get this process to work, it just seems to do nothing. I don't get warnings / errors in the logfile of the Unison process.

I tried to run the script while shutting down the laptop by the following means:
- Added the script to rc.local
- Run the command: update-rc.d synchHomeMichael.sh defaults

Below are the contents of the script synchHomeMichael.sh:
#!/bin/sh -e

case "$1" in
start|"")
su michael -c "unison default -batch > /dev/null 2>&1"
exit 0
;;
restart|reload|force-reload)
echo "Error: argument '$1' not supported" >&2
exit 3
;;
stop)
su michael -c "unison default -batch > /dev/null 2>&1"
exit 0
;;
*)
echo "Usage: synchHomeMichael.sh [start|stop]" >&2
exit 3
;;
esac

I hope somebody can help me solve this annoying problem.

Thnx

---

