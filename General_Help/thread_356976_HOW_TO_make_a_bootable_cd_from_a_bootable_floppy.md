---
title: "HOW TO: make a bootable cd from a bootable floppy"
date: 2007-02-09
forum: General Help
---

### Post by majoridiot on 2007-02-09
the last of my 3.5 floppy drives is just about dead. i think a floppy drive has reached the point
of obsolescence in my systems, so it will not be replaced.  the major hitch was that not
all of my boxes can boot from usb and i need to run western digital's utility boot disk
for tests, zeroing drives, etc.  all of my boxes are able to boot from cd boot disks (aka El-
Torito hehe), so converting the floppies to cds was the game.

i used my floppy's dying breaths to figure out how to make a bootable cd from the boot floppy
and having succeeded, i figured i would share so it's death might not be in vain ;)  

the great thing is the entire process comprises all of two rather simple terminal commands... 
ok, maybe three, if you don't have **mkisofs** already installed.

this should work for any dos-style boot floppy and is quick and easy.  open a terminal, and get **mkisofs**:
```
sudo apt-get install mkisofs
```

next, make a working directory and navigate into it (this is IMPORTANT, as **mkisofs** will
create the iso from the contents of the working directory):

```
# mkdir bootcd
# cd bootcd
```

next, we'll use the **dd** linux command to convert the entire floppy disk into one large
image file.  put the bootable floppy into your floppy drive (we're assuming it's fd0) and:

```
# dd if=/dev/fd0 of=boot.img bs=10k count=144
```

the **dd** command is normally used to copy and format a file according to the options
it recieves... because of the way linux handles devices, we can point it at the /dev entry
for the floopy drive and it will treat the entire disk as one contiguous file and output it to the
file boot.img

count=144 tells it to read 144 blocks of 10k bytes (bs=10k) each, or 1.44MB (the entire floppy)

the last step is to make a cd image we can burn:

```
# mkisofs -r -b boot.img -c boot.catalog -o bootcd.iso .
```

-r does a lot of bit fiddling, but essesntially clears the write bits for the cd filesystem (as it's read-only),
sets the read bits so anyone can read it, etc.

-b specifies an "el torito" bootable cd using the boot.img file we just created with **dd**

-c tells mkisofs to create a boot catalog named boot.catalog (it just does it and it's necessary, so i found- LOL); and

-o outputs it all to bootcd.iso, which is now ready to burn by your method of choice and boot!

(be sure not to miss the "**.**" at the end- it tells mkisofs to use the curent directory as the source directory!)

please note that this is a *very* simplistic use of **mkisofs** and the option descriptions
above are not complete, although they are accurate enough for this purpose.  be sure to 
consult the man pages for complete coverage.

```
# man dd
# man mkisofs
```

in the end, we've just used a 700MB cd for 1.44MB worth of data... so yeah, it's wasteful, but i need it.
there are ways to cram the disk full of other utilities, etc. if you would like... but it's kinda beyond the
scope of my present needs. so if it sounds like a good idea, figure it out for yourself and share it with us!

plus, it's bedtime...

---

### Post by anaconda on 2007-02-09
Wow. that is how it is done manually.

But it would be easier to just use k3b
start new data DVD project
then "project>edit boot images" then new
and select a floppy image, which will be used to boot the DVD/CD

And if you dont have a floppy image here is one way to make one:
dd if=/dev/fd0 of=name_of_the_image.img
eg. dd_copy floppy to a file..

This way it is easy to fill the DVD/CD with any data you wish and make it bootable..

---

