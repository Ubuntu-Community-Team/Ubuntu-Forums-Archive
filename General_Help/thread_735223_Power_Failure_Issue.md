---
title: "Power Failure Issue"
date: 2008-03-25
forum: General Help
---

### Post by i_am_socket on 2008-03-25
This weekend, the moron stoner who lives in the apartment below me apparently went to the breaker boxes and started flipping switches at random and cut the power to half my apartment. (tangentially related, but I just need to rant some more)

Anywho, power is cut to my computers which ends up exactly like the situation in this thread [COLOR="Blue"]_[HERE]("http://ubuntuforums.org/showthread.php?t=523754")_[/COLOR].  I would love to follow the directions on this thread but I have absolutely no idea what the solution is.

Can anyone translate the one sided conversation to general instructions?  I'm running a vanilla install of 7.10

---

### Post by Existentialist on 2008-03-26
In order to find where the system was locking up, when you get to the grub menu, press 'e' to edit the kernel you normally boot.  You should get something like this:

title	   Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root	  (hd0,4)
kernel   /vmlinuz-2.6.24-12-generic root=UUID=6d1670f0-ab0f-4d34-8760-3fd04028b089 ro **quiet splash**
initrd	/initrd.img-2.6.24-12-generic
**quiet**

Remove the parts in bold and press b to boot with the new options.  Instead of a splash screen, you will not see the actual output and can determine at what point it locks up.  

If it is the syslog thing mentioned in that post, you might want to post there and ask what he did to fix it.  It doesn't really say what he did, just that it was something with syslog.

Post back with what service or part it stops on.

---

