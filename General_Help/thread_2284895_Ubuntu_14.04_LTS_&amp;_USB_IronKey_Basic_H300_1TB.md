---
title: "Ubuntu 14.04 LTS &amp; USB IronKey Basic H300 1TB"
date: 2015-07-02
forum: General Help
---

### Post by jay97 on 2015-07-02
I cannot gain access to my IronKey USB External HDD using Ubuntu 14.04 LTS. I know my IK works because I have no problems accessing the external drive via my Windows 8 partition. I am new to Ubuntu but familiar with computer programming in general. I reinstalled Ubuntu today to insure I had not inadvertently corrupted dependencies given the variety of solutions I have attempted already. I ran the Software Updater, so everything is up to date on my system. When I plug in my IK it automatically mounts. The primary IronKey.exe file is meant to be run in the Windows OS, while the 'linux' subfolder contain a separate IronKey.exe file meant to run on Linux. I even copied the 99-ironkey.rules into the appropriate directory to ensure I had permission to use the drive. In order to run a .exe file, I Installed Wine. I had an issue with one of the fonts packages, but the Forums solved this problem for me:
sudo dpkg -P ttf-mscorefonts-installer  
sudo apt-get install ttf-mscorefonts-installer 

I have also read countless Forum Threads involving the now debunked (apparently) ia32-libs package. According the the Iron Key Technical Support, I need to be able to run a 32bit executable in order for the Iron Key Unlocker to Launch. I followed these steps according to the Forums:

[LIST]
[*]To run a 32-bit executable file on a 64-bit multi-architecture Ubuntu system, you have to add the i386 architecture and install the three library packages libc6:i386, libncurses5:i386, and libstdc++6:i386 
[*]sudo dpkg --add-architecture i386 
[*]sudo apt-get update 
[*]sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 
[/LIST]

After these steps failed me, I attempted these steps:

[LIST=1]
[*] Install Synaptic from terminal window ( Ctrl+Alt+T )  if you have not done so already. 
[*] Type or copy this in the terminal minus the quotes " sudo apt-get install synaptic " 
[*] Launch synaptic and goto &#8220;Settings then Repositories&#8221;
 
[*] Click &#8220;other software  then add&#8221;
 
[*] Insert this line in the box   "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring main restricted universe multiverse"
 
[*] click ok and close synaptic
 
[*] Type or copy minus the quotes  in the terminal &#8220;sudo apt-get update&#8221; Wait until the listing stops and you are at the prompt.
 
[*] Then type or copy minus the quotes &#8220;sudo apt-get install ia32-libs&#8221;  Wait  until install is finished then reboot your computer. 
[*]Run viewer per the readme text provided.  
[/LIST]

It would appear the ia32-libs packages no longer exists. At this point, I'm not even sure that this is the actual cause of the problem at all.

So These are the two errors that I receive while attempting to open the IronKey Unlocker: 

1. Open the primary IronKey.exe file meant to be opened in the Windows OS: "Fatal Error: Error determining if device is set up". Although, the Unlocker window does appear making me think it "almost" works.
My first response to this error was to initialize the device through Windows 8, which was successful. However, after setting up the device I continue to receive this fatal error.

2. Open the secondary IronKey.exe file in the linux subfolder: 
     "There was an error creating the child process for this terminal" 
     "Failed to execute child process "F:\linux\ironkey.exe" (No such file or directory)"

I am at a total loss of what to do next. I have searched the Forums for all available solutions and I cannot find one for my specific problem. Please help.

---

### Post by Vladlenin5000 on 2015-07-02
Hi and welcome.

Sorry, I've bad news for you: A drive using a proprietary encryption software/format with tools for Windows only, most likely won't work in Linux. The windows software may or may not run with a compatibility layer but even in the best scenario it won't be able to access the drive.
However, the IronKey Basic H300 is being market as supported by *Linux 2.6+ or higher*...

A question and a suggestion:
- How does it appear in the file manager?  
- Perhaps you should contact support and ask about software (if required) and instructions for Ubuntu.

---

### Post by jay97 on 2015-07-02
Thank you for such a quick response. I'd rather confirm incompatibility than blundering around hoping to find a nonexistent solution. I have contacted IronKey support twice about my problems and they have only pointed out the obvious so far. First response:

The H300 can be used under a Linux OS (x86, kernel 2.6 or higher). Please
check the version you have installed.

If you confirm the version is compatible, then we suggest resetting the H300
on the W8 machine (enable Reset via the H300 Control Panel), and then try
setting up on the Linux machine.

Link to the H300 basic user Guide:
[http://support2.imation.com/downloads/imn/IMS/H300/IronKey_Basic_H300_UG.pdf](http://support2.imation.com/downloads/imn/IMS/H300/IronKey_Basic_H300_UG.pdf)

My Response: 

jay@MyPC:~$ uname -a
Linux MyPC 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC
2015 x86_64 x86_64 x86_64 GNU/Linux

Second Response:

You have a 64 bit version of Linux installed. Please make sure you also have
the following:

- 32 bit libraries installed.
- You may need root privileges to launch ironkey.exe from the Linux folder.
- Make sure you have permissions to mount external SCSI and USB devices.

These are on pages 18-19 of the User Guide. The last two you may have
already looked after (I assume you saw
[http://support.ironkey.com/article/AA-02640](http://support.ironkey.com/article/AA-02640)), but the 32 bit libraries may
not have been added yet.

I wanted to try  Ubuntu Forums before returning to IronKey Technical Support for help. I would be glad to provide any additional information that may be useful.

---

### Post by jay97 on 2015-07-06
Problem Solved! These errors occurred due to the fact that I was trying to run the executable through Wine. I had made the erroneous assumption that the IronKey.exe file in the linux subfolder was a Windows Executable file, which cannot be executed from the terminal. I found this information useful from another thread:

On Linux you give the file executable permissions. It isn't the extension that determines whether or not it can be executed (as on windows.)

Assuming you have a valid file that can be executed in Linux, (not a windows/dos file) do this:

cd abc
chmod a+x info.exe
./info.exe

Note that you need the leading ./ for the shell to find the file in the current directory!

This really belongs on superuser though.


By replacing info.exe with the IronKey.exe file, I was prompted to provide my password. Once entered, the encrypted potion of the drive automatically mounted as a USB drive. I cannot use the Unlocker Program as on Windows, but the included documentation provides terminal commands to do unlock, lock, change password, etc. There is no GUI for IronKey on linux, but at least I can access the drive and all my encrypted data. I hope this helps anyone else with the same problem.

---

