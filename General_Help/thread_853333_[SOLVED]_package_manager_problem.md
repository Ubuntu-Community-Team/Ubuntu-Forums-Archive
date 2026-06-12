---
title: "[SOLVED] package manager problem"
date: 2008-07-08
forum: General Help
---

### Post by mosty friedman on 2008-07-08
hey everyone, 
i'm new to ubuntu and i have this problem with the package manager, i was installing some updates and it sorta crashed, now the package manager wont start and it displays these error messages:
Error:opening the cache
E:the list of sources could not be read

---

### Post by Bigtime_Scrub on 2008-07-08
It sounds like you don't have the correct repositories checked off. Are you sure all the repositories are available?

System-> Administration-> Synaptic Package Manager

In Synaptic go to

Settings-> Repositories

On the first tab check off all boxes except Cd-Rom and source code

Under 3rd party check off all of them.

I would then run a terminal.

Applications-> Accessories-> Terminal

```
sudo apt-get update
```

then 

```
sudo apt-get upgrade
```

---

### Post by avtolle on 2008-07-08
Try from the CLI (Applications>>Accessories>>Terminal)```
sudo apt-get clean
```to try to clear the cache. Then run the commands that Bigtime_Scrub gave.

---

### Post by mosty friedman on 2008-07-08
i tried what Bigtime_scrub said but it gives me an error when i open the synaptic package manager it gave me these errors..

E: Type ‘--04:30:50--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

---

### Post by plucky on 2008-07-08
> **mosty friedman said:**
> i tried what Bigtime_scrub said but it gives me an error when i open the synaptic package manager it gave me these errors..

E: Type ‘--04:30:50--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

**Reinstall medibuntu.list**
 Open a terminal and
```
sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.old
```

Add the list
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Add the key ```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Good Luck

---

### Post by mosty friedman on 2008-07-08
i tried what you said but the last command gives this error

E: Type ‘--01:20:03--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

---

### Post by iaculallad on 2008-07-08
> **mosty friedman said:**
> i tried what you said but the last command gives this error

E: Type ‘--01:20:03--’ is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

Open /etc/apt/sources.list.d/medibuntu.list file and delete all of its contents:

```

sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
```

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

Select all texts inside the file and delete it, Save.

And, on the terminal:

```
echo "deb http://packages.medibuntu.org/ hardy free non-free" | sudo tee -a /etc/apt/sources.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

---

### Post by mosty friedman on 2008-07-08
SUCCESS:) the last method worked..thanks a lot everyone for your time and help..ubuntu forums are truly the best.

---

