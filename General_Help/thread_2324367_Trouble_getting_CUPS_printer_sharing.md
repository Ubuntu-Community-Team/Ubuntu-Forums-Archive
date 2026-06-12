---
title: "Trouble getting CUPS printer sharing"
date: 2016-05-13
forum: General Help
---

### Post by Colin@oxford on 2016-05-13
I recently upgraded my main machine from 11.04 to 14.04 and am now unable to see the printer that is connected to this machine from another.  CUPS still says that the printers are shared locally.  What do I need to do so that I can print from the remote machine?

---

### Post by ajgreeny on 2016-05-13
Does the computer, and therefore now the printer as well, have a new and different IP address after the update from 11.04?

I presume this must have been as clean install and not an upgrade?

---

### Post by Colin@oxford on 2016-05-13
Same IP address as far as I know.  Well I thought it was, but maybe not.  I thought that it ended in 37, but /etc/hosts says it ends 91.  I think that the modem/router assigns the numbers.    Both machines are connected to the router.

It was an upgrade (I may have got the numbers wrong - it was from one LTS to the next)

---

### Post by Colin@oxford on 2016-06-13
The problem is an incompatibility of CUPS before & after version 1.5.4.  I now need to add the printer to the list of printers on the remote machine since CUPS no longer broadcasts information about printers that <1.5.4 can understand.  It seems that SuSE provides a package so that one can revert to the older version but Ubuntu does not.

---

