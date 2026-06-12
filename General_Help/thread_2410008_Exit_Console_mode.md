---
title: "Exit Console mode?"
date: 2019-01-09
forum: General Help
---

### Post by innotime22 on 2019-01-09
Hello, I'm a newb here. So please try to be as specific as possible. TY!

I am running 17.10.

No idea how I got here but instead of the normal log in screen I have an all black cmd prompt looking screen at the top it says..

Ubuntu 17.10  "Computer name" tty2

Under that it asks my login, I type that, asks pw and I type that. 

It logs me in saying my last log in and a bunch of other stuff like no warranty warnings and such.

Under that it has a command prompt looking line that looks something like... computer name:"$ 

So any help to exit out of this? TY

Also not sure if this matters but this is NOT the original laptop that this hdd was in. That Laptop is gone but the HDD is still here, obv.

---

### Post by Impavidus on 2019-01-09
You're on tty2. The graphical interface should be on tty7. You can change between them using ctrl+alt+F(1-7). So try hitting ctrl+alt+F7.

BTW, Ubuntu 17.10 is no longer supported.

---

### Post by innotime22 on 2019-01-09
TY for advice. At what screen am I supposed to hit ctr+alt+F7?  The all black log in screen? 

If you're talking about the all black log in screen then I can't use F7. Nothing happens. I can do 1-6 but nothing actually changes with any of them, I just have to re log in again but its the same text log in. unless I'm doing it wrong or at the wrong screen when doing so. Am I supposed to restart after doing this? 

Also, I will be upgrading. Just want to get everything off this Drive.

---

### Post by oldrocker99 on 2019-01-09
CTRL-ALT-Fx can be pressed in any console.

As soon as your data is backed up, install 18.04.1 ASAP, and you should have a normal login screen.

If you don't have a separate /home partition, when you install a new system, follow these instructions:[https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/](https://www.linuxtechi.com/ubuntu-18-04-lts-desktop-installation-guide-screenshots/).

Should you want  to reinstall, having a separate partition for /home makes it a lot easier.

---

### Post by deadflowr on 2019-01-10
17.10 uses gdnm which now runs on vt1 (tty1) as opposed to older versions of Ubuntu that used lightdm which ran (runs if used) on vt7 (tty7).
User sessions then run on vt2 (tty2) and up.
More here: [https://askubuntu.com/questions/856940/why-does-gdm-run-on-tty1-and-gnome-shell-on-tty2]("https://askubuntu.com/questions/856940/why-does-gdm-run-on-tty1-and-gnome-shell-on-tty2")

> Also not sure if this matters but this is NOT the original laptop that this hdd was in. That Laptop is gone but the HDD is still here, obv.
How long has it ran in the new machine?

---

### Post by innotime22 on 2019-01-10
Ok. Thanks. I just found the HDD laying around my house and put it in this laptop yesterday. That's whats pissing me off. Before formatting I just want to check and see if there's anything important on the drive before i erase it. Took me half the day yesterday just remebering the log in info and now this is problem number 2, getting out of text mode or whatever its called.

So if there is an easier way of just checking to see what files, photos etc are on this drive before deleting it then LMK. I just have no idea how to navigate around with this text mode on.

Also, at the all black text login screen, when I hit F1-6 at the top it does change from tty1 to tty6 but there is just not actual change to the screen, its still in text mode.

---

### Post by innotime22 on 2019-01-10
Also, I do have a spare HDD. So if there is a way to maybe just clone this hdd or something and add it to the other clean hdd so i can see the files, if that will be easier?

Whichever way is easiest. If changing back to gui mode is easiest cool, but my main goal is just looking through the drive before erasing it and upgrading.

---

### Post by CatKiller on 2019-01-10
The issue seems to be caused by the fact that the OS was configured for different hardware, so you aren't able to log in graphically. It's potentially relatively easy to fix with sufficient information, but:

[list=1]
[*] The OS is no longer supported
[*] You're only interested in the data
[*] You're inexperienced
[*] The original hardware is gone 
[/list]

So I would suggest installing that hard drive but booting from a live USB. You'll have a graphical environment to poke around with, and you can mount the hard drive so you have something to poke. Copy any data you're interested in to somewhere else then call it a day.

---

### Post by Impavidus on 2019-01-10
If you want a fresh install of 18.04 (yes, you should), you'll boot using a live disk. That will also allow you to get any files from that hard drive using the GUI.

---

### Post by innotime22 on 2019-01-13
Sorry been busy with work but thanks. will look into this tomorrow.

---

### Post by innotime22 on 2019-01-14
Ok, so of course a new problem, might be easy fix?

I dl the ubuntu 18 live usb. I am on there and have mounted the old drive that I want the files from. But now there are 2 folders with a grey "x" on them in which I cannot access the files. One is root folder and the other is the name of my desktop/login name inside the home folder which is obviously the one I want so i can grab my files.

Now, I know my password obviously, I just don't see where to enter it so I can unlock or open my desktop folder? I am a newb so i am sure this isn't going to be some easy thing to do or going to have to use the terminal which not good at.
Thanks

---

### Post by Impavidus on 2019-01-14
Try running the file manager with root permissions:```
sudo -H nautilus
```As you're on a live session, the password is blank. If it asks for one, just hit enter.

---

### Post by innotime22 on 2019-01-14
Tried that. Of course I get an error. Oops! Something went wrong. Create a folder or set perm such that it can be created: /root/.config/nautilus

---

### Post by innotime22 on 2019-01-14
Nevermind. I got your suggestion to work, forgot to mount first. That was able to get the actual folders open but its showing they are empty (which they definitely arent).

When I click on my home folder it has two things in it 

1) Access-your-private-data.desktop (I click an get.. The link is broken, This link cannot be used because its target "/usr/share/ecryptfs-util/ecryptfs-mount-private.desktop" doesn't exist

2) ReadME.txt. Has an error everytime I try opening it, same as above.

---

