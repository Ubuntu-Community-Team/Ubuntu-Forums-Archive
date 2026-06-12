---
title: "Comodo antivirus setup"
date: 2014-02-16
forum: General Help
---

### Post by philromford-q on 2014-02-16
I have installed Comodo antivirus, however, it has to be set up in terminal, running:-

/opt/COMODO/post_setup.sh

Terminal returns:-

Please run this script with administrator privileges.

I have no idea how to do this, can anyone help please?

Thank you.

---

### Post by lisati on 2014-02-16
A common way of running a command with Admin privileges is with help of the [sudo]("https://help.ubuntu.com/community/RootSudo") command, e.g.
```
sudo  /opt/COMODO/post_setup.sh
```

You'll probably be asked for your password. Type your password normally, even though it won't show as you type.

---

### Post by philromford-q on 2014-02-16
Thank you lisati, that's done it.

---

### Post by philromford-q on 2014-02-16
The Comodo kerel module installer does not work, as some others have found. The terminal output is this:-

make -C /lib/modules/`uname -r`/build M=/tmp/driver/redirfs modules









make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  CC [M]  /tmp/driver/redirfs/rfs_path.o

  CC [M]  /tmp/driver/redirfs/rfs_root.o
  CC [M]  /tmp/driver/redirfs/rfs_info.o
  CC [M]  /tmp/driver/redirfs/rfs_file.o
/tmp/driver/redirfs/rfs_file.c: In function &#8216;rfs_readdir&#8217;:
/tmp/driver/redirfs/rfs_file.c:259:37: error: &#8216;const struct file_operations&#8217; has no member named &#8216;readdir&#8217;
/tmp/driver/redirfs/rfs_file.c:260:35: error: &#8216;const struct file_operations&#8217; has no member named &#8216;readdir&#8217;
/tmp/driver/redirfs/rfs_file.c: In function &#8216;rfs_file_set_ops_dir&#8217;:
/tmp/driver/redirfs/rfs_file.c:313:15: error: &#8216;struct file_operations&#8217; has no member named &#8216;readdir&#8217;
make[2]: *** [/tmp/driver/redirfs/rfs_file.o] Error 1
make[1]: *** [_module_/tmp/driver/redirfs] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make: *** [all] Error 2
make -C /lib/modules/`uname -r`/build M=/tmp/driver/redirfs modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  DEPMOD  3.11.0-15-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
make -C /lib/modules/`uname -r`/build M=/tmp/driver/avflt EXTRA_CFLAGS=-I/tmp/driver/redirfs modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  DEPMOD  3.11.0-15-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
FATAL: Module redirfs not found.

RedirFS kernel modules installation failed.

$Stopping cmdagent: The cmdagent stopped successfully!
$Starting cmdagent: The cmdagent started successfully!
$Stopping cmgdaemon: The cmgdaemon stopped successfully!
$Starting cmgdaemon: The cmgdaemon started successfully!

COMODO Antivirus is successfully configured, you can start it from Menu or Desktop.

 Although this says it is successfully configured, it clearly isn't. Can anyone throw any light on this please?

---

### Post by MikeCyber on 2014-02-16
needs again sudo?

What you use comodo for? For Windows?

---

### Post by philromford-q on 2014-02-16
Not Windows, it is for Ubuntu 12.04 LTS

---

### Post by QDR06VV9 on 2014-02-16
For those having trouble with Installing and configuring Comodo AV for Linux
 
Download if you have not already from [here]("http://http://www.comodo.com/home/download/download.php?prod=antivirus-for-linux&track=3646#"). Make sure you have the right distro(Ubuntu or Mint) and the right Arc (32 or 64 Bit)

Run '/opt/COMODO/post_setup.sh'(As Root sudo)
You will get a File system driver not installed.
You will need this [driver]("http://http://www.bondoffamily-net.com/~kinta-chan/techknow/Linux/RedirFS/src/driver.tar")
Now Move that file you downloaded To /opt/COMODO/ as root.
Replacing the old driver!!


And Then run the code below again
```
sudo /opt/COMODO/post_setup.sh
```

Enjoy:)

You will need to run the setup  code after Kernel updates or upgrades(Newer Kernels)

---

### Post by philromford-q on 2014-02-16
Right, thank you I will do that once I have found how to do this as root. Being very new to all this, my ignorance of the command line is profound. I have downloaded the tar file though.

Thanks again

---

### Post by QDR06VV9 on 2014-02-16
> **philromford-q said:**
> Right, thank you I will do that once I have found how to do this as root. Being very new to all this, my ignorance of the command line is profound. I have downloaded the tar file though.

Thanks again
Your Welcome.
To move the file easy way for now do this
```
gksudo nautilus
```
Then navigate to <opt> & <COMODO> Then Copy or Move the downloaded file to that directory.
It will ask you to replace the old file say yes. Close and dont forget to run
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo /opt/COMODO/post_setup.sh[/FONT][/COLOR]
```
Ill stick around for a bit to see how you are doing.

---

### Post by 3rdalbum on 2014-02-16
I'm sure you've already been informed that Ubuntu is totally unaffected by Windows viruses, and that there are no Ubuntu viruses? In other words, you want Comodo Antivirus to check your Windows partition, not your Linux partition.

---

### Post by philromford-q on 2014-02-16
Hi Runrickus,

Very many thanks, that has done the trick. Comodo now says 'All systems active and running.

There is so much to learn!!!

---

### Post by philromford-q on 2014-02-16
Actually, no I didn't know that. This is from the Comodo web site:-

> Comodo Antivirus for Linux (CAVL) offers complete protection against  viruses, worms and Trojan horses for Linux based computers. The software  is easy to configure and use and features real-time, on-access and  on-demand virus scanning, full event logging, schedules scans and more.  The application has an email filtering system that blocks spam,  email-borne viruses and other unwanted mail from reaching user's  in-boxes. Users can start virus scans immediately by clicking the 'Scan  Now' link on the summary screen.

Is this not true then? I no longer have Windows on this machine, it is wholly Ubuntu now.

---

### Post by philromford-q on 2014-02-16
A subject of interest is key stroke logging. I do online banking on my Windows 7 machine, and have Trusteer Rapport installed that blocks key stroke logging and any other attempts to intrude. 

Question: does Ubuntu reject intrusion attempts of this kind, if not is there any software that does block in the same way as Trusteer? Trusteer don't offer a Linux version.

---

### Post by QDR06VV9 on 2014-02-16
Good Job!!:popcorn:

---

### Post by philromford-q on 2014-02-17
Thanks again!

---

### Post by MikeCyber on 2014-02-17
I don't think it's useful to use a Linux antivirus. I use Linux since 1998 without one single problem. I have used however a outgoing firewall for a while just like most OSX86 do.
[http://sourceforge.net/projects/leopardflower/](http://sourceforge.net/projects/leopardflower/)
So you can control all outgoing traffic including keys etc.

---

### Post by 3rdalbum on 2014-02-17
> **philromford-q said:**
> Actually, no I didn't know that. This is from the Comodo web site:-



Is this not true then? I no longer have Windows on this machine, it is wholly Ubuntu now.

There are no viruses, worms or Trojans that run on Ubuntu 12.04 or later. I'm pretty sure no antivirus vendor bothered to update their software to detect the last Trojan in 2011, it only affected a handful of people.

You don't need antivirus on Linux. If you run a server you would benefit from a rootkit hunter and a firewall, but for a normal desktop computer you don't need anything. No viruses means no keylogging, unless somebody got physical access to your computer.

---

### Post by QDR06VV9 on 2014-02-17
Initial Infection Method Still Primitive

The Linux platform does not have the same type of commercial exploit packs for use in mass drive-by-download campaigns (the most popular infection method for the Windows OS). Moreover, Hand of Thief&#8217;s developer did not offer a recommended infection method, other than sending the Trojan via email and using some social engineering to have the user launch the malware on their machine.
More info [Here]("http://www.darkreading.com/vulnerability/hand-of-thief-linux-trojan-not-ready-for/240160760")
And More [Here]("https://blog.avast.com/2013/08/27/linux-trojan-hand-of-thief-ungloved/")

---

### Post by 3rdalbum on 2014-02-17
> **runrickus said:**
> Initial Infection Method Still Primitive

The Linux platform does not have the same type of commercial exploit packs for use in mass drive-by-download campaigns (the most popular infection method for the Windows OS). Moreover, Hand of Thief’s developer did not offer a recommended infection method, other than sending the Trojan via email and using some social engineering to have the user launch the malware on their machine.
More info [Here]("http://www.darkreading.com/vulnerability/hand-of-thief-linux-trojan-not-ready-for/240160760")
And More [Here]("https://blog.avast.com/2013/08/27/linux-trojan-hand-of-thief-ungloved/")

Okay, I stand corrected. I'd forgotten about that one. Still, you'd have to get up pretty early in the morning to be fooled into downloading and running that trojan, and as far as anyone knows nobody has been fooled.

The Windows version gets onto your system through browser security flaws and OS security flaws. The Linux version must be downloaded, chmod +x'ed, and then run.

---

### Post by QDR06VV9 on 2014-02-17
> **3rdalbum said:**
> Okay, I stand corrected. I'd forgotten about that one. Still,**_ you'd have to get up pretty early in the morning to be fooled into downloading and running that trojan, and as far as anyone knows nobody has been fooled._**

The Windows version gets onto your system through browser security flaws and OS security flaws. The Linux version must be downloaded, chmod +x'ed, and then run.
Exactly.
COMODO has blocked a couple of browser malware incidents in real time though!+1

---

