---
title: "Question about sudo apt update (newbie user)"
date: 2023-01-29
forum: General Help
---

### Post by hallp2022 on 2023-01-29
Hi all,

When I deploy sudo apt update, my terminal attempts to fetch a bunch of information and one of the things it does is to contact the following domains: Ign:1 [https://mega.nz/linux/repo/xUbuntu_22.10](https://mega.nz/linux/repo/xUbuntu_22.10) ./ InRelease

I have deleted completely the mega sync client from my machine, but clearly there's some residue left. How can I stop sudo apt update to contact mega.nz as show in the line above? I don't want my machine to be connecting to this server if I am not using the actual mega sync client.

Thanks!

---

### Post by Frogs Hair on 2023-01-29
Open software & updates and look for the source in the other software tab. If it is there it can be removed selecting the source and using the remove option.

---

### Post by hallp2022 on 2023-01-29
Thanks I solved this!

---

