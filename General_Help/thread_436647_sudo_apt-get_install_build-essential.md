---
title: "sudo apt-get install build-essential"
date: 2007-05-08
forum: General Help
---

### Post by rygar on 2007-05-08
I'm trying to compile source code I've downloaded, and I'm under the impression I need to install build-essential.  Is this correct?

I've tried "sudo apt-get install build-essential", but it asks for my Ubuntu cd.  Even when I download the tarball from the Ubuntu website, it asks me to insert my Ubuntu cd.  I don't have the CD with me and I don't feel like downloading the ISO just to install this...  Is it really necessary?  What's the point of the repositories if I have to put my CD in?

Thanks,
jeff

---

### Post by deanjm1963 on 2007-05-08
Open synaptic, then under "Settings" open "Repositories" and uncheck the Ubuntu CD-Rom entry, you can now download directly from the repos without the need of the CD.

---

### Post by kingjere on 2007-05-08
you need to edit your sources file. 

Of course you should always make a backup first.

```
sudo cp /etc/apt/sources.list sources.list.bak
```

At the top you will see a line that starts like:

deb cdrom: blah blah blah

put a # infront of it. Then save.

```
sudo apt-get update
```
```
sudo apt-get install build-essentials
```

---

### Post by rygar on 2007-05-08
thanks guys!

---

### Post by SuciAlways on 2007-12-10
> **kingjere said:**
> you need to edit your sources file. 

Of course you should always make a backup first.

```
sudo cp /etc/apt/sources.list sources.list.bak
```

At the top you will see a line that starts like:

deb cdrom: blah blah blah

put a # infront of it. Then save.

```
sudo apt-get update
```
```
sudo apt-get install build-essentials
```

I met with 'E: Couldn't find package build-essentials'
So it should be sudo apt-get install build-essential instead of sudo apt-get install build-essentials.

---

