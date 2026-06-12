---
title: "What is (fossa-melisa X20)"
date: 2020-08-11
forum: General Help
---

### Post by exhile on 2020-08-11
When I type in what version of Ubuntu I have, the terminal displays the following.

```
exhile@XPS13:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS (fossa-melisa X20)
Release:    20.04
Codename:    focal
exhile@XPS13:~$ 

```

I am trying to see if I have updated to Ubuntu 20.04.1 or not.

---

### Post by deadflowr on 2020-08-11
Not sure what that is.
It's not part of Ubuntu's normal base-files which is what the output shown comes from.
Or at least not anything I've seen.

Is there anything special about the machine or system or are there any added PPAs?

What does
```
cat /etc/os-release
```show?

FTR the base-files package required for the output to show 20.04.1 is in the -updates repository,
which may need to be enabled.
It then will get the updated version will you apply the updates.
But if any of the three things asked above are true then that may affect it's status showing correctly.

---

### Post by exhile on 2020-08-11
The machine is a Dell XPS 13 (9300) with Ubuntu 20.04 pre-installed.

When I type in:

```

cat /etc/os-release

```

This output shows:

```
exhile@XPS13:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="20.04 LTS (Focal Fossa)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 20.04 LTS (fossa-melisa X20)"
VERSION_ID="20.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=focal
UBUNTU_CODENAME=focal
exhile@XPS13:~$ 

```

However, when I do a 
```

cat /etc/lsb-release
```

I will get the following output:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu 20.04.1 LTS"

```

I would like to enable the output to show "Ubuntu 20.04.1" or any other future point release such as "Ubuntu 20.04.2" or "Ubuntu 20.04.3"....etc... instead of (fossa-melisa X20).

I was totally confused why the output status wasn't showing correctly.

---

### Post by deadflowr on 2020-08-11
Take a quick look at the base files with
```
apt policy base-files
```
it should show were it came from, repository-wise.

---

### Post by exhile on 2020-08-11
```
exhile@XPS13:~$ apt policy base-files
base-files:
  Installed: 11ubuntu5.1
  Candidate: 11ubuntu5.1
  Version table:
 *** 11ubuntu5.1 500
        500 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     11ubuntu5 500
        500 http://archive.ubuntu.com/ubuntu focal/main amd64 Packages
exhile@XPS13:~$ 


```

---

### Post by deadflowr on 2020-08-11
Looking over some dell related stuff it looks like dell adds repositories which play around with the normal things.
You should have some dell related entries in either the main sources.list or in /etc/apt/sources.list.d sub-folder.
It also installs some dell specific packages.
I did find this [https://www.dell.com/community/XPS/Dell-repo-for-Ubuntu/td-p/7568024]("https://www.dell.com/community/XPS/Dell-repo-for-Ubuntu/td-p/7568024")
which lead eventually to this [https://github.com/jules-ch/Ubuntu20-Setup-XPS13/blob/master/setup.sh]("https://github.com/jules-ch/Ubuntu20-Setup-XPS13/blob/master/setup.sh")

---

### Post by exhile on 2020-08-11
> **deadflowr said:**
> Looking over some dell related stuff it looks like dell adds repositories which play around with the normal things.
You should have some dell related entries in either the main sources.list or in /etc/apt/sources.list.d sub-folder.
It also installs some dell specific packages.
I did find this [https://www.dell.com/community/XPS/Dell-repo-for-Ubuntu/td-p/7568024](https://www.dell.com/community/XPS/Dell-repo-for-Ubuntu/td-p/7568024)
which lead eventually to this [https://github.com/jules-ch/Ubuntu20-Setup-XPS13/blob/master/setup.sh](https://github.com/jules-ch/Ubuntu20-Setup-XPS13/blob/master/setup.sh)

Thanks.

---

