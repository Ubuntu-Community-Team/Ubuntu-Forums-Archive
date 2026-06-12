---
title: "[SOLVED] Need Advice And Some Help"
date: 2006-11-02
forum: General Help
---

### Post by valleyman7 on 2006-11-02
I have looked for a way to install several programs and I am so dumb I guess I cannot get it. I have done searches on the forum, I have purchased two great books The official Ubuntu Book, and Moving to Ubuntu Linux by Marcel Gagne. There is great for instructions on installing software from the repositories, and I have been able to update and install several programs. But I have Nero for linux, Opera and a little linux utility called Across Lite which is used for crossword puzzles from the New York Times. Can someone walk me through installing this type software or point me to a tutorial which will help me install this software. I think if I can do it once I will be on may way. So far I have the Internet working and that makes this old man happy. But when I can get my wife's Xword puzzles downloaded and printed I will really be a happy camper. Just not enough time to learn, but I refuse to give up. I also appreciate all the help I have received from this forum maybe some day I will be able to give back. :-?

---

### Post by taurus on 2006-11-02
There is a version of opera for Ubuntu and it's in the repos so you just install it with either synatic/apt-get/aptitude.  Perhaps you need to enable both universe & multiverse in /etc/apt/sources.list

Meanwhile, there is a version of nero for linux as well.  I believe it's called nerolinux and if you have the key from your Windows version, you can use the same key to activate it.  Otherwise, use k3b if you plan to do any burning at all in Ubuntu.

Now, it depends on what file format your program is in.  There are different ways to install it.  If you can be a little more specific what it is, then maybe I can walk you thru it.  Just me the exact name of the file you want to install.  Otherwise, here is something for you to read then...

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by GCR on 2006-11-02
I would recommend k3b over NeroLinux any day. Maybe its me, but in Linux, k3b is far more responsive in my PCs that Nero. But you could give it a try and choose for yourself :)

---

### Post by valleyman7 on 2006-11-02
The software utility across has the following choices for downloading. To get to this you must be able to logon with and account otherwise I would have provided a url.


 


# acllinux.smotif.tar.gz: Statically linked to Motif

# acllinux.dmotif.tar.gz: Dynamically linked (you must have Motif library installed)

---

### Post by valleyman7 on 2006-11-02
I should have provided more info on this utility. 

Downloading Across Lite for Linux (v. 1.1)



Download the program by clicking on one of the following links:


# acllinux.smotif.tar.gz: Statically linked to Motif

# acllinux.dmotif.tar.gz: Dynamically linked (you must have Motif library installed)

Across Lite is available in a statically linked (to Motif) version and a dynamically linked version. Both versions are ELF binaries. The a.out versions have been discontinued. If you must have the last a.out version, send E-mail to the Across Lite Help Desk, [email]acrossnyt@litsoft.com[/email].

You must use gunzip or an equivalent to uncompress the file and tar to extract the program and puzzle files. Check the README file in the distribution for starting instructions.

Further technical details are available here.

You should now be able to launch Across Lite and play your crosswords.

---

### Post by taurus on 2006-11-02
> **valleyman7 said:**
> I should have provided more info on this utility. 

Downloading Across Lite for Linux (v. 1.1)



Download the program by clicking on one of the following links:


# acllinux.smotif.tar.gz: Statically linked to Motif

# acllinux.dmotif.tar.gz: Dynamically linked (you must have Motif library installed)

Across Lite is available in a statically linked (to Motif) version and a dynamically linked version. Both versions are ELF binaries. The a.out versions have been discontinued. If you must have the last a.out version, send E-mail to the Across Lite Help Desk, [email]acrossnyt@litsoft.com[/email].

You must use gunzip or an equivalent to uncompress the file and tar to extract the program and puzzle files. Check the README file in the distribution for starting instructions.

Further technical details are available here.

You should now be able to launch Across Lite and play your crosswords.
Okay, you may want to download the acllinux.smotif.tar.gz unless you want to install lesstif first.  Then, you can download the dynamic version.  Let's assuming you decide to go with the static (a little larger), download it to your computer and open a terminal, Applications -> Accessories -> Terminal, and do

```
cd ~/Desktop <-- this is where all your downloads will be saved to...
tar xvzf acllinux.smotif.tar.gz <-- to uncompress and untar it...
cd allinux.smotif <-- change to new directory that...
ls -la <-- list all the files and permissions in that new directory...
```
Now, there should be an execute file that you can run and since I don't know what it's called, I can't tell you.  But if you can list the output of "ls -la" here, maybe I can tell you which one to run...

---

### Post by valleyman7 on 2006-11-02
](*,)  OK it's getting late and now my head is is going crazy. I am not  in Ubuntu right now, so tomorrow I will open the file and post a copy of the files which I think if I did it correctly are un-zipped. Thanks again and I will check back tomorrow.:confused:

---

### Post by valleyman7 on 2006-11-03
The only file is across, readme, and the license. There is a folder called man nothing but gif files and htm files. The other folder is sample puzzles. Thanks for your time.

---

### Post by taurus on 2006-11-03
Wait a second.  You do that in Windows!!!  I thought you want to unpack and play that game in Ubuntu...  Therefore, save the download to your Ubuntu partition and unpack it again with the instructions from my post above.  Then, show me the output of the "ls -la" command.

---

### Post by valleyman7 on 2006-11-03
Just wanted to say thanks for the help but I guess the cmd prompt is more than I can figure out. I guess I will just leave it to all you young guns. This old dog can't be taught. Thanks again. :confused:](*,)

---

