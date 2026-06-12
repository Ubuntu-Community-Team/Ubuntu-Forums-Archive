---
title: "Creating Users"
date: 2006-10-22
forum: General Help
---

### Post by DannyG on 2006-10-22
Hi,

I'm trying to add new users to my Ubuntu Dapper installation via SSH (the distro is on a server). I have access to the root account, but when I add a new user (using "useradd") and login then try and do *anything* with that user, such as "wget" and "unzip" i get hit with "permission denied".

Does anyone know why this is and what the solution is?

Thanks,

Daniel.

---

### Post by PriceChild on 2006-10-22
Isn't it actually "adduser" ?

---

### Post by DannyG on 2006-10-22
yeah i was under the influence both commands did the same thing, aparantly not.

problem fixed.

---

### Post by orlox on 2006-10-22
Isn't it just a problem of permissions??

maybe you're user is configured right and youre just trying to access files or folders for wich you don't have the neccesary permissions...

---

