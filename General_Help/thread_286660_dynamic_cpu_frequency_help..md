---
title: "dynamic cpu frequency help."
date: 2006-10-28
forum: General Help
---

### Post by dbcalo on 2006-10-28
I've been trying to get my my system to function the way i think it should be with cpufreq, or powernowd. so far cpufreq works, but it limited to 1ghz - 1.8ghz. powernowd is locked at 2.52ghz because "dynamic cpu frequency" is not available.

I would like to be able to get it to where it will vary between ~1ghz - 2.52ghz. is this a possibility? i think it is but im just not sure of how i would get it to work.

related systems specs:

mobo: dfi nforce 4 lan party ultra-d
cpu: amd 64 3000+
htt: 270
max multi: 9x
cool n quiet: enabled

---

### Post by dbcalo on 2006-10-28
after some reading i now believe that it has someting do to with a faulty acpi & dsdt. not quite sure how those effect the situation. would compiling a kernel help me in anyway?

---

### Post by dbcalo on 2006-10-28
after some tinkering i've found that if i remove all cpufreq daemons, that the cpu frequency will default to 2.52ghz.

---

