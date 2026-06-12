---
title: "Netsend"
date: 2006-09-01
forum: General Help
---

### Post by morrin on 2006-09-01
Hi

Anyone know of a utility that will mimic the "netsend" command from windows. i.e can I send a netsend message to a windows machine from my ubuntu command line

Thanks

---

### Post by KingBahamut on 2006-09-01
If your talking about hitting the messenger service , you can use smbclient to do that 

smbclient -M <host>

---

### Post by morrin on 2006-09-01
Grand thanks. Will try that. Does anyone know if that will work outside of my local network though. Can I send it to an arbitrary IP address

---

### Post by morrin on 2006-09-01
Actually tried that but it wouldn't work. Tried machines booted into both windows and ubuntu on my local network and all I got back was


smbclient -M XXX.XXX.XXX.X
Error connecting to XXX.XXX.XXX.X (Connection refused)
Connection to XXX.XXX.XXX.X failed

or 
smbclient -M machinename
Connection to machinename failed

---

