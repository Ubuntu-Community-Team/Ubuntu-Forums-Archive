---
title: "new 2 ubuntu, cant change exteranal HD premissions"
date: 2007-10-01
forum: General Help
---

### Post by jay123035 on 2007-10-01
im trying to change the permissions from root to 'everyone' on two external HDs (My Book and funtional name here)  

the code at this point.

ptop:~$ cd /media
jay@jay-laptop:/media$ 1s -a1
bash: 1s: command not found
jay@jay-laptop:/media$ 1s
bash: 1s: command not found
jay@jay-laptop:/media$  1s -as
bash: 1s: command not found
jay@jay-laptop:/media$ ls -al
total 348
drwxr-xr-x  6 root root      4096 2007-10-01 11:08 .
drwxr-xr-x 21 root root      4096 2007-09-30 11:25 ..
lrwxrwxrwx  1 root root         6 2007-09-29 13:57 cdrom -> cdrom0
drwxr-xr-x  2 root root      4096 2007-09-29 13:57 cdrom0
-rw-r--r--  1 root root       154 2007-10-01 11:08 .hal-mtab
--wxr-x---  1 root root         0 2007-04-15 04:56 .hal-mtab-lock
dr-xr-xr-x  1 root root    327680 2007-09-29 22:44 My Book
drwxrwx---  4 root plugdev   8192 1969-12-31 16:00 sda3
dr-xr-x---  1 root plugdev   4096 2007-09-29 20:38 sda5
jay@jay-laptop:/media$ sudo chmod a+w my book
Password:
chmod: cannot access `my': No such file or directory
chmod: cannot access `book': No such file or directory
jay@jay-laptop:/media$ 
jay@jay-laptop:/media$  
jay@jay-laptop:/media$ sudo chmod a+w dr-xr-xr-x
chmod: cannot access `dr-xr-xr-x': No such file or directory
jay@jay-laptop:/media$ ls -al
total 368
drwxr-xr-x  8 root root      4096 2007-10-01 13:43 .
drwxr-xr-x 21 root root      4096 2007-09-30 11:25 ..
lrwxrwxrwx  1 root root         6 2007-09-29 13:57 cdrom -> cdrom0
drwxr-xr-x  2 root root      4096 2007-09-29 13:57 cdrom0
drwx------  3 jay  root     16384 1969-12-31 16:00 DellUtility
dr-xr-xr-x  1 root root      4096 2007-09-21 22:09 funtional name here
-rw-r--r--  1 root root       349 2007-10-01 13:43 .hal-mtab
--wxr-x---  1 root root         0 2007-04-15 04:56 .hal-mtab-lock
dr-xr-xr-x  1 root root    327680 2007-09-29 22:44 My Book
drwxrwx---  4 root plugdev   8192 1969-12-31 16:00 sda3
dr-xr-x---  1 root plugdev   4096 2007-09-29 20:38 sda5
jay@jay-laptop:/media$ sudo chmod a+w 327680
chmod: cannot access `327680': No such file or directory
jay@jay-laptop:/media$ 


(i hope im not showing more than i should) 

ok. my book tells me i should see 'usbdisk' but i don't. i do see the names of both drives i want to change and that the drives have 'root' in two columns. so i'm guessing thats what i need to change. 

the book says 
      foo@bar;~$ sudo chmod a+w usbdisk

im guessing that i need to change 'usbisk' to something but damn if i don't know and the 4 or 5 things i can figure arnt working. so if im on the right track what is the next command if im not HELP PLEASE

sub question: is there a help doc that brakes down 'code txt' to the symbols on my key board (everyday dell laptop)
sub sub question: how do i put my code in cool gray boxes like everyone else? (seams to be ezzer to read)

---

### Post by kestas.j on 2007-10-01
To change permission you have to use the following command:
> sudo chmod a+rwx  -R  '/media/funtional name here'
This will give right to all users to create, read and execute (search) files and folders on your drive. All Linux systems are case sensitive, so your try with "my book" would not be equal to "My book". If there is space between words in files name use ' symbol as in the sample I've wrote.

kestas.j

---

### Post by strabes on 2007-10-01
Yeah, I think your problem was not using the "-R" flag, which stands for "recursive."

---

### Post by bettlebrox on 2007-10-01
If it's an external drive with a FAT32 (windows) filesystem, you can only change the permissions and ownership of the files when the drives are mounted (by editing /etc/fstab). Poke around in the forums and you'll find the solution.

Luck! :)

---

### Post by jay123035 on 2007-10-01
thanks for the quick response  :)

:(     this is what i tried. where am i going wrong.

i used copy and past as much as i could.  and  tried every combinational or alteration of the code provided that i though would make sense.  still no go.

if i remember correctly (install as on Saturday) both drives are NTFS. my friend, a long time 6.06 user, uses a ntfs drive so i would only guess that my 7.04 would support one  too. (we matched packages and programs so that shouldn't be an issue) and i can read and copy form the drives. 
            I'm also guessing that "owner ship" or permissions would come before the  file system in "order of usability requirements"  
 
code.


jay@jay-laptop:~$ sudo chmod a+rwx -/media/funtional name here
Password:
chmod: invalid option -- /
Try `chmod --help' for more information.
jay@jay-laptop:~$ sudo chmod a+rwx -R /media/funtional name here
chmod: cannot access `/media/funtional': No such file or directory
chmod: cannot access `name': No such file or directory
chmod: cannot access `here': No such file or directory
jay@jay-laptop:~$ sudo chmod a+rwx-R /media/funtional name here
chmod: invalid mode: `a+rwx-R'
Try `chmod --help' for more information.
jay@jay-laptop:~$ sudo chmod a+rwx -R /media/My Book
chmod: cannot access `/media/My': No such file or directory
chmod: cannot access `Book': No such file or directory
jay@jay-laptop:~$ /ect/fstab
bash: /ect/fstab: No such file or directory
jay@jay-laptop:~$ /cd /media
bash: /cd: No such file or directory
jay@jay-laptop:~$ cd /media
jay@jay-laptop:/media$ ls -al
total 376
drwxr-xr-x 10 root root      4096 2007-10-01 16:33 .
drwxr-xr-x 21 root root      4096 2007-09-30 11:25 ..
lrwxrwxrwx  1 root root         6 2007-09-29 13:57 cdrom -> cdrom0
drwxr-xr-x  2 root root      4096 2007-09-29 13:57 cdrom0
drwx------  2 root root      4096 2007-10-01 16:18 DellUtility
drwx------  3 jay  root     16384 1969-12-31 16:00 DellUtility_
drwxrwxrwx  2 root root      4096 2007-10-01 16:18 funtional name here
dr-xr-xr-x  1 root root      4096 2007-09-21 22:09 funtional name here_
-rw-r--r--  1 root root       546 2007-10-01 16:33 .hal-mtab
--wxr-x---  1 root root         0 2007-04-15 04:56 .hal-mtab-lock
dr-xr-xr-x  1 root root    327680 2007-09-29 22:44 My Book
drwxrwx---  4 root plugdev   8192 1969-12-31 16:00 sda3
dr-xr-x---  1 root plugdev   4096 2007-09-29 20:38 sda5
jay@jay-laptop:/media$ sudo chmod a+rwx -R funtional name here
chmod: cannot access `funtional': No such file or directory
chmod: cannot access `name': No such file or directory
chmod: cannot access `here': No such file or directory
jay@jay-laptop:/media$ sudo chmod a+rwx -R /funtional name here
chmod: cannot access `/funtional': No such file or directory
chmod: cannot access `name': No such file or directory
chmod: cannot access `here': No such file or directory
jay@jay-laptop:/media$ sudo chmod a+rwx -R /media/funtional name here
chmod: cannot access `/media/funtional': No such file or directory
chmod: cannot access `name': No such file or directory
chmod: cannot access `here': No such file or directory
jay@jay-laptop:/media$ /ect/fstab
bash: /ect/fstab: No such file or directory
jay@jay-laptop:/media$ 

i don't know why but you will notice that after i restart 'funtional name here' and 'DellUtility" have loaded twice or some strange thing like that. could that that effect it.

---

### Post by kestas.j on 2007-10-02
Have you installed ntfs-config tool to mount NTFS in RW mode? This works with internal HDD, but I've not tested on external. Use the following command:
> sudo apt-get install ntfs-config
Run the program by:
> sudo ntfs-config
and check the box to mount NTFS external drive in read/write mode.

If this still not work for you, just copy and paste the following command into the terminal:

> sudo chmod a+rwx -R '/media/funtional name here' '/media/My Book'

Now to understand what all these letters mean I explain:
As a super user - the owner of this folder (sudo) you want to change permissions (chmod) for all users (a) by adding (+) them rights to read write and execute (rwx) the folder and its contents (-R) at following locations ('/media/funtional name here' and '/media/My Book'). if you will not use ' symbol in the beginning and the end of the link, etc.: _/media/funtional name here_ , the system will try to change permissions to 3 different files, separated by space symbol. It means the system will try to change permissions for: 1. /media/funtional 2. name 3. here , any of which most probably does not exist in your system.

Hope it will work for you.
kestas.j

---

### Post by kestas.j on 2007-10-02
.

---

