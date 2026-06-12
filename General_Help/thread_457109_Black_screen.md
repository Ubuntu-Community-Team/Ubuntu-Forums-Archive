---
title: "Black screen"
date: 2007-05-28
forum: General Help
---

### Post by wwoollff on 2007-05-28
Hi.I have installed Wubi from Windows XP...everything worked fine...Ubuntu runned perfectly, until the first restart.It crashed right after the loading bar....and it doesn't display any error.I've installed Ubuntu several times through  Wubi, and I got the same problem every time.
   I'm using Ubuntu Feisty Fawn on a COMPAQ Presario V6000(laptop)

---

### Post by put4558350 on 2007-05-28
did your system using ati ?

if so. it's ubuntu problem 

this will fix
[http://nerdc0re.wordpress.com/2007/04/29/ubuntu-704-ati-gdm-black-screen-of-death/](http://nerdc0re.wordpress.com/2007/04/29/ubuntu-704-ati-gdm-black-screen-of-death/)

---

### Post by wwoollff on 2007-05-29
nope....it's a nvidia. I've searched the internet and found out that the problem is that it's a Compaq....and Compaqs have a serious problem with Linux...or other systems beside Windows.It should be a thread about how to install Ubuntu on Presatio, because many had this problem, and it's not solved yet.

---

### Post by aqueous on 2007-05-29
i have the exact same problem and on exactly the same laptop.  sometimes it's a carbonfiber looking screen w/ the brightness phasing in and out.

---

### Post by minhmeoke on 2007-05-29
Hi guys, I had the same problem; it is due to the fact that the Compaq Presario V6000 uses a widescreen display that the default Ubuntu settings could not recognize. Here is how I fixed it:

1) Boot into recovery mode. To do this, you have to restart your computer, then select "Ubuntu" at the GRUB bootloader menu (the other choice should be windows). Right after you select Ubuntu and hit enter, press the "esc" key rapidly. If you were fast enough, another menu should appear almost instantly. There should be 3 choices, the first one is default mode, the second is the recovery mode, and the third is a memory test. Choose the second choice, it should be something like "Ubuntu kernel 2.6.20-15 generic (recovery mode)".

2) After choosing recovery mode, you will eventually get a shell (command prompt), which looks something like this: "root@mycomputer:~#". Now you have to use a text editor to change the Xorg configuration file, which handles the display modes. To do this, type in
```
nano /etc/X11/xorg.conf
```
Note that "X11" is spelled with a capital X; if you use a lowercase x, then you will get a "directory not found" error message.

3) Ok, now you should be seeing the xorg.conf file in a text editor. Scroll down to the bottom, at the section that starts with

```
Section "Screen"
	Identifier	"Default Screen"
	....
```

Inside this section, there should be lines that say 
```
	SubSection "Display"
		Depth	1
		Modes		"1024x768"
	EndSubSection
```

Next to each of the mode entries, there should be a number, such as 1024x768. Change this to:
```
	SubSection "Display"
		Depth	1
**		Modes		"1280x800"**
	EndSubSection
```

In other words, change the value of each "Modes" entry to "1280x800".

Press Ctrl + o to save your changes, then Ctrl + x to quit the text editor. Now type in "exit" in the shell, and you should be up and running. Good Luck!

---

### Post by aqueous on 2007-05-30
ok... i tried to do what u suggested reboot, esc, recov. mode, and then enter nano/etc/x11/xorg.conf but it said that it didn't recognize the directory. 

Then, when i rebooted and tried again it showed:
> * Checking file systems...
fsck 1.40 - WIP (14 -Nov-2006)
/dev/loop6: recovering journal
/dev/loop6: clean, 16/256000 files, 17000/512000 blocks

it doesn't move any further than this (waited for 10-15 min) and wont show "root@mycomputer:~#"

---

### Post by ago on 2007-05-30
> **aqueous said:**
> ok... i tried to do what u suggested reboot, esc, recov. mode, and then enter nano/etc/x11/xorg.conf but it said that it didn't recognize the directory.
There is a space between nano and /etc/X11/xorg.cong 

> it doesn't move any further than this (waited for 10-15 min) and wont show "root@mycomputer:~#"
Did you hard reboot? Or did you type "reboot"? It's probably easier to reinstall

---

### Post by aqueous on 2007-05-30
now when i enter the text editor to edit the xorg.conf file, where do i scroll down to? when i enter it, it's blank

---

### Post by ago on 2007-05-30
> **aqueous said:**
> now when i enter the text editor to edit the xorg.conf file, where do i scroll down to? when i enter it, it's blank

It means you have created a new file as opposed to edit an existing one, check well that the path to xorg.cong is not misspelled. You can use "ls" to list folder content

---

### Post by wwoollff on 2007-05-30
every ubuntu has the file xorg.conf

try this way if the above doesn't work

```
cd /etc/X11/
```

this will get you in the folder X11
and now

```
sudo nano xorg.conf
```

if you get an empty file after the command nano, it means that you have created a new file...so you have to close it(CTRL+X) and check if you wrote correctly the command or the path to the file you want to edit ( in this case, /etc/X11/xorg.conf

And the tip about the wide screen is perfect...this thread should be renamed 'Compaq Presario V6000' and sticked

---

### Post by strucebag on 2007-06-02
I too am having this problem, but when I get into the xorg.conf file the modes are already set to 1280x800. Any help would be great.

---

### Post by minhmeoke on 2007-06-02
What is your computer's default screen resolution? It might not be 1280x800; for example, Apple's MacBook Pro uses 1440x900. You can check in Windows by left-clicking on your desktop; then in the display properties window, click on the settings tab. Now just edit the xorg.conf file and substitute the appropriate value.

Oh, and if you are using an ATI graphics card, then see [http://nerdc0re.wordpress.com/2007/04/29/ubuntu-704-ati-gdm-black-screen-of-death/]("http://nerdc0re.wordpress.com/2007/04/29/ubuntu-704-ati-gdm-black-screen-of-death/")

---

