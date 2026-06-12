---
title: "Lockout: Double Fail Passwd Reset on 14.04"
date: 2014-05-05
forum: General Help
---

### Post by Kurt_Alan on 2014-05-05
[SIZE=5][COLOR="#000000"]****[/COLOR][/SIZE]

Lockout: Double Fail Passwd Reset

Prefatory to my double passwd reset fail on 14.04:
a. OS: clean install 10.04 LTS, < upgrade to 12.04 < upgrade to 14.04 LTS, all 32 bit.
b. Immediate event prior to password/login fail: Utilizing a tutorial from ubuntuhandbook.org, from CLI, I used gedit to edit grub to select my preference for text-only boot (I like to watch the O.K.'s rather than have this information hidden by Plymouth).

Although this grub edit and succeeding text-only boot was successful, my login failed and I could not initiate GUI.  I forgot my login so I retrieved it via ```
 ls /home/ 
```   However, as I said, my "correct" login failed.  Then my password also failed.

I used the standard method for password reset:
```
 sudo mount -rw -o remount / 
```
And: ```
 passwd lucas 
```
This offered me a new UNIX password and the change was accepted.  However, my password/login combination failed again.

I also re-edited grub to replace text-boot with GUI Plymouth. This was successful but didn't change my password/login status.

I then googled an ubuntu forums solution for a "drastic" method: Create an empty or null password.  Here, from CLI, I brought up nano and found a line beginning with my user name.  From this line I deleted everything except numbers and colons, saved, exited, rebooted.  Password/login fail again.

What I can and cannot do: I can access my root prompt via recovery mode.  I can enter GUI Guest session.  I have internet access.  I cannot enter my personal account.  I have spent 20+ hours configuring.  I do not want to re-install.
Solutions? Please specify discrete procedures.  Although I have been using Ubuntu since Dapper Drake, and Ubuntu is now my primary system, actually my only OS, I am still a beginner trying to "take it to the next level."  Yesterday was the first time I used a text editor and this was by virtue of copy/paste and not personal knowledge.

Thank you! Thank you!

---

### Post by bapoumba on 2014-05-05
Can you make a new user ?
From recovery mode, you can proceed as described here : [https://help.ubuntu.com/community/AddUsersHowto#Command-line](https://help.ubuntu.com/community/AddUsersHowto#Command-line)
Now you'll have to add this user to the standard groups, here are mine :
```
groups
bapoumba adm dialout fax cdrom floppy tape sudo dip video plugdev fuse lpadmin sambashare
```
Can you log in ?

I suppose the procedure you are describing to reset the user password is the one from here : [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Now could you please describe this "drastic method" you used and may be give the link you used ?

---

### Post by deadflowr on 2014-05-05
Your mount command was wrong.

```
mount -o rw,remount /
```

so you were still in read-only mode.

---

### Post by Impavidus on 2014-05-06
How did you know that your password was not accepted? Did it tell you "Incorrect password" or did the login bounce, that you were returned to the login screen at once? That would indicate that the session crashed as soon as it is started. It is unlikely that modifying some config files with gedit+root privileges would alter your password.

Check the ownership of the files in your home directory (/home/yourusername). If any files are owned by root, change ownership back to yourself. The most likely suspect is .Xauthority, a hidden file. From the recovery console you can check with```
ls -al /home/yourusername/.Xauthority
```and you can recover with```
chown -R yourusername:yourusername /home/yourusername
```

However, I think that your drastic method may have done more damage. You used nano to open a file and delete some things from the line with your user name. Which file did you open? /etc/passwd? /etc/shadow? There may still be a backup of the old versions of those files.

---

### Post by kurt18947 on 2014-05-06
I've used the method suggested by bapoumba when I FUBARed a user account. Create a new user and copy any important data files using a live install. I guess that's one risk to encrypting a home folder, I don't know what would be involved in recovering files stored there if that user's password were messed up.

---

### Post by Kurt_Alan on 2014-05-06
[SIZE=5]****[/SIZE]
(1001)
Hello bapoumba,

Thanks for your many suggestions.  I have tried all and I am still caught in log-in bounce return to log-in loop.  Recovery mode output affirms password change but to no avail.

Per your suggestions:

1. You asked if I could make a new user.  Although my inputs were accepted, the result failed.  Output: [code] Adding user 'lucas1' . . . THEN Adding new group 'lucas1' (1001) . . . THEN groupadd: cannot lock /etc/group: try again later THEN adduser: '/usr/sbin/groupadd -g 1001 lucas1' returned error code 10. Exiting.

2. Confirmed.  The "psyocats" method is the "standard" method I used for passwd reset.  Again, the password reset successfully but it does not function.

3. Link for "drastic" method:

[URL="http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password"]  Scroll down to the bottom of this page.  The location I editd with nano was /etc/shadow

Looking forward to hearing from you and thanks again.

---

### Post by Kurt_Alan on 2014-05-06
Hello deadflowr,

Yes, you are corrrect, I made an error for mount as rw.
I applied your correction, my password change was made successfully.  Unfortunately, my "new" password is not accepted and I a stuck in a log-in loop.

Thank you for your help.

---

### Post by Kurt_Alan on 2014-05-06
****[SIZE=5][/SIZE]

Hello impavidus,

Thank you for your suggestions and help.  I have applied all but unfortunately I am still stuck in a log-in loop with my "new" password not being accepted.

To wit:

1. You asked how I knew that my password was not accepted.  Per above, in recovery mode my UNIX password was changed successfully there according to that output.  But it failed because the log-in bounced and returned to log-in.

2. I checked file ownership accordingly ```
 ls -al /home/lucas/ .Xauthority 
```

I wish I could give you the output but in my GUI guest session, where I am now, I do not have root in terminal and in recovery mode I have root but no GUI tools.

However, from memory, my input was accepted.  In that list I found a line with my user name and .Xauthority at the end of it.  Doesn't the dot mean root?
I failed to write down the status of ownership at the beginning of the line.  

With chown, I thought I'd be removing the . from Xauthority.  So then I did this: ```
 chown -R lucas:lucas /home/lucas 
```
----
I noticed that my user line still showed .Xauthority so this confused me.  I thought that dot would have been removed.
 
But I did write down my present ownership.  It is: -rw----

Please clarify above.  And, again, "no go" on log-in

3. In the "drastic" method I used nano to edit /etc/shadow   Here is the link for this method--scroll down to the bottom: [URL="http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password[/URL]

---

### Post by Kurt_Alan on 2014-05-06
Hi fellow kurt,

My Home Folder was not encrypted.  So were you successful?

---

### Post by deadflowr on 2014-05-06
The dot in Xauthority, or any file for that matter, means it's hidden, not root owned.

It's been a long time since I've had a login loop so I'm not sure, but perhaps try moving the file
```
mv .Xauthority .Xauthority.bak
```
I can't remember if it regenerates a new one or not, but if it does it should fix the login.
If it doesn't, no harm just reverse the command and start over.

---

### Post by Impavidus on 2014-05-06
> **Kurt_Alan said:**
> 
1. You asked how I knew that my password was not accepted.  Per above, in recovery mode my UNIX password was changed successfully there according to that output.  But it failed because the log-in bounced and returned to log-in.

Without explicitly stating the login was incorrect? That suggests there was no problem with the password, but your graphical session crashed the moment is was started, returning you to the login screen. This may have been caused by running a text editor with root permissions the wrong way.
Can you login using the console? Hit ctrl+alt+F2 and try. If it works we can be sure the problem is in starting the graphical session. You can return to the GUI login with ctrl+alt+F7.

And set a password.

Edit: That guide said you had to use **nano -B /etc/shadow**. This means that there should be a backup file /etc/shadow~, the valid old version of the shadow file with the password in it. That is the last password you set before manually editing the shadow file.

---

### Post by bapoumba on 2014-05-06
Well, if you messed up with the /etc/shadow file, you may end up seeing what you see : impossible to log in..
[http://ubuntuforums.org/showthread.php?t=2026413](http://ubuntuforums.org/showthread.php?t=2026413)
[http://linux.die.net/man/5/shadow](http://linux.die.net/man/5/shadow)

---

### Post by kurt18947 on 2014-05-06
> **Kurt_Alan said:**
> Hi fellow kurt,

My Home Folder was not encrypted.  So were you successful?

I was.  If the messed up account was "user", I'd create another account like "user1".  Then move any data I wanted to keep from "user" to "user1".  i tried to delete "user" then rename "user1" to user but there were remnants from the corrupted "user".  I'm not sure why that happened, unless I didn't choose to delete the user account **and** data and config files.

---

### Post by Kurt_Alan on 2014-05-06
[SIZE=5]****[/SIZE]

Hello:

I think I am making progress! I now realize, per indications of deadflowr, and yourself, that I likely do not have a password error/reset problem at all.  I have an instantaneous GUI crash problem which led me to believe that the problem was with my password.

My password is accepted without an error message but I get a log-in loop back.  If, however, I type in a false password, I do get an error message.

Please look at deadflowr's notes.  His last recommendation was ```
 mv .Xauthority .Xauthority.bak 
```

The result of this, from the recovery root CLI was: ```
 mv: cannot stat ' .Xauthority ' : No such file or directory. 
```  I am copying/pasting this post as a reply to deadflowr and bapoumba as well.  I hope this is not violating protocol.

Where do you guys recommend I go from here? Thank you.

---

### Post by Kurt_Alan on 2014-05-06
[SIZE=5]****[/SIZE]


Hello:

I think I am making progress! I now realize, per indications of deadflowr, and yourself, that I likely do not have a password error/reset problem at all.  I have an instantaneous GUI crash problem which led me to believe that the problem was with my password.

My password is accepted without an error message but I get a log-in loop back.  If, however, I type in a false password, I do get an error message.

Please look at deadflowr's notes.  His las recommend was ```
 mv .Xauthority .Xauthority.bak 
```

The result of this, from the recovery root CLI was: [code] mv: cannot stat ' .Xauthority ' : No such file or directory.  I am copying/pasting this post as a reply to deadflowr as well.

Where do you guys recommend I go from here? Thank you.

---

### Post by deadflowr on 2014-05-06
Yeah, if your in the root cli (rocovery mode), then the command would need to look a little different.
The file is in your home folder.
```
mv /home/you/.Xauthority /home/you/.Xauthority.bak
```

When you run the recovery mode, it puts you in root mode, which doesn't put you in the home folder, since it doesn't know your the user of that home folder.
If that makes sense.

Anyway, I'll make two points.

1)Again, it has been a long time since a login loop has happened to me, myself, and I *think* moving/removing that file helps.
Though, I'm not positive.

2)If it doesn't fix it, then it's simple, just reverse the command and move it back with
```
mv /home/you/.Xauthority.bak /home/you/.Xauthority
```
I believe the file .Xauthority regenerates if it doesn't exist, which is why you move it to a backup file (.bak).
Which is a better way, than say, deleting the file. Since, I can't remember off the top if it does regenerate, or if it is at all the problem. If moving it to a backup doesn't fix the issue, then moving it back is a no harm no foul, start from scratch situation.
whatever you do with that file, though, make sure the owner is you.
```
ls -l filepath/.Xauthority
```
or whatever the path to the file is.
```
chown you:you filepath/.Xauthority
```
if it is not owned by you.

Whenever running as root, root tends to like to take ownership of whatever is moved or copied.

I hope something in here makes sense, or helps.

---

### Post by Kurt_Alan on 2014-05-07
**[SIZE=5][/SIZE]**

Hello deadflowr,

Thanks for keeping up with me.  This reply is limited to the question of ownership of .Xauthority as you said I should first confirm ownership of that (by me) before proceeding to your solution of move and regeneration. 

The code follows but here is my take.  Please tell me if I'm understanding the problem correctly.  It appears that I am not the owner because “root” is substituted for “lucas” my user name/account.  So this means that my personal GUI session will not initiate because “lucas” does not have permission. And, further, chown failed because this file is read only.

To wit:

I entered: ```
 ls -al /home/lucas/ .Xauthority 
```

Output: ```
 -rw---- 1 root root 57 May 4 19:11 .Xauthority 
```

Then I tried chown: ```
 chown -R lucas:lucas /home/lucas 
```

Output: ```
 chown: changing ownership of ' /home/lucas: Read-only file system 
```

Do I understand the problem correctly? What next? Find a way to change read-ony to rw so I can make the ownership change??

---

### Post by Impavidus on 2014-05-07
Yes, you understand correctly, except that not the file, but the entire file system is read-only. If you boot into recovery mode, first remount the file system rw, then change ownership of that file. Or simply every file, to be sure.```
mount -o rw,remount /
chown -R lucas:lucas /home/lucas
```

Actually, you can do without recovery mode if you can login in the console (ctrl+alt+F2). In that case remounting won't be necessary.

---

### Post by deadflowr on 2014-05-07
If your booting into the recovery mode, it defaults to read-only.
To change run this
```
mount -o rw,remount /
```

this will remount the file system read/write, allowing you to write.

---

### Post by Kurt_Alan on 2014-05-07
**[SIZE=5][COLOR="#000000"][/COLOR][/SIZE]**

Wow! Clean as a whistle! I remounted file system to write, chown ownership of .Xauthority from root to user (lucas), confirmed via ls -al . . . 

And logged into my personal session!  So I never had a password reset problem. I had an X windows permissions config error.

Thanks to deadflowr, impavidus and bapouma for sticking with me and for all your help!  ):P

---

### Post by bapoumba on 2014-05-07
Glad to see you got it sorted out !

---

