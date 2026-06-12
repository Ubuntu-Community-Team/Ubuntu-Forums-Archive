---
title: "winbind/samba capital names issue repost:"
date: 2012-11-02
forum: General Help
---

### Post by CorrupterTheLost on 2012-11-02
Hello and thanks for considering helping me out; here is the story.

I am an Ubuntu Server 12.10 box running in an Active Directory environment where the PDC (Primary Domain Controller) is a Windows Server 2008 R2 system for roaming profiles etc. I have everything configured exactly as i would like it with one exception.

When a user logs in for the first time the PDC creates a folder named like so on the Ubuntu server's Samba share:
/share/Users/Testuser.V2
the name is capitalized in accordance with the username as it is stored on the PDC and the .V2 is added simply because this is a Windows 7 user profile that was just created on the samba share.

Now i would like Samba to use this folder as that users home directory and share it so i configured smb.conf accordingly with the following values:
```
template homedir = /share/Users/%U.V2
[homes]
browseable = no
read only = no
```
and Samba WOULD recognize this as the path however since the folder is capitalized kicks out this error in the samba log for that machine:
```
[2012/10/31 06:10:33.937635,  0] smbd/service.c:1055(make_connection_snum)
  canonicalize_connect_path failed for service tester, path /share/Users/tester.V2
```
Now, i didn't really think it would work since its not directly connected to samba / winbind or network authentication but since from that statement you can surmise i don't really know what i am doing (lol) i figured i'd give it a shot anyway because i learn by tinkering... thus, decided to change /etc/adduser.conf to include capitalized names and so made the following change:
```
NAME_REGEX="^[a-zA-Z][-a-zA-Z0-9_]*\$"
```
and even went so far as to do a complete system reboot (because i had just finished updating some other unrelated things and figured it couldn't hurt to reboot anyway) to encourage all changes to take effect in a fresh boot environment.

Tested again to get the same path fail error. Now since i knew that wouldn't really work i continued to investigate and found that winbind handles how the names are checked against the PDC and a quick view of getent passwd shows that winbind is grabbing the names and automatically setting their case to all lowercase, here is that output from getent passwd.
```
tester:*:10004:10000:Test:/share/Users/tester.V2:/bin/bash
```
as you can see the template homedir = /share/Users/%U.V2 has taken effect however the names are still downgraded to a lowercase setting. Further investigation lead me back to the samba manual page for more thorough reading to discover i'd overlooked a possible lead on how to get this working which refers to winbind normalize names = no however setting that in smb.conf has no effect on my results. furthermore there is a statement in ([http://www.samba.org/samba/docs/man/...NBINDENUMUSERS](http://www.samba.org/samba/docs/man/...NBINDENUMUSERS)) which refers to the fact winbind normalize names = no has something to do with how nss_info is processed and that i should consult the man page for more information however no further information is given.

Anyone have any clues, leads, tips, hints, pinatas etc? I've been searching, working, crying, pulling hair literally for 7 hours straight and am now exHAUSTED.

PLEASE! PLEASE PLEASE PLEASE!

Sorry for the repost but i fear im not getting the coverage from the other forum.

---

### Post by CorrupterTheLost on 2012-11-03
no one?

---

### Post by CorrupterTheLost on 2012-11-07
well in case anyone was wondering what / if anything / i did to get around this.

I wrote a shell script that was ran on a cron job every 5 minutes to detect a folder that was created with the extension .V2 and then create a sym link to it both using all lowercase and Uppercase without the .V2 so that all 3 folder name variations used by windows and linux would be available in the share.

---

