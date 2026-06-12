---
title: "Was my computer hacked?"
date: 2013-11-12
forum: General Help
---

### Post by kocikocev on 2013-11-12
Hey I try to see if my roommate accessed my Ubuntu system  last night. I went to bed before two and I left my computer in the  living room, but i cant remember if I did shut it down. I tried to check  the log files and this is what I see. Can you help me make sense of it?


  So with the 'last' command gives me the following: 


  me       pts/0        :0                 Tue Nov 12 08:55 - 09:20  (00:24)
reboot   system boot  3.8.0-33-generic Tue Nov 12 03:01 - 10:57  (07:55)
me       pts/0        :0                 Tue Nov 12 01:14 - crash  (01:47)    



  and I have the auth.log file from 03:01 but I cant make sense of it. I  want to see if there is a log that says that in 3 there was a  successful login in the system and he had access to the desktop where he  accessed a file, which I opened the morning after and I lost the Last  Accessed entry in the file log.



  By the way this is the auth.log from that time I was surely asleep:


  Nov 12 03:01:35 user lightdm: pam_unix(lightdm:session): session  opened for user lightdm by (uid=0) Nov 12 03:01:35 user lightdm: pam_ck_connector(lightdm:session): nox11  mode, ignoring PAM_TTY :0 

Nov 12 03:01:49 user lightdm: pam_succeed_if(lightdm:auth): requirement  "user ingroup nopasswdlogin" not met by user "my user name was here" 

Nov 12 03:01:51 user dbus[980]: [system] Rejected send message, 2  matched rules; type="method_call", sender=":1.28" (uid=104 pid=1634  comm="/usr/lib/indicator-datetime/indicator-datetime-ser")  interface="org.freedesktop.DBus.Properties" member="GetAll" error  name="(unset)" requested_reply="0" destination=":1.18" (uid=0 pid=1248  comm="/usr/sbin/console-kit-daemon --no-daemon ") 

Nov 12 03:01:53 user dbus[980]: [system] Rejected send message, 2  matched rules; type="method_call", sender=":1.37" (uid=104 pid=1745  comm="/usr/lib/indicator-datetime/indicator-datetime-ser")  interface="org.freedesktop.DBus.Properties" member="GetAll" error  name="(unset)" requested_reply="0" destination=":1.18" (uid=0 pid=1248  comm="/usr/sbin/console-kit-daemon --no-daemon ") Nov 12 03:02:03 user su[1974]: Successful su for lightdm by root 

Nov 12 03:02:03 user su[1974]: + ??? root:lightdm Nov 12 03:02:03 user su[1974]: pam_unix(su:session): session opened for  user lightdm by (uid=0) 

Nov 12 03:02:03 user su[1974]: pam_unix(su:session): session closed for  user lightdm

 Nov 12 03:02:03 user su[1984]: Successful su for lightdm by root Nov 12 03:02:03 user su[1984]: + ??? root:lightdm 

Nov 12 03:02:03 user su[1984]: pam_unix(su:session): session opened for  user lightdm by (uid=0) 

Nov 12 03:02:03 user su[1984]: pam_unix(su:session): session closed for  user lightdm 

Nov 12 03:02:03 user su[1999]: Successful su for lightdm by root Nov 12 03:02:03 user su[1999]: + ??? root:lightdm 

Nov 12 03:02:03 user su[1999]: pam_unix(su:session): session opened for  user lightdm by (uid=0) 

Nov 12 03:02:03 user su[1999]: pam_unix(su:session): session closed for  user lightdm Nov 12 03:02:03 user su[2027]: Successful su for lightdm by root 

Nov 12 03:02:03 user su[2027]: + ??? root:lightdm 

Nov 12 03:02:03 user su[2027]: pam_unix(su:session): session opened for  user lightdm by (uid=0) Nov 12 03:02:03 user su[2027]: pam_unix(su:session): session closed for  user lightdm

---

### Post by TheFu on 2013-11-12
With physical access to the machine, it is possible to look at all the files on it without altering any of them or leaving any other trace. The fact that it was rebooted is suspicious.

If you don't want anyone using the system, use strong encryption with as much of the HDD encrypted as possible and no not use passwords for system access - use a setup with a smartcard with gpg keys.  Passwords are often the weakest part of any security system, but when physical access is allowed, all bets are off ... [even for some sorts of disk encryption]("http://www.irongeek.com/i.php?page=videos/bsideslasvegas2013/5-1-1-attacking-and-defending-full-disk-encryption-tom-kopchak").

---

