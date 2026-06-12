---
title: "install fuzelinuxclient"
date: 2014-11-25
forum: General Help
---

### Post by rawlins02 on 2014-11-25
Trying to install fuze. I was directed to this page:

[https://apt.fuzebox.com/README.txt](https://apt.fuzebox.com/README.txt)

Then I entered the following commands:

```

> sudo bash -c 'echo "deb http://apt.fuzebox.com/apt $(lsb_release -sc) main" > /etc/apt/sources.list.d/fuzebox.list'
> sudo wget -O /etc/apt/trusted.gpg.d/fuzebox.gpg http://apt.fuzebox.com/apt/keyring.gpg
> sudo apt-get update
> sudo apt-get install fuzelinuxclient
>sudo apt-get install fuzelinuxclient

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fuzelinuxclient
 

```

I see the package manager has no fuzelinuxclient. Suggestions?

---

