---
title: "version `GLIBCXX_3.4.26' not found"
date: 2022-02-22
forum: General Help
---

### Post by harivecc on 2022-02-22
Hello!
I am using ubuntu 20.04 . 
I am trying to install the mvme_root_client install from the mesytec.
However, I am getting the error below.

hari@S4JC8256:~/mvme$ make -C ${MVME}/share/mvme_root_client install
make: Entering directory '/home/hari/mvme/share/mvme_root_client'
rootcling -f mvme_root_event_rdict.cxx -rml libmvme_root_event.so -rmf mvme_root_event.rootmap /home/hari/mvme/share/mvme_root_client/mvme_root_event_objects.h /home/hari/mvme/share/mvme_root_client/mvme_root_event_objects_LinkDef.h
rootcling: /home/hari/mvme/lib/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /home/hari/Root/build/lib/libCling.so)
make: *** [Makefile:19: mvme_root_event_rdict.cxx] Error 1
make: Leaving directory '/home/hari/mvme/share/mvme_root_client'

Kindly help me.

It is working in ubuntu 18.04.

Best regards
Hari

---

### Post by schragge on 2022-02-22
> **harivecc said:**
> 
rootcling: /home/hari/mvme/lib/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /home/hari/Root/build/lib/libCling.so)

You're using a non-standard libstdc++ version. The **libstdc++6** library provided by Ubuntu has the symbol in question:
```
[color=green]$[/color] objdump -p /lib/x86_64-linux-gnu/libstdc++.so.6|grep 'GLIBCXX_3\.4\.26'[color=green]
28 0x00 0x0297f876 GLIBCXX_3.4.26
    GLIBCXX_3.4.26[/color]
```

---

