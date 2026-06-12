---
title: "Running &quot;sudo nano&quot;"
date: 2007-09-17
forum: General Help
---

### Post by goclimb4123 on 2007-09-17
> Okay! So I figured it out, in case anyone is curious, even though I didn't get any replies.

If you are using the Feisty live-CD to make a live-flash and you want that flash drive to be read/write, do the following.

`fdisk -l` and find out what device/partition your flash drive is, e.g. /dev/sdd1

`sudo nano /etc/mtab' and add the following line at the bottom:

/dev/sdd1 /cdrom vfat ro 0 0

This is descriptive of what it's currently doing, mounting the flash drive read-only into /cdrom as type vfat. Then run:

`sudo mount -t vfat -o rw,remount /dev/sdd1 /cdrom`

and BOOM! you have r/w access.

I am trying to run these commands, but what does he mean when he says: "add the following line at the bottom", plus when i run the 'sudo nano' command it opens a new type of interface that i don't know how to use. Can anyone give advice?

thanks, 

luke

---

### Post by Maestro23 on 2007-09-17
Nano is easy.  It's like moving around in a word processor.  Use your arrows keys, backspace, etc...

It even has commands at the bottom highlighted in white for Save, Exit, etc...

So when it tells you to add something at the bottom of a file, arrow down until you hit the bottom of the file and start plugging in stuff.

---

### Post by goclimb4123 on 2007-09-17
but when i press 'enter' to run the command it just goes to the next line of text...

---

### Post by jocko on 2007-09-17
nano is a text editor that you use to edit text files. Instead of "sudo nano", you can type "gksudo gedit" to get an easier editor.

---

### Post by nick_h on 2007-09-17
I think that you should be editing /etc/fstab rather than /etc/mtab.  /etc/mtab is updated by mount and should not normally be edited.

---

