---
title: "HELP - No Longer Boots!"
date: 2008-06-01
forum: General Help
---

### Post by Quantumstate on 2008-06-01
This morning I started my laptop (Hardy), it started to boot, but after about two pages of commands it flipped over and rebooted again!  It does this over and over.  Something is failing in the boot process.

I changed LILO to boot in single-user mode, and no difference.  Booting to the Kubuntu install CD, I can examine the filesystem just fine, although there is no /etc/inittab which I find perplexing.  I put in place a Debian inittab (only one I have), but it didn't help.

Examining dmesg, it ends with:
"Ending clean XFS mount for filesystem: sda1"
... although maybe that is not from my boot failure as that fails too early to be writing logs, and I don't know how to enable boot logging.

I use swsusp1 hibernate, and I thought maybe that got corrupted, so in lilo.conf I changed the line to 
append="root=/dev/sda1 noresume "
... but exactly the same failure.  It loops back to boot too fast for me to see where the failure is.

One odd thing is I get an error on 'lilo' I've never gotten before:
"Warning: The initial RAM disk is too big to fit between the kernel and the 15M-16M memory hole.  It will be loaded in the highest memory as though the configuration file specified "large-memory" and it will be assumed that the BIOS supports memory moves above 16M."

... never gotten this before.  Could be a symptom of the problem.  I've researched this, and it seems nothing to worry about;  someone said just disable the memory hole in bios, but my bios doesn't have that option. (new HP 8710w notebook)  However I have never seen this error on 'lilo' before.

Can someone please advise?

---

### Post by Amarsingh0793 on 2008-06-01
Have you installed a new application recently or added new hardware?

---

### Post by Amarsingh0793 on 2008-06-01
Also does recovery mode work or does it have the same problem?

---

### Post by bingoUV on 2008-06-01
Ubuntu has done away with inittab, so don't waste your time on it. If inittab does exist, it is supposed to take the default runlevel from it into consideration, but it did not do so at least in feisty.

---

### Post by Quantumstate on 2008-06-01
Thanks Amar and Bingo.

It was fscking splashy!  I'd installed fscking splashy yesterday and hadn't set it up.  Something about fscking splashy was causing this problem, and with boot to CD I just deinstalled it and now my resume worked.

Something's wrong with fscking splashy, as this sort of thing should never, never happen.

How do you boot into recovery mode?

---

### Post by Amarsingh0793 on 2008-06-01
At startup, you should see a OS selection list, where you can choose what to boot into.

---

### Post by Quantumstate on 2008-06-02
Amar, I got your PM but I am not allowed to send any until I have at least 75 posts, LOL.

Basically, when I discovered that fscking splashy was the problem and deinstalled it, the problem was fixed.

---

