---
title: "Removing splash and quiet options from grub file"
date: 2020-10-11
forum: General Help
---

### Post by helen314 on 2020-10-11
It has been few years since I have done this , so I do no want screw  it up.
I could just delete both from the  file, but 
1. can I comment these options out of the line of code ? 
2. can I comment out the entire line and make a copy without the "quiet splash" ?

NO , I do not know how to post the file contents here. 
( I woudl have to reboot and pay more attention...)

---

### Post by rbmorse on 2020-10-11
I believe the correct way would be to edit those options in the regular text file /etc/default/grub, then run the command update-grub.

---

### Post by helen314 on 2020-10-11
Thanks, after  I gain access to the file of course.

---

### Post by Bashing-om on 2020-10-11
helen314; Hello -

rbmorse means to make the line so:
/etc/default/grub
> 
GRUB_CMDLINE_LINUX_DEFAULT=""


And again the reminder to:
```

sudo update-grub

```

once you have saved the changed file.

[INDENT][INDENT]my bit to try and help[/INDENT][/INDENT]

---

### Post by CelticWarrior on 2020-10-11
And the current recommendation is to use 'sudoedit' for editing system configuration files:
```
sudoedit [COLOR=#000000]/etc/default/grub[/COLOR]
```

---

### Post by helen314 on 2020-10-12
> **CelticWarrior said:**
> And the current recommendation is to use 'sudoedit' for editing system configuration files:
```
sudoedit [COLOR=#000000]/etc/default/grub[/COLOR]
```

Wha, technology marches on 
but what is this file being edited ?? 

 File: /var/tmp/grub.XXNta1hN

---

### Post by CelticWarrior on 2020-10-12
It's just a temporary file.

---

### Post by helen314 on 2020-10-12
> **helen314 said:**
> Wha, technology marches on 
but what is this file being edited ?? 

 File: /var/tmp/grub.XXNta1hN

So after the file is edited - standard ^X  will close it without changing grub . 
REALLY ??? 

( Inmates are running the asylum   - AGAIN )

---

### Post by CelticWarrior on 2020-10-12
No, it needs to be saved first. That's when the temporary file is shown, just ignore it.

---

### Post by helen314 on 2020-10-12
> **CelticWarrior said:**
> No, it needs to be saved first. That's when the temporary file is shown, just ignore it.

Huh?
When I edit using nano I always do ^x , there is no "save" , then I am asked if I want to save it and how.

---

### Post by ajgreeny on 2020-10-12
Use ^O before ^X.
The former asks you if you want to save the file with its real name, not the temporary name, with the default being "Yes" if you hit Enter, then ^X simply closes nano.

Much less confusing!

---

### Post by tea for one on 2020-10-12
> **helen314 said:**
> Huh?
When I edit using nano I always do ^x , there is no "save" , then I am asked if I want to save it and how.

Nano has ^O as [COLOR="#0000FF"]save[/COLOR]

Whoops, too slow again

---

