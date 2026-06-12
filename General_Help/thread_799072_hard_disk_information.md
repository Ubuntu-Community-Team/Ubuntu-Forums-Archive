---
title: "hard disk information"
date: 2008-05-18
forum: General Help
---

### Post by lenetfm on 2008-05-18
how can i get hard disk information using C  without using system call help plzzzzzzzzz

---

### Post by Monicker on 2008-05-18
What kind of information are you wanting exactly?

You can use gparted to get information about the size and partitions.

You can also get that from the terminal:

```
sudo fdisk -l
sudo hdparm -I /dev/sda
```

---

### Post by sdennie on 2008-05-18
You should be able to open some of the files in /sys/block/some_device and read the information from C.  You'll have to look around at some of those files but, you can just cat them to see what is in them.  For example, this will return the model of the first SATA drive:

```

cat /sys/block/sda/device/model

```

---

### Post by ibuclaw on 2008-05-18
Are you needing to build a specific program, or do you just need the info to look at?

If you are building a program, I'd advise that you'd best ask in the Programming Forums (I would help, but I'm in need to brush up on my C skills a bit).

Linux has everything you need to read the hard disk information.
But, I'd recommend that you'd use the "**popen()**" command, rather than the "**system()**"  command. Reasons because it is much safer, and more CPU/kernel friendly. (The System() command takes full priority of any other job, so all other programs (and in some case even the Linux kernel) are left to hang/wait till the command has finished!)

Here is a small program that will show the disk info file:
[PHP]
#include <stdio.h>

int main()
{
  FILE *cmd;
  char output[512];
  /* Open the pipe and get the information */
  cmd = popen("cat /proc/scsi/scsi","r");
  /* Read from the pipe line by line */
  while (fgets(output, sizeof(output), cmd) != NULL ) {
    printf("%s", output);
  }
  return 0;
  /* Close the pipe */
  pclose(cmd);
}
[/PHP]

Now, all information about all hard disk drives are stored in the file "**/proc/scsi/scsi**"

As the above code shows, you can get this information using "**cat /proc/scsi/scsi**".
Although, if you download and install **lsscsi**
```
sudo apt-get install lsscsi
```
you can obtain a more human readable version.

[EDIT]
Or, if you wish to exhibit specific devices, there is a package in the repository called "scsitools" too.
```
sudo apt-get install scsitools
```
Just type in "man scsiinfo" to find out more about it.

Though, if you are certain that you want to avoid the use of external programs, you can always just use the "**fopen**" and "**fclose**" C features to read the "**scsi**" file character by character.

Regards
Iain

---

### Post by lenetfm on 2008-05-19
> **tinivole said:**
> Are you needing to build a specific program, or do you just need the info to look at?

If you are building a program, I'd advise that you'd best ask in the Programming Forums (I would help, but I'm in need to brush up on my C skills a bit).

Linux has everything you need to read the hard disk information.
But, I'd recommend that you'd use the "**popen()**" command, rather than the "**system()**"  command. Reasons because it is much safer, and more CPU/kernel friendly. (The System() command takes full priority of any other job, so all other programs (and in some case even the Linux kernel) are left to hang/wait till the command has finished!)

Here is a small program that will show the disk info file:
[PHP]
#include <stdio.h>

int main()
{
  FILE *cmd;
  char output[512];
  /* Open the pipe and get the information */
  cmd = popen("cat /proc/scsi/scsi","r");
  /* Read from the pipe line by line */
  while (fgets(output, sizeof(output), cmd) != NULL ) {
    printf("%s", output);
  }
  return 0;
  /* Close the pipe */
  pclose(cmd);
}
[/PHP]

Now, all information about all hard disk drives are stored in the file "**/proc/scsi/scsi**"

As the above code shows, you can get this information using "**cat /proc/scsi/scsi**".
Although, if you download and install **lsscsi**
```
sudo apt-get install lsscsi
```
you can obtain a more human readable version.

[EDIT]
Or, if you wish to exhibit specific devices, there is a package in the repository called "scsitools" too.
```
sudo apt-get install scsitools
```
Just type in "man scsiinfo" to find out more about it.

Though, if you are certain that you want to avoid the use of external programs, you can always just use the "**fopen**" and "**fclose**" C features to read the "**scsi**" file character by character.

Regards
Iain

thanks for the answer but i want to see the how many partition disk there is in my disk and their free size and total size in a C program is there any system function can do this ? so can you help me with this ? thanks again

---

### Post by ibuclaw on 2008-05-19
Yes, there is...
```
df -h
```
Take my code and replace the popen line with this:
[PHP]cmd = popen("df -h","r");[/PHP]
Although, it will give you a bit more information that what you asked for, though if you know how to manipulate strings, your job is pretty much done for you!

[EDIT]
Also, if you want to know what type the filesystem is, add a "T" to the command too.
```
df -hT
```

Regards
Iain

---

