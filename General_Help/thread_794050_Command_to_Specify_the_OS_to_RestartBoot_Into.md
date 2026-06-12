---
title: "Command to Specify the OS to Restart/Boot Into"
date: 2008-05-14
forum: General Help
---

### Post by navneeth on 2008-05-14
Is there an option I could specify along with the command

```
sudo shutdown -r now
```

to boot into a particular OS/Kernel listed in the GRUB?

---

### Post by Sukarn on 2008-05-14
> **navneeth said:**
> Is there an option I could specify along with the command

```
sudo shutdown -r now
```

to boot into a particular OS/Kernel listed in the GRUB?

OK, this is going to take some work to set up, but you can do this to achieve what you want -
Open your /boot/grub/menu.lst and set the default value to whatever you want. For example, if you have them in this order -
0 Ubuntu
1 Memtest
2 SUSE
3 Windows
I'm not sure whether it starts from 0 or from 1. Test it and see.

Now, edit the default value and set it to 0, and save the file as /boot/grub/ubuntu.lst
set it to 2 and save as /boot/grub/suse.lst
and set it to 3 and save as /boot/grub/windows.lst
Run this command once to backup your current menu.lst, and run this every time there is a kernel update -
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```

Now, you can write shell scripts to do what you want.
Here's an example for rebooting into SUSE -
```

sudo cp /boot/grub/suse.lst /boot/grub/menu.lst
sudo /sbin/shutdown -r now

```
If you save the above code in suse.sh then to run it just open terminal and type **sh suse.sh**

When you reboot into Ubuntu the next time, then make sure you run **sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst** so that the next time you reboot, you get Ubuntu as the default option again.

Hope that helps.

I did not go into much detail because it appeared from your post that you are somewhat used to the terminal.

---

### Post by pointone on 2008-05-14
```
man grub-set-default
```

Counting starts at 0.

---

### Post by navneeth on 2008-05-14
Thank you, Sukarn. I'll give a that try and let you know how it went. :)

---

### Post by kevdog on 2008-05-14
sudo init 6 also reboots

---

### Post by Sukarn on 2008-05-14
> **kevdog said:**
> sudo init 6 also reboots

The main aim here is not to find different methods of rebooting the computer, but to find methods of rebooting into a different OS.

Imagine this, you need to go somewhere for a couple of minutes, and you also need to reboot into a different OS. It would be much better to run a shell script which would automatically reboot you into the desired OS, instead of making you wait in front of the PC until the GRUB screen appears, or else not start the computer until you're back from where ever you needed to go.


Thanks for telling us about that rebooting method though. Its always good to know new stuff. Knowledge can only be increased.



> **pointone said:**
> ```
man grub-set-default
```

Counting starts at 0.

Thanks for that information. I was not sure about it, although I did have the feeling that it should start from 0. I had not edited my grub in quite a while to change the default OS. The last time I did it was about two years ago at a friend's house to make Windows XP his default OS.

---

### Post by pointone on 2008-05-14
Actually, what you should've taken away from my post is that it's not necessary to create multiple menu.lst files and switch them around (very messy, in my opinion, especially when kernel updates are involved). Rather, simply run:

```
sudo grub-set-default 2 && reboot
```

...to reboot into SUSE, using your example above.

---

### Post by Sukarn on 2008-05-15
> **pointone said:**
> Actually, what you should've taken away from my post is that it's not necessary to create multiple menu.lst files and switch them around (very messy, in my opinion, especially when kernel updates are involved). Rather, simply run:

```
sudo grub-set-default 2 && reboot
```

...to reboot into SUSE, using your example above.

oh... ahh... my bad.

---

### Post by meierfra. on 2008-05-15
And even easier:

```
sudo grub-reboot 2
```

But  for "grub-reboot" or "grub-set-default"  to work one needs to change

"default 0"  to "default saved" in  the file menu.lst

---

### Post by Sukarn on 2008-05-15
/me goes to sit in a corner wearing a hat that reads "donkey".

---

### Post by navneeth on 2008-05-15
> **meierfra. said:**
> And even easier:

```
sudo grub-reboot 2
```

But  for "grub-reboot" or "grub-set-default"  to work one needs to change

"default 0"  to "default saved" in  the file menu.lst

So do I change 2 in my menu.lst to saved? Just making sure...

```
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		2
```

And if I want to reboot into Windows from Ubuntu, I type

```
sudo grub-reboot 9
```

?

[There are currently four Linux kernels (and their respective recovery modes), memtest and Windows XP listed in the grub.]

Thanks a lot for all your helpful replies.

---

### Post by meierfra. on 2008-05-15
> So do I change 2 in my menu.lst to saved? 

Yes


> I type  sudo grub-reboot 9

It depends. You might have 

title  Other Operating Systems

in your menu lst. In this case you would have to use "sudo grub-reboot 10"

(you have to count all "title" starting at 0)

---

### Post by navneeth on 2008-05-15
> **meierfra. said:**
> Yes

Thanks.



> It depends. You might have 

title  Other Operating Systems

in your menu lst. In this case you would have to use "sudo grub-reboot 10"

(you have to count all "title" starting at 0)



:redface: True. I realised that after typing the post.

---

