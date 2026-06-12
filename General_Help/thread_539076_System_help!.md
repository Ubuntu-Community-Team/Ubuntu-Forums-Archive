---
title: "System help!"
date: 2007-08-30
forum: General Help
---

### Post by illbashu on 2007-08-30
ok, whenever i go into my package manager it doesn't have anything and i allways have to refresh it and download the files again.. and also when i go to the softwere update program when it tells me that ubuntu put out an update i get a screen saying 
"Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first." and i checked on the program manager and it doesn't show any any of those, which means they are both closed.. can someone please help me!:(

---

### Post by illbashu on 2007-08-30
i need help! someone???

---

### Post by merlinus on 2007-08-30
Look in System/Administration/Services to make sure nothing else is running that might be causing this problem.  If so, untick the box.

Then you might try this:

```

sudo aptitude update

```-merlin

---

### Post by illbashu on 2007-08-30
i got this error message.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: Couldn't rebuild package cache
at the very end when it was at like 99%
any help?

---

### Post by merlinus on 2007-08-30
Run the suggested command in a terminal:

```

sudo dpkg --configure -a

```

-merlin

---

### Post by illbashu on 2007-08-30
thx! that fixed ever proble i was getting :)

---

### Post by merlinus on 2007-08-30
Great!  You might write it down for future reference.

-merlin

---

