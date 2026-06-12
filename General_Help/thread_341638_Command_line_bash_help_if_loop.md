---
title: "Command line bash help? if loop"
date: 2007-01-18
forum: General Help
---

### Post by fokuslee on 2007-01-18
if ls /etc/*release 1>/dev/null 2>&1; then 
My understanding is that all the files listed will be dumped, and then clause is executed. however if ls fails to find anyfile ending with release error is sent to stdout and we just exit from ls with non-zero status. So i guess the if condition is not satisfied b/c status 0 = true status anyother = false? is my understanding rite?

---

### Post by mssever on 2007-01-19
> **fokuslee said:**
> if ls /etc/*release 1>/dev/null 2>&1; then 
My understanding is that all the files listed will be dumped, and then clause is executed. however if ls fails to find anyfile ending with release error is sent to stdout and we just exit from ls with non-zero status. So i guess the if condition is not satisfied b/c status 0 = true status anyother = false? is my understanding rite?

If I'm following you right, you're correct, but your syntax is wrong. Try this: ```
if $(ls /etc/*release >/dev/null 2>&1); then
``` You need $(...) for command substitution.

EDIT: I just noticed that the parentheses aren't required; however, I think that it's still a good idea to include them for clarity's sake.

If one or more files match the pattern, ls will exit with a 0 exit status and the if block will execute. if no files match, ls will exit 2 and the else block (if any) will execute. In no case will ls print anything to the screen, because you're redirecting both stdout and stderr to the bit bucket. If you want an error message, leave off 2>&1.

---

