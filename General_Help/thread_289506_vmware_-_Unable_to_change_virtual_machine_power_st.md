---
title: "vmware - Unable to change virtual machine power stat"
date: 2006-10-31
forum: General Help
---

### Post by ruf on 2006-10-31
I'm experiencing a problem with vmware. I tried both with vmware workstation and vmware server.

After installing a new virtual machine (in my case it's a WinXP one), everything works perfectly. After turning it off or suspending it, it is impossible restart it. In this case I obtain the following message:

"Unable to change virtual machine power state: Failed to connect to peer process."

Sometines I find an unterruptible vmware process that is impossible to kill. So I restart my computer ( :mad: ), but the virtual machine still doen't work!!

Any idea?

Thanks

---

### Post by Divan Santana on 2006-11-03
No idea unfortunately! But I must say am having the same problem!! :(

Maybe because of Edgy? I am running Edgy, with Vmware server and having same error message.

Anyone have any ideas?

---

### Post by ForeverNoob on 2007-03-13
I also have a power-up problem. I started getting this message when trying to power up my Windows XP VM in Edgy:

"Unable to change virtual machine power state: The process exited with an error:
Could not exec /usr/lib/vmware/bin/vmware-vmx: Exec format error
End of error message."

Any help will be greatly appreciated -- sure don't want to spend another afternoon getting another VM set up! ](*,) 

Thanks all.

---

### Post by cosmoshell on 2007-03-26
has anyone found the fix to this yet?

---

### Post by scxtt on 2007-03-28
has anyone tried re-running vmware-config.pl?

i moved 1 vm from a HDD on PC1 to a HDD on PC2 (no problem before) and then got this error ... reran the script and it's fine now ...

---

### Post by tomplast on 2007-04-09
> **scxtt said:**
> has anyone tried re-running vmware-config.pl?

i moved 1 vm from a HDD on PC1 to a HDD on PC2 (no problem before) and then got this error ... reran the script and it's fine now ...

Yup, today. Sadly it didn't worked :(

---

### Post by quickk on 2007-04-17
I had the same problem.  For some reason the ownership of the folder where I stored my virtual machine files changed.  To fix the problem:

1. Find where your virtual machine files are stored
2. See if you have read/write permission
3. If not, change permissions so that you do

I always get messed up with the chmod and chown commands, so I did steps 2 and 3 using nautilus in superuser mode.  

Hope this helps!

---

### Post by Jabb3r on 2007-12-05
Rerunning vmware-config.pl worked for me this time. Last time I had to remove the virtual soubcard and also theres a suggestion on the vmware site that deleting your nvram file from the directory where your virtual machine is.

---

### Post by patsissons on 2007-12-08
Not sure if this is too late, but I ran into this problem today and managed to fix it right away.  So for those that run into this problem in the future, my issue was caused by the binary vmware-vmx not having the set UID bit set.  The fix is pretty simple:

sudo chmod +s <vmware_install_dir>/lib/vmware/bin/vmware-vmx

that's it, everything should just magically work again.

---

### Post by tjbonzo on 2007-12-25
This worked for me (probably the same as vmware-config.pl, but I couldn't "locate" that script on my system.

# apt-get install -reinstall vmware-server

---

### Post by usingruby on 2008-05-04
Only if the problems are still unsolved, I found this solution on the web:
"sudo apt-get install ia32-libs"

Fixed it for my AMD64 installation...

---

