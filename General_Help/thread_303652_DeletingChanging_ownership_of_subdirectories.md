---
title: "Deleting/Changing ownership of subdirectories"
date: 2006-11-20
forum: General Help
---

### Post by juantovarm on 2006-11-20
I have a directory that has many subdirectories and files within it. I want to delete it. I went to terminal and wrote: 

sudo rmdir gaim-2.0.0

and not being empty it didn't let me. So i tried to erase the subdirectories with nautilus but i didn't have permission. So i "chown" every directory and subdirectory from the terminal. Long process to say the least...

I imagine there hast to be an easier and more time efficient way of doing this...

any ideas

Thanks

---

### Post by aidanr on 2006-11-20
sudo rm -Rf gaim-2.0.0

**warning** be very very very careful using rm - Rf with sudo, i can't stress this enough, you have been warned

---

### Post by firebadger on 2006-11-20
A little perhaps...

sudo chown -R user:group directory
sudo rm -rf directory

---

### Post by aysiu on 2006-11-20
> **aidanr said:**
> sudo rm -Rf gaim-2.0.0

**warning** be very very very careful using rm - Rf with sudo, i can't stress this enough, you have been warned
I agree. The characters *sudo rm -rf* should never be typed in the terminal. If you're not careful, you could delete your entire Ubuntu installation.

It's far better to use ```
gksudo nautilus
``` for this task.

---

### Post by qamelian on 2006-11-20
Try ```
sudo rm -d -r name_of _dir
```

EDIT: Beaten to the punch again!

---

### Post by juantovarm on 2006-11-20
Thanks!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by juantovarm on 2006-11-20
> **aysiu said:**
> I agree. The characters *sudo rm -rf* should never be typed in the terminal. If you're not careful, you could delete your entire Ubuntu installation.

It's far better to use ```
gksudo nautilus
``` for this task.

What does gksudo nautilus do? How can i try it safely?

---

### Post by aidanr on 2006-11-20
basically it opens up nautilus as root so you can browse to any directory and delete files with the file manager rather than through the terminal, which is safer because in the terminal one slight typo and you could be in big trouble

---

### Post by firebadger on 2006-11-20
There are certain commands that when you type you should get into the habit of double checking before pressing return and rm -rf (as root) is one of them.  Personally, I find it far too useful to refrain from using it at the command line, but it is important to be aware that you could zap everything (an I mean everything) with it.

---

