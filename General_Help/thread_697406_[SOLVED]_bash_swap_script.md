---
title: "[SOLVED] bash swap script"
date: 2008-02-15
forum: General Help
---

### Post by dougleduck on 2008-02-15
I've written the following script to add extra swap file space when needed but I keep getting on error

"extraswap.sh: line 7: [4000: command not found" where 400 is the value of size entered. Any idea's? the command echo $size \< $freeMB | bc seems to work fine on its own giving output of 0 or 1.


 #!/bin/bash
freespace=`df | grep -i "/dev/sda2" | awk '{print $4}'`
freeMB=`echo scale=3\; $freespace / 1024 | bc`
echo "Please enter desired swap file size in MB less than the free space on storage, $freeMB MB"
read size
#if [`echo $size \< $freeMB | bc`]
if [$size -lt $freemB]
then
	dd if=/dev/zero of=/media/storage/swapfile bs=1048576 count=$size
	sudo mkswap /media/storage/swapfile
	sudo swapon /media/storage/swapfile
else 
	echo "You must enter a value less than the free disc space or free some up"
	exit
fi

---

### Post by kerry_s on 2008-02-15
there's a program in the repo> sudo apt-get install swapd
there's also swapspace, i never used
there's more, just can't remember the names.

---

### Post by dougleduck on 2008-02-15
I'd like it to be a bash script for the learning experience if nothing else as its my first one.

---

### Post by dougleduck on 2008-02-15
I'd like it to be a bash script for the learning experience if nothing else as its my first one.

---

### Post by mali2297 on 2008-02-15
> **dougleduck said:**
> I've written the following script to add extra swap file space when needed but I keep getting on error

"extraswap.sh: line 7: [4000: command not found" where 400 is the value of size entered. Any idea's? the command echo $size \< $freeMB | bc seems to work fine on its own giving output of 0 or 1.


 #!/bin/bash
freespace=`df | grep -i "/dev/sda2" | awk '{print $4}'`
freeMB=`echo scale=3\; $freespace / 1024 | bc`
echo "Please enter desired swap file size in MB less than the free space on storage, $freeMB MB"
read size
#if [`echo $size \< $freeMB | bc`]
**[COLOR="Red"]if [$size -lt $freemB][/color]**
then
	dd if=/dev/zero of=/media/storage/swapfile bs=1048576 count=$size
	sudo mkswap /media/storage/swapfile
	sudo swapon /media/storage/swapfile
else 
	echo "You must enter a value less than the free disc space or free some up"
	exit
fi

Change the line to
```

if [ $size -lt $freeMB ]

```
Note the space after "[".

---

### Post by dougleduck on 2008-02-16
Thanks, bash is far too senstive; I don't like dynamic white space

I had to change to

freeMB=`echo** scale=0\;** $freespace / 1024 | bc`

as -lt only works with integers.

---

### Post by ghostdog74 on 2008-02-16
use CODE tags to make your code more readable
[quote=dougleduck]
```

 #!/bin/bash
freespace=`df | grep -i "/dev/sda2" | awk '{print $4}'`

```
[/quote]
when using a tool, try to make full use of its options. (so far there is not one option in df to display only the size of one partition)... you can just display /dev/sda2 with du
```

freespace=`df /dev/sda2 | awk 'NR>1{print $4}'`

```
also, awk can perform the tasks of sed,grep,cut , you name it....I would suggest you get familiar with awk in your free time to explore its capabilities. In the above, you got rid of the grep process.
[quote=dougleduck]
```

freeMB=`echo scale=3\; $freespace / 1024 | bc`

```
[/quote]
how about not performing this step and leave it as bytes. It makes your design simpler.You can do whatever calculations later...

---

### Post by dougleduck on 2008-02-16
CODE tags?

I don't actually know what awk does yet, I stole this from someone else :O. I'll look into it some more though,

Its easier in MB to tell how much space is free, then I don't run the risk of trying to make a swap bigger than the space on the drive.

I didn't want to chance it but any idea what would happen if I tried to make a file bigger than the free space? It would just throw up an error I take.

---

### Post by ghostdog74 on 2008-02-16
> **dougleduck said:**
> CODE tags?

the "#" button at the toolbar

---

### Post by dougleduck on 2008-02-17
ooh. I hadn't taken notice of that before. Thought this was something in my code. Noted, thanks.

---

