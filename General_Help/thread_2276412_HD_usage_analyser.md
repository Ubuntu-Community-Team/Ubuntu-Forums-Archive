---
title: "HD usage analyser?"
date: 2015-05-02
forum: General Help
---

### Post by majabl on 2015-05-02
I'm looking for a program to show me how the space on my hard drive is being used.

I'm using Xubuntu 14.04 LTS on an IBM T42 around 10 years old. Is Baobab my best bet or is there something better for Xubuntu/older laptops?

Thanks in advance.

---

### Post by dragonfly41 on 2015-05-02
in my old laptop I have Ubuntu 14.04 and I use System Tools > Disk Usage Analyser.

It takes a few minutes to build up an analysis of your drives but then you have an interactive display
where you hover over large areas in the diagram.

---

### Post by Bucky Ball on 2015-05-02
Xubuntu should already have Gparted installed. If not, install it from Synaptics Package Manager and have a look at your disks there. I'm running a minimal install with xfce4 as the DE, not a straight Xubuntu, so don't know what apps are default in that anymore. But Gparted will certainly do what you're after and more.

---

### Post by tgalati4 on 2015-05-02
MATE will probably run OK on that machine.  I have it running on my T43p.  Disk Analyzer is similar to Baobab.  There was an old program called Disk Hog, but I can't find it.  Perhaps that code base was rolled into another utility.  Baobab and Disk Analyzer are very similar.  It's interesting that there are literally hundreds of disk hog programs on Windows.

---

### Post by oldos2er on 2015-05-02
Filelight is kind of a cool program if you don't mind GUI.

---

### Post by ajgreeny on 2015-05-02
Disk-usage-analyser is baobab but I don't know about Disk-Analyzer in Mate; could that also be the same executable?

How much detail do you need? Does it have to be a GUI application as **du -h -d 1** might be all you need to see where the disk usage is highest, though I can't figure out how to sort the output directly in terminal, nor how to get that command to show all the file-system main folders, eg, /etc, /lib, /usr, and so on.

---

### Post by oldfred on 2015-05-02
I do not know these commands but have them all in my notes:
 With sorting and cd / or cd /home first:
du -ks * | sort -nr | cut -f2 | xargs -d '\n' du -sh
      
 # check sizes of 
Partition sizes
df -Th | sort
Inodes:
 df -i
cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

Not sure this still works, they have made it more difficult to get to /root.
to also see hidden in /root folder
sudo du -sh /root/.[A-z]* /root/*

---

### Post by majabl on 2015-05-26
Thanks, everybody, for your help.

I've decided to stick with Disk Usage Analyser. I didn't realise it was the same thing as Baobab - funny that one or the other doesn't get renamed for simplicity!

The program takes a good 10-15 minutes to analyse my C: on this laptop, but once it's done the graphical output's straightforward to navigate. The only other thing I should add is that I had to launch the program from Terminal Emulator with 'sudo' because if I didn't then there were parts of my hard drive that DUA couldn't touch. (Without 'sudo' I get the error message: 'Could not scan folder "/" or some of the folders it contains. Permission denied'.)

---

### Post by Bucky Ball on 2015-05-27
If you're happy please mark the thread as solved to help future travelers. See second link in my signature for how. This _doesn't_ close the thread for further discussion. Good luck. ;)

---

### Post by majabl on 2015-05-27
Done! :)

---

