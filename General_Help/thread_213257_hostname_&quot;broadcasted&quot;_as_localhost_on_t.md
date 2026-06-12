---
title: "hostname &quot;broadcasted&quot; as localhost on the net?"
date: 2006-07-11
forum: General Help
---

### Post by RikoW on 2006-07-11
Hi everyone,

I have the following "problem" - not much of a problem, but it bugs me a bit.

In our organization we have a big number of network printers. So that people can separate their printout easily, each print job is preceeded by a green cover page which names the user and the host from which the print job was send.

When I print from my 6.06 installation, the host name of the cover page is always "localhost", even though I gave the correct host name during installation, it is set by DHCP and the $HOST variable and uname -a give the correct name.

Any hint on why this host name is not used when sending print jobs?
I set up the printers via System -> Administration -> Printing. The printers are LDP network printers.

Thanks,

         Riko

PS: BTW, in Breezy the hostname was send properly.

---

### Post by tribaal on 2006-07-11
Yeah I had the same problem.

To fix this you need to edit /etc/hosts and change the line that sais
"127.0.0.1 localhost <yourhostname>" to "127.0.0.1 <yourhostname> localhost".

That's all it took for me.

Cheers :)

- trib'

---

### Post by RikoW on 2006-07-11
Thanks! Trip' !

That did the trick :)

Cheers,

          Riko

---

### Post by RikoW on 2006-07-18
Unfortunately, the /etc/hosts file seems to be reset after each reboot and localhost is used again instead of the 'real' hostname.

Since I'm on a laptop, reboots (or better shutdown, start) occur essentially daily.

How to set that for good?

Thanks and cheers,

              Riko

---

