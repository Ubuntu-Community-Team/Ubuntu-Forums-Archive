---
title: "re: not in sudoers group_cant update Gutsy"
date: 2008-02-22
forum: General Help
---

### Post by fallsoff on 2008-02-22
Hello,
Gutsy newbie here.

 I can download updates and see them, but I cannot install them. I can't do much of anything administratively, and I cannot find clear instructions as to why and how to fix this step by step. The logs tell me that I am not in the sudoers group. How do I fix that?  Also, should I not have set an admin password when I installed Gutsy? The pw I used does not seem to work although the user pw does. I have searched for explicit instructions and had no luck yet.

id:
uid=1001(user name) gid=1001(user name)) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),1001((user name))

 who:  my username and< tty7>

Please advise. I am very much enjoying Gutsy except for this  issue. The wireless so far is better and easier to use than XP pro SP2.
Thanks and please set me straight.
fallsoffmotorcycle

---

### Post by xeth_delta on 2008-02-22
Can you run sudo from the console? For example "sudo nano"?
Can you please post the contents of "/etc/group"?

---

### Post by fallsoff on 2008-02-22
Hello,

I am unable to send the copy paste of etc/groups as an error message says I have 60-odd images in the response. This is new to me and has never happened before. I had to do some copy/paste and that must be the reason. I tried reformatting in abiword but nothing changed. Now what? 

Sudo nano gave a pw prompt and nothing. I am now trying to attach the /etc/group doc. Lets see if that gets through. I edited the computer and user names for security.
Thanks
fallsoff
ps:
no .abw or .txt are invalid file errors and wont fly as attachments.
Sorry for the confusion and irritation!!

---

### Post by xeth_delta on 2008-02-22
> **fallsoff said:**
> Hello,

I am unable to send the copy paste of etc/groups as an error message says I have 60-odd images in the response. This is new to me and has never happened before. I had to do some copy/paste and that must be the reason. I tried reformatting in abiword but nothing changed. Now what? 

Sudo nano gave a pw prompt and nothing. I am now trying to attach the /etc/group doc. Lets see if that gets through. I edited the computer and user names for security.
Thanks
fallsoff
ps:
no .abw or .txt are invalid file errors and wont fly as attachments.
Sorry for the confusion and irritation!!

place the file contents between CODE statements. You cn use the # button in the posting page.

sudo nano should ask you for a password. Did you type it in? The password characters you type are not shown.

---

### Post by samkline on 2008-02-22
The output of the "id" program shows that you aren't in the admin group, you need to be in this in order to use sudo (or run other commands as the superuser/administrator). To fix this:

First login as root (you will be prompted for the administrator password you set):
[FONT="Courier New"]su[/FONT]

Then run this command to add yourself to the admin group:
[FONT="Courier New"]usermod -aG admin username[/FONT]
(make sure you type the "a" as lowercase and the "G" as uppercase)

Then type [FONT="Courier New"]exit[/FONT] to logout of root, and then you should be able to use sudo or any other programs that need to be run as the superuser.

---

### Post by aysiu on 2008-02-22
[This tutorial](http://www.psychocats.net/ubuntu/sudo) will help you get back into the *admin* group.

---

### Post by sisco311 on 2008-02-22
if your root account is not enabled(default in ubuntu) reboot in recovery mode(select it from the grub menu at start up)
and type:
```
usermod -a -G admin username
reboot
```

---

### Post by fallsoff on 2008-02-23
Hi 8 am here yawn.went in through recovery mode and i don't think the pw was recognized. followed cmd sequence and no joy. i wrote down the admin pw so it IS good but the system doesn't seem to respond to it. i understand that we don't get the row of dots etc but aso i did not get a wrong pw error msg so i am sure the pw is good. ubuntu didn't recognize the cmd sequence or syntax. i believe that was the error msg [yawn].
advice?
fallsoff

---

### Post by fallsoff on 2008-02-23
went in again and tried. used usermod -a -G admin username. no joy. rebooted and got this:  '''coudn't open network socket....check dcopserver not running? also a private msg sethdelta that wont open. working on that now.
tnx
fallsoff

---

### Post by fallsoff on 2008-02-23
Hello and thanks to xeth_delta and all of the others . I was able to <esc> boot and edit the grub menu. I had a second note to <nano /etc/group> on reboot, but that didnt work as far as I can tell.
I am now able to download 301 updates and we will see if they install. I could not get this far before, so thank you all. I may still be stuck, so lets please keep the thread open for the next instalment!!
Thanks again,
fallsoff

---

### Post by fallsoff on 2008-02-23
Hi al
I saw another admin user post and added myself via visudo to sudoers using <'echo <username> ALL+(ALL) ALL'>. I see now that I failed to add < I tee -an /etc/sudoer> to that.
OOPS!
However my user pw is now accepted to get into different things that were blocked before.
Please advise as to my current situation Am I fully qualified as a sudoer now and free to make my next mistake or not??
TIA
fallsoff

---

### Post by Iowan on 2008-02-24
[Here]("http://ubuntuforums.org/showthread.php?t=706277") is another thread that suggests it may be as simple as adding your username to the **admin** group.

---

### Post by aysiu on 2008-02-24
> **Iowan said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=706277") is another thread that suggests it may be as simple as adding your username to the **admin** group.
Yes, which is one of the steps outlined in [the link](http://www.psychocats.net/ubuntu/sudo) I linked to in [post 6 of this thread](http://ubuntuforums.org/showpost.php?p=4384081&postcount=6).

---

### Post by Iowan on 2008-02-24
Hmmm... I suppose I ought to see what other gems are in that psychocats link in my sig...:)

That, and read the ENTIRE thread - not just the last page...

---

