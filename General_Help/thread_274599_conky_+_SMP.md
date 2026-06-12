---
title: "conky + SMP"
date: 2006-10-10
forum: General Help
---

### Post by jworr on 2006-10-10
I have a new core 2 duo and I want to get conky to display the usage of each cpu.  I looked through the manual pages and the info on the conky website but the info they provided did not work.  More specifically, they say to reference the variable cpu1 and cpu2 but conky complains that they don't exist.  I've heard there are problems with ubuntu's build of conky - is this part of it? Has anyone out there gotten cpu usage info for multiple cpus in ubuntu from conky?

---

### Post by 5-HT on 2006-10-10
> **jworr said:**
> Has anyone out there gotten cpu usage info for multiple cpus in ubuntu from conky?  Yup, but I'm running 1.4.2.  Here are the relevant bits of my .conkyrc*:
```
$alignc${color white}Total CPU Usage: ${cpu cpu0}% 
${cpubar cpu0} 
$alignc${color white} CPU0: ${cpu cpu1}% 
${cpubar cpu1} 
$alignc${color white} CPU1: ${cpu cpu2}% 
${cpubar cpu2}
```*NOTE: CPU number can be provided as an argument with cpu0 referring to total CPU usage, and >=cpu1 the individual cores.
> **jworr said:**
> 
I've heard there are problems with ubuntu's build of conky - is this part of it?   Could be if Conky's complaining the variables do not exist... Haven't tried it with the version in the repos. Here's a nice guide on compiling Conky if you're not familiar with the process (though written for 1.4.0 it'll be fine for 1.4.2): [http://ubuntuforums.org/showthread.php?t=139262](http://ubuntuforums.org/showthread.php?t=139262).

Hope that helps.

---

### Post by castor_fou on 2006-10-29
and how is it working for cpugraph ? can you provide 2 different colors for each CPU ?

---

### Post by castor_fou on 2006-10-30
I answer to myself:
```

${color #4582B5}Usage CPU 1:$color ${cpu cpu1}% ${color #FFFFFF} ${cpubar cpu1}
${color #4582B5}Usage CPU 2:$color ${cpu cpu2}% ${color #FFFFFF} ${cpubar cpu2}
$color ${cpugraph cpu1 32,309 000000 7f8ed3}
$color ${cpugraph cpu2 32,309 000000 7f8ed3}
```

---

