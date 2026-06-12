---
title: "Copy to USB"
date: 2007-12-20
forum: General Help
---

### Post by mahiyar on 2007-12-20
This I have observed for all, thumb drives, music players etc. When I copy a huge amount of data say over 150MB, the copy to the USB indication flashes and the copy indication finishes in a jiffy. I can even see the music file names in the thumb drive, leading one to believe that the copy is over. It is only that when you try to unmount the drive that you get a message that files are still being written. The problem is we don't know how long they will take to finish writing files as there is no indication or progress bar. Can this behavior be changed or is it native to linux?

---

### Post by kidders on 2007-12-22
Hi there,

All operating systems do this sort of thing (asynchronous I/O) for performance purposes. It's the reason unmounting (safely removing, ejecting, etc.) filesystems is important, rather than simply disconnecting them.

Most OSs also allow you to turn off this feature ... after all, despite the performance pay-off, it can sometimes be irritating. On Linux, you can use the "sync" and "async" mount options (see the man page for "mount"). The "async" option is usually the default, so you won't often see people actually use it, but mounting something with the "sync" option in /etc/fstab, a **mount** command, or elsewhere forces all I/O to be processed and written to disk immediately.

You can also do a sort of "sync on demand" if you want to, with the **sync** command. Obviously, performing a buffer sync is part of the unmount process, but if (for some reason) you didn't want to use the "sync" mount option, you could still flush your I/O buffers that way, without having to unmount your filesystems.

---

### Post by Josh1 on 2007-12-22
My thumbdrive does the same sort of thing. I copy over all files then when I am done there is a bar on the top of the window saying unmount or copy or something, then it copies everything over and you can remove it.
I don't have a USB handy to test this as I'm not in my room at the moment.

---

### Post by mahiyar on 2007-12-25
Thanks kidders well in spite of the sync or async option my main focus was on the unavailability/misleading of the copy bar in Ubuntu just to show the progress of copy.

---

### Post by kidders on 2007-12-26
I'm not completely sure I'm understanding your problem correctly When you copy something, for example, two things happen...
[LIST=1]
[*]Your file is copied from one location to the other.
[*]The physical media is updated to reflect the changes.[/LIST]These two don't always happen synchronously (and may even take place hours apart), because I/O operations to physical media are far too time-consuming. If an operating system had to wait for your disks to be updated every time something was changed, your computer would be totally unusable.

Progress bars for I/O operations are intended to give you an idea of how long a copy/etc. will take to complete ... any disk operations which may or may not take place as a result are totally disregarded. It is normal policy for most operating systems to put them off for as long as possible anyway.

I hope that helps.

---

### Post by mahiyar on 2007-12-27
Well that does make things somewhat clear. For my understanding even at the cost of repeating. If a disk is mounted with the asynch options the writing will be done at its own sweet time (and we will not get a progress bar), this can be avoided by using the synch option (which I guess windows uses?). Thanks for bearing with me.

---

### Post by kidders on 2007-12-27
> **mahiyar said:**
> Thanks for bearing with me.No worries :-)

All operating systems default to asynchronous I/O. Constantly flushing buffers is a real performance killer, so OSs only tend to do it in special cases where, for example, a device is liable to become suddenly unavailable without warning.

Under normal circumstances, write operations to physical media are postponed until the OS finds a good time to perform them (eg there is no more buffer space), and changes are then flushed to disk all in one go. You should get a progress bar either way ... a buffered copy just finishes more quickly.

Both Windows and Linux allow you to override the default behaviour if you want to, at the cost of the performance (and often the lifetime) of the device in question.

---

