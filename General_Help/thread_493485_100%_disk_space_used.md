---
title: "100% disk space used?"
date: 2007-07-05
forum: General Help
---

### Post by Zyrshnikashnu on 2007-07-05
Today Ubuntu informed me that I had used up all of the free space on /. I knew this couldn't be possible, since I had at least 10 GiB free earlier today and the only thing I'd downloaded was Abiword, which is not a significantly large package.

So I checked with df -h:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              48G   45G     0 100% /
varrun                125M  232K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb            125M  128K  125M   1% /proc/bus/usb
udev                  125M  128K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   33M   92M  27% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1             101G   67G   34G  67% /media/Windows Storage_
/dev/scd0             324M  324M     0 100% /media/cdrom1
```
Obviously, sda2 is the relevant device here. Sure enough, it's completely full!

What could be happening to consume my HDD so fast? Is there a log I can dig up? Someone please point me in the right direction.

---

### Post by kevinlyfellow on 2007-07-05
I've had that happen in the past when running seti@home on redhat 8.  But that was a while ago.  Use the following command to see where the problem lies
```
du -h / | sort -nr | less
```

---

### Post by AlexThomson_NZ on 2007-07-05
Hmm kevinlyfellow that did not seem to work for me.

Do you have a tool in 'Accessories' called 'Disk Usage Analyzer'? (I can't remember if that came with default install or synaptic'ed later)  That should give you a good oversight Zyrshnikashnu...

---

### Post by Zyrshnikashnu on 2007-07-05
Thanks a lot, Alex. Your Disk Usage Analyzer tip did the trick.

On a hunch, I thought cups might be causing the problem because I was having the worst trouble attempting to print today. So I scanned /var and found /var/log/cups was occupying 13.3 GB of disk space. Outrageous!

Thanks a lot.

EDIT:
I used rm to delete the directory and its contents, but df -h still reports no free space. I ran updatedb, but nothing changed. This is strange.

EDIT 2:
Fixed. A cupsys process was somehow impeding progress. I killed it.

---

### Post by kevinlyfellow on 2007-07-05
> **AlexThomson_NZ said:**
> Hmm kevinlyfellow that did not seem to work for me.

Do you have a tool in 'Accessories' called 'Disk Usage Analyzer'? (I can't remember if that came with default install or synaptic'ed later)  That should give you a good oversight Zyrshnikashnu...

Cool, last time I filled up my harddisk gnome refused to start!  I wonder what happened to my command, I've saved it for years!  I must have lost an option somewhere along the way....

Edit: I found my mistake, I can't use the human readable format (duh).  The command should have been
```
du / | sort -nr | less
```

---

### Post by yamraaj on 2007-11-05
i have a 2gb /var partition. of late i am unable to install or uninstall packages. the error:

> dpkg: unable to fill /var/lib/dpkg/updates/tmp.i with padding: No space left on device
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:


so i did this:
> $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              20G  6.6G   13G  35% /
varrun                995M  224K  995M   1% /var/run
varlock               995M     0  995M   0% /var/lock
procbususb            995M  124K  995M   1% /proc/bus/usb
udev                  995M  124K  995M   1% /dev
devshm                995M     0  995M   0% /dev/shm
lrm                   995M   39M  957M   4% /lib/modules/2.6.20-16-generic/volatile
/dev/sda1              99M   33M   62M  35% /boot
/dev/sda7             112G   26G   81G  25% /home
/dev/sda6             9.9G  1.1G  8.4G  11% /opt
/dev/sda5             2.0G   68M  1.9G   4% /tmp
/dev/sda3             2.0G  2.0G     0 100% /var


so my 2 gb is being eaten up by varrun and varlock! how do i tackle this?i think the problem started when i tried to install a LAMP server (i was trying to learn php :( )

PS: I dont know if this is relevant, but i am using 64bit feisty on an hp dc 7700 desktop

---

### Post by Cariboo1938 on 2008-01-19
Hello Ubuntu fans and experts...I need advice....
I have a similar issue as Zyrshnikashnu, the starter of this thread. 
Since a few days, when I restart my computer, I get immediately after logging-in the message:
> Low Disk space
100% of the disk space on /  in use.
When I installed the system, I have made an extra partition of 2 GB for / .

> karibu@karibu-desktop:~$ sudo df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"][SIZE="3"]**/dev/sda2             2.5G  2.3G     0 100% /**[/SIZE][/COLOR]
varrun                503M   96K  503M   1% /var/run
varlock               503M  4.0K  503M   1% /var/lock
udev                  503M  128K  503M   1% /dev
devshm                503M     0  503M   0% /dev/shm
lrm                   503M   38M  466M   8% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             888M   69M  774M   9% /boot
/dev/sda3             7.8G  6.5G  965M  88% /Misc
/dev/sda5              29G  2.2G   26G   8% /home
/dev/sda6              20G  2.4G   16G  13% /usr
/dev/sda7              15G  6.7G  7.1G  49% /var
overflow              1.0M   44K  980K   5% /tmp
karibu@karibu-desktop:~$ 

I followed the advices in this thread but I cannot find the culprit. 
Then I checked /  and I found that the /proc folder uses 1 GB of space...see (1).
It looks like this 1 GB is used by /proc/kcore...see (2),(3).

It also seems that my computer is not as fast as it was and I wonder if the "Low Disk space" is causing a problem. 
I have no idea what's going on on my computer:confused: and I would appreciate if somebody could give me an hint what I should to!

---

### Post by Cariboo1938 on 2008-01-20
Never mind ....issue buried...I don't understand what happened.
After some "cleaning" with```
sudo aptitude autoclean
sudo aptitude remove
```and "Getting rid of Residual Config packages" with Synaptic
the computer is back to "normal", (although /proc/kcore still has 1.02GB in size = half ot the / partition sda2):> karibu@karibu-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**[COLOR="Red"][SIZE="3"]/dev/sda2             2.5G  370M  2.0G  16% /[/SIZE][/COLOR]**
varrun                503M   80K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M  128K  503M   1% /dev
.................
......
karibu@karibu-desktop:~$ 
If somebody has an idea or thought to this, I would like to learn more.....
Thanks:)

---

### Post by chrisccoulson on 2008-01-20
> **yamraaj said:**
> so my 2 gb is being eaten up by varrun and varlock! how do i tackle this?i think the problem started when i tried to install a LAMP server (i was trying to learn php :( )

PS: I dont know if this is relevant, but i am using 64bit feisty on an hp dc 7700 desktop

Your 2GB on /var is not being eaten up by /var/run or /var/lock, as these both use temporary filesystems (in RAM), and use no space on disk.

The 2GB on /var is most likely being used up by /var/cache/apt or /var/log. Have you tried:
```
sudo apt-get clean
```

---

### Post by chrisccoulson on 2008-01-20
> **Cariboo1938 said:**
> Never mind ....issue buried...I don't understand what happened.
After some "cleaning" with```
sudo aptitude autoclean
sudo aptitude remove
```and "Getting rid of Residual Config packages" with Synaptic
the computer is back to "normal", (although /proc/kcore still has 1.02GB in size = half ot the / partition sda2):
If somebody has an idea or thought to this, I would like to learn more.....
Thanks:)

Remember, /proc takes up no physical space on your disk. See [http://en.wikipedia.org/wiki/Procfs]("http://en.wikipedia.org/wiki/Procfs")

---

