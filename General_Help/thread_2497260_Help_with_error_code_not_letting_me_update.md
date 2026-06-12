---
title: "Help with error code not letting me update"
date: 2024-04-28
forum: General Help
---

### Post by sum1overthere on 2024-04-28
I am on Ubuntu 24.04 and I clicked a box in software and updates that bugged it out and will not open now. I get the follow code when updating: Malformed entry 1 in list file /etc/apt/sources.list.d/packagecloud-shiftky-desktop.list (URI). When I try to do the commands to update it will not let me due to this error code. I think I opened the contents of the file to get this. Types: deb   
     URIs: cdrom:[Ubuntu 22.04.4 LTS _Jammy Jellyfish_ - Release amd64 (20240220)]/ Suites: jammy   Components: main restricted . How do I fix this?

---

### Post by deadflowr on 2024-04-28
Post the output of 
```
cat /etc/apt/sources.list.d/packagecloud-shiftky-desktop.list 
```
so it's clear what the file actually says.

Most likely you'll need to rm (remove) the file and try again.
I'm guessing based on the information provided, you copy-pasted the wrong stuff into the file.
But that's a guess as I'm not entirely sure what the file has in it.

---

