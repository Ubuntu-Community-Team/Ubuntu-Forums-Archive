---
title: "No Bootscreen"
date: 2007-01-13
forum: General Help
---

### Post by nezermundy on 2007-01-13
Hi, 

I have installed ubuntu on a dell 1100 laptop with good success, however there is no bootscreen or shutdown screen. You just get the little blink in the corner.

Is there anyway I can solve this.

Thanks.

---

### Post by Pollywoggy on 2007-01-13
> **nezermundy said:**
> Hi, 

I have installed ubuntu on a dell 1100 laptop with good success, however there is no bootscreen or shutdown screen. You just get the little blink in the corner.

Is there anyway I can solve this.

Thanks.

I am getting that too.  I can usually get the screen by Ctrl-Alt-F7 if I have not left the laptop unattended for more than a few minutes.   I had Linspire and Freespire on the laptop before I installed Ubuntu and did not have this problem, so I am sure there is a fix somewhere.

---

### Post by nezermundy on 2007-01-14
Could it be because of the screen resolution? I had the problem of 640x480 when I first installed ubuntu, so maybe it is booting up in a to low resolution to display the bootscreen?

---

### Post by Tux Aubrey on 2007-01-14
If I understand the problem correctly, you are not seeing the bootsplash/progress bar after GRUB and when the machine is shutting down?

I had a similar problem when I switched monitors and it was a resolution problem.

You need to tell grub to use a different resolution - like this

TEST IT FIRST

When the GRUB menu comes up on the screen, select the "boot" you want but press "e" (for edit).

On the next screen, use the down arrow key to highlight the line that begins "kernel  /boot/vmlinuz-..." Press "e" again.

That line will then come up on a black screen with stuff at the top about  "minimal BASH-like line editing"

Just navigate to the end of that line, add a space and "vga=791"

Then press escape, then "b"

Watch the screen.

If its not right, reboot and use another number (instead of 791) from the attached table. [Attachment]("http://ubuntuforums.org/attachment.php?attachmentid=21756&d=1167279032")

When all is good for you, you will need to edit the file called /boot/grub/menu.lst (finding the right line and adding the "vga=791", or whatever)

Sorry that this sounds like a recipe for idiots, but I don't know how much experience with sort of thing you already have (or whether or not you are, in fact, an idiot;)  ).  Anyway, this worked for me and there is a proper technical explanation for all this (somewhere).

Oh, welcome to the forums.

---

### Post by nezermundy on 2007-01-14
> **Tux Aubrey said:**
> If I understand the problem correctly, you are not seeing the bootsplash/progress bar after GRUB and when the machine is shutting down?

I had a similar problem when I switched monitors and it was a resolution problem.

You need to tell grub to use a different resolution - like this

TEST IT FIRST

When the GRUB menu comes up on the screen, select the "boot" you want but press "e" (for edit).

On the next screen, use the down arrow key to highlight the line that begins "kernel  /boot/vmlinuz-..." Press "e" again.

That line will then come up on a black screen with stuff at the top about  "minimal BASH-like line editing"

Just navigate to the end of that line, add a space and "vga=791"

Then press escape, then "b"

Watch the screen.

If its not right, reboot and use another number (instead of 791) from the attached table. [Attachment]("http://ubuntuforums.org/attachment.php?attachmentid=21756&d=1167279032")

When all is good for you, you will need to edit the file called /boot/grub/menu.lst (finding the right line and adding the "vga=791", or whatever)

Sorry that this sounds like a recipe for idiots, but I don't know how much experience with sort of thing you already have (or whether or not you are, in fact, an idiot;)  ).  Anyway, this worked for me and there is a proper technical explanation for all this (somewhere).

Oh, welcome to the forums.

Hi I have found the number I need which is 773, however I do not know where to put it in the menu.lst.

So is there a chance someone can post where I put it in the file.

Thanks.

---

### Post by Tux Aubrey on 2007-01-14
The first thing you need to do is make a backup of menu.lst

In a terminal window (Applications>Accessories>Terminal)

```
sudo cp /boot/grub.menu.lst /boot/grub/menu.lst.bak
```

It will ask for your password (you can't "sudo" without it)

Then open menu.lst in a text editor, again with root privileges (because you don't "own" menu.lst, root does):

Assuming you are using "Ubuntu" (with Gnome), in the terminal

```
gksudo gedit /boot/grub/menu.lst
```

enter your password if asked

Scroll down through all the instructions and commented lines (the stuff with # starting the lines)

In the Section near the bottom of the file that has the uncommented boot options find the first set of lines that looks like this:
> 
title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=ba66d7c8-1983-4175-8e10-9f0ec1547a3a ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

(Don't worry if the "hd0,1" and UUID is different to mine - you want to edit the long line that starts with "kernel" and ends with "ro quiet splash".

**To the end of that line (after "splash") add your " vga=773"**

Save the file.

Note - I'm assuming that the first "stanza" is your default boot.   There is no harm in adding "vga=773" to the other lines that have the same form.

Again, this is a recipe.  I'd recommend reading through all that stuff in menu.lst at some stage.  You may want to use the Power of Grub later and its handy stuff to know.

Also, wait for 10 minutes or so before trying this just in case there is someone else here who wants to jump in a correct my instructions.  I'm fairly new to this myself.

Good luck.

*Note - you can copy and paste the "code" bits above from your browser to the terminal.  A very cool feature of Linux is to highlight the text you want to copy, go to the terminal and click the "middle mouse button" (the wheel).  Otherwise use the right mouse button in terminal to do the paste.*

---

### Post by nezermundy on 2007-01-14
> **Tux Aubrey said:**
> The first thing you need to do is make a backup of menu.lst

In a terminal window (Applications>Accessories>Terminal)

```
sudo cp /boot/grub.menu.lst /boot/grub/menu.lst.bak
```

It will ask for your password (you can't "sudo" without it)

Then open menu.lst in a text editor, again with root privileges (because you don't "own" menu.lst, root does):

Assuming you are using "Ubuntu" (with Gnome), in the terminal

```
gksudo gedit /boot/grub/menu.lst
```

enter your password if asked

Scroll down through all the instructions and commented lines (the stuff with # starting the lines)

In the Section near the bottom of the file that has the uncommented boot options find the first set of lines that looks like this:

(Don't worry if the "hd0,1" and UUID is different to mine - you want to edit the long line that starts with "kernel" and ends with "ro quiet splash".

**To the end of that line (after "splash") add your " vga=773"**

Save the file.

Note - I'm assuming that the first "stanza" is your default boot.   There is no harm in adding "vga=773" to the other lines that have the same form.

Again, this is a recipe.  I'd recommend reading through all that stuff in menu.lst at some stage.  You may want to use the Power of Grub later and its handy stuff to know.

Also, wait for 10 minutes or so before trying this just in case there is someone else here who wants to jump in a correct my instructions.  I'm fairly new to this myself.

Good luck.

*Note - you can copy and paste the "code" bits above from your browser to the terminal.  A very cool feature of Linux is to highlight the text you want to copy, go to the terminal and click the "middle mouse button" (the wheel).  Otherwise use the right mouse button in terminal to do the paste.*

Thank you much! It woks now...

---

### Post by Pollywoggy on 2007-01-14
> **nezermundy said:**
> Could it be because of the screen resolution? I had the problem of 640x480 when I first installed ubuntu, so maybe it is booting up in a to low resolution to display the bootscreen?

I had not considered that.  I will check on that, thanks for the tip.

---

### Post by Pollywoggy on 2007-01-14
> **Tux Aubrey said:**
> If I understand the problem correctly, you are not seeing the bootsplash/progress bar after GRUB and when the machine is shutting down?

I had a similar problem when I switched monitors and it was a resolution problem.

You need to tell grub to use a different resolution - like this

TEST IT FIRST

When the GRUB menu comes up on the screen, select the "boot" you want but press "e" (for edit).

On the next screen, use the down arrow key to highlight the line that begins "kernel  /boot/vmlinuz-..." Press "e" again.

That line will then come up on a black screen with stuff at the top about  "minimal BASH-like line editing"

Just navigate to the end of that line, add a space and "vga=791"

Then press escape, then "b"

Watch the screen.

If its not right, reboot and use another number (instead of 791) from the attached table. [Attachment]("http://ubuntuforums.org/attachment.php?attachmentid=21756&d=1167279032")

When all is good for you, you will need to edit the file called /boot/grub/menu.lst (finding the right line and adding the "vga=791", or whatever)

Sorry that this sounds like a recipe for idiots, but I don't know how much experience with sort of thing you already have (or whether or not you are, in fact, an idiot;)  ).  Anyway, this worked for me and there is a proper technical explanation for all this (somewhere).

Oh, welcome to the forums.

It's a good recipe for me.  I will try that out.  I did something similar when I installed Linspire the first time, had to change the video mode to vesa to get a proper boot.

thanks

---

### Post by SpreX on 2007-12-21
I have the same problem but mine ain't solved yet. I tried all modes but unsuccessful. ALL still don't work and for 793,794,795 says that their are  
unsupported. I have amilo l1310g and that sh**y widescreen that works best 
on 1280x800. Is there any way to get this done. I can use 1024x768 on my laptop but it doesn't work with bootscreen.

---

