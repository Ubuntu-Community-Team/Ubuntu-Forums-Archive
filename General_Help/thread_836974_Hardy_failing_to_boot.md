---
title: "Hardy failing to boot"
date: 2008-06-22
forum: General Help
---

### Post by oznog on 2008-06-22
Hi

I have a notebook that is suddenly failing to boot.  Has been running Hardy fine until today.

Cycles the following message

Bug: soft lockup -CPU#0 stuck for 11s!

This was preceded by ndiswrapper (ndisWriteErrorLogEntry:194) code: .0xfgbd6000

Any ideas

cheers

Neale

---

### Post by p_quarles on 2008-06-22
That message would indicate that it's hanging during the kernel loading process (rather than during the BIOS). Given that this is the case, you should be able to boot to single-user/recovery mode from the GRUB boot menu. Please boot into this mode to confirm.

---

### Post by oznog on 2008-06-22
H'mmm no not really.

New cycle begins (or at least the first screen line I can see does)

```
Pid: 6, comm: events/0 Tainted: P (2.6.24-19-generic #1)
EIP: 0060:[<c031c42f>] EFLAGS: 00000286 CPU: 0
EIP is at _spin_lock_bh+0xf/0x20

etc etc

```

---

### Post by p_quarles on 2008-06-22
What about a live boot disk? If it can run this, it would rule out a hardware problem (other than the hard drive).

---

### Post by oznog on 2008-06-22
OK, I was able to boot using an earlier recovery and proceeds through to login.  Subsequent restart reverts to original problem.

---

