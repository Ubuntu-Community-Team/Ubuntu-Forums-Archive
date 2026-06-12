---
title: "Problems with the APT system"
date: 2006-07-29
forum: General Help
---

### Post by ProjectGod on 2006-07-29
i've actually installed ubuntu 3 times on this one machine... 
after the initial installation everything is fine. 

but for some reason after doing a few updates with aptitude... whenever i try to remove add or install new packages via the apt-get, aptitude or synaptic... the 

building dependency tree...1% section 
reading extend state info...
initialising packet states ...

sections take a long long long long long time... has anyone else experienced this?? its slow degradation reminds me of windows.

---

### Post by jordilin on 2006-07-29
I haven't experienced sth like this. Take a look at system logs /var/log/messages or syslog and tell us sth.

---

### Post by ProjectGod on 2006-07-29
the problem seems to have solved itself! i certainly did nothing. but a good reboot did the trick maybe maybe not... 

i noticed when things were slowing down that invoking aptitude without any options would take around 1 minute to load... "loading cache" would sit there...

hmmm nothing too obvious in the logs too. anyways cheers. how does one close these threads when questions have been answered, issues resolved? is there such an option?

---

