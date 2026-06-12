---
title: "Trouble installing .bin file. Sudo: unable to execute, no such file or directory."
date: 2017-04-26
forum: General Help
---

### Post by kelleeeh on 2017-04-26
Hello...as you can tell, I'm brand spanking new. 

I've looked in the forums, and I've followed all the instructions I've seen, but I'm still having trouble.

I'm attempting to install a Java based program called Snowflake Pro.  It's a .bin file.  As far as I can tell, I'm following all the proper instructions, but I keep getting the same error, which I've included, below.

 I'm running ubuntu 16.04 and I've checked to make sure that the file is executable. Also,if it matters, Java is installed. 

Can anyone tell where I'm going wrong?

Thanks in advance for your help!

[ATTACH=CONFIG]274781[/ATTACH]

---

### Post by &amp;KyT$0P# on 2017-04-26
Please post the output from running this command in Terminal -
```
uname -a
```

---

### Post by kelleeeh on 2017-04-26
kelly@KellyEliteBook:~$ uname -a
Linux KellyEliteBook 4.8.0-46-generic #49~16.04.1-Ubuntu SMP Fri Mar 31 14:51:03 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
kelly@KellyEliteBook:~$

---

### Post by &amp;KyT$0P# on 2017-04-26
I think that error is because you are trying to run a 32-bit program on a 64-bit Linux system.  You can either install the needed 32-bit libraries, or just use a 64-bit installer (if available).

---

### Post by kelleeeh on 2017-04-26
Looks like I'll be spending the rest of my evening researching how to install 32-bit libraries, as I just forked over $50 for the program, and that's the only installer available.

Thanks so much for your help!

---

### Post by &amp;KyT$0P# on 2017-04-26
You're welcome! :KS

The "how to install 32-bit libraries" is the easy part - just use [FONT=Courier New]sudo apt-get install[/FONT] in a Terminal, and make sure to add [FONT=Courier New]:i386[/FONT] on the end of each package name.  For example, if it needs [FONT=Courier New]libexpat1[/FONT] and [FONT=Courier New]libxcursor1[/FONT], you would do this -
```
sudo apt-get install libexpat1:i386 libxcursor1:i386
```

The question to research is, which 32-bit libraries does it need?

---

### Post by Yellow Pasque on 2017-04-26
Your screenshot shows the file is in your Downloads directory and you're running the command from your home directory. Need to:
```
cd ~/Downloads
sudo ./filename
```

But yes, you may need some 32-bit libs.

---

### Post by &amp;KyT$0P# on 2017-04-26
> **Temüjin said:**
> Your screenshot shows the file is in your Downloads directory 
Nope, it's showing the home directory.  And yes, it's confusing. :)

Look at the rest of the folder contents, and look *really* closely at the path bar.

---

### Post by Yellow Pasque on 2017-04-26
^Yeah, you're right. Ignore my previous comment.

---

### Post by ju2wheels on 2017-04-26
Did you set the execute permissions on it first?

```

chmod 755 SnowflakePro.bin

```

Also post output of this:

```

ls -al

```

Im pretty sure you are in the wrong directory despite your screenshot. Otherwise you would be getting permission denied error.

---

### Post by &amp;KyT$0P# on 2017-04-26
ju2wheels, have you ever tried to run a 32-bit executable on a 64-bit system which **doesn't** have the required 32-bit libraries? -
```
$ stat ./palemoon
  File: './palemoon'
  Size: 249440          Blocks: 488        IO Block: 4096   regular file
Device: xxxxx/xxxxxx    Inode: xxxxxx      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: ( xxxx/  xxxxxx)   Gid: ( xxxx/  xxxxxx)
Access: 2017-04-26 xxxxxxxxxxxxxxxxxxxxxxxx
Modify: 2017-03-22 xxxxxxxxxxxxxxxxxxxxxxxx
Change: 2017-04-26 xxxxxxxxxxxxxxxxxxxxxxxx
 Birth: -
$ file ./palemoon
./palemoon: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.18, BuildID[sha1]=f74bd5ebf69ad97e72190ab5954ca84e1903e8ba, stripped
$ ./palemoon
bash: ./palemoon: No such file or directory
$ 
```

Also, quoting the original post -
> **kelleeeh said:**
> I've checked to make sure that the file is executable.

---

### Post by kelleeeh on 2017-04-27
> **halogen2 said:**
> You're welcome! [IMG]https://ubuntuforums.org/images/smilies/star.png[/IMG]

The "how to install 32-bit libraries" is the easy part - just use [FONT=Courier New]sudo apt-get install[/FONT] in a Terminal, and make sure to add [FONT=Courier New]:i386[/FONT] on the end of each package name.  For example, if it needs [FONT=Courier New]libexpat1[/FONT] and [FONT=Courier New]libxcursor1[/FONT], you would do this -
```
sudo apt-get install libexpat1:i386 libxcursor1:i386
```

The question to research is, which 32-bit libraries does it need?



So...after a car accident during my commute home from work and a trip to the hospital (you never know what a day is going to bring) I can't sleep.  SO, I'm going to stay up all night to figure this out.

I keep reading conflicting suggestions regarding the 32-bit libraries:  On one hand, some people say I should install a virtual machine, and then a 32-bit version of ubuntu, and run the program from there...and others say to just install "all" the 32-bit libraries, and call it a day.  I don't suppose you have any opinions on the subject?  :redface:

---

### Post by &amp;KyT$0P# on 2017-04-27
The 32-bit virtual machine is the easiest solution, if your hardware is powerful enough.  It's also a better long-term option - [https://ubuntuforums.org/showthread.php?t=2312451&p=13512079&viewfull=1#post13512079]("https://ubuntuforums.org/showthread.php?t=2312451&p=13512079&viewfull=1#post13512079")

Indiscriminately installing 32-bit libraries is a lottery that will leave you with a bloated system.

---

