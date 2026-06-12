---
title: "initramfs at boot please help"
date: 2008-07-04
forum: General Help
---

### Post by njmbb8 on 2008-07-04
When i try to boot ubuntu it starts to work normally but then it goes to a screen with the following text

busybox v1.1.3 (debian 1:1.1.3-5ubuntu12) Built-in shell (ash) enter 'help' for a list of builtin commands

initramfs

---

### Post by ago on 2008-07-04
Use Wubi 8.04.1, run chkdsk /r in windows and shutdown cleanly.

---

### Post by NIMBUS007 on 2008-07-05
i have the same problem... 
1) i dl 8.04.1 iso and 8.04.1 wubi
2) i put them in the same folder and run and install wubi
3) i restart win and choose ubuntu at boot 
4) i get ubuntu loading screen for about 12 secs and then i see that annoying initramfs 
5) than i booted win did 'chkdsk /r'... restarted win chkdks happened found nothing and booted win
6) than i tried to boot ubuntu and was shown the middle finger (initramfs)

any suggestions or should i kick my compuer really hard? m? any1? :)

pls help what m i doing wrong? is 2nd line wrong?

---

### Post by jmszr on 2008-07-05
This is from the Wubi Wiki-lots of good information there:

The Ubuntu splash screen loads for awhile then exits to a BusyBox/(initramfs) prompt.

Try The Following Solutions : 1) Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in.Click Properties.

    *

      Select the "Tools" tab and click "check now" under error checking( On Vista, You might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After The checking is done, restart the pc by using the start menu(Do not hard reboot) and try using ubuntu now.

2) Reboot and hit Esc when prompted to enter the boot menu. Hit 'e' to edit the first line. Next select the second line and hit 'e' again. Input 'irqpoll' towards the end of the bootline. Then hit 'enter' and then 'b' to boot.

---

### Post by NIMBUS007 on 2008-07-05
jmszr i have tried that like 4 times and one more time with 8.04.1 ... my pc is doomed 

i give up.

---

### Post by ago on 2008-07-05
When you are in initramfs what is the ouput of

cat /proc/cmdline
cat /proc/partitions
cat /proc/mounts
grep -i err /casper.log

---

### Post by NIMBUS007 on 2008-07-06
ok here it is - i did what u said ago 

cat /proc/cmdline
cat /proc/partitions  are in this picture
[http://hosting05.imagecross.com/image-hosting-18/4881DSC00140.JPG](http://hosting05.imagecross.com/image-hosting-18/4881DSC00140.JPG)

cat /proc/mounts
grep -i err /casper.log
[http://hosting05.imagecross.com/image-hosting-18/2958DSC00145.JPG](http://hosting05.imagecross.com/image-hosting-18/2958DSC00145.JPG)

i dont know if it changes anything but those outputs are on a new wubi install. that irqpoll thing hasnt been done.

thanks for helping :)

---

### Post by ago on 2008-07-06
Do you have a raid 0? That is not supported at the moment

---

### Post by NIMBUS007 on 2008-07-06
yea well it looks like im not getting my hands ubuntu with my screwed up cdrom :/

---

### Post by prabath_fun on 2008-07-07
Hi,
  I got it solved, just by booting system with windows and proper shutdown. My Windows was improperly shutdowned because of power failure.

---

