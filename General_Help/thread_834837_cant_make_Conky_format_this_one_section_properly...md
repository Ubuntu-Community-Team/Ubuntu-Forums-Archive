---
title: "cant make Conky format this one section properly..."
date: 2008-06-19
forum: General Help
---

### Post by wolfe on 2008-06-19
I'm trying to add sensor output for my 4 core temps in Conky.  It returns the data correctly on 2 lines, but not the other 2.  can anyone tell me what I am doing wrong?

Core 0 Temp: ${execi 8 sensors | grep -A 1 'Core 0' | cut -c13-16 | sed '/^$/d'} C 
Core 1 Temp: ${execi 8 sensors | grep -A 1 'Core 1' | cut -c13-16 | sed '/^$/d'} C
Core 2 Temp: ${execi 8 sensors | grep -A 1 'Core 2' | cut -c13-16 | sed '/^$/d'} C
Core 3 Temp: ${execi 8 sensors | grep -A 1 'Core 3' | cut -c13-16 | sed '/^$/d'} C

and it looks like this:

---

### Post by wolfe on 2008-06-19
update:

I fixed it.  nothing like reading the man pages.  my 2 offending strings were grep'ing the vcore and the core at the same time.  adding -w solved it

Core 0 Temp: ${execi 8 sensors | grep 'Core 0' | cut -c13-16 | sed '/^$/d'} C
Core 1 Temp: ${execi 8 sensors | grep -w 'Core 1' | cut -c13-16 | sed '/^$/d'} C
Core 2 Temp: ${execi 8 sensors | grep -w 'Core 2' | cut -c13-16 | sed '/^$/d'} C
Core 3 Temp: ${execi 8 sensors | grep 'Core 3' | cut -c13-16 | sed '/^$/d'} C

---

