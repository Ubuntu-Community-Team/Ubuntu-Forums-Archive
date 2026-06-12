---
title: "data recovery"
date: 2013-05-11
forum: General Help
---

### Post by amarnathg on 2013-05-11
Hi All,

This is Amarnath,

I have installed the **ubuntu13.4 version on windows-7 i**n my laptop(samsung R518 model).
At the time installation i have selected the replace with windows 7 and after completion of the installation procedure all of my files are gone.
in the installation procedure did not asked about the partitions..
[B]

Now how can i recover the lost data[/B]..

[COLOR=#008000]**Please help me to get back of my lost data**[/COLOR]

---

### Post by prodigy_ on 2013-05-11
You may try [Testdisk](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step). Check [this thread](http://ubuntuforums.org/showthread.php?t=2144073) for more info.

Also, though it won't help you right now, in the future please remember to make a full backup before installing, upgrading or otherwise heavily modifying any operating system, making changes to partitions or partitions tables or performing other potentially destructive operations.

---

### Post by Mark Phelps on 2013-05-11
Did you:
1) Replace Win7 with Ubuntu -- or --
2) Replace Ubuntu with Win7

It's not clear which you did from what you wrote.

My own experience is that Windows apps do a better job at recovering data from former Windows filesystems; Linux apps do a better job from former Linux filesystems.

---

### Post by amarnathg on 2013-05-12
Hi Mark Phelps

replace win7 with ubuntu..

---

### Post by amarnathg on 2013-05-13
Hi prodigy,

I tried with testdisk and when i am extract the downloaded testdisk file(testdisk-6.13 and testdisk-6.14-WIP) it giving the error.
it is not installing in my machine.
please help me...

---

### Post by Zteam on 2013-05-13
Just install Testdisk with apt-get (and make sure u have the multiverse repository activated before)

Just run this from the terminal
> sudo apt-get install testdisk

---

