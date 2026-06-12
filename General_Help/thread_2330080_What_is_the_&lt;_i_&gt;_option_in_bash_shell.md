---
title: "What is the &lt; i &gt; option in bash shell?"
date: 2016-07-07
forum: General Help
---

### Post by mikodo on 2016-07-07
Hi,

Why is < i > used in terminal instance below. I understand  the run, mount bind. I am guessing < i >** allows one to run in the terminal's interactive shell with non-option arguments**. But, I dunno.

```
sudo mount /dev/sda1 /mnt 

for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done

# instead of running each individually.

#sudo mount --bind /dev /mnt/dev
#sudo mount --bind /pts /mnt/pts
#sudo mount --bind /proc /mnt/proc
#sudo mount --bind /sys /mnt/sys

sudo chroot /mnt 

```
Thank you.

[https://www.gnu.org/software/bash/manual/html_node/What-is-an-Interactive-Shell_003f.html#What-is-an-Interactive-Shell_003f](https://www.gnu.org/software/bash/manual/html_node/What-is-an-Interactive-Shell_003f.html#What-is-an-Interactive-Shell_003f)

---

### Post by steeldriver on 2016-07-07
In that case, i is just the name of a variable - it is nothing to do with the -i ("minus i") command line option to bash itself - you could equally well write

```

for banana in /dev /dev/pts /proc /sys /run; do sudo mount -B $banana /mnt$banana; done

```

---

### Post by mikodo on 2016-07-07
Okay :)

I'll look up variables.

Thank you.

Addendum: Just like you said. It's the name of the variable.

---

