---
title: "Please Help"
date: 2008-06-10
forum: General Help
---

### Post by Dave--B on 2008-06-10
Hi All

I need help with my hard drive, I was reinstalling Ubuntu and when i was partitioning i changed my c:/ drive (win Vista) to a ext3 file system (i did not format the drive) by mistake.I can no longer boot up Vista. I have two 500GB hard drives one internal and one external, i have installed Ubuntu to the external drive and is working fine. Can you help return my internal drive back to NTFS with out formatting as it has my win vista on it with all my data ? If not is there any software (to run on Ubuntu) i can use to read the files so i can get my data off and i will reinstall vista. Im sure someone can help.

Thanks 

Dave

---

### Post by Pjotr123 on 2008-06-10
Changing it to EXT3 means formatting it..... Vista is probably gone. Tough luck, I'm afraid.

---

### Post by didac on 2008-06-10
Check this program:

[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Dave--B on 2008-06-10
Hi

Thank you for the link for that software, it looks like it could do the job. One question thought how do i install it im very new to linux and im sure i missing something very simple. If you could send some instructions on how to install software i would be very thank full.

Thanks

Dave

---

### Post by Pjotr123 on 2008-06-10
1. An operating system should be on an internal disk, not on an external USB disk.
2. Check this easy how-to:
[http://ubuntutip.googlepages.com/installationofubuntu](http://ubuntutip.googlepages.com/installationofubuntu)

---

### Post by doorman on 2008-06-10
To install the software, download this file: [http://www.cgsecurity.org/testdisk-6.9.tar.bz2](http://www.cgsecurity.org/testdisk-6.9.tar.bz2)

Then, after extracting the files, open the file compile_linux.html, located in the doc/ subdirectory. There, find the ubuntu section and enter the line in a terminal ( if you're not the superuser, then the command must be preceded by "sudo" ).

Now, navigate to the TestDisk directory. Type in the terminal:
```
$ ./configure
$ make
```

If all went good, you should have a running program now...

Good luck with the recovery!

P.S. Please make sure that whatever you do / install / change is on the extern disk. If you write to the internal disk by mistake, all your data will be gone!

---

### Post by Dave--B on 2008-06-10
Hi 

Thanks for the help. When you say navigate to the testdisk directory what do you mean (were is it) ? 

Thanks Dave

---

### Post by doorman on 2008-06-10
by navigating I mean positioning yourself to that directory. That is, supposing you extracted the archive contents onto your desktop, open up a terminal. You should already be positioned in your home directory, so all you have to do is enter:
```
$ cd Desktop
```After you extracted the archive, you should have noticed a new directory (or "folder") appeared on your desktop. So, you have to enter that directory by punching
```
$ cd name_of_dir
```in the terminal. You should now be able to compile and run the program

Good luck with the recovery!

[Edit] P.S. you shouldn't actually punch the "$" sign in the terminal, it's already there! :)

---

### Post by didac on 2008-06-11
Download from the following link

[http://www.cgsecurity.org/testdisk-6.9.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.9.linux26.tar.bz2)

It has already been compiled fpr you and it should work. If it shouldn't, follow doorman's directions.

Once you download it, let's say to the Desktop, right click on the icon, choose "Extract here". Now go to Applications menu and open a terminal. There type:

```
cd ~/Desktop/testdisk-6.9/linux
sudo ./testdisk_static
```

I've omitted the $ bit . . .

Create a log file when prompted. Now select the partition to recover. Move with arrows, tab and enter keys. Select Intel partition. Then "Analyse", "Quick Search," "Y" to search for Vista partitions. If it finds your deleted parition, select Enter and Write. If it doesn't find it yet, select Enter and Deeper Search. If it finds it, then Write. By now it should be a Vista partition again and your files will be back.

If it doesn't find anything -- sorry -- get out of testdisk and do in a terminal:

```
sudo ./photorec_static
```

Proceed and Intel partition. Choos e Other partition, and Whole. Select anopther hard disk to start recoverinbg as many files as possible.

Good luck

---

