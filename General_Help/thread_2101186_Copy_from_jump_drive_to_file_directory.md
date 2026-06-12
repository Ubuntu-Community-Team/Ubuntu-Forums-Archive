---
title: "Copy from jump drive to file directory"
date: 2013-01-04
forum: General Help
---

### Post by seacher on 2013-01-04
I have tried copy a file from my jump drive which has already been formatted for Ubuntu use, because, I use it in Ubuntu and nothing else.

I copied a cd for Wireless Sensor Network Support to the jump drive and need to get the Surge-View file copied to the file directory.

When I use the command cp /media/usb/Surge-View the prompt tells me read the help manual for directions

Anyone have any ideas as to how to accomplish the copying of this file to the file directory?

---

### Post by Wim Sturkenboom on 2013-01-04
> 
When I use the command cp /media/usb/Surge-View the prompt tells me read the help manual for directions

Did you read the help manual (man page) :D

You need to specify the destination directory
```

cp /media/usb/Surge-View [COLOR="Red"]your_destination_directory[/COLOR]

```
This assumes that Surge-View is a file and not a directory; the command might differ if Surge-View is a directory.

---

### Post by fdrake on 2013-01-04
> **seacher said:**
> I have tried copy a file from my jump drive which has already been formatted for Ubuntu use, because, I use it in Ubuntu and nothing else.

I copied a cd for Wireless Sensor Network Support to the jump drive and need to get the Surge-View file copied to the file directory.

When I use the command cp /media/usb/Surge-View the prompt tells me read the help manual for directions

Anyone have any ideas as to how to accomplish the copying of this file to the file directory?

i this a folder or a file? iof it's a folder you have to use -R
```

cp -R /media/usb/Surge-View ~/Desktop/Surge-View 

```

---

### Post by seacher on 2013-01-04
I have tried both of the above methods and the command line reads:

'cp: cannot stat 'home/Surge-View': No such file or directory', but when I go to the home folder I see Surge-View in the folder.

---

### Post by Cheesemill on 2013-01-04
Can you post the *exact* command your trying to use please...

---

### Post by Wim Sturkenboom on 2013-01-04
OOPS, not true, sorry for posting

---

### Post by seacher on 2013-01-04
The commands I used are as follows:

1. cp /home/Surge-View ~/home/usr/share/Surge-View
2. cp -R /home/Surge-View ~/home/usr/share/Surge-View

---

### Post by Wim Sturkenboom on 2013-01-04
Your source is the jump drive (that's the first argument of cp), not something in the directory /home.

Also make sure that the full destination path exists.

You indicated in your opening post _/media/usb/Surge-View_; that's the first argument.

~/home also does not make sense; '~' is already your home directory; however, it might be correct.

---

### Post by Impavidus on 2013-01-04
Find some tutorials on the command line and on the file system structure. It helps if you understand how these work before working with them.

Those commands try to copy the file or directory /home/Surge-View (being the home directory of the user Surge-View, which doesn't and shouldn't exist) to  some elaborate path in you own home directory, vaguely resembling the path to a directory somewhere else on your file system.

What should work is (use the first if you're copying a file, the second if copying an entire directory)```
cp /media/usb/Surge-View ~/some/directory
cp -R /media/usb/Surge-View ~/some/directory
```or substitute a directory outside your home directory if you need it somewhere else (you probably need some more rights if you want so). I guess that you actually want to use the command```
sudo cp -R /media/usb/Surge-View /usr/local/share/Surge-View
``` (maybe you want to skip the local/ part). The directory whereto you copy the file has to exist already. ~ is shorthand for your own home directory, which is located inside the /home directory.

---

### Post by seacher on 2013-01-04
Great!

Thanks for the help guys!

I got it and used  command sudo cp -R ~/Surge-View /usr/share/Surge-View to do it.

Thanks again to all!

---

### Post by dannyboy79 on 2013-01-04
FYI, that is NOT copying anything from a jump drive as your title suggests but glad you got it working

---

