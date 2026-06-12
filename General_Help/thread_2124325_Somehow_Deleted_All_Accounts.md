---
title: "Somehow Deleted All Accounts"
date: 2013-03-10
forum: General Help
---

### Post by Tununias on 2013-03-10
This is probably in the wrong section, but I don't really know where it goes.

I have not idea how this happened. I had an account that I didn't need anymore so I used system settings to delete it. Somehow, instead both that account and my administrator account were deleted even though that's not supposed to be possible.(I think it happend when because I clicked delete twice after I thought it didn't work the first time.)

I noticed it when I saw that my background was missing and I couldn't open any other programs. Also the menu and the upper right corner didn't show anything. I manually restarted the computer and now I have no accounts. The login just tells me to enter my username and password. That doesn't work and says my username and password are incorrect. Is there any way to retreive my account or my files, or am I screwed? (I told it to delete the files from the account I was trying to delete).


Also I think this is a glitch, although I don't think there's much left(if the files are competely gone) to report with. I did have some files that would be nice if I could get back, but it won't be the end of the world if I can't get them back.

I will do a reinstall at the end of Monday (March 11, 2013 10:00 pm EST) if I don't get any replies. It's nothing personal, I just really don't have much time to wait. Anyway, thank you in advance to anyone who tries to help me. And sorry if this isn't very organized, this all just happened and I'm not thinking clearly.

---

### Post by Tununias on 2013-03-10
I do have the guest login available, but I don't have any permission and can't see if my personal files are still there. The programs I have installed are still there. Also, if Its possible to make a new administrator account without reinstalling, please let me know. I have a lot of programs and stuff that would take a while for me to track down and install.

---

### Post by kuifje09 on 2013-03-10
If you are able to log in as root, then you can see, if you deleted per accident all the users, eventually with or without their homes.
If the homes and content are there, then you might be able to rebuild the userlist.
When also the content of the homes is lost, then your system can be considdered empty.
Or, do you mean to say that also the whole /etc/passwd is empty ?

---

### Post by Tununias on 2013-03-10
/etc/passwd isn't empty. There's about 30 lines of text in there. How would I log into the root acount?

---

### Post by kuifje09 on 2013-03-10
Well, If you dont have a root passwd or forgot, you have to boot into singleuser mode.

Then you are root , and can set a passwd of choice. choose one good and dont forget.

Ubuntu has a boot entry when you startup the computer, usualy the second line, or the one below the default.
Maintenance mode I gues.  
But when in maintenance mode you also can check /home for its content.

---

### Post by Frogs Hair on 2013-03-10
There is a way to add a user from the terminal but the guest account won't save changes and has limited function for security reasons .  [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

To access tty you need to login and enter a password so it is a catch 22 . I did see some methods for file recovery but they were dated .

---

### Post by Tununias on 2013-03-10
The second option is Advanced Options which has several versions of the kernel and a Recovery Mode for each kernel. In recovery mode, it has a window that says > Recovery Menu (filesystem state: Read-Only)
resume_____ Resume normal boot
clean_____ Try to make free space
dpkg_____ Repair broken packages
failsafex_____ Run in failsafe graphic mode
fsck_____ Check all file systems
grub_____ update grub boot loader
network_____ Enable Networking
root_____ Drop to root shell prompt
system-summery_____ System summery
<OK>
Should I select root, fsck, or is this not the right place?
I added the "_____" because I it got rid of all my spaces.

---

### Post by kuifje09 on 2013-03-10
Okay when to recreate the accounts, thats easy. But when the content of the homes is lost is does not make any sense.
So first chek if there is something worth to save in the home, then recreate the passwd entries.
Any uid created above the id==1000 is displayed in the grafical usermanager.
After creation you can change the homepath and id's by hand if needed.

But also,  when you lost your users, you dont need to reinstall.  users are just users,  not a whole system.

When you are able to login as root, then you could just create one user in the grafical manager, give him admin rights and you can do the rest as usual.
The guest account you do'nt need,  I think it was better if it wasn't there. ( I deleted it )

---

### Post by lisati on 2013-03-10
> **Tununias said:**
> I added the "_____" because I it got rid of all my spaces.
*** aside begins ***
Although it might seem a little bit counter-intuitive at first, using [noparse]```
 and 
``` instead of >  and [/noparse] can sometimes be useful if you want to preserve the formatting of something you are quoting.
*** aside ends ***

---

### Post by kuifje09 on 2013-03-10
Oops we missed each other,  I never saw that menu, must be special to 12.XX.
So that is not funny. 

Choose for failsafex,  then you are grafical, that is always helpfull.

Update: if failsafx is not a root environment, then choose for rootshell.
But then you realy need to know what to do. if not, things are easily broken.

---

### Post by Tununias on 2013-03-10
I chose failsafex and it said: > Continuing will remount your / filesystem in readwrite mode and mount any other filesystem defined in /etc/fsta6.
<Yes> <No>

I selected yes and a terminal displayed > fsck from util-linux 2.20.1
/dev/sda6: clean, 459150/7536640 files, 5744013/30129408 blocks
Then it just shows a blinking "_" shaped cursor on the line below it.
Nothing else happens.

---

### Post by kuifje09 on 2013-03-10
This is diasappointing, I never used to do this, it is new to me also. But after the check it should continue somehow.
Just a blinking cursor is not good.
If nothing else will heppen in a little time, just reboot and try the same again.
You should/must end up with a grafical environment.

---

### Post by Tununias on 2013-03-10
I tried it several times, but it still did the same thing. I tried the root option and was able to view my old account's home directory. All that was in was a file called Access-Your-Private-Data.desktop and a README.txt file. Does that mean all my files have been erased?

---

### Post by Tununias on 2013-03-10
If there's no way to recover my account files, I'd be happy with just setting up a new administrator account. I had made a flashdrive backup a few months back and it's only slightly outdated. A lot of my programming projects have the source files uploaded on my college's website. The only thing I think I would lose is about 3 gigs of family photos which I think my sister has a copy on her computer.

---

### Post by kuifje09 on 2013-03-10
I am afraid you accidently erased all use user id's and their contend.
So that is bad luck as it can be.

But... You don't need to reinstall ubuntu now.

Just add a line to the end of the /etc/passwd and the /etc/shadow.
Add the userid at the end of the line in the /etc/group   file and you might be able to log in again to the grafical env you like.
And start over again, an create all the users you had before.

To /etc/passwd :
user1:x:1001:1001:User1,,,,:/home/user1:/bin/bash

to /etc/shadow :
user1:*:15752:0:99999:7:::

add user1 after adm in the /etc/group.
adm:x:4:user,user,user.....,user1

create a passwd for the user

passwd user1
set and repeat the passwd

Create a /home for that user

mkdir /home/user1
chown user1 /home/user1

I hope not forgot something, but you may be able to log in with user1

Thos silly smilies does not belog there... fixed.

Extra update, to become administrator, I thought it is adm in the group file, but it is not.
Have to search for it, or maby someone else can tell , that could help a lot.


Ureka, found it already,   it is the    admin    entry not the     adm     entry ( sorry )

---

### Post by steeldriver on 2013-03-10
Seeing **access-Your-Private-Data.desktop** probably just means you had an encrypted home directory, which will make recovery a bit more complicated IF the data didn't get deleted with the account

I would suggest you create a new user account with administrator priviledges then you can log in to a graphical environment with that which will make the recovery easier for you. 

I'm a bit lost with what's going on in this thread but basically once you are in the recovery mode and have dropped to a root shell you can do the following. **There is no need to directly edit the /etc/passwd file to do this.**

1. remount the filesystem with write permissions - if you've done an fsck it may already be read-write but this command won't hurt either way:

```
mount -o remount,rw /
```

[note there is NO SPACE between the rw and remount options - just a comma]

2. create a new user:

```
adduser *newname*
```

and just follow the on screen prompts

3. add the user to the sudo group

```
usermod -aG sudo *newuser*
```

If you plan on keeping the newuser as a regular administrator account you will probably want to add it to all the other typical groups i.e.

```
usermod -aG adm,cdrom,sudo,dip,plugdev,lpadmin,sambashare *newuser*
```

At that point you should be able to exit the root shell

```
exit
```

and resume normal boot, where you can log in via the GUI as *newuser*

---

### Post by kuifje09 on 2013-03-10
If this : Access-Your-Private-Data.desktop  does mean there is an encrypted file system, then the contend is lost I think?

Not lost ? [http://ubuntuforums.org/showthread.php?t=1810825](http://ubuntuforums.org/showthread.php?t=1810825)  But then why should I encrypt?

But it could mean his data is not lost, thanks for jumping in.

---

### Post by kuifje09 on 2013-03-10
When you managed to create a user one way or the other. Then you could enter your old homedir ( cd /home/OLDUSER ) and as suggested in the other post ( link ) try to mount it :  Just run ecryptfs-mount-private and enter your log in password.  and copy ...   read other post .
But with a little precise work you can also recreate your old user by hand...  Not with usermod. ( I would not use usermod for that )

( i have to quit for now... )

---

### Post by Tununias on 2013-03-10
Ok, I made a new administrator account(I tested that sudo works and stuff). I don't think I'll be able to recover those files, but I'll be able to use this new account instead. Thank you everyone for all your help with this. I still don't know how to mark this as solved(someone sent a forum link about it, but it didn't help much), but I think that's it then.

---

### Post by kuifje09 on 2013-03-11
Well I wish you good luck recovering your accounts and the encrypted filesystems.
I found a nice piece of documentation about ecryptfs  : [ECryptfs]("https://wiki.archlinux.org/index.php/ECryptfs#Setup_.28in_detail.29")
So if the crypted filesystem is still there, you should find the .Private filesystem.

I am very curious if you had some luck in recovering.

---

