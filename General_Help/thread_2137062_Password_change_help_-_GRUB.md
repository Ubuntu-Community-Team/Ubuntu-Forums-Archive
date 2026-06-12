---
title: "Password change help - GRUB"
date: 2013-04-19
forum: General Help
---

### Post by CB07 on 2013-04-19
Hiya. We are having some issues when trying to reset a lost password of some computers we've been given that run Ubuntu (that not even the person who donated them seems to know)

So I have gone to drop root shell prompt after clicking recovery mode in GRUB. That is all fine.

This seems to be the issue.

The main admin account for one computer has the admin user as Vision2 (note the lack of space) when I enter after clicking "drop root shell prompt" "passwd Vision2" I get "enter new UNIX password" and all is well. The password changes.

However, when I do this to a different computer with the user Vision 5 (note the space) and enter "passwd Vision 5" (note the space) I get a list of options such as "-d,  --delete" that we have know idea how to select (need something typed to do).

If I type "passwd Vision5) (no spaces this time) it doesn't recognize it, same if I make the "vision" all lower case.

So, simply put, does anyone know the single user code for the space, or knows how I can get to "Enter new UNIX password" for the Vision 5 user.

Apologies if this is in the wrong thread. Just took a guess that it was pretty general :P

Cheers.

---

### Post by oldfred on 2013-04-19
I have seen quotes and \040 used. But I thought user name & passwords could not have spaces.

Eample I have seen was mounting a Windows folder with spaces.
 /mnt/windrv/Documents\040and\040Settings /home/Documents\040and\040Settings none bind 0 0


 [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
[http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges](http://askubuntu.com/questions/140513/how-can-i-regain-admin-privileges)

---

### Post by grahammechanical on 2013-04-19
This might help
[http://www.computerhope.com/unix/upasswor.htm](http://www.computerhope.com/unix/upasswor.htm)

I think that in the command "passwd Vision 5" the number 5 is being interpreted as a command argument and as it is an incorrect argument you are being shown a list of correct arguments. For example "passwd Vision -d" would delete the password for the name "Vision"

Not much help but may be a little more understanding. You might try the -f argument. According to that link it is supposed to force the user to change the password at the next login by expiring the password for the name.

```
passwd Vision 5 -f
```

I think that it is correct that we cannot have spaces in a password but you have a space in a username (Vision 5) and may be that is acceptable.

Regards.

---

### Post by ajgreeny on 2013-04-19
It may be easier, once you have the first user running as the admin user, to change the **vision 5** username to something without a space, though like oldfred, I did not think it was possible to have a username with a space.

You could even make a new user with another username, and simply copy all the home contents across to the new username, then delete the **vision 5** user.

---

### Post by steeldriver on 2013-04-19
Well I had a quick play, it seems both adduser and useradd reject the name - but if it is shoehorned into /etc/passwd then other tools accept it, you just need to backslash escape the space (quoting works as well i.e. "Vision 5")

```
steeldriver@steeldriver-VirtualBox:~$ [COLOR=#0000ff]**sudo adduser Vision\ 5**[/COLOR]
adduser: To avoid problems, the username should consist only of
letters, digits, underscores, periods, at signs and dashes, and not start with
a dash (as defined by IEEE Std 1003.1-2001). For compatibility with Samba
machine accounts $ is also supported at the end of the username
steeldriver@steeldriver-VirtualBox:~$ 
steeldriver@steeldriver-VirtualBox:~$ [COLOR=#0000ff]**sudo useradd Vision\ 5**[/COLOR]
useradd: invalid user name 'Vision 5'
steeldriver@steeldriver-VirtualBox:~$ 
steeldriver@steeldriver-VirtualBox:~$ [COLOR=#0000ff]**echo 'Vision 5:x:1001:1001:Vision 5,,,:/home/Vision 5:/bin/bash' | sudo tee -a /etc/passwd**[/COLOR]
Vision 5:x:1001:1001:Vision 5,,,:/home/Vision 5:/bin/bash
steeldriver@steeldriver-VirtualBox:~$ 
steeldriver@steeldriver-VirtualBox:~$ [COLOR=#0000ff]**id Vision\ 5**[/COLOR]
uid=1001(Vision 5) gid=1001 groups=1001
steeldriver@steeldriver-VirtualBox:~$ 
steeldriver@steeldriver-VirtualBox:~$ [COLOR=#0000ff]**sudo passwd Vision\ 5**[/COLOR]
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
steeldriver@steeldriver-VirtualBox:~$ 

```

Personally if I "inherited" computers I'd copy any important data off them and then do a clean install though

---

### Post by CB07 on 2013-04-21
@grahammechanical sounds logical. Gives me one option.

@Aj - what I plan to do. Once I'm in with the password and can change it. Keep it nice and simple to change stuff in the future for anyone else.


@steeldriver - Again same with graham. Makes sense and I'll take a look. And yeah, problem was I didn't do any work on these. They were inherited and then someone else set them up with Ubuntu installed (does this stuff for a living so makes sense.), so presumably, he has copied any data. Somehow though, he and no one else can seem to get in as there is a password (despite claims there isn't. It may well be that the five* I see by it are standardly put there and there indeed isn't a password and I've wasted yours and my time. Yet that would seem weird if I'm getting a password prompt.


I'll try this stuff anyway so I will let you guys know. The PCs are for a Youth Cafe so I'll only be able to try this when I'm next helping out and have access to them on Wednesday. Expect a few more threads probably as well with fresh issues. Not used to Linux. :p

---

