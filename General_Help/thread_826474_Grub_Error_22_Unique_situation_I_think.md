---
title: "Grub Error 22: Unique situation I think"
date: 2008-06-11
forum: General Help
---

### Post by joeshie on 2008-06-11
Okay I have a common problem but in a sort of unique way.

I have a Dell computer that came with Windows XP SP2 on it pre-installed. I've been using it for years now and decided to install Ubuntu 8.04 Hard Heron. IT sounded great since it takes forever for Windows to load when I simply want to do homework or similar things. I play games on my windows and that is why I still have it.

Anyway, I put in the live CD I got in the mail and did a disk check thing and it came out alright. I tested it out and I thought it was good so I decided to install it.

Now here is the probably unique part. I decided to install it on my external HD with 250 GigaBytes. Okay, my HD *was* split into two partitions: a approximately 210gb one and an approximately 40gb one. The 40gb one had nothing on it while the 250gb on had quite a lot of important stuff on it.

So, I started the install thing an I went through the steps. Then I got to the partition thing and I chose the first option. It made another 40 gigabyte section and installed Ubuntu on their. Then it wanted to migrate stuff from XP. I thought it was strange when it said their was nothing to migrate but I continued on. Then, I restarted my computer and a grub error 22 appeared. Well, I am using Ubuntu Desktop Edition Live CD everytime I want to use my computer. 

Is there anyway to fix it? I want to fix grub and **not** replace grub with the original windows mbr. How do I fix it?

Thanks in advance!

---

### Post by meierfra. on 2008-06-11
I'm pretty sure your  problem can be  fixed. Actually I suggest to install Grub onto the MBR of the external drive and fix the MBR of the internal drive. (otherwise you won't be able to boot into windows when the external drive is unplugged)

To be able to give you detailed instruction  I need some information:

1)  Are you able to switch the boot order in the bios?

2)  Open a terminal in ubuntu (Applications->Accessories->Terminal)

Type

```
sudo fdisk -l
```
(l is a lowercase L)
and post the output.

3)  Still in the terminal type

```
sudo grub
```
and at the "grub>" prompt

```
find /boot/grub/stage2
```

Post the output. 



4) Go to Places->Computer. One of the icon is for your ubuntu partition. Double click it. Go to the folder "/boot" and then to the folder "grub" inside "boot". The folder "grub" contains the file "menu.lst", posts its content.


5)  As long as you are in Places->Computer, you might as well explore the other icons and make sure you can access all you partitions and see all your data.

---

### Post by joeshie on 2008-06-11
Yah, I've switched the boot order before trying to install something else before. That failed because my bios wouldn't read my dvds lol.

Okay:
Here is the sudo information:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+  de  Dell Utility
/dev/sda2   *           5        9366    75200265    7  HPFS/NTFS
/dev/sda3            9367        9725     2883667+  db  CP/M / CTOS / ...

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f9c798a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       25063   201318516    c  W95 FAT32 (LBA)
/dev/sdb2           25064       25113      401625    c  W95 FAT32 (LBA)
/dev/sdb3           25114       30401    42475860    5  Extended
/dev/sdb5           25114       30213    40965718+  83  Linux
/dev/sdb6           30214       30401     1510078+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 


Okay:
Here is the stage 2 output thing:
> (hd1,4)

Thanks!

---

### Post by meierfra. on 2008-06-11
I was faster than your bump:)

---

### Post by joeshie on 2008-06-12
Yes you were lol.

---

### Post by meierfra. on 2008-06-12
> Then, I restarted my computer and a grub error 22 appeared.

Does the grub menu appear before you get error 22? (you might have to press "Esc" after the bios screen) 


Does you external drive show up in the bios?


Try   this

```
sudo grub
```
and  the grub prompt:

```
root (hd1,4)
setup (hd1)
quit

```

Then open "menu.lst" via

```

mkdir ubuntu
sudo mount -t ext3 /dev/sdb5 ubuntu
cd ubuntu/boot/grub
sudo cp menu.lst menu.lst.bu
gksudo  gedit menu.lst
```

Change "hiddenmenu" to "#hiddenmenu"

Change 
"# groot=(hd1,4)" to "# groot=(hd0,4)"

Change all three 

"root (hd1,4)" to "root (hd0,4)"

Save the file.

Then set your bios to boot from the external drive.  Hopefully the Grub menu will appear and let you boot into Ubuntu (we'll work on Windows later)

---

### Post by joeshie on 2008-06-12
Okay, this won't hurt my data on anything right? And no, after the computer loads and the screen that gives you the option to click F2 or F12 appears Grub appears and after a few stuff, error 22 appears. Well, in my bios, there is an option for an USB Drive Device.

---

### Post by meierfra. on 2008-06-12
> Okay, this won't hurt my data on anything right? 

No. You are installing grub the mbr of the external drive  and editing one file.

---

### Post by joeshie on 2008-06-12
K, I'll test it right now. I need to save everything onto my drive.

---

### Post by joeshie on 2008-06-12
Umm meierfra., when i use the find thing i see two areas. Which one do i change and change it into what?

> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

---

### Post by meierfra. on 2008-06-12
Just leave it as it is.

---

### Post by joeshie on 2008-06-12
> 

Change 
"# groot (hd1,4)" to "#groot (hd0,4)"

Change all three 

"root (hd1,4)" to "root (hd0,4)"

Save the file.

Then set your bios to boot from the external drive.  Hopefully the Grub menu will appear and let you boot into Ubuntu (we'll work on Windows later)

Sorry to be annoying, but okay for the groot thing I find this:

> ## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,4)


So when I change it, I don't put a space between the number sign (#) and groot? And how come in the file already, there aren't any spaces to the left and right of the equal sign? What do i do?


> ## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=30597c3b-0cab-4f3d-88f9-e88dd92813ca ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=30597c3b-0cab-4f3d-88f9-e88dd92813ca ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

The root thing looks so far away from the (hd1.4) thing. Is this right? Do I simply change the 1s to 0s? 

Note: When I paste it it looks close to each other O_O

Thanks for helping me.

---

### Post by meierfra. on 2008-06-12
> The root thing looks so far away from the (hd1.4) thing. Is this right? 
Yes


> Do I simply change the 1s to 0s? 
yes. That is all you need to do. Leave everything else as it is

---

### Post by joeshie on 2008-06-12
K. For reals I will check it now lol.

No wait. You didn't answer the groot thing. What do I do about the # sign and the groot. Are they separate or next to each other?

---

### Post by meierfra. on 2008-06-12
Just change the 1 to 0.

---

### Post by joeshie on 2008-06-12
K thanks. For reals reals now.

---

### Post by meierfra. on 2008-06-12
I messed that up in my original post. 

So it needs to be 

# groot=(hd0,4)

---

### Post by joeshie on 2008-06-12
Well I only changed the numbers and nothing about spaces so that wouldn't matter except to people who read this. YOU SOLVED 1/3rd OF THIS PART OF THE PROBLEM!

Okay, I can only choose my CD-ROM drive or the normal hard drive for to boot automatically but I don't mind having to manually choosing the external hard-drive every time I want to use Ubuntu so this part is solved.

I can get into Ubuntu without the CD because of you!

Now the problem: I can get to the login screen but I don't know what to do. Remember I said that I couldn't migrate anything over? How do I log in then? I don't have a username or password I think.

This is typed using the Live CD

---

### Post by meierfra. on 2008-06-12
> Now the problem: I can get to the login screen but I don't know what to do. Remember I said that I couldn't migrate anything over? How do I log in then? I don't have a username or password I think.


You didn't set-up a username and password during installation?

That is very strange and probably means that the LiveCD is defect.

Do this

 At the grub menu at boot up choose recovery mode.  
Once you are  in recover mode type

```
ls /home
```
If you have a username it should be listed.


Then type

```
passwd your_username_here
```

This will let you set a password. type "reboot"

If "ls /home" does not return a username  boot into the LiveCD. At the first screen choose "check CD for errors" (or something like that)

---

### Post by joeshie on 2008-06-12
Well... I got this CD in the mail for free from them.

Okay I'll do what you say.

Um.... Wouldn't that make it easy for hackers to get in if they can easily change the pw word like that?

Okay.. But I did check the CD for errors..

Okay going now.

Umm.. Do I type in "passwd" or the password i want?

---

### Post by meierfra. on 2008-06-12
You type in "passwd" followed by your actual user name. Then it will ask you to choose a password.

---

### Post by meierfra. on 2008-06-12
> Um.... Wouldn't that make it easy for hackers to get in if they can easily change the pw word like that?

If somebody gets physical hold of your computer, yes.

---

### Post by meierfra. on 2008-06-12
> except to people who read this. 

I always go back and fix my mistakes. So post 6 does not have the groot error anymore.

---

### Post by joeshie on 2008-06-12
Back! Anyway, here are my results.

I choose recovery mode.
A whole bunch of stuff start scrolling down the screen and then it gets a menu.

It's called the "Recovery Menu" (How unexpected)

Then there are three options: 

> Resume
Root
X Fix

I'm guessing root so I click that. Then at the bottom a place to type appears.

EDIT: Well, I didn't really click it, I selected it with the keyboard.

I type "ls /mode"

It doesn't work. It says something similar to to like "no such blah". (I'm not sure what it says)

Then I can't do anything else other than keep trying to type that in so I decided to turn it off and check my CD.

It checks the integrity and finds no errors.

Did I do something wrong?

---

### Post by meierfra. on 2008-06-12
>  "ls /mode"

"ls /home"

---

### Post by joeshie on 2008-06-12
Lol! I know what I did wrong... I was looking at the words recovery mode while writing that... Oh well. I need to finish my homework and if you're still on I'll do what you said. Thanks ^_^!

---

### Post by meierfra. on 2008-06-12
I'll probably will be gone by then. But I'll check back in about 10 hours.

If you want to get back into Windows you can fix the  MBR of the internal drive (Since grub is on the external drive, this will not harm Ubuntu).
Click on FixMBR in my signature for a variety of ways how to fix you MBR.

---

### Post by meierfra. on 2008-06-12
You can also add Windows to the Grub menu: Open the file "menu.lst" as before (but skip the "sudo cp menu.lst menu.lst.bu" part)

and add this to the very end of the file


title XP
root (hd1,1)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

---

### Post by joeshie on 2008-06-12
Hey I'm back! So, when I turn on my comptuer it will load grub automatically eve  though I cna't set the USB drive as my main boot load choice. So, Windows XP is already an option. So when I selected that and clicked enter, It says it cannot load or something similar and that the system cd isnot inserted and after you insert it press enter. 

Can you help me?

---

### Post by meierfra. on 2008-06-12
Did you try my previous two posts?

If you fix your MBR (see post 17)  you should be able to boot straight into Windows by booting from internal drive.

If you edit menu.lst (see post 18 ) you should be able to boot into Windows, by booting from the external drive and then pick "Windows XP" at the grub menu.

---

### Post by joeshie on 2008-06-12
Well, I sort of don't want to fix my MBR because if I fix it and I can't access grub anymore (for some reason, I can't choose USB drive device anymore at the boot menu; GRUB loads automatically somehow) then I can't get back to Ubuntu. Okay, but on the grub menu, windows XP is already there. Should I do what you said still?

---

### Post by meierfra. on 2008-06-12
> o, when I turn on my comptuer it will load grub automatically eve though I cna't set the USB drive 

Does the Grub menu also  appear if you boot from internal drive?

---

### Post by meierfra. on 2008-06-12
Seems our two  last posts crossed in cyberspace.

>  (for some reason, I can't choose USB drive device anymore at the boot menu; GRUB loads automatically somehow) 

??????? Maybe you can permanently switch the boot order and you did it by accident? ???????????????????????????/


> Should I do what you said still? 

Try editing "menu.lst" and see what happens.

---

