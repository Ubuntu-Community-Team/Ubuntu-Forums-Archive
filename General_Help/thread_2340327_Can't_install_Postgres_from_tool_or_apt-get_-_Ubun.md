---
title: "Can't install Postgres from tool or apt-get - Ubuntu One fails"
date: 2016-10-17
forum: General Help
---

### Post by rbarrimond2 on 2016-10-17
I've signed up with Ubuntu One and I think that was a mistake. Now when I try to install Postgres, I'm told my SSO email or password are incorrect. This is impossible since I log into, out of, and back into the Ubuntu One site with no problems. When I tried to get around this using apt-get postgres install failed. What in the blue blazes is going on?

16.04 LTS
vmware fusion VM

---

### Post by howefield on 2016-10-17
Is this a snap package that you are trying to install ?

If so, trying installing from the terminal..

```
sudo snap install postgresql-9-6
```

The apt package would be postgresql, I believe..

```
sudo apt install postgresql
```

---

