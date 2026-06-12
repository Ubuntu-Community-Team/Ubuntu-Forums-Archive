---
title: "Installing packages system-wide"
date: 2017-03-15
forum: General Help
---

### Post by jnsgs2 on 2017-03-15
Hi guys first post here,

My current setup is a machine running Ubuntu 16.04. We have a list of users from our work that can connect to this machine. If a a user from our database at work connects for the first time to this machine, it will automatically create its own personal directory with your usual folders, like Downloads, Documents and so on.

My problem is that when I want to install for instance the python packages manager, pip, it will be installed in the folder ~/.local/bin
Now, if I install for example the numpy package via the pip command, it will install itself in ~/.local/lib/python3.5/site-packages

You can see that this will be a problem as any other user will need to install all these packages in their own folder... is there any way to make a "clean" install? As in, a user (with administrator rights if needed) installs all these packages once and then any other user can use them?
Forgive me if I made any mistakes as I'm not fully familiar with this environment yet. I hope you understand my problem and where I want to go from this. Cheers

---

### Post by oldos2er on 2017-03-15
How are you installing python-pip? If you're running  ```
sudo apt install python-pip 
``` it should be available for all users.

---

### Post by jnsgs2 on 2017-03-15
So if I install it this way, and I type
```
which pip
```
from any user it should lead me to /usr/local/bin ?

Because I'm 99% that's how I installed pip in the first place, yet when I type "which pip" I get the ~/.local/bin location...

---

### Post by oldos2er on 2017-03-16
/usr/local/ is for manually installed compiled code; as far as I know no package installed by the APT system will put anything in that path.

If you have a ~/.local/bin folder, it must have been created by that user since it wouldn't exist on a default Ubuntu system. Any python code installed with python-pip is not an APT package, and APT won't recognize it as such. But I'm pretty far from being an expert on these things, so you might want to wait for someone else to corroborate (or not).

---

### Post by #&amp;thj^% on 2017-03-16
> **oldos2er said:**
> /usr/local/ is for manually installed compiled code; as far as I know no package installed by the APT system will put anything in that path.

If you have a ~/.local/bin folder, it must have been created by that user since it wouldn't exist on a default Ubuntu system. Any python code installed with python-pip is not an APT package, and APT won't recognize it as such. But I'm pretty far from being an expert on these things, so you might want to wait for someone else to corroborate (or not).

I would have to agree with oldos2er:.....This install that I have now is 2 years old and as you see from:
```
cd ~/.local
me@me-750-417c:~/.local$ ls
share

```
There is no bin there.
And i do a lot of installing and un-installing.
```
~$ which pip
/usr/bin/pip

```

```
 apt policy python-pip
python-pip:
  Installed: 8.1.1-2ubuntu0.4
  Candidate: 8.1.1-2ubuntu0.4
  Version table:
 *** 8.1.1-2ubuntu0.4 500
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     8.1.1-2 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe i386 Packages

```

---

