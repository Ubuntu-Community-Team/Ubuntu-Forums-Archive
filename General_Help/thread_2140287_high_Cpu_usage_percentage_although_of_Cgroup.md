---
title: "high Cpu usage percentage although of Cgroup"
date: 2013-04-29
forum: General Help
---

### Post by ThethundarBird on 2013-04-29
Although i make a cgroup and run a process under it but i still have very high cpu usgae percentage in system monitor 
  here u are the code of my cgroup which i put in cgconfig.conf :
  
```
group ahmedCpuUsage { 
# Specify which users can admin (set limits) the group
 perm {       
 admin {      
  uid = ahmedubuntu;  
       gid = ahmedubuntu;    } 
#Specify which users can add tasks to this group  
  task {        uid = ahmedubuntu;
        gid = ahmedubuntu;     }
 } 
# Set the cpu and memory limits for this group
 cpu {     cpu.shares = 10;    }
 } 
 mount 
{ cpu = /sys/fs//cgroup/ahmedCpu; } 
  
```
  then  i run for instance a chorme browser like this :
  
 ```
`ahmedubuntu@ahmedubuntu:~$  cgexec -g cpu:ahmedCpuUsage --sticky   google-chrome 
```   so what is it wrong that make it doesnt work  ?`**P.S : my processor is dual core**

---

