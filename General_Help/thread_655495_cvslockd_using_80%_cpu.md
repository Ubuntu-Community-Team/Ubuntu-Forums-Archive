---
title: "cvslockd using 80% cpu"
date: 2008-01-01
forum: General Help
---

### Post by snacker on 2008-01-01
cvslockd is using ~80% of the cpu all of the time.

I waited for a while and it was still using ~80% cpu.

I don't even have any cvs repositories yet :-?

I checked the processes, because the fan on my laptop (hp ze5570us) was on constantly.

acpi -fV showed the cpu at 140 F.

After uninstalling cvs the fan got a lot quieter and acpi -fV shows 120 F.

Any idea what was going on?

I think I'm going to setup svn and see if that is nicer on the cpu.

---

