---
title: "Unable to install build-essential on a fresh install of ubuntu 20.04 LTS"
date: 2021-10-10
forum: General Help
---

### Post by Indian_Guy101 on 2021-10-10
I am trying to install build-essential on a fresh install of ubuntu 20.04 LTS, but am met with errors stating that I have some unmet dependencies that cannot be resolved. When I run sudo apt install build-essential, I get: 

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 build-essential : Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: gcc (>= 4:9.2) but it is not going to be installed
                   Depends: g++ (>= 4:9.2) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by TheFu on 2021-10-10
Did you run 
```
sudo apt update
```
today?

---

