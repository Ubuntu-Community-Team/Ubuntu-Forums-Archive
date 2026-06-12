---
title: "update-rc.d error"
date: 2015-08-05
forum: General Help
---

### Post by atux on 2015-08-05
hello. i do need to update a script and it gives me errors. 
#update-rc.d checkname
update-rc.d: error: not enough arguments
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> disable|enable [S|2|3|4|5]
                -n: not really
                -f: force

  The disable|enable API is not stable and might change in the future.
#update-rc.d -f checkname
update-rc.d: error: no runlevel symlinks to modify, aborting!




how do i fix that?

---

### Post by dino99 on 2015-08-05
as your first error says: not enough arguments

[http://manpages.ubuntu.com/manpages/vivid/man8/update-rc.d.8.html](http://manpages.ubuntu.com/manpages/vivid/man8/update-rc.d.8.html)

---

### Post by atux on 2015-08-05
i have seen that, but i have not found a solution.

---

### Post by ian-weisser on 2015-08-05
Hmmm. What, exactly, are you trying to do? 
Update-rc.d is not a clever application (if I recall, it's just a script), and needs to be told clearly what you want it to do.

---

### Post by atux on 2015-08-05
in /etc/init.d i have a file which checks connectivity.
then iam trying to add it 
update-rc.d defaults checkname

but it returns the aforementioned errors.

---

