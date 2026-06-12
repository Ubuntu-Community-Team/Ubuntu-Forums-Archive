---
title: "How to change default font size in console mode?"
date: 2016-04-06
forum: General Help
---

### Post by gtree on 2016-04-06
I want to use the console - not simply a terminal from within X windows, but in full console text mode. This can be achieved by pressing ```
ctrl-alt-F1
``` or any of F1 to F6. Press F7 to return to X windows.

Anyway, the default console font size is far too small and I need to increase it to a reasonable size. Only last year, it was easy to do this by ```
sudo dpkg-reconfigure console-setup
```. However, with the latest release of ubuntu this command will only work to reset the font size for the current session. Once the system is rebooted, the console font size will return to the default small size. I found a thread here:
[http://ubuntuforums.org/showthread.php?t=2275119&highlight=change+default+console+font+size](http://ubuntuforums.org/showthread.php?t=2275119&highlight=change+default+console+font+size) but like I say, the fix no longer works with the latest release of ubuntu.

So I searched around online and asked this question on the ubuntu forum in stack exchange. I found a thread there about this problem, but the solution was very poorly explained and I could not get it to work for me. When I asked the question, my tread was closed and they simply said it has been asked before. The fact that the answers were not clear did not seem to make any difference. Because I could not find a solution which works to change the default console font size and what is maintained after rebooting, I am asking for help with this here.

Can anyone help with this please?

---

### Post by sudodus on 2016-04-06
Welcome to the Ubuntu Forums :-)

It makes it easier to help, if you tell us about your computer hardware and the version of Ubuntu. (I am also curious about the reason why you want to run in console mode, but I need not know it.)

-o-

See this link: [Grub2/Setup](https://help.ubuntu.com/community/Grub2/Setup)

The grub file is a system file, therefore any editing must be done by a user with 'Administrator/root' privileges. The file is a simple text file and can be edited by any text editor. The default text editor in Ubuntu is Gedit, and the file can be edited with the following command. "gksu" is the graphical equivalent of "sudo" and the "&" allows the terminal to be used to update GRUB 2 once the user saves the file.

```
sudo apt-get install gksu
gksu gedit /etc/default/grub &
```

I think there are two options for you to try:

10. **GRUB_TERMINAL=console** (you should remove the # character to make it active) I think this gives you a crude 80 characters x 25 lines screen.

12. **GRUB_GFXMODE=640x480** (you should remove the # character to make it active, and also consider ***other resolutions*** as described in the link)

***Important:*** After making changes and saving the file, the GRUB 2 menu must be updated to include the changes by running:

```
sudo update-grub
```

and rebooting.

---

### Post by gtree on 2016-04-06
Hi sudodus, thank you for a prompt reply. I'm afraid the solution you suggested was not quite what I needed. I did a little more experimentation and have now managed to achieve the configuration that I wanted. I will set out the solution below in case anyone else here wants to do the same.

If you are running Ubuntu 15.10 or later, then running > sudo dpkg-reconfigure console-setup will not work to permanently change the default font size of the console. To do this you will need to follow these steps: 

1.  There is a set of custom fonts for your console. You must first download them with this command:
```
sudo apt-get install fonts-ubuntu-font-family-console
```

2. Next, you will use a text editor to create a script. I simply used gedit. You must create the file as root / administrator - so enter the command:
```
sudo gedit /usr/local/bin/fontset
```

Once the new empty file is open in gedit, you need to specify the font that you want to use as your console default. Now you can see a list of all the available fonts by visiting the directory ```
 /usr/share/consolefonts/
```. There are in total 302 available fonts, so you may want to test a few until you find one that you like. You should adjust the code below to reflect the font that you want to use. This is the larger font that I selected. Enter this code into the new empty file /usr/local/bin/fontset using gedit:
```
#!/bin/sh
setfont /usr/share/consolefonts/Uni3-TerminusBold32x16.psf.gz
``` 

To clarify once more, Uni3-TerminusBold32x16.psf.gz is the font that I choose to use. There are 301 others in the font directory that you downloaded & installed earlier! So you set the path to the exact name of the font you want to use. Once done, save the file with the changes and exit gedit.

3. You must next edit your ```
.profile
``` which is a hidden file located in your home directory. I simply used gedit again to do this. As .profile is your file, you have permissions to change it and there is no need to type sudo first. So enter:
```
gedit .profile
```
This will open up your .profile file. There will be lines of entries in this file that you should not change. Just scroll down to the bottom and add these lines to your .profile:
```
if [ "$TERM" == "linux" ]; then
/usr/local/bin/fontset
fi
```

Save the file with the changes and exit gedit.

4. Next, you need to change the permissions of the script that you created earlier. Because it was created as root using sudo, you should enter the following command:
```
sudo chmod 777 /usr/local/bin/fontset 
```

Finally, reboot your system.

Once you restart, you can log onto anyone of the 6 consoles pressing the keys:
```
ctrl-alt-F1
``` or F2-F6

At first the console text at the prompt is the tiny default. Enter your username and password at the prompt and your new customised font will be displayed.

---

### Post by sudodus on 2016-04-07
Congratulations and thanks for sharing your advanced solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by sudodus on 2016-05-16
@ gtree,

Thanks again for sharing your advanced solution :-) I have made it part of a system, which can be used to install a text-only Ubuntu based system to be expanded into Ubuntu Server or one of the Ubuntu desktop flavours (Kubuntu, Lubuntu, ... Xubuntu).

A compressed image file can be expanded and cloned into a drive as easily as you make a USB boot drive from an iso file. And the result is a system, that can boot in UEFI and BIOS mode.

See this link: [UEFI and BIOS mini system with 'text' screen user interface](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#Mini_system_with_.27text.27_screen_user_interface)

Please notice the third screenshot with the menu to select font, the 'font submenu'. It works well to get a suitable size of the text with different screen resolutions and for different eyes :-)

---

