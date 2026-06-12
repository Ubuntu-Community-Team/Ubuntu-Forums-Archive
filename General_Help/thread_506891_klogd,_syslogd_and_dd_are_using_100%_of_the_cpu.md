---
title: "klogd, syslogd and dd are using 100% of the cpu"
date: 2007-07-22
forum: General Help
---

### Post by RembrandtQEinstein on 2007-07-22
I am new to Ubuntu but not new to Linux. I installed Ubuntu 2 weeks ago. Everything has been going smooth until last night. klogd, syslogd and dd are taking 100% of the cpu. I look at the output of /var/log/kern.log and it is constantly getting updated with:

Jul 22 09:41:45 Jacob kernel: s errobus errobus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errobus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errobus errbus errbus errobus errbus errobus errbus errobus errbus errbus errbus errobus errbus errbus errobus errobus errbus errbus errbus erbus errobus errobus errbus erbus errbus errbus errbus errbus erbus errbus errbus errbus errbus errbus errobus errbus errbus errbus errbus errobus errbus erbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errobus errobus errbus errbus errobus errbus errbus erbus errobus errobus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errbus errobus errbus erbus errbus errbus errbus errbus errbus errobus errobus errobus errobus errbus errbus errobus errbus errobus errbus errbus erbus errbus errbus errobus errbus errobus errbus errobus errobus errbus errbus errobus errobus errbus er


sometimes is just "bbbbbbb..."

What is going on?

---

### Post by RembrandtQEinstein on 2007-07-22
OK. I ran dmesg and saw this:

[ 5669.337255] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337292] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337325] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337362] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337395] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337431] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337464] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337497] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337529] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337565] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337602] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337639] dmfe: System bus error happen. CR5= ffffffff
[ 5669.337676] dmfe: System bus error happen. CR5= ffffffff


So dmfe is generating this error. I ran modprobe -r dmfe and klogd quit hogging the cpu and /var/log/kern.log is no longer getting loaded with the errbus message. I still have ethernet though so I guess my system wasn't using dmfe. I searched around a bit and found that there are issues if dmfe an tulip are running together and you should unload tulip and dmfe and reload dmfe. In my case I am not running tulip. So I wonder which driver is for my ethernet hardware? Also, why is dmfe getting loaded if it causes this problem. I did blacklist dmfe so I hope this doesn't come back. I also wonder why it just started after running Ubuntu on this hardware for two weeks?

---

