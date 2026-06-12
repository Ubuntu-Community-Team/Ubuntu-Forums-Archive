---
title: "Ubuntu runs so slow!"
date: 2007-06-27
forum: General Help
---

### Post by Dimitrianos on 2007-06-27
I've installed the normal Ubuntu through Wubi with no problems or anything, but when I login everything goes so slow. Firefox takes about a minute to load and apt-get takes ages to install programs.

My computer specifications:

P4 2.8 GHz
256mb RAM
60 GB HDD
20 GB HDD

Wubi has installed Ubuntu on my second, 20 GB hard drive.
I did defragment the drive before installing.

Any suggestions?

Dimitri.

---

### Post by pardesi on 2007-06-27
well what version are you using?
assuming you are using Fiesty Fawn
i think this is(may be) because of yor memory...well ahat's your graphics card memory if it eats away a chunk then that may be a cause ...becaus ethe specified rather reqd. memeory for fiesty fawn is 256MB  of RAM

---

### Post by ago on 2007-06-27
Can you please monitor swap usage and benchmark HD access?

---

### Post by Dimitrianos on 2007-06-27
> **ago said:**
> Can you please monitor swap usage and benchmark HD access?

Sure, but I'm not too sharp with Ubuntu yet, do you think you could tell me how to do that?

---

### Post by ago on 2007-06-27
Well a firts step is the System Monitor. 

As for hd benchmarking see for instance [http://www.wlug.org.nz/HarddiskBenchmarks](http://www.wlug.org.nz/HarddiskBenchmarks), [http://www.linuxinsight.com/how_fast_is_your_disk.html](http://www.linuxinsight.com/how_fast_is_your_disk.html) and hdparm

---

### Post by Dimitrianos on 2007-06-27
Now it won't start up!

Freezes with the progress bar just a little way across.

---

### Post by ago on 2007-06-27
Press alt+f1 to see what is happening, or edit c:\wubi\boot\grub\menu.lst and delete "quiet spalsh" to have a verbose boot.

---

### Post by Dimitrianos on 2007-06-27
Okay, something has just came up but I'll be sure to do that soon (in about 45 mins).

---

### Post by miketowninc on 2007-06-27
I have the same problem. I have 256 ram also. You can try Xubuntu. Its made for slow pc. I used it and it helped. But NOt that much. But you should definitely try it.

thegreyspot

---

### Post by murmelhunter on 2007-06-27
Maybe Wubi messed up some things..

Make a clean install from the install cd/dvd and choose at the first menue the option =>
install in text mode
( due to the low amount of ram the first option from the menu will not work)

Once the installation is done feisty will work not super fast but fine => firefox need than only 3-5 seconds.

I have been testing Feisty 7.04 with Beryl on Notebook with 256 MB and no issues with freezing or such slow reactions from firefox

---

### Post by miketowninc on 2007-06-27
Really but wubi is so easy.. Crap. maybe i will try it

---

### Post by Dimitrianos on 2007-06-27
I ended up installing from the CD in graphical mode.
Worked perfectly and Ubuntu is much faster than Windows.

---

