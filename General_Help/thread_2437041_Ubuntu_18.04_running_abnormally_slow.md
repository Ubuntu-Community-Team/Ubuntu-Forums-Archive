---
title: "Ubuntu 18.04 running abnormally slow"
date: 2020-02-17
forum: General Help
---

### Post by jamesoreilly on 2020-02-17
My ubuntu installation is running abnormally slow. Simple processes like running the gnome terminal are causing massive spikes in CPU usage and I cannot figure out why.

The slowing down seems to be caused by gnome-shell and Xorg having abnormally high CPU %. 

I have adequate disk space and memory (as far as i can tell), and everything is up to date. I would appreciate any help in determining the potential cause of this issue. 

Cheers!

---

### Post by EuclideanCoffee on 2020-02-17
You can use pstree to map processes to their parents, in order to find the root of the problem.

$ pstree -p

This will show you PIDs.

---

### Post by TheFu on 2020-02-17
"slow" can mean almost anything.  It isn't surprising when an Atom N270 w/ 1GB RAM system runs slow with Gnome3. That is expected.

Generic troubleshooting:
* check if any processes are sucking all the RAM and CPU.  **top**   and **free -h**
* check the log files for any warnings or errors.  /var/log/*og
* check that storage has 1-2GB of free space for / and /var.   **df -Th** and **lsblk -o name,size,type,fstype,mountpoint**

If those thing don't show the issue and you want help, then we need to know about your system setup. 
The easy way to provide an overview is :  **inxi -Fz**

Whenever posting any command output here, please .... 
a) always show the actual command and all options used.  copy/paste it.
b) always copy/paste the output text as shown in the terminal.
c) Wrap the command and output in **code tags**. Use the "Advanced Editor" - *Go Advanced* or *Adv Reply* then select all of the above and use the (#) button just like quote or bold works.
d) If you forget to use code tags, fix it by editing the post. No need to create another post.

_Code tags_ makes columns line up just like they do on the terminal.  Experts are used to this. We know where the most critical stuff in the output is located. We see it all the time.  The exact command AND options are needed too, so we can lookup any unfamiliar options AND so other people with a similar issue can as well.  Without code tags, the output is usually too hard to read.   With the text copy/pasted, a knowledgeable expert can easily copy/paste the specific parts of interest to explain stuff.  Images don't allow that.

---

