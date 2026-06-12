---
title: "update manager not requesting password??"
date: 2013-07-17
forum: General Help
---

### Post by greenbag on 2013-07-17
Recently I've noticed the update manager is not asking for a password.. not everytime. Most times it does, but every now and then it just starts downloading and installing.. without requiring a password. Doesn't matter how long the computer's been on either.. either just booted, or been on for 2 days straight. I'm guessing this is a bug, but thought I'd bring it up.

---

### Post by BBQdave on 2013-07-17
I believe *feature*?

After fresh install of Ubuntu Unity 12.04LTS, I entered my admin password once for updates and after that it updates with out me re-entering the password. I say re-enter, because I believe it is a *feature* of being logged in to the system as an admin user.

---

### Post by slickymaster on 2013-07-17
Update manager will only ask for a password if new packages are being installed, like a new kernel, etc. If it's updating software already installed it will not ask for a password.

---

### Post by greenbag on 2013-07-17
Thanks for the replies. I've always had to enter password when updating.. it's an "update manager", not the Ubuntu Software Center. It's only been acting like this for the last month or so.. since a new kernel update.

---

### Post by gleedadswell on 2013-07-18
Yup, slickymaster is correct.  Update manager only asks for a password if the update involves installing completely new software.

---

