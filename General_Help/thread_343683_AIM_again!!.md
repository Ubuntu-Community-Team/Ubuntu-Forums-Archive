---
title: "AIM again!!"
date: 2007-01-21
forum: General Help
---

### Post by DougieFresh4U on 2007-01-21
I must get the real "AIM" running on this machine. Seems there are some depen. problems:    dougie@DougiesToyBox:~$ ls -l /usr/lib/libstdc++-libc6*
ls: /usr/lib/libstdc++-libc6*: No such file or directory
dougie@DougiesToyBox:~$                                                                     Please can any one give me a heads up?:(                                                    Yes I know all about gaim!!

---

### Post by taurus on 2007-01-21
Whichever way you installed aim, remove it.  Make sure it's not on your system by running this command.

```
aim
```
You should get an error message of "command not found."  Now, download this version and unpack it as

```
cd ~
wget -c http://ftp.newaol.com/aimgen/380469/aim-1.5.286.tgz
sudo cp aim-1.5.286.tgz  /
sudo tar xvzf aim-1.5.286.tgz
ldd /usr/bin/aim
```
Post the output of the last command here.

---

### Post by DougieFresh4U on 2007-01-21
dougie@DougiesToyBox:~$ aim
bash: aim: command not found
dougie@DougiesToyBox:~$ aim
bash: aim: command not found
dougie@DougiesToyBox:~$ cd ~
dougie@DougiesToyBox:~$ wget -c [http://ftp.newaol.com/aimgen/380469/aim-1.5.286.tgz](http://ftp.newaol.com/aimgen/380469/aim-1.5.286.tgz)
--21:34:17--  [http://ftp.newaol.com/aimgen/380469/aim-1.5.286.tgz](http://ftp.newaol.com/aimgen/380469/aim-1.5.286.tgz)
           => `aim-1.5.286.tgz'
Resolving ftp.newaol.com... 152.163.212.243
Connecting to ftp.newaol.com|152.163.212.243|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,118,089 (1.1M) [application/x-gzip]

100%[====================================>] 1,118,089    321.14K/s    ETA 00:00

21:34:20 (310.80 KB/s) - `aim-1.5.286.tgz' saved [1118089/1118089]

dougie@DougiesToyBox:~$ sudo cp aim-1.5.286.tgz  /
dougie@DougiesToyBox:~$ sudo tar xvzf aim-1.5.286.tgz
./
./usr/
./usr/bin/
./usr/bin/aim
./usr/lib/
./usr/lib/aim/
./usr/lib/aim/CoolBos.so
./usr/lib/aim/CoolBos.so.1
./usr/lib/aim/CoolBucky.so
./usr/lib/aim/CoolBucky.so.1
./usr/lib/aim/CoolHttp.so
./usr/lib/aim/CoolHttp.so.1
./usr/lib/aim/CoolPeer.so
./usr/lib/aim/CoolPeer.so.1
./usr/lib/aim/CoolSocket.so
./usr/lib/aim/CoolSocket.so.1
./usr/lib/aim/CoolSos.so
./usr/lib/aim/CoolSos.so.1
./usr/lib/aim/extra/
./usr/lib/aim/extra/AIM.desktop
./usr/lib/aim/extra/AOL Instant Messenger (SM).desktop
./usr/lib/aim/extra/aim.png
./usr/lib/aim/extra/aim.xpm
./usr/lib/aim/extra/install.sh
./usr/lib/aim/feed.so
./usr/lib/aim/feed.so.1
./usr/lib/aim/help/
./usr/lib/aim/help/about_buddy_privacy.htm
./usr/lib/aim/help/about_the_buddy_list.htm
./usr/lib/aim/help/adding_a_group_or_buddy.htm
./usr/lib/aim/help/after_regis.htm
./usr/lib/aim/help/allowing_everyone_to_send_you_me.htm
./usr/lib/aim/help/allowing_only_your_buddies_to_se.htm
./usr/lib/aim/help/allowing_specific_users_to_conta.htm
./usr/lib/aim/help/away_message.htm
./usr/lib/aim/help/away_prefs.htm
./usr/lib/aim/help/banner.htm
./usr/lib/aim/help/banner_2.htm
./usr/lib/aim/help/blocking_everyone_from_sending_y.htm
./usr/lib/aim/help/blocking_specific_users.htm
./usr/lib/aim/help/changing_address.htm
./usr/lib/aim/help/changing_password.htm
./usr/lib/aim/help/chat.htm
./usr/lib/aim/help/chat_invite.htm
./usr/lib/aim/help/confirming_account.htm
./usr/lib/aim/help/connection_prefs.htm
./usr/lib/aim/help/defining_away.htm
./usr/lib/aim/help/deleting_a_group.htm
./usr/lib/aim/help/deleting_away.htm
./usr/lib/aim/help/format_messages.htm
./usr/lib/aim/help/fs_about_bl.htm
./usr/lib/aim/help/fs_about_buddy_privacy.htm
./usr/lib/aim/help/fs_about_the_buddy_list.htm
./usr/lib/aim/help/fs_adding_a_group_or_buddy.htm
./usr/lib/aim/help/fs_after_regis.htm
./usr/lib/aim/help/fs_allowing_only_your_buddies.htm
./usr/lib/aim/help/fs_allowing_specific_users_to_con.htm
./usr/lib/aim/help/fs_away_message.htm
./usr/lib/aim/help/fs_away_prefs.htm
./usr/lib/aim/help/fs_blocking_specific_users.htm
./usr/lib/aim/help/fs_changing_address.htm
./usr/lib/aim/help/fs_changing_password.htm
./usr/lib/aim/help/fs_chat.htm
./usr/lib/aim/help/fs_chat_invite.htm
./usr/lib/aim/help/fs_confirming_account.htm
./usr/lib/aim/help/fs_connection_prefs.htm
./usr/lib/aim/help/fs_deleting_a_group.htm
./usr/lib/aim/help/fs_everyone_from_sending.htm
./usr/lib/aim/help/fs_format_messages.htm
./usr/lib/aim/help/fs_general_prefs.htm
./usr/lib/aim/help/fs_im.htm
./usr/lib/aim/help/fs_insert_hyperlink.htm
./usr/lib/aim/help/fs_insert_smileys.htm
./usr/lib/aim/help/fs_installing.htm
./usr/lib/aim/help/fs_privacy_prefs.htm
./usr/lib/aim/help/fs_registering.htm
./usr/lib/aim/help/fs_sending_chat.htm
./usr/lib/aim/help/fs_sending_im.htm
./usr/lib/aim/help/fs_signing_on.htm
./usr/lib/aim/help/fs_sounds.htm
./usr/lib/aim/help/fs_sounds_prefs.htm
./usr/lib/aim/help/fs_turning_an_away.htm
./usr/lib/aim/help/fs_uninstalling.htm
./usr/lib/aim/help/general_prefs.htm
./usr/lib/aim/help/help_contents.htm
./usr/lib/aim/help/im.htm
./usr/lib/aim/help/im_hyperlink.htm
./usr/lib/aim/help/images/
./usr/lib/aim/help/images/add_buddy.gif
./usr/lib/aim/help/images/aimheaderleft.gif
./usr/lib/aim/help/images/away.gif
./usr/lib/aim/help/images/buddyList.gif
./usr/lib/aim/help/images/chat_invite_scr.gif
./usr/lib/aim/help/images/chat_message.gif
./usr/lib/aim/help/images/chat_message2.gif
./usr/lib/aim/help/images/im.gif
./usr/lib/aim/help/images/sign_on.gif
./usr/lib/aim/help/index.htm
./usr/lib/aim/help/insert_hyperlink.htm
./usr/lib/aim/help/insert_smileys.htm
./usr/lib/aim/help/installing.htm
./usr/lib/aim/help/inviting.htm
./usr/lib/aim/help/overview.htm
./usr/lib/aim/help/privacy_prefs.htm
./usr/lib/aim/help/registering.htm
./usr/lib/aim/help/saving_im.htm
./usr/lib/aim/help/sending_chat.htm
./usr/lib/aim/help/sending_im.htm
./usr/lib/aim/help/signing_on.htm
./usr/lib/aim/help/sounds_prefs.htm
./usr/lib/aim/help/turning_an_away.htm
./usr/lib/aim/help/uninstalling.htm
./usr/lib/aim/service.so
./usr/lib/aim/service.so.1
./usr/lib/aim/sounds/
./usr/lib/aim/sounds/cashregister.wav
./usr/lib/aim/sounds/dooropen.wav
./usr/lib/aim/sounds/doorslam.wav
./usr/lib/aim/sounds/imrcv.wav
./usr/lib/aim/sounds/imsend.wav
./usr/lib/aim/sounds/moo.wav
./usr/lib/aim/sounds/newalert.wav
./usr/lib/aim/sounds/newmail.wav
./usr/lib/aim/sounds/phone.wav
./usr/lib/aim/sounds/ring.wav
./usr/lib/aim/sounds/talkbeg.wav
./usr/lib/aim/sounds/talkend.wav
./usr/lib/aim/sounds/talkstop.wav
./usr/lib/aim/source/
./usr/lib/aim/source/extgtktext.c
./usr/lib/aim/source/extgtktext.h
./usr/lib/aim/source/line-arrow.xbm
./usr/lib/aim/source/line-wrap.xbm
./usr/lib/aim/ui.so
./usr/lib/aim/ui.so.1
./usr/lib/libXpcs.so
./usr/lib/libXpcs.so.1
./usr/lib/libXprt.so
./usr/lib/libXprt.so.1
./usr/lib/libXptl.so
./usr/lib/libXptl.so.1
./usr/lib/libextgtk.so
./usr/lib/libextgtk.so.1
dougie@DougiesToyBox:~$ ldd /usr/bin/aim
ldd: /usr/bin/aim: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-21
```
ls -la /usr/bin/aim
```

---

### Post by DougieFresh4U on 2007-01-21
dougie@DougiesToyBox:~$ ls -la /usr/bin/aim
ls: /usr/bin/aim: No such file or directory
dougie@DougiesToyBox:~$ 
WTF, where did it go???

---

### Post by taurus on 2007-01-21
Why don't you log out and back in again.  Then, run that command again.

---

### Post by DougieFresh4U on 2007-01-21
dougie@DougiesToyBox:~$ ls -la /usr/bin/aim
ls: /usr/bin/aim: No such file or directory
dougie@DougiesToyBox:~$ 
Next!!

---

### Post by taurus on 2007-01-21
```
sudo find / -name aim -print
```

---

### Post by DougieFresh4U on 2007-01-21
dougie@DougiesToyBox:~$ ls -la /usr/bin/aim
ls: /usr/bin/aim: No such file or directory
dougie@DougiesToyBox:~$ sudo find / -name aim -print
Password:
/home/dougie/.gaim/logs/aim
/home/dougie/usr/bin/aim
/home/dougie/usr/lib/aim
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-21
```
cd /
ls -la aim-1.5.286.tgz
sudo tar xvzf aim-1.5.286.tgz
cd ~
rm -rf ~/usr
ldd /usr/bin/gaim
```

---

### Post by DougieFresh4U on 2007-01-21
dougie@DougiesToyBox:~$ cd /
dougie@DougiesToyBox:/$ ls -la aim-1.5.286.tgz
-rw-r--r-- 1 root root 1118089 2007-01-21 21:34 aim-1.5.286.tgz
dougie@DougiesToyBox:/$ sudo tar xvzf aim-1.5.286.tgz
./
./usr/
./usr/bin/
./usr/bin/aim
./usr/lib/
./usr/lib/aim/
./usr/lib/aim/CoolBos.so
./usr/lib/aim/CoolBos.so.1
./usr/lib/aim/CoolBucky.so
./usr/lib/aim/CoolBucky.so.1
./usr/lib/aim/CoolHttp.so
./usr/lib/aim/CoolHttp.so.1
./usr/lib/aim/CoolPeer.so
./usr/lib/aim/CoolPeer.so.1
./usr/lib/aim/CoolSocket.so
./usr/lib/aim/CoolSocket.so.1
./usr/lib/aim/CoolSos.so
./usr/lib/aim/CoolSos.so.1
./usr/lib/aim/extra/
./usr/lib/aim/extra/AIM.desktop
./usr/lib/aim/extra/AOL Instant Messenger (SM).desktop
./usr/lib/aim/extra/aim.png
./usr/lib/aim/extra/aim.xpm
./usr/lib/aim/extra/install.sh
./usr/lib/aim/feed.so
./usr/lib/aim/feed.so.1
./usr/lib/aim/help/
./usr/lib/aim/help/about_buddy_privacy.htm
./usr/lib/aim/help/about_the_buddy_list.htm
./usr/lib/aim/help/adding_a_group_or_buddy.htm
./usr/lib/aim/help/after_regis.htm
./usr/lib/aim/help/allowing_everyone_to_send_you_me.htm
./usr/lib/aim/help/allowing_only_your_buddies_to_se.htm
./usr/lib/aim/help/allowing_specific_users_to_conta.htm
./usr/lib/aim/help/away_message.htm
./usr/lib/aim/help/away_prefs.htm
./usr/lib/aim/help/banner.htm
./usr/lib/aim/help/banner_2.htm
./usr/lib/aim/help/blocking_everyone_from_sending_y.htm
./usr/lib/aim/help/blocking_specific_users.htm
./usr/lib/aim/help/changing_address.htm
./usr/lib/aim/help/changing_password.htm
./usr/lib/aim/help/chat.htm
./usr/lib/aim/help/chat_invite.htm
./usr/lib/aim/help/confirming_account.htm
./usr/lib/aim/help/connection_prefs.htm
./usr/lib/aim/help/defining_away.htm
./usr/lib/aim/help/deleting_a_group.htm
./usr/lib/aim/help/deleting_away.htm
./usr/lib/aim/help/format_messages.htm
./usr/lib/aim/help/fs_about_bl.htm
./usr/lib/aim/help/fs_about_buddy_privacy.htm
./usr/lib/aim/help/fs_about_the_buddy_list.htm
./usr/lib/aim/help/fs_adding_a_group_or_buddy.htm
./usr/lib/aim/help/fs_after_regis.htm
./usr/lib/aim/help/fs_allowing_only_your_buddies.htm
./usr/lib/aim/help/fs_allowing_specific_users_to_con.htm
./usr/lib/aim/help/fs_away_message.htm
./usr/lib/aim/help/fs_away_prefs.htm
./usr/lib/aim/help/fs_blocking_specific_users.htm
./usr/lib/aim/help/fs_changing_address.htm
./usr/lib/aim/help/fs_changing_password.htm
./usr/lib/aim/help/fs_chat.htm
./usr/lib/aim/help/fs_chat_invite.htm
./usr/lib/aim/help/fs_confirming_account.htm
./usr/lib/aim/help/fs_connection_prefs.htm
./usr/lib/aim/help/fs_deleting_a_group.htm
./usr/lib/aim/help/fs_everyone_from_sending.htm
./usr/lib/aim/help/fs_format_messages.htm
./usr/lib/aim/help/fs_general_prefs.htm
./usr/lib/aim/help/fs_im.htm
./usr/lib/aim/help/fs_insert_hyperlink.htm
./usr/lib/aim/help/fs_insert_smileys.htm
./usr/lib/aim/help/fs_installing.htm
./usr/lib/aim/help/fs_privacy_prefs.htm
./usr/lib/aim/help/fs_registering.htm
./usr/lib/aim/help/fs_sending_chat.htm
./usr/lib/aim/help/fs_sending_im.htm
./usr/lib/aim/help/fs_signing_on.htm
./usr/lib/aim/help/fs_sounds.htm
./usr/lib/aim/help/fs_sounds_prefs.htm
./usr/lib/aim/help/fs_turning_an_away.htm
./usr/lib/aim/help/fs_uninstalling.htm
./usr/lib/aim/help/general_prefs.htm
./usr/lib/aim/help/help_contents.htm
./usr/lib/aim/help/im.htm
./usr/lib/aim/help/im_hyperlink.htm
./usr/lib/aim/help/images/
./usr/lib/aim/help/images/add_buddy.gif
./usr/lib/aim/help/images/aimheaderleft.gif
./usr/lib/aim/help/images/away.gif
./usr/lib/aim/help/images/buddyList.gif
./usr/lib/aim/help/images/chat_invite_scr.gif
./usr/lib/aim/help/images/chat_message.gif
./usr/lib/aim/help/images/chat_message2.gif
./usr/lib/aim/help/images/im.gif
./usr/lib/aim/help/images/sign_on.gif
./usr/lib/aim/help/index.htm
./usr/lib/aim/help/insert_hyperlink.htm
./usr/lib/aim/help/insert_smileys.htm
./usr/lib/aim/help/installing.htm
./usr/lib/aim/help/inviting.htm
./usr/lib/aim/help/overview.htm
./usr/lib/aim/help/privacy_prefs.htm
./usr/lib/aim/help/registering.htm
./usr/lib/aim/help/saving_im.htm
./usr/lib/aim/help/sending_chat.htm
./usr/lib/aim/help/sending_im.htm
./usr/lib/aim/help/signing_on.htm
./usr/lib/aim/help/sounds_prefs.htm
./usr/lib/aim/help/turning_an_away.htm
./usr/lib/aim/help/uninstalling.htm
./usr/lib/aim/service.so
./usr/lib/aim/service.so.1
./usr/lib/aim/sounds/
./usr/lib/aim/sounds/cashregister.wav
./usr/lib/aim/sounds/dooropen.wav
./usr/lib/aim/sounds/doorslam.wav
./usr/lib/aim/sounds/imrcv.wav
./usr/lib/aim/sounds/imsend.wav
./usr/lib/aim/sounds/moo.wav
./usr/lib/aim/sounds/newalert.wav
./usr/lib/aim/sounds/newmail.wav
./usr/lib/aim/sounds/phone.wav
./usr/lib/aim/sounds/ring.wav
./usr/lib/aim/sounds/talkbeg.wav
./usr/lib/aim/sounds/talkend.wav
./usr/lib/aim/sounds/talkstop.wav
./usr/lib/aim/source/
./usr/lib/aim/source/extgtktext.c
./usr/lib/aim/source/extgtktext.h
./usr/lib/aim/source/line-arrow.xbm
./usr/lib/aim/source/line-wrap.xbm
./usr/lib/aim/ui.so
./usr/lib/aim/ui.so.1
./usr/lib/libXpcs.so
./usr/lib/libXpcs.so.1
./usr/lib/libXprt.so
./usr/lib/libXprt.so.1
./usr/lib/libXptl.so
./usr/lib/libXptl.so.1
./usr/lib/libextgtk.so
./usr/lib/libextgtk.so.1
dougie@DougiesToyBox:/$ cd ~
dougie@DougiesToyBox:~$ rm -rf ~/usr
rm: cannot remove `/home/dougie/usr/bin/aim': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolBos.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolBos.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolBucky.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolBucky.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolHttp.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolHttp.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolPeer.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolPeer.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolSocket.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolSocket.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolSos.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/CoolSos.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/extra/AIM.desktop': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/extra/AOL Instant Messenger (SM).desktop': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/extra/aim.png': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/extra/aim.xpm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/extra/install.sh': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/feed.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/feed.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/about_buddy_privacy.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/about_the_buddy_list.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/adding_a_group_or_buddy.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/after_regis.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/allowing_everyone_to_send_you_me.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/allowing_only_your_buddies_to_se.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/allowing_specific_users_to_conta.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/away_message.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/away_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/banner.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/banner_2.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/blocking_everyone_from_sending_y.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/blocking_specific_users.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/changing_address.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/changing_password.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/chat.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/chat_invite.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/confirming_account.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/connection_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/defining_away.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/deleting_a_group.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/deleting_away.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/format_messages.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_about_bl.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_about_buddy_privacy.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_about_the_buddy_list.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_adding_a_group_or_buddy.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_after_regis.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_allowing_only_your_buddies.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_allowing_specific_users_to_con.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_away_message.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_away_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_blocking_specific_users.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_changing_address.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_changing_password.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_chat.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_chat_invite.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_confirming_account.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_connection_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_deleting_a_group.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_everyone_from_sending.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_format_messages.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_general_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_im.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_insert_hyperlink.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_insert_smileys.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_installing.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_privacy_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_registering.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_sending_chat.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_sending_im.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_signing_on.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_sounds.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_sounds_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_turning_an_away.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/fs_uninstalling.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/general_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/help_contents.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/im.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/im_hyperlink.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/images/add_buddy.gif': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/images/aimheaderleft.gif': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/images/away.gif': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/images/buddyList.gif': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/images/chat_invite_scr.gif': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/images/chat_message.gif': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/images/chat_message2.gif': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/images/im.gif': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/images/sign_on.gif': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/index.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/insert_hyperlink.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/insert_smileys.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/installing.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/inviting.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/overview.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/privacy_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/registering.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/saving_im.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/sending_chat.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/sending_im.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/signing_on.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/sounds_prefs.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/turning_an_away.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/help/uninstalling.htm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/service.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/service.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/cashregister.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/dooropen.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/doorslam.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/imrcv.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/imsend.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/moo.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/newalert.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/newmail.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/phone.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/ring.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/talkbeg.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/talkend.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/sounds/talkstop.wav': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/source/extgtktext.c': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/source/extgtktext.h': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/source/line-arrow.xbm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/source/line-wrap.xbm': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/ui.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/aim/ui.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/libXpcs.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/libXpcs.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/libXprt.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/libXprt.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/libXptl.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/libXptl.so.1': Permission denied
rm: cannot remove `/home/dougie/usr/lib/libextgtk.so': Permission denied
rm: cannot remove `/home/dougie/usr/lib/libextgtk.so.1': Permission denied
dougie@DougiesToyBox:~$ ldd /usr/bin/gaim
        linux-gate.so.1 =>  (0xffffe000)
        libgstreamer-0.10.so.0 => /usr/lib/libgstreamer-0.10.so.0 (0xb7ec4000)
        libXss.so.1 => /usr/lib/libXss.so.1 (0xb7ec1000)
        libgtkspell.so.0 => /usr/lib/libgtkspell.so.0 (0xb7ebc000)
        libstartup-notification-1.so.0 => /usr/lib/libstartup-notification-1.so.0 (0xb7eb4000)
        liblaunchpad-integration.so.0 => /usr/lib/liblaunchpad-integration.so.0 (0xb7eb0000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb7b57000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb7ad1000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb7ab6000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb7a9f000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb7a61000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb7a27000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb7991000)
        libgaim.so.0 => /usr/lib/libgaim.so.0 (0xb78e5000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb78dc000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb78c4000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb77f9000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb77e2000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb77ba000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7679000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb7670000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb766b000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb7668000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7664000)
        libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb7549000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb753c000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb7533000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb7508000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb7505000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb74fc000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb74f9000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb74f0000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb74eb000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb7481000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb7479000)
        libaspell.so.15 => /usr/lib/libaspell.so.15 (0xb73c2000)
        libnm_glib.so.0 => /usr/lib/libnm_glib.so.0 (0xb73bd000)
        libdbus-glib-1.so.2 => /usr/lib/libdbus-glib-1.so.2 (0xb73a2000)
        libdbus-1.so.3 => /usr/lib/libdbus-1.so.3 (0xb7370000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb7358000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb7345000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb7342000)
        libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb733d000)
        /lib/ld-linux.so.2 (0xb7f6f000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb7329000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb72fd000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb7293000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb7274000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb7251000)
        libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0xb7167000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb715b000)
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-21
```
sudo rm -rf /home/dougie/usr
aim
```

---

### Post by DougieFresh4U on 2007-01-21
dougie@DougiesToyBox:~$ aim
aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by taurus on 2007-01-21
```
whereis aim
/usr/bin/aim
```

---

### Post by DougieFresh4U on 2007-01-21
its got dependency problems-correct me if I am wrong please;                          dougie@DougiesToyBox:~$ whereis aim
aim: /usr/bin/aim /usr/lib/aim /usr/X11R6/bin/aim /usr/bin/X11/aim
dougie@DougiesToyBox:~$ /usr/bin/aim
/usr/bin/aim: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory
dougie@DougiesToyBox:~$

---

### Post by DougieFresh4U on 2007-01-22
Can some one please come up with a solution before I make myself crazy over this? [-o<

---

### Post by DougieFresh4U on 2007-01-22
Sorry for the Bump, but I am still on that mission:-s

---

