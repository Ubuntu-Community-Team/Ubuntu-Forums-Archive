---
title: "What port does LivePatch use?"
date: 2022-04-22
forum: General Help
---

### Post by psychohermit on 2022-04-22
Greetings folks,

Does anyone know what port LivePAtch uses?  I have outgoing blocked unless there is a rule for it, and LivePatch complains that it needs a network connection.

Thanks in advance,
--glenn

[edit]
Maybe I should have posted this in networking?
[/edit]

---

### Post by #&amp;thj^% on 2022-04-22
On firewalled machines, canonical-livepatch needs access to two hostnames:

    livepatch.canonical.com, port 443
    livepatch-files.canonical.com, port 80

If livepatch client is enabled using ubuntu-advantage, additional access to contracts.canonical.com on port 443 will be required.

---

### Post by psychohermit on 2022-04-22
That port is allowed out, but LivePatch is complaining that it needs a network connection.

Thanks!
--glenn

---

### Post by #&amp;thj^% on 2022-04-22
Are you using NetWorkManager?
```
cat /etc/netplan/*.yaml | grep renderer
  renderer: networkd
```
and 
```
nm-online
```
then
```
curl -i http://connectivity-check.ubuntu.com/
```

---

