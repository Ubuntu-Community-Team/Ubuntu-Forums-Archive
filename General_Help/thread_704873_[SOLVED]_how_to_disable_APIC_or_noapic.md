---
title: "[SOLVED] how to disable APIC or noapic"
date: 2008-02-22
forum: General Help
---

### Post by JimBuntu on 2008-02-22
Some one please give step by step on how to append 'noapic' to our boot up. There are lots and lots of posts, but none seem to give directions clear enough for a newb.

Please list all steps including how to update grub. Literally, I'm talking word for word. Some of us do not know how to work with command line yet. 

Thank you

---

### Post by ajmorris on 2008-02-22
hi there,
1) open terminal
2) sudo nano -w /boot/grub/menu.lst
3) locate towards the bottom of the file, your entry for booting the current kernel you are in (kernel version can be found by uname -r in the terminal)
4) add this to the kernel line (at the very end of this line): noapic
5) save, close the file, then reboot

Now you have noapic

---

### Post by spiderbatdad on 2008-02-22
If you are trying to use this to get the livecd to boot, press F6 at the install options screen, and remove ro --quiet splash from the end of the boot line. Then replace with noapic. You will also need to specify some vga settings like vga=771. If you also press F1 and F6 again you can read some examples of boot parameters.

---

### Post by JimBuntu on 2008-02-22
Thanks guys.

To all who have this question here is another set of codes you can put in terminal to make the 'noapic' permanent.

In terminal type:

sudo gedit /boot/grub/menu.lst

Once you see the text file that comes up, you should look carefully about halfway down the file and find the section that says '#defoptions'

In that section you should see the words 'quiet splash' at the end. Type 'noapic' after the 'quiet splash'. Remember to leave a space between the added text.

Once done type this code in the terminal:

sudo update-grub

You should see the list of text saying 'done' at the end.

There it is now official. Restart your computer and you should not have an IO-APIC error.

---

### Post by mariomatejka on 2008-02-23
Excelent Post!  I'm an Ubuntu newb, and I have been struggling with this issue for a while now, until now that is.  I thought that editing the menu.lst file was good enough and that saving changes was equivalent to the sudo update-grub command.  Boy- was I ever wrong.  I kept changing the menu.lst file yet my changes never took effect.  It turns out that the sudo update-grub command is the key.  After you edit the menu.lst file and save your changes you must issue the sudo update-grub command for the changes to take effect.

Most people probably know this, I just thought I would post it if any other newbs have the same problem as I did.

---

### Post by JimBuntu on 2008-02-24
Cool man. Yes I was in the exact same boat as you. There were post that showed something similar but never showed the details that a newbie would need to know like using the word 'sudo' in front of update-grub. Or even putting a dash in between the words update and grub. I'm glad I was able to make it clear enough to help.

Peace

---

### Post by mrgmhale on 2008-03-05
JimBuntu, I am a "seasoned newbie" (got into Suse Linux Enterprise Server v-10 in November 2007, Ububtu in January 2008), and have learned enough thus far to be dangerous.  I have been cutting folks from Windows to Ubuntu Linux since February 2008, for home users who do not absolutely have to use Windows, and have gotten nailed with Spyware, Viruses, etc.  

Until today all went well, and then I got a friend with a Compaq Presario SR2002X that threw an IO-APIC error at me upon bootup.  Your having shared your steps to get around that problem were dead on, and much appreciated.

Gil

---

