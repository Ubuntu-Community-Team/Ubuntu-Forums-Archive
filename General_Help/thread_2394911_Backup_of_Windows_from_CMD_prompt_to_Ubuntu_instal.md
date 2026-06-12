---
title: "Backup of Windows from CMD prompt to Ubuntu installation - Can't access"
date: 2018-06-23
forum: General Help
---

### Post by nomonitor on 2018-06-23
Good morning,

I did a direct command prompt copy from Windows (not the GUI, it was command prompt using a recovery or installation CD)

This backup was to an external hard drive that was a live-boot installation of Ubuntu.

I am trying to recover the files from within another installation (on a laptop) and I have access to the whole folder structure but when I tried in the past, I do not have permissions to access the files.

Please help, let me know what I can do.

---

### Post by nomonitor on 2018-06-23
It was a backup of files, not the Windows Backup.

---

### Post by nomonitor on 2018-06-23
/media/matt/5376865e-ec05-4a68-a2d9-9a8f51cf859e/home/matthew/WindowsBackup

This is the location of the documents I need.  I would be happy to back them up to a flash drive but I have no permissions.  Need to be able to access them on Windows when I copy them off.

---

### Post by nomonitor on 2018-06-23
```
matt@matt-laptop:/media/matt/5376865e-ec05-4a68-a2d9-9a8f51cf859e/home/matthew/WindowsBackup$ chmod 755
chmod: missing operand after ‘755’
Try 'chmod --help' for more information.
matt@matt-laptop:/media/matt/5376865e-ec05-4a68-a2d9-9a8f51cf859e/home/matthew/WindowsBackup$ chmod 755 matth
chmod: changing permissions of 'matth': Operation not permitted
matt@matt-laptop:/media/matt/5376865e-ec05-4a68-a2d9-9a8f51cf859e/home/matthew/WindowsBackup$

```

---

### Post by nomonitor on 2018-06-23
I take that back...

I want to copy:
/home/matt/Documents/matth/Pictures

to:
/home/matt/Documents/new

---

### Post by nomonitor on 2018-06-23
```
matt@matt-laptop:/home$ cp  /home/matt/Documents/matth/Pictures  /home/matt/Documents/new 
cp: omitting directory '/home/matt/Documents/matth/Pictures'
```

---

### Post by nomonitor on 2018-06-23
```
matt@matt-laptop:/home$ sudo cp -r ~/home/matt/Documents/matth/Pictures  ~/home/matt/Documents/new 
[sudo] password for matt: 
cp: cannot stat '/home/matt/home/matt/Documents/matth/Pictures': No such file or directory


```

---

### Post by steeldriver on 2018-06-23
Your last command looks close, but remove the ~ at the front of each path

---

### Post by nomonitor on 2018-06-23
Thank you.   It worked, but it looks like my specific files aren't there.   Is there a way to give me a list of all of the files on the HDD?

These are ALL of my wife's GoPro pictures and I lost them due to a RAM stick issue a year ago.

This is my only backup.

Since it was command prompt in Windows I could have backed them up to ANY directory outside of Ubuntu.

---

### Post by yancek on 2018-06-23
You can list files in a directory with the ls command by changing to the directory above it or by putting the full path in the command.  To see all the files/folders in /home/matt/Documents/new just do:

> ls /home/matt/Documents/new/ 

Change the path to whichever other directory you want a list of files for.
Also, any time you are writing to (copying to) a location outside your /home/user directory, you will need root permissions which means using sudo.

---

