---
title: "Do and Don'ts, Tips and Tricks, Preventive, Predictive and Proactive Maintenance"
date: 2013-02-20
forum: General Help
---

### Post by auxilium on 2013-02-20
Hello Everyone,

Among all the forums here, it discuss solutions after the problem occurs. To makes some difference, I create this thread to avoid problem before it happen and to give solutions or advices before it occurs.

We have the Do and Don'ts, Tips and Tricks and Preventive Maintenance of our Dear Ubuntu System. Your idea and keeping Ubuntu System up and running will do a great difference and a lot of help to others. This would be particularly helpful to our new Users in Ubuntu.

Once again Welcome!!!

[CENTER]**[SIZE=4]They say, "A rolling stone gathers no moss".[/SIZE]**
[/CENTER]

 To start the stone rolling here are my tips:

Tip: Choose wisely how to install your video card driver. You can do the manual or automatic.

Do: 
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```to up-to-date you Ubuntu system. I am using it to my Ubuntu 12.04 32-bit

Do:
Back-up your file by putting ".bak" (without the quotation) on your file name, like
```
 cp /path/to/your/file/original.txt /path/to/your/file/original.bak  
```Check these out

[http://www.desktoplinux.com/articles/AT2280165098.html](http://www.desktoplinux.com/articles/AT2280165098.html)

[http://www.computerhope.com/unix/ucp.htm](http://www.computerhope.com/unix/ucp.htm)

Don't:
Don't mess on something until you fully understands how it really works. Make sure you will not create conflicts on what you will do.

 
Feel free to share how you put in shape your Ubuntu System





Cheers,

---

### Post by auxilium on 2013-02-20
Installing a program/software using the Windows Platform, usually you look for Setup.exe. But in Ubuntu its a different thing.

[SIZE=4]Tip:[/SIZE] Use the Ubuntu Software Center to install, to install the software automatically. USC handles the download and installation without worrying shared lib or dependencies

Some times what you need was not there on USC instead you got downloaded it from somewhere

[SIZE=4]Tip:[/SIZE] After downloading extract it where you want to place it. Follow its instruction, most times its in ReadMe.txt. Look for the .bin script and make it executable. 

[SIZE=4]Or[/SIZE] you can go to terminal > go to the directory where you place it > and 

```
 ./executablefile.bin  
```where "executablefile" is your application name. There are time you need a root privilege so you just add sudo like so

```
 sudo ./executablefile.bin  
```* To make it executable do(make sure you are in the current directory of that file you wish to make executable
```
sudo chmod +x excutablefile.bin
```[SIZE=4]Or[/SIZE] if it is a source, after extracting it, go to the current directory using terminal
do
```
 ./configure.sh
``````
make
``````
make install
```I may not that good doing it but if you have do this in a better way, glad to see it posted here. Right me, if I got it wrong. I am happy to get it the right way


Thanks for reading

---

### Post by auxilium on 2013-03-28
Hi to all viewers,

I think I found it more convenient(for me, atleast) to update Ubuntu 12.04  using terminal. To do this, open a terminal and input

```
sudo apt-get update 
```

then supply your password

```
sudo apt-get upgrade 
```

or you can do the two command in one line

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by auxilium on 2013-03-28
Cont...

Sometimes you could encounter problems, you can do

```
sudo apt-get install -f 
```

then re-update



Cheers,

---

### Post by coldraven on 2013-03-28
After you have installed Ubuntu do this in a terminal, you will be asked for your password but it will not be displayed.
```
sudo lshw > hardware.txt
```
This makes a file called hardware.txt in your home directory.
If you need help with a hardware problem then you can easily scroll through this file and copy/paste the relevant details by opening the file in a text editor.
Just double click the file to open it.
Gedit is the default text editor in Ubuntu or just search in the dash for "text".

---

### Post by slickymaster on 2013-03-28
> **coldraven said:**
> After you have installed Ubuntu do this in a terminal, you will be asked for your password but it will not be displayed.
```
sudo lshw > hardware.txt
```
This makes a file called hardware.txt in your home directory.
If you need help with a hardware problem then you can easily scroll through this file and copy/paste the relevant details by opening the file in a text editor.
Just double click the file to open it.
Gedit is the default text editor in Ubuntu or just search in the dash for "text".

+1 on colraven's advice.

Chances are, specially if you're a new user, that you'll need the detailed information on the hardware configuration of the machine, and that's what this command does. It extracts the exact memory configuration, firmware version, mainboard configuration, CPU version and speed, cache configuration, bus speed, etc, into a txt file.

---

### Post by Irihapeti on 2013-03-28
BACKUP before you trying installing anything unusual, or start playing with configuration files, drivers and so on. Then it's easy to go back if you make a terrible mess.

BACKUP before installing a new version of Ubuntu or any other system. Make sure you've got your Windows restore DVDs prepared if you've got one of those computers that allows you to make DVDs from your restore partition.

BACKUP regularly, anyway. It may be a pain but it's much less painful than realising that you've lost all your photos, your only copy of your dissertation, or other valuable files.

---

