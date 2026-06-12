---
title: "Can't install JBuilder 7."
date: 2007-04-03
forum: General Help
---

### Post by cawebster on 2007-04-03
I'm new to Linux and Ubuntu.  I know basic commands in terminal that carry over from my limited experience with Unix.  I have no experience with installing applications in Linux.  I have installed the latest JRE from Synaptic Package Manager.  I also install RPM using Synaptic in the vain hope that since it was packaged for Red Hat that this would make a difference.

I'm having trouble installing JBuilder 7 Standard Edition.  The documentation that came with the CD lists "Read Hat Linux 6.2 or 7.2 with GNOME or KDE desktop managers" as a system requirement.  Following the directions for installation yields the following results:

curtis@curtis-desktop:~$ cd /media/cdrom0
curtis@curtis-desktop:/media/cdrom0$ ls
autorun.inf    install_linux        install_solaris.lax  Linux   setup
index.html     install_linux.lax    install_windows.exe  MacOSX  Solaris
InstallerData  install_mac_osx.app  install_windows.lax  offer   Windows
install.jar    install_solaris      lax.jar              pdf
curtis@curtis-desktop:/media/cdrom0$ install_linux
bash: install_linux: command not found
curtis@curtis-desktop:/media/cdrom0$ 

(Sorry, I don't know how to put the terminal data in a box on the post.)

Can JBuilder be installed on Ubuntu?  If so, how should I proceed?

---

### Post by amohanty on 2007-04-03
> curtis@curtis-desktop:/media/cdrom0$ install_linux

A few points about running commands from the command line. For this to work install_linux would have to be in a folder that is in the PATH environment variable. To see what folders are in a terminal type:

echo $PATH

Now there are lots of programs that you may download, create, compile. You do not want to add all possible locations to te environment PATH variable. So you just run them from where they are.

So if you have an app called foo in your home folder you can run that from any by typing:

/home/username/foo

OR

~/foo

or you cand change to your home folder and then type 

./foo

So in this case you need to type: ./install_linux

HTH
AM

---

### Post by cawebster on 2007-04-03
I tried running the program as suggested.  I got permission denied messages even using sudo.

curtis@curtis-desktop:/media/cdrom0$ sudo ./install_linux
Password:
sudo: unable to execute ./install_linux: Permission denied
curtis@curtis-desktop:/media/cdrom0$ sudo /media/cdrom0/install_linux
sudo: unable to execute /media/cdrom0/install_linux: Permission denied
curtis@curtis-desktop:/media/cdrom0$ 

further suggestions appreciated.

---

### Post by amohanty on 2007-04-03
Can you post the output of **ls -l** in that directory?

AM

---

### Post by cawebster on 2007-04-03
curtis@curtis-desktop:/media/cdrom0$ ls -l
total 1063
-rw-r--r-- 1    99    99     96 2002-05-20 10:00 autorun.inf
-rw-r--r-- 1    99    99    609 2002-05-20 10:00 index.html
drwxr-xr-x 2    99    99   2048 2002-05-20 10:00 InstallerData
-rw-r--r-- 1    99    99 594992 2002-05-20 10:00 install.jar
-rwxr-xr-x 1    99    99  35903 2002-05-20 10:00 install_linux
-rw-r--r-- 1    99    99   3541 2002-05-20 10:00 install_linux.lax
drwxr-xr-x 3    99    99   2048 2002-05-20 10:00 install_mac_osx.app
-rwxr-xr-x 1    99    99  35903 2002-05-20 10:00 install_solaris
-rw-r--r-- 1    99    99   3543 2002-05-20 10:00 install_solaris.lax
-rw-r--r-- 1    99    99 374784 2002-05-20 10:00 install_windows.exe
-rw-r--r-- 1    99    99   3683 2002-05-20 10:00 install_windows.lax
-rw-r--r-- 1    99    99   7196 2002-05-20 10:00 lax.jar
drwxr-xr-x 3    99    99   4096 2002-05-20 10:00 Linux
drwxr-xr-x 3    99    99   2048 2002-05-20 10:00 MacOSX
drwxr-xr-x 3    99    99   2048 2002-05-20 10:00 offer
drwxr-xr-x 2    99    99   2048 2002-05-20 10:00 pdf
drwxr-xr-x 3    99    99   2048 2002-05-20 10:00 setup
drwxr-xr-x 3 60001 60001   4096 2002-05-20 10:00 Solaris
drwxr-xr-x 3    99    99   4096 2002-05-20 10:00 Windows

---

### Post by amohanty on 2007-04-03
Try copying over the files to a local folder and running it from there. Apparently the files on the cd are owned by uid 90 which on a default install is not you.

AM

---

### Post by cawebster on 2007-04-03
got this message on install, after copying and changing rights on all files.  I looked for the shared libraries in synaptic, but no luck.  I'm not sure where the program is looking for the libstdc++ file.


curtis@curtis-desktop:~/JBuilder$ sudo ./install_linux
/home/curtis/JBuilder/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

Thanx

---

### Post by Maestro23 on 2007-04-03
> **cawebster said:**
> got this message on install, after copying and changing rights on all files.  I looked for the shared libraries in synaptic, but no luck.  I'm not sure where the program is looking for the libstdc++ file.


curtis@curtis-desktop:~/JBuilder$ sudo ./install_linux
/home/curtis/JBuilder/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

Thanx

Do you have libstdc++6 installed?  libstdc++6-dev as well.

---

### Post by cawebster on 2007-04-03
No.  Where can I get it?  Is there a debian package?

---

### Post by Maestro23 on 2007-04-03
> **cawebster said:**
> No.  Where can I get it?  Is there a debian package?

Repositories.  Use Synaptic, search "libstdc++6"

If you don't see it, you might need to enable extra Respositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by cawebster on 2007-04-03
Never mind.  Found it.  gonna take a few minutes to download dependencies.

---

### Post by cawebster on 2007-04-03
That did not resolve issue.  The same error occurred.

curtis@curtis-desktop:~/Desktop$ sudo dpkg -i --force configure-any libstdc++6_4.1.1-21_i386.deb
(Reading database ... 133314 files and directories currently installed.)
Preparing to replace libstdc++6 4.1.1-21 (using libstdc++6_4.1.1-21_i386.deb) ...
Unpacking replacement libstdc++6 ...
Setting up libstdc++6 (4.1.1-21) ...

curtis@curtis-desktop:~/Desktop$ cd ..
curtis@curtis-desktop:~$ cd JBuilder
curtis@curtis-desktop:~/JBuilder$ ./install_linux
/home/curtis/JBuilder/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
curtis@curtis-desktop:~/JBuilder$

---

### Post by amohanty on 2007-04-04
> curtis@curtis-desktop:~/Desktop$ sudo dpkg -i --force configure-any libstdc++6_4.1.1-21_i386.deb
(Reading database ... 133314 files and directories currently installed.)
Preparing to replace libstdc++6 4.1.1-21 (using libstdc++6_4.1.1-21_i386.deb) ...
Unpacking replacement libstdc++6 ...
Setting up libstdc++6 (4.1.1-21) ...


Please dont do that. That's dangerous especially --force. Please follow Maestro's instrcutions and use System->Administration->Synaptic. Then click on Search to look for the relevant package and install it. Its safer and you dont have to deal with dependencies and stuff.

If you cannot find it lookup enable universe repositories either in the forums or wiki.ubuntu.com

HTH
AM

---

### Post by cawebster on 2007-04-04
Damage may already be done.  Synaptic now wants to uninstall almost everything when I mark any program for action (install or remove).  Any advice?  Will I need to basically start over with Ubuntu?

---

### Post by cawebster on 2007-04-04
Made clean install of Ubuntu.  I also installed libstdc6 and libstdc6-dev using synaptic.
Copied JBuilder install CD to directory "JBuilder" in my home directory.  Changed permissions on all files as shown below.  Still getting same error when I try to install JBuilder.


curtis@curtis-desktop:~/JBuilder$ ls -l
total 1096
-rwxrwxrwx 1 curtis curtis     96 2002-05-20 10:00 autorun.inf
-rwxrwxrwx 1 curtis curtis    609 2002-05-20 10:00 index.html
drwxrwxrwx 2 curtis curtis   4096 2002-05-20 10:00 InstallerData
-rwxrwxrwx 1 curtis curtis 594992 2002-05-20 10:00 install.jar
-rwxrwxrwx 1 curtis curtis  35903 2002-05-20 10:00 install_linux
-rwxrwxrwx 1 curtis curtis   3541 2002-05-20 10:00 install_linux.lax
drwxrwxrwx 3 curtis curtis   4096 2002-05-20 10:00 install_mac_osx.app
-rwxrwxrwx 1 curtis curtis  35903 2002-05-20 10:00 install_solaris
-rwxrwxrwx 1 curtis curtis   3543 2002-05-20 10:00 install_solaris.lax
-rwxrwxrwx 1 curtis curtis 374784 2002-05-20 10:00 install_windows.exe
-rwxrwxrwx 1 curtis curtis   3683 2002-05-20 10:00 install_windows.lax
-rwxrwxrwx 1 curtis curtis   7196 2002-05-20 10:00 lax.jar
drwxrwxrwx 3 curtis curtis   4096 2002-05-20 10:00 Linux
drwxrwxrwx 3 curtis curtis   4096 2002-05-20 10:00 MacOSX
drwxrwxrwx 3 curtis curtis   4096 2002-05-20 10:00 offer
drwxrwxrwx 2 curtis curtis   4096 2002-05-20 10:00 pdf
drwxrwxrwx 3 curtis curtis   4096 2002-05-20 10:00 setup
drwxrwxrwx 3 curtis curtis   4096 2002-05-20 10:00 Solaris
drwxrwxrwx 3 curtis curtis   4096 2002-05-20 10:00 Windows
curtis@curtis-desktop:~/JBuilder$ ./install_linux
/home/curtis/JBuilder/Linux/resource/jre/bin/i386/native_threads/java: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory


Thanks for any help.

---

### Post by amohanty on 2007-04-04
Try this:

sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++-libc6.1-1.so.2

and then try it again.

HTH
AM

---

### Post by cawebster on 2007-04-04
I hope this means we're making progress.  Now I'm getting segmentation fault.

curtis@curtis-desktop:~/JBuilder$ sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++-libc6.1-1.so.2
Password:
curtis@curtis-desktop:~/JBuilder$ ./install_linux
Segmentation fault (core dumped)

---

### Post by amohanty on 2007-04-05
That means theres a hard dependency on the version of the library. Delete the link you just created and see if this works:

[http://qc.borland.com/wc/qcmain.aspx?d=39392](http://qc.borland.com/wc/qcmain.aspx?d=39392)

AM

---

### Post by cawebster on 2007-04-05
How do I delete the link?

---

### Post by cawebster on 2007-04-05
got the link deleted.

---

### Post by cawebster on 2007-04-05
> **amohanty said:**
> That means theres a hard dependency on the version of the library. Delete the link you just created and see if this works:

[http://qc.borland.com/wc/qcmain.aspx?d=39392](http://qc.borland.com/wc/qcmain.aspx?d=39392)

AM

I deleted the link and then went to the above url.  Those directions must be for a different version.  My CD doesn't contain any of the file paths listed in the work around.  Is there a find feature in Ubuntu so that I can find a specific filename in a directory?  I am thinking that the work around might still work, but the file I need to change is in a different directory than the posting on borland.com.

---

### Post by amohanty on 2007-04-06
find -iname filename

will search in the current and all subfolders. -iname means case insensitive by name search

HTH
AM

---

### Post by cawebster on 2007-04-06
No file named install.bin on the CD.  I'm editing the install_linux.lax file.  There is a path set that launches Java VM from the CD.  I thought that it might help if I redirected this line to the VM on the my machine.  I've install java using synaptic, but I don't know where to direct the path.  I tried /usr/bin/java but that didn't work.

curtis@curtis-desktop:~/JBuilder$ ./install_linux
No Java virtual machine could be found from your PATH
environment variable.  You must install a VM prior to
running this program.

If I'm barking up the wrong tree please let me know.  How do check to see if I have a JVM working on my machine and how do I direct the program to look for it in the correct location?

---

### Post by amohanty on 2007-04-07
in a terminal

**type java**

yes the command is called **type**

AM

---

### Post by cawebster on 2007-04-07
That seemed to work.  I installed j2sdk and changed the path to the VM in the install_linux.lax file.  Now the JBuilder install gui appears on the screen with install options.  When I click on an option, nothing happens.  Any ideas on this one?

---

### Post by amohanty on 2007-04-08
Can you post the link to the download?

let me try it on this machine and I will post any results.
AM

PS: is there anything that eclipse cant do that jbuilder can? other than not bloating, but from what I know jbuilder is no light weight either :)

---

### Post by cawebster on 2007-04-08
I don't have a download.  The borland site has downloads, but the earliest version they have is JBuilder X that I could find.  I actually bought JBuilder 7 in 2002 and wanted to get it installed on my new Linux installation.  I will try to zip the entire CD and see if it is small enough to post.

---

### Post by amohanty on 2007-04-08
actually if you bought it, that would be illegal.. :) just post the install_.. file.

AM

---

### Post by cawebster on 2007-04-09
I finally got it up and running.  I will post what I did later after I've gotten a little sleep.  Thank you for your help.  There are probably some more efficient ways to accomplish this installation and I would be interested to see any responses to the steps that I took.

---

### Post by cawebster on 2007-04-10
I went through all of the suggestions that I received in this forum to finally get the install_linux program to run.  It took several days, but thanks to the help of amohanty and maestro23 (Thank you both) I finally got install_linux to run from the command line.  After all the tweaking and even reinstalling Ubuntu (warning: carefule with using --force option when installing debian packages.) that program launched an html gui that gave me the option of installing JBuilder.  Clicking on the button yielded no result.  I viewed the html and found that the href was for the linux subdirectory and the se_install.bin program.  I ran into many similar errors to those experienced with the install_linux shell.  The following post from amohanty helped me resolve this problem.

> **amohanty said:**
> That means theres a hard dependency on the version of the library. Delete the link you just created and see if this works:

[http://qc.borland.com/wc/qcmain.aspx?d=39392](http://qc.borland.com/wc/qcmain.aspx?d=39392)


These directions gave the following workaround:
 go to the directory where you extracted the downloaded file and:
$ cd jb2006_linux/Disk1/InstData/Linux/VM/
$ cp install.bin install.bin.orig
$ cat install.bin.orig | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > install.bin


$ cp se_install.bin se_install.bin.orig
$ cat se_install.bin.orig | sed "s/export LD_ASSUME_KERNEL/#xport LD_ASSUME_KERNEL/" > se_install.bin

This got JBuilder to install.  Then I got another error when I tried to launch JBuilder.  Long story short, JBuilder installed JRE1.3.1 and I already was running JRE1.4.  JBuilder kept searching for files and libraries in JRE1.3.1 that were not their.  To work around this I copied the JRE 1.4 files and subdirectories into the JRE1.3.1 and launched the program again.  JRE 1.4 had all the connections that JBuilder was looking for and now runs without a hitch.  Copying the JRE 1.4 files to the JRE 1.3.1 was probably not the best solution, but it worked.

---

### Post by amohanty on 2007-04-11
good for you :)

---

