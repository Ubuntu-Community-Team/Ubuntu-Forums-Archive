---
title: "Shutdown problem"
date: 2008-05-02
forum: General Help
---

### Post by Settenano on 2008-05-02
Treat me as a complete newby, not only on linux but on anything related to harware and software.

I have installed xubuntu on a 10 year old PC. It took 4 installations, because it would freeze in the process, but now it works fine.
My problem is with the shutdown. It runs some command lines and then goes onto the shutdown screen (all black, with Xubuntu written in the middle and a status bar). Nothing else happens. No more command is accepted, including ctrl+alt+canc.
I have to shut it down manually holding the power button.

I am reading that it might be an issue with the graphic drivers, but I don't even know how to check what grafic card I have in this PC.

Any idea, please?

---

### Post by pdoma on 2008-05-02
It would probably a good idea to get ride of the Splash screen (the pretty picture) during boot up and shutdown. You can do this by typing this command into the console.

sudo apt-get remove usplash

after it's done try shutting down and see on which line it hangs.

Good Luck

---

### Post by Settenano on 2008-05-02
Nope.
Usplash was already not installed. I even tried installing it and uninstalling. I still get to the same screen.
The image I get in the end is not the pretty picture, but just a black screen with the xubuntu name in the middle. The one I get when it starts, before it asks for login.

Still can't shut it down properly.

---

### Post by eriqjaffe on 2008-05-02
Some older systems require you to add acpi=force to the kernel line in /boot/grub/menu.lst.

[http://ubuntuforums.org/showthread.php?p=2595626](http://ubuntuforums.org/showthread.php?p=2595626)

---

### Post by Settenano on 2008-05-02
I added the string, but the sistem wont let me save the changes.
The message is: Can't open file to write

Now what? Remember how noob I am :)

---

### Post by eriqjaffe on 2008-05-02
You have to be root to edit that file.  From a terminal:

```
sudo mousepad /boot/grub/menu.lst
```

That should let you save it.  If you're using a different text editor (Mousepad is the Xubuntu default, IIRC), just substitute that instead of Mousepad in there.

---

### Post by Settenano on 2008-05-02
Thank you. I'll do it next weekend.
I will also post the messages I got in my last shutdown, with no splash screen.
It looks like the problem is in the network. It fails doing something, I guess closing the connection.

---

### Post by Settenano on 2008-05-09
It doesn't let me save the file even if I open it from terminal with sudo :(

Still can't shut down

---

### Post by Tomatz on 2008-05-09
Your 10 year old pc probably does not support atx.  Basically the powersupply is independent of the motherboard so the motherboard cant switch it off.

Do you remember windows 95/98 when you shut it down it would say "it is now safe to turn off your computer" then you would switch it off. 

That was pre atx.

So as long as xubuntu is unmounting your drives correctly you have nothing to worry about.

When you turn your computer on does it check your drives every time? If not all is fine.

---

### Post by Settenano on 2008-05-09
It actually checks stuff.
The first line when it goes on says that the bios is too old and needs acpi=force, indeed.
The problem is that I cannot have it save the command in the menu.lst

Anyway, the shutdown is annoying but it doesn't seem to create problems

---

### Post by Tomatz on 2008-05-09
in a terminal:

```
sudo gedit /boot/grub/menu.lst
```

Enter your password (no text will appear while typing your password)

Then you will have permissions to save it ;)

---

