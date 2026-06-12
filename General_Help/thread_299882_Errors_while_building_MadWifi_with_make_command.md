---
title: "Errors while building MadWifi with make command"
date: 2006-11-14
forum: General Help
---

### Post by Robert.Zapata on 2006-11-14
Hi Team:

I'm following the instructions in the link:

[http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)

The only part that I'm missing from the Requirements is the Kernel parameters *(still trying to figure out how to configure those)*

Requirements for Building the driver. (besides the Kernel sources & headers)

    * gcc -- The same GCC version used to compile the kernel
             o otherwise, "Invalid module format" errors may occur 
    * subversion -- If you choose to get the most recent MadWifi code,
      you'll need to check it out of our Subversion repository.
    * make -- Used to automatically build programs.
    * madwifi -- Download the latest MadWifi driver. 

> 
Building MadWifi 

Now that you have the MadWifi code, it's time to compile it into the actual driver. Thankfully, this is easy.

Assuming that you've met all of the requirements above, and you're inside the MadWifi directory, you can just type:

make

Which will start the build process. Watch for any questions you might be prompted to answer - when it finishes, quickly scan through for any errors. If everything went according to plan, you can proceed to the next step. Make sure you have all the Requirements or the build process may fail. 


Here are the errors (just the beginning)

> 
rob@Thinkpad:~/Downloads/madwifi-0.9.2$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.15-27-686/build SUBDIRS=/home/rob/Downloads/madwifi-0.9.2 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-27-686'
make[3]: Warning: File `/home/rob/Downloads/madwifi-0.9.2/ath/.ah_osdep.o.cmd' has modification time 1.5e+04 s in the future
  HOSTCC  /home/rob/Downloads/madwifi-0.9.2/ath/uudecode
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:26:19: error: stdio.h: No such file or directory
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:27:19: error: errno.h: No such file or directory
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:28:20: error: getopt.h: No such file or directory
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:29:20: error: string.h: No such file or directory
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:30:20: error: stdlib.h: No such file or directory
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:32:23: error: sys/fcntl.h: No such file or directory
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:33:22: error: sys/stat.h: No such file or directory
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c: In function 'uudecode_usage':
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:37: warning: implicit declaration of function 'printf'
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:37: warning: incompatible implicit declaration of built-in function 'printf'
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c: At top level:
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:40: error: syntax error before '*' token
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c:41: warning: function declaration isn't a prototype
/home/rob/Downloads/madwifi-0.9.2/ath/uudecode.c: In function 'get_line_from_fil......................................


Any ideas what I'm missing...??

---

### Post by Robert.Zapata on 2006-11-15
Hello Team:

Atheros card is now working...!!

I wipe out the whole HD and fresh install the latest and greatest (6.10) and IT WORKS....!!!!

Everything worked out of the box...!!! I was afraid of installing 6.10 due to all the bad crap but I guess you need to try first and check for yourself.

Mods: This thread can be closed.

Thank you very much.

---

