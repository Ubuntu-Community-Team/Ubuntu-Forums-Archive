---
title: "Error &quot;I/O error&quot; while copying &quot;/home/david....part3.rar&quot;"
date: 2006-12-10
forum: General Help
---

### Post by min0r on 2006-12-10
Hey everyone,

I have a file [b-r5.part3.rar] on my internal drive that I want to copy to an an external hard drive, but whenever I attempt a transfer, it gives me this about 3/4 of the way through:

```
Error "I/O error" while copying "/home/david....part3.rar".
```

I know that the disk isn't corrupted as I've tried a seperate USB thumbdrive to no avail. And the other files named [b-r5.part*.rar] transferred fine on to both drives.

Thanks for your help,

min0r.

EDIT: Even copying it from folder to folder doesn't work.. help?

---

### Post by DaveBorealis on 2006-12-10
> **min0r said:**
> 
```
Error "I/O error" while copying "/home/david....part3.rar".
```

Hello,

Last time I had a problem similar to that, the hard drive containing the original file was going bad.  At first it was one file I couldn't move.  Then a second....   You might want to back up anything not previously saved to another disk before doing anything else.

Best regards,
Dave

---

### Post by riven0 on 2006-12-10
Have you tried this:

> sudo cp -r /home/david....part3.rar /media/whatever-your-hd-is

---

### Post by min0r on 2006-12-10
Thanks guys, but I still can't move the file.

**riven0:** I tried that, but I got the error message:

```
cp: reading `/home/admin/.vidz/extra/b-r5.part3.rar': Input/output error
```


So, does this mean that I'm not going to ever be able to copy the file and that it's just beyond repair?

Thanks,

min0r.


EDIT: And by the way, the file transfer doesn't fail instantly, it only fails when it's at 69.1MB/95.4MB.

---

### Post by riven0 on 2006-12-10
> **min0r said:**
> EDIT: And by the way, the file transfer doesn't fail instantly, it only fails when it's at 69.1MB/95.4MB.

Oh! Definitely sounds like a corrupted file. If you don't already have the program unrar, install it (sudo apt-get install unrar), try to extract your files and see what you can recover.

Other than that, I have no idea on how to save it.:confused:

---

### Post by Take0n on 2008-01-13
Hello

I know the post is from 2006, 2 years old, but I had a similar problem and that's how I found this post so I decided to say how I solved this in case people run in to this forum/post while searching for a solution.

I had the same problem, the same message, but the problem seemed to be that I was connecting my hdd through a USB-hub. I tried all the ports in that hub but I still got the same error. I tried to connect my hdd on a windows machine and everything worked fine so there was something either with ubuntu or the connection (since it worked on another computer).

The first thing I tried was to connect the hdd through a normal USB port and not a hub or something like that (in other words directly to the computer). This worked just fine so I hadn't to look farther!

I hope this will help people out there looking for a solution to this problem. And remember to always unmount something before you unplug it... If you still get this error after connecting the device directly to the computer try to unmount the device, unplug it and then reconnect it. If you run two or more operating systems (like windows or mac) and had the device connected to one of those operating system, try to connect it there again, unmount it (in windows safe remove) and then connect it to Ubuntu.

That's all from me folks..

---

