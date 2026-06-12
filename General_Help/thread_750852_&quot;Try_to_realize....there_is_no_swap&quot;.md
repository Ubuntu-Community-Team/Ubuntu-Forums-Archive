---
title: "&quot;Try to realize....there is no swap&quot;"
date: 2008-04-09
forum: General Help
---

### Post by AdrianStrays on 2008-04-09
Rather than explain my confusion regarding swap, I'll show a picture:

[IMG]http://img.photobucket.com/albums/v322/ThePaleWhiteRose/Screenshot.png[/IMG]

There is a partition for swap....but there is no swap?

PS did I allocate to much for swap?

---

### Post by ELF_O8 on 2008-04-09
I don't know how to help, but i would like to know what distro/theme you are running.
it looks freaking sweet.

---

### Post by AdrianStrays on 2008-04-09
Ubuntu Studio.  I originally was hestiant to use Ubuntu because...well....its really ugly. (Shallow I know) but I am a musician and happened to stumble upon Ubuntu Studio.  It is gorgeous, the login screen is gorgeous, the background is gorgeous, the splash is and theme is...well its okay but its light years ahead of what we've got on Ubuntu now. If you want you can look at screen shots, or the various stuff for the different versions.

[http://ubuntustudio.org/]("http://ubuntustudio.org/")

> [https://wiki.ubuntu.com/UbuntuStudio/Artwork](https://wiki.ubuntu.com/UbuntuStudio/Artwork)

---

### Post by sujoy on 2008-04-09
try manually with swapon.

# swapon /dev/sda4

and if that doesn't work then read this 

[http://www.linuxmanpages.com/man8/mkswap.8.php](http://www.linuxmanpages.com/man8/mkswap.8.php)

---

### Post by Charkel on 2008-04-10
You made a 5GB swap? :D
512mb is enough ;)

---

### Post by ELF_O8 on 2008-04-10
since it is already on this thread:

what does the swap file for?
is it like windows page files?

---

### Post by AdrianStrays on 2008-04-10
> You made a 5GB swap?
:oops: Well I didn't know what it was for!  

> # swapon /dev/sda4

I entered that into the terminal and nothing happened.

---

### Post by sujoy on 2008-04-10
that means the command worked. 

so now you can check if your swap file is being recognised by the system with this command

$ free -m 

this will show RAM and SWAP usage in megabytes. check the out put to see if your swap space is recognised.

my output looks like this:

> sujoy@debian:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1002        673        328          0         92        277
-/+ buffers/cache:        303        699
Swap:         1906          0       1906
sujoy@debian:~$ 

---

### Post by hyperair on 2008-04-10
Swap in Linux is similar to the Page File in Windows. It's a file (or partition in this case) on the disk where bits of the RAM are swapped out in order to make space for currently running applications. In other words, when your RAM cannot hold everything, it starts to fill your Swap. By this logic, it would be appropriate to assign a small Swap if you have a large memory space which you never fill. However, there is one more function of the Swap that is not in the Windows Page File. When you hibernate your computer, ALL the contents of the RAM are swapped out. basically the Swap is not only the place for you to store bits of memory temporarily while it cannot fit in the RAM, it's also a place to store the entire RAM to hibernate the computer.

---

### Post by AdrianStrays on 2008-04-10
adrian@Alpha-60-Workstation:~$ free -m 
             total       used       free     shared    buffers     cached
Mem:          1887        929        957          0         26        579
-/+ buffers/cache:        323       1563
Swap:            0          0          0

:(

---

### Post by Saint Angeles on 2008-04-10
> **ELF_O8 said:**
> since it is already on this thread:

what does the swap file for?
is it like windows page files?
yes... except linux uses a swap partition which is faster than a swap file.

---

### Post by gsmanners on 2008-04-10
If you're in a 32-bit system, then the upper limit for swap is 2 GB.

---

### Post by sujoy on 2008-04-10
so does that mean that since he has 5GB dedicated to swap, the kernel is just ignoring that, because its > 2GB? 

well in that case i guess it can be resized with gparted

---

### Post by hyperair on 2008-04-10
That is incorrect. I just created a temporary swap file and used it. This is the output of "free -m" on my system:
```
             total       used       free     shared    buffers     cached
Mem:          1265       1239         26          0          5        923
-/+ buffers/cache:        309        955
Swap:         2537        596       1940

```

This is a Pentium 4 2.66GHz system.

@sujoy: I also noticed that some time is required for the swap to come on. It's not instantaneous. Wait for somewhere around 10 seconds then try "free -m" after doing "sudo swapon /dev/sda4" To get it to start up on boot you should have an entry in your /etc/fstab file.
```
/dev/sda4 swap sw 0 0
```

---

### Post by 3rdalbum on 2008-04-10
Don't worry about the lack of swap. 1.8 gigs of RAM is plenty enough to avoid having to use swap.

---

### Post by solitaire on 2008-04-10
You have a swap disk but it's not needed by the OS at the moment (that's why it's marked as "NO Swap" on the system info) don't worry it will use it if it needs it. (Unlike windows which uses SWAP files no matter if it's needed or not! i think..)

---

### Post by hyperair on 2008-04-10
When turned on, whether it is needed or not, the swap will be shown as present. If it isn't then there is something definitely wrong.

---

### Post by anaconda on 2008-04-10
> **sujoy said:**
> try manually with swapon.

# swapon /dev/sda4

and if that doesn't work then read this 

[http://www.linuxmanpages.com/man8/mkswap.8.php](http://www.linuxmanpages.com/man8/mkswap.8.php)

I think you need to use sudo for that command!

eg.
```
sudo swapon /dev/sda4
```

And if the partition isn't formatted as swap you will also need to run the:
```
sudo mkswap /dev/sda4
sudo swapon /dev/sda4
```
(be careful that the partition you run mkswap is correct, because if you accidentally run mkswap on a wrong partition.. all data in that partition is lost!

another thing. if you have run the mkswap command, or eg. reinstalled linux the UUID of your swap partition has changed. and your /etc/fstab file propably tries to mount the swap using the old UUID -address, so mounting swap at boot time wont work.

That is why it is better to refer to a swap partition in your fstab by using the /dev/sda4 mode and not the UUID!

If this is the case you might want to edit your /etc/fstab -file and change the UUID format to /dev/sda4..

```
sudo gedit /etc/fstab 
```
and search for this kind of lines:
# /dev/sda4
UUID=64d0f868-095f-4970-9da8-89e3ae8aa2ed none            swap    sw              0       0

and change that to :
# /dev/sda4
/dev/sda4 none            swap    sw              0       0

OR you could just check that the UUID is correct.
to see which are the existing (correct)  UUID:s just type:
ls -l /dev/disk/by-uuid/
in terminal

---

### Post by sujoy on 2008-04-10
> **anaconda said:**
> I think you need to use sudo for that command!

eg.
```
sudo swapon /dev/sda4
```




yep thats why i put the "#" specifically.

anyways lets wait for the OP to try out the commands and report.

---

### Post by Nathan_M on 2008-04-10
Can't help with the problem, but I suggest going with a swap size of 1.5 times your RAM. that way there's plenty available if you want to hibernate the computer. There's nothing wrong with 5G of swap... except that it unnecessarily takes up 5G of disk space!

---

### Post by AdrianStrays on 2008-04-11
Actually, I found a solution that didn't even involve the terminal.  I was about to resize the swap to make it smaller, when I noticed that their was an option called "swapon" I clicked that, and now it reports that there is swap.

So you can have a swap file bigger than two GB, apparently.

---

### Post by munkyeetr on 2008-04-11
EDIT: Sorry, missed a whole page of posts when I posted this! :oops:

```

sudo swapon /dev/sda4

```

Don't put the # sign in front of it.

---

### Post by hyperair on 2008-04-11
Actually, the "#" in front indicates that the command is to be run as root. "$" indicates that it is to be run as a regular user. An easy example to see how this comes about is to run "sh". The prompt has "$" in front if you're a regular user and "#" in front if you're root.

---

