---
title: "How to add gpe interrupts to cron in Ubuntu 14.04"
date: 2015-05-30
forum: General Help
---

### Post by uxbal on 2015-05-30
I've had a lot of usage on one core of my cpu, so i entered this:
  grep . -r /sys/firmware/acpi/interrupts
  And as an output, i've got that the gpe13 is fishy:
  /sys/firmware/acpi/interrupts/gpe13:760362706   enabled
  How do i make this problem go away?

Thing is, sudo won't let me edit /etc/cron.d folder.



  Thanks a lot!

---

### Post by ajgreeny on 2015-05-30
I can not help you with the specific problem of the interrupts, I'm afraid, but what do you mean by "Thing is, sudo won't let me edit /etc/cron.d folder."

/etc/cron.d is a folder and you can not "edit" a folder, you can only change permissions using sudo, so I do not understand what you're trying to do.

---

