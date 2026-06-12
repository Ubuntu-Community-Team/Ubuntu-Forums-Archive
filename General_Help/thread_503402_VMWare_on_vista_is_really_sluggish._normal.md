---
title: "VMWare on vista is really sluggish. normal?"
date: 2007-07-17
forum: General Help
---

### Post by syxbit on 2007-07-17
Vista: Host
Ubuntu: Guest

I can't run ubuntu on my laptop yet, cause it's not supported (Thinkpad T61)

the performance is HORRIBLE
i can barely browse the web.
is this normal?

are there any other better options? like parallels or VirtualPC ?
I just assumed VMware would be the best option

---

### Post by mbeierl on 2007-07-17
The problem with vmware on windows is that vmware cannot properly schedule itself as a process.  Windows decides for itself what's most important to run, and if it wants to index your disk, too bad for vmware...

/rant

So, all that aside, did you give enough memory to the virtual machine?  How much physical mem, etc, do you have?

---

### Post by syxbit on 2007-07-17
512mb
that should be enough!

so, are there better options?

---

### Post by mbeierl on 2007-07-17
You mean you gave 512 of your physical to vmware?  How much physical do you have?

<quote>640k ought to be enough</quote>

---

### Post by syxbit on 2007-07-17
i have 2gb
i upped it to 768
i also told it to use 2 cores (cpus) that seemed to speed it up a bit

---

### Post by veloce on 2007-07-18
> **syxbit said:**
> i have 2gb
i upped it to 768
i also told it to use 2 cores (cpus) that seemed to speed it up a bit

Vista is a bit of a memory hog, I'd suggest cutting **down** the memory for the vm to 256.

Also, under XP, telling the vm to use 2 cores was a **BAD** idea - performance was shocking.

---

### Post by vmaric on 2007-07-18
i have toshiba tecra8 with windows vista and i alocate to vmware(ubuntu) 512MB RAM
This work fine!
Caple day ago Ivev crash ubuntu He can't access vm disk. 
Maby indexsing is have been problem?

---

