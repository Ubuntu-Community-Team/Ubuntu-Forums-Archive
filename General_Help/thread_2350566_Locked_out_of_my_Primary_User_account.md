---
title: "Locked out of my Primary User account"
date: 2017-01-25
forum: General Help
---

### Post by brandonrosano on 2017-01-25
Hello Ubuntu Community,

I need some serious help I was trying to update my user name by editing the /etc/host /etc/hostname. Everything went well, but I still saw the original name that I was trying to get rid of still showing up. I decided to look elsewhere online and one forum mentioned editing the /etc/passwrd which I ended up doing and after doing so I realized that it locked me out of my ability to have root privleges. I have a very special ubuntu machine, it is a 2009 macbook pro with ubuntu as the only os on it. I tried to boot into grub using the control + shift but could not get in. Is there anyway I can edit the /etc/passwrd again to regain access to that user account? I appreciate any responses I feel so lost without my PC :(

Thanks,
Brandon

---

### Post by sisco311 on 2017-01-25
Welcome to the forums, Brandon!

You can boot a live cd/usb, mount the root partition and edit the file.

If you need further help please feel free to ask.

---

### Post by brandonrosano on 2017-01-25
Thank you sisco311

I am new to this and don't want to make any mistakes. So I would boot it into the live disc/usb then what steps do I take after that? How do I mount it?

---

### Post by yancek on 2017-01-25
Too many unknowns to be specific so I'll give you an example.  Boot the Ubuntu flash drive, open a terminal and run:  sudo fdisk -l (Lower Case Letter L in the command).  Take a look at the output.  Your output should be similar to below.

```
Disk /dev/sda: 931.5 GiB, 1000204885504 bytes, 1953525167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00064fef

Device     Boot     Start        End    Sectors   Size Id Type
/dev/sda1            2048   50794495   50792448  24.2G 83 Linux

``` 

The above shows a 1TB device with one partition of Linux format so to mount it first create the mount point.  sudo mkdir /mnt/sda1  then the mounting.
sudo mount -t ext4 /dev/sda1 /mnt/sda1

This is simply an example and you will have to change the parameters to fit your system.  You can also use another directory name, you don't need 'sda1'.

---

### Post by ajgreeny on 2017-01-25
> I need some serious help I was trying to update my user name by editing the /etc/host /etc/hostname.
There is no **/etc/host** file; it is probably **etc/hosts** but in fact editing that or **/etc/hostname** will do nothing to change your username on the system.

You can change the hostname in those files, ie the computer name which you see in the terminal prompt **user@[B]hostname**:~$[/B] but it will do nothing to your username.

Which do you really want to change, hostname or username?

---

### Post by brandonrosano on 2017-01-25
Then after mounting I would be able to tap into my user account make the edits needed?

---

### Post by brandonrosano on 2017-01-25
username and your right it didnt do anything until I made changes to the etc/passwrd file

---

### Post by brandonrosano on 2017-01-25
I was able to successfully fix my issue. Thank you very much for your help.  What would be the proper way to remove the jimmy part of this "jimmy@brandon-MacBookPro:~$" Because that's what I was originally trying to do.

---

### Post by ajgreeny on 2017-01-25
> **brandonrosano said:**
> I was able to successfully fix my issue. Thank you very much for your help.  What would be the proper way to remove the jimmy part of this "jimmy@brandon-MacBookPro:~$" Because that's what I was originally trying to do.
You will need to edit the .bashrc file in your home folder.

Read the section "Setting Prompt Without Color" at [https://help.ubuntu.com/community/CustomizingBashPrompt](https://help.ubuntu.com/community/CustomizingBashPrompt) and you may get what you want.
Look for the lines ```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\][COLOR="#FF0000"]\u@[/COLOR]\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}[COLOR="#FF0000"]\u@[/COLOR]\h:\w\$ '
```
and remove the \u@ shown in red above.
Your prompt will then be **brandon-MacBookPro:~$**
Backup .bashrc first just in case you mess up and can not login into your user.

---

### Post by sisco311 on 2017-01-25
I'm a bit confused here. Are you trying to change the shell prompt or your user name?

Changing the shell prompt is trivial and it does not require root privileges. See ajgreeny post above.

It shouldn't be, but changing your user name is much harder. For users who aren't familiar with Linux I would suggest to simply create a new user account (with admin rights).

---

