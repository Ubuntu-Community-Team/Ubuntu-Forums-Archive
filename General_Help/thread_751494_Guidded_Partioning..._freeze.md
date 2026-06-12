---
title: "Guidded Partioning... freeze"
date: 2008-04-10
forum: General Help
---

### Post by thedoorguy on 2008-04-10
Am trying to set up ubuntu to run inside windows 98se using Wubi. Running a Celeron D 2.93 GH with 512K ram.

Load starts, get progress bar and box titled " Checking The Installation"
Check gets 20% into step title "Guided Partioning" and error box opens titled "No Root File System" with instruction "Please Correct this from the Partioning Menu"  

The error box reappears evertime it is closed so the computer hangs at this point.

I don't know how to access the "Partioning Menu" or what other steps may be required to finish the installation.  Help Please.

---

### Post by ago on 2008-04-10
press ctrl+alt+f2
and run

sh /custom-installation/finish-command.sh

You should now have c:\ubuntu\installation-logs.zip in windows. Post it here

---

### Post by thedoorguy on 2008-04-10
Thanks for your response ago...
 
I got the message "can't open"  when I entered sh /custom-installation/finish-command.sh at the prompt."

Anything else I can try?

---

### Post by ago on 2008-04-10
sorry my bad

sh /custom-installation/hooks/finish-command.sh

---

### Post by thedoorguy on 2008-04-10
Once again got the "can't open" message for sh /custom-installation/hooks/finish-command.sh  (I  tried running without space after first sh and got message that the file doesn't exit)

there are 4 sh file in the "hooks" folder but finish-command.sh is not one of them.
  casper-premount.sh
  early-command.sh
  failure-command.sh
  success.command.sh

Can I down load that finish-command.sh file from somewhere and the try it or what esle. 

Thanks again!

---

### Post by ago on 2008-04-10
it is failure-command.sh ...

---

### Post by thedoorguy on 2008-04-10
Well ago, I got a bunch of feedback but no file....  below is what I copied from the screen..
---------------
ubuntu@ubuntu:~$ sh /cutom-installation/hooks/failure-command.sh
+ [ -e /host/ubutu ]
+ zip -r /host/unbutu/installation-logs.zip /var/log

zip error: Coulds not create output file (/host/ubuntu/installation-logs.zip)
+ [ -e /isodevice/ubuntu ]
+ msg=The installation failed. Logs have been saved in: c:\ubuntu\installations-logs.zip

Note: that in the verbose mode, the logs may include  the password.

The system will now reboot.
+ [ -x /usr/bin/zenity ]
+ zenity  --error –text The Installation failed Logs have been save in: c:\ubuntu\installation-logs.zip

Note that in verbose mode, the logs may include the password.

The system will now reboot

(zenity;9821): Gtk-warning **: cannot open display:
+ root
reboot: Need to be root
ubuntu@ubuntu:~$
--------------------------
Doesn't help me any ... does it mean anything to you...anything helpful that is.

Thanks,  thedoorguy   aka Richard

---

### Post by ago on 2008-04-11
Hmm you have to run that when you see the error box, use ctrl+alt+f2 to geta shell

ah and use sudo

sudo sh /cutom-installation/hooks/failure-command.sh

---

### Post by thedoorguy on 2008-04-11
Ahhh ago..... the sweet smell of sucess....finally got the file!

Thanks for hanging in there so long with me!

---

### Post by ago on 2008-04-12
please uninstall and reinstall
when you reboot, after you select "ubuntu", press esc and select "verbose mode"

If it fails again, pls post the new logs

---

### Post by ago on 2008-04-12
please attach any log comment to [https://bugs.launchpad.net/wubi/+bug/216161](https://bugs.launchpad.net/wubi/+bug/216161)

---

### Post by thedoorguy on 2008-04-12
ago... thanks for your help!

I don't have the knowledge to extract relevant comments from the several files in the installations-logs.zip and have therefore attached the entire zip file to the lauchpad bug you referenced.

I'll monitor the bug thread and this one for additional info re my problem.

Thanks a million for your help.  Don't know why but I am more anxious than ever to get ubuntu installed.  

thedoorguy

---

