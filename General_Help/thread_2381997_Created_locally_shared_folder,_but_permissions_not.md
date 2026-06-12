---
title: "Created locally shared folder, but permissions not working correctly"
date: 2018-01-07
forum: General Help
---

### Post by LtTuvok on 2018-01-07
I created locally a family share, but there is something wrong with the persmissions. I started with the following

- created a user group family and added members
- I entered the following commands.:
mkdir /usr/local/share/familie
cd /usr/local/share/familie
sudo chmod 2770 .
sudo chgrp familie .
umask 002

The permissions did not work well thus I added umask 002 to the ~/.profile folder. Using terminal copying, editing and deleting files and folders with different accounts work well. When I create files and folders using Gnome the following permissions are set. drwxr-sr-x 2 patrick familie 4096 which gives problems with other accounts.

I searched on the Internet so find how to set umask 002 for the Gnome environment. I tried serveral suggestions but nothing works. Has anyone had this issue as well and solved it? I hope anyone van help me with this.


Is this the correct way to create a shared folder where all family members can save and edit files and create and modify folders?

---

### Post by TheFu on 2018-01-08
The default umask for all accounts on Ubuntu is 002.  If a GUI isn't honoring the g+s on a directory, then the issue is with the GUI.  

Can you please create another directory using the steps you've outlined above and post the **ls -al** for it **before** using any GUI?  Also the output from the 'id' command for each userid would be good.  Just checking, though it does read like you did everything correctly.

You want```
 drwxrwsr-x 2 patrick familie
```
That would be 775 and g+s.

---

### Post by Morbius1 on 2018-01-08
Are we talking about Ubuntu 17.04 / 17.10?

It's a bug. Well ... Mr Poettering says it's not a bug so it must not be. Some blame systemd. Some blame Gnome. Some blame gdm. Let's just say any attempt to change it based on the documented ways we have changed it in the past do not seem to work:

Here's some links - there are many many more: 
[https://bugzilla.gnome.org/show_bug.cgi?id=780622](https://bugzilla.gnome.org/show_bug.cgi?id=780622)
[https://github.com/systemd/systemd/issues/901](https://github.com/systemd/systemd/issues/901)
[https://github.com/systemd/systemd/issues/6077](https://github.com/systemd/systemd/issues/6077)

Maybe someone has found a workaround for this but until then you might consider the following:

Install bindfs:
```
sudo apt install bindfs
```
Do a temporary remount of your folder:
```
sudo bindfs -o force-group=familie,perms=0660:ug+D /usr/local/share/familie /usr/local/share/familie
```
[COLOR=#0000cd]*Note: that looks like a typo but it's not. You are mounting a "view" of the familie folder onto itself with a completely different set of permissions.*[/COLOR]

If that does what you want you need to have this done at boot time. Back in the olden tymes you could just add the line ( without sudo ) to /etc/rc.local but ... um ... well ... um ... there is no /etc/rc.local any more because Mr. Poettering doesn't like it. You could create your own systemd rc.local service if you want or just add a line to the end of /etc/fstab. 

The syntax in fstab changes just to confuse folks:
```
/usr/local/share/familie /usr/local/share/familie fuse.bindfs force-group=familie,perms=0660:ug+D 0 0
```

**[COLOR=#0000cd]NOTE[/COLOR]**: There is another way around all of this. Stop using Ubuntu and start using Xubuntu. The default umask in Xubuntu 17.04 / 17.10 is 0002 just as < fill in the name of your personal deity > intended.

---

### Post by LtTuvok on 2018-01-08
Hi TheFu,

The newly created folder have the following persmission:
drwxrws---  2 root familie 4096 jan  8 14:52 .
drwxr-xr-x 11 root root    4096 jan  8 14:52 ..

The Id's are the following:
UID=1002(patrick) GID=1002(patrick) groepen=1002(patrick),1005(familie)



UID=1003(balbina) GID=1003(balbina) groepen=1003(balbina),4(adm),20(dialout),24(cdrom),25(floppy),26(tape),29(audio),44(video),46(plugdev),110(netdev),118(lpadmin),121(scanner),128(sambashare),1005(familie)

---

### Post by TheFu on 2018-01-08
Well, that means the OS is working correctly.  Look for Gnome to be the problem.  BTW, please use "code tags" for all output so things line up. I've edited my first reply with them to show.  Also, it is best to show the command run and all options too.  Long-time users and beginners sometimes make mistakes that are easily seen by others. I do all the time. ;)

---

### Post by LtTuvok on 2018-01-08
Nice, good tips for future threads. Do you have any suggestions to get started looking in Gnome?

---

### Post by TheFu on 2018-01-08
> **LtTuvok said:**
> Nice, good tips for future threads. Do you have any suggestions to get started looking in Gnome?

Sorry, no. I don't use DEs or GUIs for file management.

---

### Post by QIII on 2018-01-08
@LtTuvok --

Would you please translate the Dutch paragraph to English?  This is an English-speaking area of the Forums.

Thanks!

---

### Post by LtTuvok on 2018-01-08
This is a nice workaround for me, I will give it a try. Meanwhile I'll keep looking for a permanent solution in Gnome

---

