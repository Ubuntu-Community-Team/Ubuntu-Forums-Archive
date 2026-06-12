---
title: "Create a boot diskette with Bash"
date: 2008-06-23
forum: General Help
---

### Post by jeroensd on 2008-06-23
Hello everyone,

I'm following some Bash lessons at school and I have to make some examples. I'm now working on this one:

[I]Create a script that writes a boot image to a diskette using the dd utility. If the user tries to interrupt
the script using Ctrl+C, display a message that this action will make the diskette unusable.[/I]

So i'm stuck on how to create a boot diskette with the dd utility. Can anyone help me with that? 

Right now I have a script that can format a diskette using the fdformat functions. I've searched internet and I found some boot diskette examples but they are not working well... I hope someone can help me...

Greetings,
Jeroen

---

### Post by VMC on 2008-06-23
Maybe something like this:

```
dd if=floppy.img of=/dev/fd0 count=1 bs=1440k
```

---

### Post by logos34 on 2008-06-23
maybe this will help:
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

---

### Post by jeroensd on 2008-06-23
> **VMC said:**
> Maybe something like this:

```
dd if=floppy.img of=/dev/fd0 count=1 bs=1440k
```

It says "Opening floppy.img: no such file or directory"

What can I do about this?

---

### Post by jeroensd on 2008-06-23
> **logos34 said:**
> maybe this will help:
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

Yeah, But i need to place it in a bash script So i think I can't use that example. But thanks anyway!

---

### Post by plucky on 2008-06-23
> **jeroensd said:**
> It says "Opening floppy.img: no such file or directory"

What can I do about this?

Floppy.img has to be a bootable floppy image.

If you have a live CD mount it in your CD drive and navigate to the /install directory.Search for a file called **sbm.bin** and copy it to your home directory.

Then cd to home directory and in a terminal window ```
dd if=sbm.bin of=/dev/fd0
```
This will create a bootable floppy of Smart Boot Manager provided there are no errors during the copy.

sbm.bin is a bootable floppy image.


Good Luck

---

### Post by VMC on 2008-06-23
> **jeroensd said:**
> It says "Opening floppy.img: no such file or directory"

What can I do about this?

I'm sorry, I thought you already had a floppy boot image.

Here's one: [ftp://mirror.cs.wisc.edu/pub/mirrors/linux/redhat/9/en/os/i386/images/bootdisk.img](ftp://mirror.cs.wisc.edu/pub/mirrors/linux/redhat/9/en/os/i386/images/bootdisk.img)

---

### Post by jeroensd on 2008-06-24
Hi! Is there a way to create a boot diskette without a Ubuntu cd?

Lets say, i'm writing a script and If I send that script to a friend and if he runs it, a boot diskette will be automatticaly made (using the dd command)(without a ubuntu cd). Would that be possible

---

### Post by VMC on 2008-06-24
> **jeroensd said:**
> Hi! Is there a way to create a boot diskette without a Ubuntu cd?

Lets say, i'm writing a script and If I send that script to a friend and if he runs it, a boot diskette will be automatticaly made (using the dd command)(without a ubuntu cd). Would that be possible

You need some sort of Linux to run dd commands. They do have a complete(albeit small) Linux on a floppy, but I'm not sure exactly what your wanting to do.

Here is [Toms Floppy Boot Disk]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/tomsrtbt-1978.shtml")

---

### Post by jeroensd on 2008-06-25
> **VMC said:**
> You need some sort of Linux to run dd commands. They do have a complete(albeit small) Linux on a floppy, but I'm not sure exactly what your wanting to do.

Here is [Toms Floppy Boot Disk]("http://linux.softpedia.com/get/System/Operating-Systems/Linux-Distributions/tomsrtbt-1978.shtml")

I'm right now running on Ubuntu 7.10.  It should be possible to create a boot diskette with Ubuntu too right? I mean, without the live cd.

I'm using Windows for years, and it's always been possible to click a button for a boot diskette to be created.


The meaning of the script is this:
I e-mail you (or a friend) this script. You place a diskette in your computer, you run the script with the terminal, and a boot diskette would be created (without the use of the Ubuntu live cd) with the dd command.

I think that should be possible right? :D

Greetings, 
Jeroen

---

### Post by VMC on 2008-06-25
> **jeroensd said:**
> I'm right now running on Ubuntu 7.10.  It should be possible to create a boot diskette with Ubuntu too right? I mean, without the live cd.

I'm using Windows for years, and it's always been possible to click a button for a boot diskette to be created.


The meaning of the script is this:
I e-mail you (or a friend) this script. You place a diskette in your computer, you run the script with the terminal, and a boot diskette would be created (without the use of the Ubuntu live cd) with the dd command.

I think that should be possible right? :D

Greetings, 
Jeroen

Then you would do as I suggested above, with:

dd if=floppy.img of=/dev/fd0 count=1 bs=1440k

The floppy.img would be a floppy bootable image like Toms Bootable image.
That's the only way to use the "dd" command. You need to supply an image to the command.

I think your thinking that if you supply a "dd" script then your friend will be able to make a bootable disk. But you still need to supply the image as well

---

### Post by jeroensd on 2008-06-30
Hello everyone,

I've got my script almost working. But i'm still stuck with the trap command.

This is the script so far:

```

clear
#!/bin/bash

echo "Do you want to create a boot diskette (yes/no)?"
echo

read answer
echo

function sigterm
{
	trap "" 1 2 3
 	echo -n "Are you sure you want to interupt this action (Y/N)?"
	read -nl -s reply
	case "$reply" in
		Y|y)
			echo
			stty echo
			exit 1
			;;
		N|n)
			echo "continuing..."
			;;
		*)
			tput cub 21
			sigterm
			;;
		esac
}

if [ $answer == "yes" ]
then
	stty -echo
	while true; do
	trap "sigterm" 1 2 3
	sleep 10
	
	sudo umount /dev/fd0
	fdformat /dev/fd0
	dd if=/home/jeroen/Linux/Opdrachten/bootdisk.img of=/dev/fd0 count=1 bs=1440k
	echo
	done
	
	echo "Your boot diskette is ready for use!" 
	echo "U can use the prompt now."
	echo

else
	echo
	echo "No boot diskette will be made. You can work in the prompt now"
	echo
fi

```

I can't get the trap command working. I also tried only this line:

```

trap "echo 'You cannot interupt this process'" INT TERM

```

And the line will be printed when inserting a command but the action right at that moment stops too.

So the program work this way:

   1. Question if the user wants to make a boot diskette
   2. Read input
   3. Format the diskette
   4. Copy image to the diskette
   5. Display a complete message
   6. else the script will be closed


During the progress of point 3 and 4 I want a message "Are you sure you want to interrupt this process (Y/N)"

If Yes; a message will be displayed and users can work further in the prompt

if No; all actions will go on.

How can I do this? I understand the trap command but I just can't get it to work....

---

### Post by VMC on 2008-06-30
It's when a while since I've used bash traps, but arn't you trapping on the signal instead of a commend? Ex. trap "rm $TEMP_F; exit" SIGHUP SIGINT SIGTERM

You have a function name the same as a trap signal name only in lower case .

---

