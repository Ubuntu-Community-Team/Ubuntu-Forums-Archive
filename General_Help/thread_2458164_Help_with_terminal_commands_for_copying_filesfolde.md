---
title: "Help with terminal commands for copying files/folders"
date: 2021-02-17
forum: General Help
---

### Post by 4dri4n on 2021-02-17
hi, i'm beginner with linux community

who know the terminal commands that can copy files, folders to the flash USB and how the steps exactly? 
and thanks. (y)

---

### Post by Bashing-om on 2021-02-18
4dri4n - Hello

Sure -
1) insert the USB flash drive
wait for it - wait for it - when the notices of mountage completes on your desktop
2) open a terminal and execute
```

ls -al /media/

```
  a) the usb device gets automounted by the gvfs system at the mount point /media
  b) to identify the target that you intend to copy files to -
3) once the target is known, change directory (cd) to where you want to copy files from ( saves key strokes for multiple files)
4) execute terminal commandish - assuming "you" own the directories at each end -
```

cp <file> /media/<user_name>/<directory>

```
5) As you are working in the terminal you want to insure that the USB device is unmounted once you are done copying -
```

mount

```
to know the device name that is mounted on /media - say it shows as "/dev/sdb"
6) UNmount the drive:
```

sudo umount /dev/sdb
udisksctl power-off -b /dev/sdb

```
##as required change the "sdb" for the device that mount refers to##

you may now unplug the usb drive,

[INDENT][INDENT]help is what we do
[/INDENT][/INDENT]

---

### Post by 4dri4n on 2021-02-18
thanks sir for the reply i appreciate you
i'm a beginner i don't understand what "mount" do and "unmounted" too and how at the same time i can specify my USB name? because when i tap "lsusb" command it shows me all the devices connected.

---

### Post by Bashing-om on 2021-02-18
4dri4n; Well ...

Yeah - learning a new operating system can be daunting - :D

Though it is bad form to direct " RTFM" ( Read The Fine Manual). sometimes there just is not better way.
Most commands and many many applications have entries in the on-board manual.
See the result of terminal command:
```

man man

```

in this instance you want to know more about the "mount" command. Where the command not only attaches file systems to the system file tree, will also show all the "attachments".
```

man mount

```

And next you ask about "umount" [unmount] where the file system is detached and released There is a lot that goes on in this action.
see:
```

man umount

```


The command "lsusb" does indeed list all usb attached devices that the kernel is aware of, however, this does not tell where the attachment is. That is the function of the "mount" command. The linux philosophy is do one thing and do it well.

So, now you want to copy files from the operating system onto a USB storage device. Where are you currently in your thought process?

copying files >>
[INDENT]Ain't nothing but a thing
[/INDENT]

---

### Post by TheFu on 2021-02-18
A free book that teaches linux, in order.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

+1 for using manpages. Most mysteries of Linux are answered therein.

---

### Post by 4dri4n on 2021-02-18
my os is stuck i cant even login to browse the web!

---

### Post by 4dri4n on 2021-02-18
@Bashing-om
well this is part of the problem you can read this to understand what happened and sorry for this long

- obviously you're wondering why i am doing all this when i can enter the graphical interface and copy it as if it were in Windows !, i cannot even log in to my user account because i'm facing a problem while three days ago and  i was taking free courses from firefox browser then when i felt that the system was somewhat crashed i opened the CPU graph because i was monitoring the processor traffic and then accidentally pressed my finger on the "kill session" so the screen blackened and when i  reboot the machine i couldn't open my user account to access the desktop.  so when i type in the username and password technically a window pops out that says: (Xsession: warning: unable to write to / tmp; X session may exit with an error) .. 3 days ago and i've been trying to solve  this problem and it didn't work so I got an idea to open the terminal with CTRL + ALT + F1 to copy my stored data on the hard disk to my 4G flash drive to protect from data corruption in case something happens when i type "  apt-get clean "my data will be safe
check it to be sure: http://s01.geekpic.net/di-GX1K5T.jpeg

---

### Post by Bashing-om on 2021-02-18
4dri4n; Ouch !

Hate when these things happen - but ubuntu: always fixable.

If you want to investigate the GUI issue, please start a new thread on that topic.

Here is like dead men:
[INDENT]only one to the box[/INDENT]

---

### Post by 4dri4n on 2021-02-18
> **Bashing-om said:**
> 4dri4n; Ouch !

Hate when these things happen - but ubuntu: always fixable.

If you want to investigate the GUI issue, please start a new thread on that topic.

Here is like dead men:
[INDENT]only one to the box[/INDENT]
 
already i post a threats on the linuxquestions.org but none have the solution i'm sad just for my data cause when i format my drive everything is will be gone! 
but if i copy them to the flash drive it will be okay somewhat

---

### Post by Bashing-om on 2021-02-18
4dri4n
> 
I post a threats on the linuxquestions.org but none have the solution

I meant that you post here on a new thread.

As to saving my files - my goto is "rsync";
Example to transfer to a USB storage device:
```

rsync -aiv --exclude=".*" /home/sysop/ /media/sysop/store/

```

where I do not want to keep a copy of the dot files ( generally config files ), my username is "sysop" on this system, and the target - /store - directory exists.

Do not forget to "UNmount, and poweroff the device when done.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by 4dri4n on 2021-02-18
> **Bashing-om said:**
> 4dri4n

I meant that you post here on a new thread.

As to saving my files - my goto is "rsync";
Example to transfer to a USB storage device:
```

rsync -aiv --exclude=".*" /home/sysop/ /media/sysop/store/

```

where I do not want to keep a copy of the dot files ( generally config files ), my username is "sysop" on this system, and the target - /store - directory exists.

Do not forget to "UNmount, and poweroff the device when done.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

thanks a lot, i will try it and if you have a social media account or anything give me your name to contact you and follow the case with me via screenshots for every step and i'll send you some satoshi if you have a Bitcoin wallet

---

### Post by Bashing-om on 2021-02-18
4dri4n;

Naw - I do this support thing as pay back for this system I admire so.
If this forum medium is too slow for you -- there is #ubuntu on Freenode for real-time support.
(if you are not on IRC, you are missing out)

[INDENT]Oh Ubuntu, how do I love you
[INDENT][INDENT]let me count the ways
[/INDENT][/INDENT][/INDENT]

---

