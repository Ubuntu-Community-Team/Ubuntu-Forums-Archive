---
title: "Linux newb need terminal help"
date: 2007-02-03
forum: General Help
---

### Post by Skull Kid on 2007-02-03
Hi, I just installed Dapper last night so I'm not familiar at all with terminal commands. I am trying to use [this]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28WifiDocs%2FDriver%29#head-afca59bb303accf7d6ee9144facd385f7c55fde3")
guide to install my Ralink rt2500 wireless adapter. I downloaded the rt2570 driver (since that's what I've read works with my adapter) from the site provided. Down at step 2 it tells me to type ```
tar -xzf rt2570-1.1.0.tar.gz
```
but I get 
```
tar: rt2570-1.1.0.tar.gz: Cannot open no such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
```

I'm obviously doing something wrong here.... thanks for any help.

---

### Post by taurus on 2007-02-03
You probably saved it to Desktop.

```
cd ~/Desktop
tar xvzf rt2570-1.1.0.tar.gz
```

---

### Post by banditti on 2007-02-03
It looks like you are not in the directory where the file is located when you are running that command.  Perhaps it didn't download right, but I think not the same directory.

---

### Post by Skull Kid on 2007-02-03
So basically I just type in the directory where the file is and then type the command? I did that and it just said "is a directory".

---

### Post by taurus on 2007-02-03
What did you type exactly?  What's the output of this command from a terminal?

```
ls -la ~/Desktop
```

---

### Post by blackened on 2007-02-03
As has already been said, first you need to be in the directory where the file is. You can do this through the terminal or with nautilus (the file manager). From the terminal type
```
cd */directoryname*
```
cd stands for "change directory"
now since you likely saved it to the desktop, and because the terminal defaults to opening in your home directory you should be able to just type
```
cd Desktop
```
and then the tar command should work.

You can also accomplish this through the file manager. Open your home directory, then go to the Desktop directory and right click on the file. From there select the "Extract Here" option.

Hope this helps.

---

### Post by Skull Kid on 2007-02-03
It shows the folder where I saved the driver. The actual file is in  /home/user/Desktop/ralink2500driver/rt2750/rt2570-1.1.0-b2.tar.gz

edit: Thanks blackened I will try that.

---

### Post by taurus on 2007-02-03
```
cd ~/Desktop/ralink2500driver/rt2750
tar xvzf rt2570-1.1.0-b2.tar.gz
```

---

### Post by Skull Kid on 2007-02-03
Finally extracted it, but now when I go to the Module folder like it says and type 'make' it says "command not found".

---

### Post by Polygon on 2007-02-03
do you have build-essential installed? 

```

sudo apt-get update
sudo apt-get install build-essential

```

edited: forgot the update thx taurus =P

---

### Post by taurus on 2007-02-03
```
sudo aptitude update
sudo aptitude install build-essential
```

You probably have to run the ./configure first though!

---

### Post by Skull Kid on 2007-02-03
I guess that means I will need an internet connection then? Because it said failed to download some files. I'm currently using another computer that is hooked up via an ethernet connection and got the drivers to ubuntu with a usb drive. But thanks for sticking with me this far guys.

---

### Post by taurus on 2007-02-03
Build-essential is on the CD.  Insert the CD into the drive, open a terminal, and type

```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Skull Kid on 2007-02-03
Did that and it seemed to work except for aptitude update where it told me the same thing : 'temporary failure resolving mx.archive.ubuntu.com' and something from security.ubuntu.com.

---

### Post by taurus on 2007-02-03
Don't worry about that error message since you don't have a network connection yet.  Now, you can build whatever you want from source.

---

### Post by Skull Kid on 2007-02-04
I get some other error when typing 'make' in the Module directory. I am going to bed now but Ill post back later.

---

### Post by Skull Kid on 2007-02-04
Ok, first I type cd and then the module directory and press enter. When I type 'make' I get this:

```
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory. Stop.
rt2570.ko failed to build!
make *** [module] Error 1
```

Thanks again for the help

---

