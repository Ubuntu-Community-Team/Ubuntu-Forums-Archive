---
title: "Help nomachine NXserver fatal error~~~"
date: 2008-03-22
forum: General Help
---

### Post by lzlgboy on 2008-03-22
Hi everyone:
      I have been enjoy ubuntu for a moment. I have it installed on my Desktop computer and I use nomachine NXclient to connect to it, so I can enjoy it on my laptop too.

      Things were fine before this problem occured.

      I have three Users on my Ubuntu "root" "kenian" and "biolab".

     I have successfully setup Nxserver following the thread that post in the forum. (Thanks a lot guys).

     And I connect to it with User "biolab", everything is fine , I successfully connected to my Ubuntu .

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=63479&stc=1&d=1206238969[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=63480&stc=1&d=1206238969[/IMG]
    But when I come to the User "kenian", problem happened:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=63481&stc=1&d=1206238969[/IMG]

 I search the forum and try a lot to figure out what is happend ,but I was failed. So I post this and hope some one will give me a hand....

The following is the error detail that comes from the Nxclient:
======================================================
NX> 203 NXSSH running with pid: 5088
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 202.116.90.254 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.1.0-2 - LFE
NX> 105 Hello NXCLIENT - Version 3.0.0
NX> 134 Accepted protocol: 3.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: kenian
NX> 102 Password: ********
NX> 103 Welcome to: KNserver user: kenian
NX> 105 Listsession --user="kenian" --status="suspended\054running" --geometry="1280x800x32+render+fullscreen" --type="unix-gnome" 
NX> 127 Available sessions: 

Display Type             Session ID                       Options  Depth Screen         Status      Session Name
------- ---------------- -------------------------------- -------- ----- -------------- ----------- ------------------------------

NX> 148 Server capacity: not reached for user: kenian
NX> 105 Start session with: --link="lan" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="ubuntu" --type="unix-gnome" --geometry="1280x770" --fullscreen="1" --client="winnt" --keyboard="pc102\057us" --screeninfo="1280x800x32+render+fullscreen" 
NX> 595 ERROR: A fatal error occurred in NX Server.
NX> 595 ERROR: The exception id is: A934B586. To get detailed information about
NX> 595 ERROR: the error search for the string A934B586 in the system log
NX> 595 ERROR: file (usually '/var/log/messages').
NX> 500 ERROR: Last operation failed.
NX> 280 Exiting on signal: 15

---

### Post by daflame on 2008-03-25
Did you follow the error advise and check /var/log/messages for that error number?  I suspect you have run into the classic NoMachine 2 user limitation.  You can only use two users at any given time in NX Server Free Edition.  FreeNX does not have this limitation.

If you still can't get it to work you could always install FreeNX instead.  It has all the same features now without the limitations:
[FreeNX on Ubuntu Gutsy]("http://ubuntuforums.org/showthread.php?t=620057")

---

