---
title: "sudo commands don't work in Ubuntu 14.04 LTS"
date: 2014-04-29
forum: General Help
---

### Post by michael146 on 2014-04-29
Hi. I have a Dell Inspiron 1525 running Ubuntu 14.04 LTS. I'm new to Ubuntu, and it was easy to get used to. I ran into a problem about a couple weeks after installing it. I had figured out how to use "sudo" commands. However, what always worried me was that it always gave me an error message, but whatever i was trying to do still seemed to work. then,i was trying to set up xscreensaver, and i used a sudo command. it came up with this message:

[FONT=courier new]sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'[/FONT]
[FONT=courier new]sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner[/FONT]
[FONT=courier new]sudo: fatal error, unable to load plugins[/FONT]

and since then, no matter what i tried, "sudo" commands just don't work.I've tried looking up tutorials & stuff, but I either don't understand it, or there's nothing on it. If anyone knows how to fix this, please help me! :(

---

### Post by jbaerboc on 2014-04-29
Hmm it does work on my 14.04 install. Not sure how to help you fix it but a way around the problem temporarily would be to use su. So when in your terminal you type su then your password and from then on the terminal is in root mode. Once you exit the terminal if you were to go back in you'll be back to normal user mode.

---

### Post by papibe on 2014-04-29
Hi michael146.

It looks like you created a custom /etc/sudo.conf file, and it has a syntax error. Since you don't need one to run sudo I'd recommend booting into recovery mode, get a root prompt and rename the file:
```
mv -iv /etc/sudo.conf /etc/sudo.conf.old
```
Then reboot:
```
reboot
```
Let us know if you need more directions to solve this problem.
Regards.

---

### Post by Dane_Jorgensen on 2014-04-29
Had this same issue and it was from a typo in sudo.conf

---

### Post by michael146 on 2014-05-15
Tried this and any thing with the word "sudo" in it won't work. I don't have anything important on this computer, should I just do a full reset?

---

### Post by michael146 on 2014-05-15
I've already tried this, too. It just comes up w/ the same error.

---

### Post by steeldriver on 2014-05-15
Did you boot to recovery mode and rename the conf file like papibe suggested? you probably need to remount with read-write permissions first

```

# **mount -o remount,rw /**
# mv -iv /etc/sudo.conf /etc/sudo.conf.old

```

You don't need to precede these commands with sudo, since you will be in a root shell already

---

### Post by michael146 on 2014-05-16
It says 

" '/etc/sudo.conf' : no such file or directory"

---

### Post by steeldriver on 2014-05-16
Hmm... what are the permissions / ownership on the sudoers.so lib?

```
ls -l /usr/lib/sudo/sudoers.so
```

---

### Post by michael146 on 2014-05-16
It says:

-rw-rw-rw 1 root root 322096 Feb 10 13:16 /usr/lib/sudo/sudoers.so

---

### Post by steeldriver on 2014-05-16
OK well let's try to fix that and see if the other error goes away as well - in the recovery root shell,

```
chmod 644 /usr/lib/sudo/sudoers.so
```

which will make it read-only for everyone except the owner (root)

---

### Post by michael146 on 2014-05-17
Never mind I just reset my whole laptop and that fixed it. Thanks fortifying to help though.

---

### Post by michael146 on 2014-05-17
I mean for trying

---

### Post by Denis_Uyeda on 2014-07-17
Sorry for bringing this topic back...
But I just wanted to say that I had this problem too.

I solved it by changing /usr/lib/sudo/sudoers.so permission

First, log into root account
su

Insert root's password

Then change the file permissions. I did
chmod 755 /usr/lib/sudo/sudoers.so

Btw, I only had this problem because I accidentally changed the whole /usr/lib permissions... =\
Don't do this! I am having a lot of problems now.

But for this sudo problem, changing the sudoers.so permissions worked fine for me

---

### Post by Sydney_Warner on 2014-12-28
I too am having an issue with this. I did the same thing as Denis.

> **steeldriver said:**
> OK well let's try to fix that and see if the other error goes away as well - in the recovery root shell,

```
chmod 644 /usr/lib/sudo/sudoers.so
```

which will make it read-only for everyone except the owner (root)

```
sudo: error in /etc/sudo.conf, line 0 while loading plugin `sudoers_policy'
sudo: /usr/lib/sudo/sudoers.so must be only be writable by owner
sudo: fatal error, unable to load plugins
```

Unfortunately, I can't access the sudo command to fix the sudo commmand. The particular file also needs root permission to open and edit it, however, I can't access root, I never set a password for it, so I am locked out... Is there a way to manually configure the file(s) sudo.conf or sudoers.so file? I'm going to reinstall, but I'm more than likely going to run into this problem again. 

Update: Recovery option did not work, same error is given. Upon looking at the file itself, "others" seems to still have read and write permission. Did not reinstall yet.

---

### Post by Sydney_Warner on 2014-12-28
> **steeldriver said:**
> OK well let's try to fix that and see if the other error goes away as well - in the recovery root shell,

```
chmod 644 /usr/lib/sudo/sudoers.so
```

which will make it read-only for everyone except the owner (root)

Okay, so, I got it! I poked around and found I ha to remount the drive to do anything ([http://askubuntu.com/questions/91188/authentication-token-manipulation-error](http://askubuntu.com/questions/91188/authentication-token-manipulation-error)) while trying to change the root password. took a bit of poking around, but:
From root menu in recovery mode:

```
mount -rw -o remount /
passwd root
#enter your password twice
exit
```

Then I exited, booted, and from terminal:

```
sydney@dragonsden:~$ su
Password: 
root@dragonsden:/home/sydney# cd
root@dragonsden:~# chmod 644 /usr/lib/sudo/sudoers.so
```

To save time, or if you already know of the legend of the root account, then you could probably just do it from recovery. Sorry if I'm repeating you all, but in case another person like me who needs it spelled out comes along, it's here.

Now I have to figure out how to exit the root account safely. Thanks for your help guys! I'm a newbie at this, so this is really exciting to me.

---

### Post by steeldriver on 2014-12-28
You should be able to exit the root shell just by typing 

```

exit

```

It should return you to the recovery mode menu, from which you can choose to continue to boot normally

---

### Post by james_king2 on 2015-01-04
I got here through a search so, I am not certain if I should ask a question or not. If nothing else please point me in to the proper area. 
What I seem to be running into when I use a sudo command in Ubuntu 14.04.1 LTS is it just continually asks me for a password. The cusor blinks for a few seconds then goes to a solid block and not blinking. First, I haven't setup a pass word in Terminal and don't know the reasons it is asking for one. The next problem is even it I try to type in my system sign-on password, no text gets intered after the cusor. It is like it has shut down with no indication of anything being entered in by typing in anything on the keyboard. The only responce I get is if I hit return it will go blank for a second and on another line say sorry please try again.
The same thing happens even if I click and close the terminal and then reopen it. I am totally new at this and also totally stumped at what to try. I read most of the Unbuntu users manual but it doesn't address any of this. 
Thank you for any help in this situation, Jim

---

### Post by lisati on 2015-01-04
> **james_king2 said:**
> I got here through a search so, I am not certain if I should ask a question or not. If nothing else please point me in to the proper area. 
What I seem to be running into when I use a sudo command in Ubuntu 14.04.1 LTS is it just continually asks me for a password. The cusor blinks for a few seconds then goes to a solid block and not blinking. First, I haven't setup a pass word in Terminal and don't know the reasons it is asking for one. The next problem is even it I try to type in my system sign-on password, no text gets intered after the cusor. It is like it has shut down with no indication of anything being entered in by typing in anything on the keyboard. The only responce I get is if I hit return it will go blank for a second and on another line say sorry please try again.
The same thing happens even if I click and close the terminal and then reopen it. I am totally new at this and also totally stumped at what to try. I read most of the Unbuntu users manual but it doesn't address any of this. 
Thank you for any help in this situation, Jim

You are being asked for a password because prefixing a command line with "sudo" is one way of temporarily elevating user privileges to that of the Ubuntu equivalent of the Administrator account in Windows. If you're using the user account created during installation of Ubuntu, you should be able to use the same password as the one associated with your login. Don't panic if it doesn't show while you're typing, that's normal, and your password should be accepted.

More information can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by james_king2 on 2015-01-05
Thanks, I did try my pass word /s but it still produces an error. I will check out the information given and see what happens, Jim

---

