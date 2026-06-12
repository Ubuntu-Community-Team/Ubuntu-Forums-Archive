---
title: "lid state gets stuck on closed"
date: 2008-03-16
forum: General Help
---

### Post by jeff.sadowski on 2008-03-16
I was experiencing an issue when my screen closed. My screen would keep blinking constantly. It was really annoying. I fixed it by sudo chmod a-x /etc/acpi/lid.sh

I would like to do things on lid close but not if it causes an unusable system.

Here is what I find out from experimenting.

When I first start my system
(this is after my modifying of the permissions of /etc/acpi/lid.sh)

# cat /proc/acpi/button/lid/*/state
.open

if I press the button and let off and

# cat /proc/acpi/button/lid/*/state
.open

if I press the button and then cat the file then let off

# cat /proc/acpi/button/lid/*/state
state:      closed

from this point on it remains closed. something about catting the state when the lid is closed is locking its state.

I have a hp nc6220.

looking at the /var/log/acpid log

[Sun Mar 16 15:45:00 2008] completed event "button/lid C1ED 00000080 000000cf"
I see that the number 000000cf keeps getting incremented. it gets an event when the lid is down. I could use this to run some scripts.
I get a lid event every 30 seconds when the lid is closed

---

