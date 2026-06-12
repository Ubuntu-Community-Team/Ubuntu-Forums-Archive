---
title: "Upstart ignores /etc/init"
date: 2014-03-03
forum: General Help
---

### Post by switzel on 2014-03-03
Hi,

I had my first encounter with upstart when I tried to just stop NetworkManager. My understanding is that I should just do

stop network-manager

as root and that should do the job. However I only get "stop: Unknown Instance: network-manager" (I can only guess that this is the translation because initctl ignores the LC_ALL, LANG, LANGUAGE variables). In fact it seems that the only services upstart seems to know are the old system v scripts in /etc/init.d. The config files in /etc/init are completely ignored. Can somebody explain this behavoir to me? (I am running Ubuntu 13.10 btw.) Thanks a lot!
Also concrete help on how to stop NetworkManager would be appreciated. Of course I tried just killing it but then it is restarted.

Stefan

---

### Post by ian-weisser on 2014-03-03
Network Manager is a system service. You must use sudo when you stop it.

See for yourself. Look at the output difference:
```
initctl list
sudo initctl list
```


EDIT: This assumes, of course, that you are logged in as yourself. If you are logged in as root, the output should be identical.

---

### Post by switzel on 2014-03-04
That's surprising. What is the difference between being root and using sudo? And what's the point? I have the habit of doing su for administrative purposes so it seems strange to do sudo as root.

---

### Post by deadflowr on 2014-03-04
sudo is a one time event, per a command.
(though you can set it to run interactively)
root is forever, in which every action is a root action.

---

