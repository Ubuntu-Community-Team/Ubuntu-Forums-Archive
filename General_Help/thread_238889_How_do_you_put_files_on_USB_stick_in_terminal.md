---
title: "How do you put files on USB stick in terminal"
date: 2006-08-18
forum: General Help
---

### Post by jsmidt on 2006-08-18
I screwed up X, so I want to backup all my files to my USB stick before I try to turn my computer upsidown to get X to work again.  How do I do that?

---

### Post by Tomosaur on 2006-08-18
First you'll need to find out how linux is seeing your USB stick. Type the follow into a terminal:

```

ls /dev/sd*

```

This should provide you a list of your USB ports - they will look something like 'sda, sdb, sdc' etc. If you have a USB stick plugged in, one of them will have a numeral afterwards. For example, I have a USB stick plugged in right now, and this is my output:
```

tom@tom-computer:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sdb  /dev/sdc  /dev/sdd  /dev/sde

```

Therefore, my USB stick is sda1.

So you need to create a mount point. First of all, make a directory in your  home dir called 'MyUSB':
```

mkdir ~/MyUSB

```

And now mount your usb stick to that point:
```

sudo mount /dev/sda1 ~/MyUSB

```

This will allow you to access your USB stick through the 'MyUSB' directory. 
Copying files to and from it is as simple as this:
```

cp ./MyFiles/MyTextFile.txt ~/MyUSB/

```

Hope that helps.

---

### Post by jsmidt on 2006-08-18
That is a really nice Howto, thanks.

---

### Post by taurus on 2006-08-18
No need to turn your computer up side down to fix X.  Just run this command to reconfigure your X again...

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by arumugam on 2007-10-10
> **Tomosaur said:**
> First you'll need to find out how linux is seeing your USB stick. Type the follow into a terminal:

```

ls /dev/sd*

```

This should provide you a list of your USB ports - they will look something like 'sda, sdb, sdc' etc. If you have a USB stick plugged in, one of them will have a numeral afterwards. For example, I have a USB stick plugged in right now, and this is my output:
```

tom@tom-computer:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sdb  /dev/sdc  /dev/sdd  /dev/sde

```

Therefore, my USB stick is sda1.

So you need to create a mount point. First of all, make a directory in your  home dir called 'MyUSB':
```

mkdir ~/MyUSB

```

And now mount your usb stick to that point:
```

sudo mount /dev/sda1 ~/MyUSB

```

This will allow you to access your USB stick through the 'MyUSB' directory. 
Copying files to and from it is as simple as this:
```

cp ./MyFiles/MyTextFile.txt ~/MyUSB/

```

Hope that helps.


1.can you explain how to access files or data from USB in linux platform with code?
i want to know the operation going on  in background when USB is connected to system.

---

### Post by arumugam on 2007-10-10
can anyone explain about how to access files from USB in linux with codes. and also i want to know  what is going on in background.

---

### Post by jsmidt on 2007-10-10
I have altered the above quoted text so that you access your files over a command line.  I hope this helps.  


> **Tomosaur said:**
> First you'll need to find out how linux is seeing your USB stick. Type the follow into a terminal:

```

ls /dev/sd*

```

This should provide you a list of your USB ports - they will look something like 'sda, sdb, sdc' etc. If you have a USB stick plugged in, one of them will have a numeral afterwards. For example, I have a USB stick plugged in right now, and this is my output:
```

tom@tom-computer:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sdb  /dev/sdc  /dev/sdd  /dev/sde

```

Therefore, my USB stick is sda1.

So you need to create a mount point. First of all, make a directory in your  home dir called 'MyUSB':
```

mkdir ~/MyUSB

```

And now mount your usb stick to that point:
```

sudo mount /dev/sda1 ~/MyUSB

```

This will allow you to access your USB stick through the 'MyUSB' directory. 
To access files in that directory go to that directory.
```

cd ~/MyUSB/

```

Now to look at the files in this directory issue this command:

```

ls

``` 

Hope that helps.

---

### Post by arumugam on 2007-10-11
I want to run linux commands to access the files from usb and then i want to use the files for browsing  by directFB. how i can do that. and also i donot want to use extra memory for storing the files which was accessed from usb.

---

