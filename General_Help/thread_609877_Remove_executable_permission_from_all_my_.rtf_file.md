---
title: "Remove executable permission from all my .rtf files"
date: 2007-11-11
forum: General Help
---

### Post by motoperpetuo on 2007-11-11
For some reason Ubuntu thinks many of my .rtf files are executable. That is, when I double-click on an .rtf file in File Browser, I get a message saying that it is an executable file and asking if I want to run it or display it.

I've been able to get this message to go away with the following command:

sudo chmod -Rv a-x *.rtf

From reading the man page for chmod, it is my understanding that the R option should cause this command to be run recursively, that is, on all .rtf files in all subdirectories. However, the executable permission is only removed from .rtf files in my present working directory, not from subdirectories.

How can I modify this command so that it will work on subdirectories? Does it make a difference that I'm running this on a FAT32 partition? (I dual boot with Windows XP, and having a FAT32 partition to store files I need to manipulate under both OSs seems like the best solution). Any idea why Ubuntu thinks my .rtf files are executable to begin with?

Thanks!

---

### Post by Sebastian Stein on 2007-11-11
> **motoperpetuo said:**
> For some reason Ubuntu thinks many of my .rtf files are executable. That is, when I double-click on an .rtf file in File Browser, I get a message saying that it is an executable file and asking if I want to run it or display it.

I've been able to get this message to go away with the following command:

sudo chmod -Rv a-x *.rtf


Try the following command, it should work recursively:

find . -type f -exec chmod 644 {} \;

> **motoperpetuo said:**
> 
How can I modify this command so that it will work on subdirectories? Does it make a difference that I'm running this on a FAT32 partition? (I dual boot with Windows XP, and having a FAT32 partition to store files I need to manipulate under both OSs seems like the best solution). Any idea why Ubuntu thinks my .rtf files are executable to begin with?


FAT32 doesn't support such permissions, so it might be that the permissions are lost. Actually, the files should have permissions set by the mount command.

Sebastian
--

---

### Post by motoperpetuo on 2007-11-13
thanks very much for your reply. strangely, it didn't work. even more strangely, the .rtf files that on which i wasn't getting the "run or display" message after running my command are now back to displaying the message after a reboot. weird.

here's the output from my command:

mode of `Clonezilla Notes.rtf' retained as 0600 (rw-------)
mode of `notes_openvpn.rtf' retained as 0600 (rw-------)
mode of `qemu.rtf' retained as 0600 (rw-------)

so, it looks to me as if the three .rtf files in this directory do, indeed, have the execute permission removed, but in the GUI the system still gives the option to run them (which does nothing, of course, because they're just text files).

i just tried copying one of the above .rtf files from my FAT32 partition to an ext3 partition, and i don't get the "run or display" message on it when it's on ext3. so maybe this is a quirk with how linux sees certain files on non-native file systems? if anyone has any info, please let me know. thanks!

---

### Post by trash on 2007-11-13
samething happened to me right after I installed Wine.. just curious if this is when it happened to you?

---

### Post by motoperpetuo on 2007-11-14
> **trash said:**
> samething happened to me right after I installed Wine.. just curious if this is when it happened to you?

not sure if it was right after i installed WINE, but i do have WINE installed. maybe that's it.

anyway, it's not a big deal. i'll just chalk it up to the random weirdness that sometimes happens on my six-year-old gateway laptop. it still runs WAY better with ubuntu than it does with windows.

---

### Post by motoperpetuo on 2008-02-09
i just reinstalled my OS and my problem with .rtf files is back. anyone have any idea why ubuntu would think an .rtf file is executable by default? if i go into the file properties and clear the "Allow executing file as a program" check box, i don't get asked whether or not i want to run it when i open it in the GUI, but i have a lot of .rtf files and would rather not do that manually for each one. anyone know some way to clear that check box for all my .rtf files in all subdirectories all at once?

---

### Post by Whiffle on 2008-02-09
Its probably because they're on a fat32 filesystem, which doesn't support permissions.  If I remember correctly, when a fat32 system gets mounted, all files on it are mounted with the same permissions, and that includes executable permissions (probably because directories need to be executable in order to be allowed to open them)

---

### Post by motoperpetuo on 2008-02-09
> **Whiffle said:**
> Its probably because they're on a fat32 filesystem, which doesn't support permissions.  If I remember correctly, when a fat32 system gets mounted, all files on it are mounted with the same permissions, and that includes executable permissions (probably because directories need to be executable in order to be allowed to open them)

i forgot to mention that they are now on my main ext3 partition after reinstalling my OS (i still have a windows XP partition, but i hardly ever use it). does anyone know why ubuntu thinks .rtf files are executable? it's not a major problem, but it seems like fairly bizarre behavior to me.

---

### Post by motoperpetuo on 2008-04-06
and now i've got a totally new dell desktop that came with ubuntu preinstalled. however, all my rtf files are still marked as executable. it's hard to believe that no one else has experienced or noticed this, but i don't see a lot of references to it on the forum.

anyone know how i can remove that "allow executing file as a program" flag en masse with a shell script or something of that manner?

---

### Post by motoperpetuo on 2008-04-07
> **motoperpetuo said:**
> and now i've got a totally new dell desktop that came with ubuntu preinstalled. however, all my rtf files are still marked as executable. it's hard to believe that no one else has experienced or noticed this, but i don't see a lot of references to it on the forum.

anyone know how i can remove that "allow executing file as a program" flag en masse with a shell script or something of that manner?

i found a semi-helpful workaround. it looks like you can go into the permissions of a folder and clear the "allow executing as a program" checkbox (not sure that's the exact name, since i'm at work on a windows computer now), and it removes the executable attribute from all files in all subfolders below that folder. however, it also removes the executable attribute from files that are supposed to have it, so you have to go back in and readd it manually where it's needed.

there's probably some way to automate all of this from the command line, but i don't know what it is yet.

---

