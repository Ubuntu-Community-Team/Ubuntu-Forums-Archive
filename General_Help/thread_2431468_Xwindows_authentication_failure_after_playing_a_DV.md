---
title: "Xwindows authentication failure after playing a DVD"
date: 2019-11-16
forum: General Help
---

### Post by donb21 on 2019-11-16
I have Ubuntu-Mate, 18.04, which works quite well.  I copied a  family DVD onto it tried to play it in MythTV; screen went black,  "Please wait...." was displayed, and it stopped there. I logged in  remotely and tried to kill x (sudo service lightdm stop).  The TV screen  went black and displayed "Started bpfilter" at the top left corner. 

I'm not sure I recall all the steps, but I tried "sudo startx"  manually.  It partially started and gave this message: 

"You must be a member of the "mythtv" group before starting any mythtv  applications.  Would you like to automatically be added to the group?   (Note: sudo access required)" 

I answered "No" and it didn't work, so I pressed the reset button. After  reboot, x-windows tries to start and displays a password dialogue box.   If I enter the correct password, it goes black for a few seconds, then  returns back to the same display and dialogue.  If I enter an incorrect  password, it gives an an "Invalid password..." message and returns to  the same dialogue. 

Not sure where to go from here, any suggestions? 

PS - Seeing these errors in the logs:

From /var/logs: 

lightdm.log has this at the end: 
... 
[+366.97s] DEBUG: Continue authentication 
[+368.91s] DEBUG: Session pid=3387: Authentication complete with return  value 7: Authentication failure 
[+368.91s] DEBUG: Authenticate result for user don: Authentication failure 
[+368.91s] DEBUG: Greeter start authentication for don 
[+368.91s] DEBUG: Session pid=3387: Sending SIGTERM 
[+368.91s] DEBUG: Session pid=3493: Started with service 'lightdm',  username 'don' 
[+368.91s] DEBUG: Session pid=3387: Exited with return value 1 
[+368.91s] DEBUG: Seat seat0: Session stopped 
[+368.92s] DEBUG: Session pid=3493: Got 1 message(s) from PAM 
[+368.92s] DEBUG: Prompt greeter with 1 message(s) 

auth.log has this at the end: 
... 
Nov 16 14:21:30 johnny systemd-logind[956]: New session c7 of user lightdm. 
Nov 16 14:23:34 johnny lightdm: pam_unix(lightdm:auth): authentication  failure; logname= uid=0 euid=0 tty=:0 ruser= rhost= user=don 
Nov 16 14:23:34 johnny lightdm: pam_winbind(lightdm:auth): getting  password (0x00000388) 
Nov 16 14:23:34 johnny lightdm: pam_winbind(lightdm:auth): pam_get_item  returned a password 
Nov 16 14:23:34 johnny lightdm: pam_winbind(lightdm:auth): request  wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_USER_UNKNOWN  (10), NTSTATUS: NT_STATUS_NO_SUCH_USER, Error message was: The sp 
Nov 16 14:23:36 johnny lightdm: PAM unable to dlopen(pam_kwallet.so):  /lib/security/pam_kwallet.so: cannot open shared object file: No such  file or directory 
Nov 16 14:23:36 johnny lightdm: PAM adding faulty module: pam_kwallet.so 
Nov 16 14:23:36 johnny lightdm: PAM unable to dlopen(pam_kwallet5.so):  /lib/security/pam_kwallet5.so: cannot open shared object file: No such  file or directory 
Nov 16 14:23:36 johnny lightdm: PAM adding faulty module: pam_kwallet5.so 
Nov 16 14:23:36 johnny lightdm: pam_succeed_if(lightdm:auth):  requirement "user ingroup nopasswdlogin" not met by user "don" 
Nov 16 14:25:24 johnny sudo:      don : TTY=pts/0 ; PWD=/home/don ;  USER=root ; COMMAND=/usr/bin/mc 
Nov 16 14:25:24 johnny sudo: pam_unix(sudo:session): session opened for  user root by don(uid=0)

---

### Post by TheFu on 2019-11-18
What about the X log file in /var/log/ ?

I don't know anything about mythtv.
DVDs with DRM need extra libraries installed to play or even copy.  Cannot just copy the .vob files.  vobcopy or something like that must be used.

Best to start from the first error in any log file and fix that, then move onto the next, then the next, then the next.

X has a ~/.Xauthority file.  It should recreate with new credentials, provided the file exists and is empty.

And being fully patched is the first thing I'd try.
```
sudo apt update && sudo apt upgrade
```
If there are errors in that process, fix those.

---

