---
title: "virus on virtual machine"
date: 2008-05-20
forum: General Help
---

### Post by kakyoism on 2008-05-20
If files saved on my virtual Windows in vmware are infected by virus,
how can I get rid of the virus without having to erase them..?

Is it basically the same way as in the real OS?
I was expecting that virtual machine can be easily turned off and on and the virus would be gone after that....

---

### Post by jcwmoore on 2008-05-20
> **kakyoism said:**
> If files saved on my virtual Windows in vmware are infected by virus,
how can I get rid of the virus without having to erase them..?

Is it basically the same way as in the real OS?
I was expecting that virtual machine can be easily turned off and on and the virus would be gone after that....

same way you clean a real install, you need anti-virus software on the VM.

---

### Post by sdennie on 2008-05-20
In the future, if you take a snapshot of the virtual machine just after install, you should be able to roll the VM back to a clean state.  You can also take periodic snapshots and rollback.  However, any rollback will lose the changes/data in the VM from the time of the snapshot to the time of the rollback.

---

### Post by EXCiD3 on 2008-05-20
> **jcwmoore said:**
> same way you clean a real install, you need anti-virus software on the VM.
At least its just a VM so you can wipe it and reinstall without having to worry about your host os getting hosed.

---

### Post by jcwmoore on 2008-05-21
> **EXCiD3 said:**
> At least its just a VM so you can wipe it and reinstall without having to worry about your host os getting hosed.

very true, and +1 to the snapshot idea.  running native anti-virus software can be very resource intensive, so using it in a VM only makes it more expensive.  In general I think the snapshot idea is the safest bet.

---

### Post by kakyoism on 2008-05-22
Thx guys!

But how do I take a OS snapshot thru VMWare?

---

