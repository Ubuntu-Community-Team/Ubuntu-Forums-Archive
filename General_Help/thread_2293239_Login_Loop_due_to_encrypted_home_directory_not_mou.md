---
title: "Login Loop due to encrypted home directory not mounting"
date: 2015-09-03
forum: General Help
---

### Post by RichDavey on 2015-09-03
Hi there,

I am having trouble logging on to Xubuntu - I get the login loop and can only login as a guest. I've tried booting into recovery to change the password and have also tried the .Xauthority in terminal but still no joy. I am a relative novice with Ubuntu and am not sure what needs to be done to fix it.
Any help at all will be greatly appreciated!

Many thanks,
Rich

---

### Post by Bashing-om on 2015-09-03
RichDavey; Hi !

The 2 more prevalent causes are
A loss of authorization to access your /home.
Do you own the file in the /home directory ?
```

ls -al /home/
ls -al /home/<user_name>

```

And next is proprietary graphic's drivers . Look'n at in such a circumstance that a proprietary was in use, and in a system update that driver got broke.
In that instance we can purge and re-install the driver .

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RichDavey on 2015-09-05
hi Bashing-Om, thanks for your reply - I typed in the code you provided and am not sure how to tell if I own the file; the out put I got was:

> total 16
drwxr-xr-x 4 root root4096 sep 20 2014 .
drwxr-xr-x 22 root root 4096 aug 29 18:07 ..
drwxr-xr-x 3 root root 4096 sep 20 2014 .ecryptfs
dr-x------ 2 rich rich 4096 sep 20 2014 rich

and 

> total 8
dr-x------ rich rich 4096 sep 20 2014.
drwxr-xr-x 4 root root 4096 sep 2014 ..
lrwxrwxrwx 1 rich rich 56 sep 20 2014 access your private data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
lrwxrwxrwx 1 rich rich 30 sep 20 2014 .ecryptfs -> /home/.ecryptfs/rich/.ecryptfs
lrwxrwxrwx 1 rich rich 29 sep 20 2014 .private -> /home/ .ecryptfs/rich/.private
lrwxrwxrwx 1 rich rich 52 sep 20 2014 readme.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt


Not sure if that tells you anything!

---

### Post by Bashing-om on 2015-09-05
RichDavey; Yeah ;

That output does tell us that "you" are authorized to access your /home - maybe. We can rule that out as a possible cause.
But the output also raises another possibility - .ecryptfs - that is encryption is a factor here. Now encryption requires a separate /boot partition, and many times we find that that partition is filled to capacity and a new kernel does not install properly.
I do not know encryption & not totally sure, as I expect to also see that "you" own .Xauthority and .ICEauthority files ( authorization). As in my example:
```

-rw-------  1 sysop sysop    2608 Sep  5 13:33 .ICEauthority
-rw-------  1 sysop sysop     209 Feb  4  2015 .Xauthority

``` where I am "sysop" .

To check for that probability of /boot partition constraints:
```

df -h
df -i
ls -al /boot

```

And lastly to look at the graphics situation:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```

[INDENT][INDENT]poke'n and alook'n
[/INDENT][/INDENT]

---

### Post by steeldriver on 2015-09-05
I'm not really familiar with the ecryptfs setup, but it seems odd to me that the home directory would not even be writeable by its owner - wouldn't that prevent decryption (as well as subsequent writes like .Xauthority)?

```

d[COLOR=#ff0000]r-x[/COLOR]------ 2 rich rich 4096 sep 20 2014 rich

```

---

### Post by Bashing-om on 2015-09-05
Oh steeldriver ;

> **steeldriver said:**
> I'm not really familiar with the ecryptfs setup, but it seems odd to me that the home directory would not even be writeable by its owner - wouldn't that prevent decryption (as well as subsequent writes like .Xauthority)?

```

d[COLOR=#ff0000]r-x[/COLOR]------ 2 rich rich 4096 sep 20 2014 rich

```

What sharp eyes
[INDENT][INDENT][INDENT]you have :)
[/INDENT][/INDENT][/INDENT]

---

### Post by RichDavey on 2015-09-09
Hi there,
Sorry for the delay in replying; I tried the code that Bashing-Om posted: df -h, df -I, ls -al /boot. The output was vast and (as I am using another laptop) I couldn't copy it all out to post here. I also tried the graphics code, but that didn't seem to do anything. 
Anything else that I could try? Or. if all else fails, is there a way to uninstall Ubuntu completely so I can try re-installing it or another OS?
Thanks for your help so far!
Rich

---

### Post by Bashing-om on 2015-09-09
RichDavey; Hey ;

We work at your pace. keep in mind a (RE-)install is the nuclear solution, and is not advocated. Given time and effort 'buntu is always fixable.
Just keep in mind that I am not familiar nor experienced with the complexity that encryption entails.
Boot to a terminal and then ->
We can obliterate the transfer of information problem ! We do have a tool to handle the condition of " The output was vast and (as I am using another laptop) I couldn't copy it all out to post here. : The solution is :
```

sudo apt-get install pastebinit

```
which installs the tool to xfer files to our pastebin site, from which we can access.
Presently as steeldriver notes is the access rights to your /home.
Let's look once more at what is presently:
```

ls -al /home/ | pastebinit

```
The result is a URL returned to your terminal. Pass that link back here to the thread and we access the site/file to read what was sent.

For the other requested outputs, one can do a number such as:
```

df -h > stuff-txt
df -i >> stuff-txt
ls -al /boot >> stuff-txt
cat stuff-txt | pastebinit

```
Where we redirect the commands outputs to a file and xfer this file to the bin site.

[INDENT][INDENT]it's buntu
[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by RichDavey on 2015-09-20
Hi there,

Have managed to get the Pastebinit installed:

the output from ls -al /home/ can be found here: [http://paste.ubuntu.com/12506291/](http://paste.ubuntu.com/12506291/)

df -h: [http://paste.ubuntu.com/12506392/](http://paste.ubuntu.com/12506392/)
df -I:[http://paste.ubuntu.com/12506406/](http://paste.ubuntu.com/12506406/)
ls -al /boot: [http://paste.ubuntu.com/12506416/](http://paste.ubuntu.com/12506416/)
lspci -vnn | grep VGA -A 12: [http://paste.ubuntu.com/12506464/](http://paste.ubuntu.com/12506464/)
sudo lshw -C display: [http://paste.ubuntu.com/12506492](http://paste.ubuntu.com/12506492)

Hope this helps and isn't too much of an information overload!
Many thanks again,
Rich

---

### Post by Bashing-om on 2015-09-20
RichDavey; Ouch .....

You have encrypted the file system:
> 
drwxr-xr-x  3 root root 4096 Sep 20  2014 .ecryptfs

I have no experience in this realm and do not know how to proceed.

We can rule out a graphics problem - though the GMA500 is a problem in and of it's self - as the driver is loaded and is in use.
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)
[http://ubuntuforums.org/showthread.php?t=1984236](http://ubuntuforums.org/showthread.php?t=1984236)
You might be able to tweak on it a bit and get some improvements - once the login issue is resolved.

Nor is the issue space constraints.

I am not too sorry to say I do not know
[INDENT][INDENT][INDENT]there are some things I do not want to know
[/INDENT][/INDENT][/INDENT]

---

### Post by RichDavey on 2015-09-22
Thank you for your reply and for all your help; is there any one who may be able to shed some light on how to unencrypt the file system (really have no idea how this even happened!).

---

### Post by Bashing-om on 2015-09-22
RichDavey; Welp;

I have been but a small amount of help in this matter as you still are not able to login .
As I have no interest in encryption, it follows that I do not know who else has the experience to guide.

You are doing proper, just hang in here and see who does respond in our time of need. Bump thus thread back to the top daily.

I will continue to watch.

[INDENT][INDENT]1 for all
[/INDENT][/INDENT]

---

### Post by RichDavey on 2015-09-24
Just bumping this to see if anyone can help with login / encryption issues

---

### Post by steeldriver on 2015-09-24
It sounds like the system is failing to decrypt and mount your private directory on login

Like Bashing-om, I don't use an encrypted home directory so I don't have any experience with fixing these things either

You may find some useful guides if you google ecryptfs-recover-private - there's some official Ubuntu documentation here --> [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory) but it may not be up to date (it seems to refer to Ubuntu 11.04 in places)

I'm sure there are people on this forum with ecryptfs experience however their eyes may not be caught by what appears to be 'yet another login loop' question - I've been criticized previously for suggesting it, but in cases like this IMHO it's justifiable to start a new thread focusing on the problem you've identified in this one e.g. "ecryptfs private directory failing to mount during login" - if you do so, please provide a link to this question for background.

Or you could change the title of your thread to include the encryption aspect specifically e.g. "Login Loop due to encrypted home directory not mounting"

---

### Post by RichDavey on 2015-09-25
Thanks for the info; have amended the thread as suggested. 

Can anyone help with this issue? Don't even recall encrypting the the home directory in the first place!
Kind regards,
Rich

---

### Post by RichDavey on 2015-10-02
bumping for any help

---

### Post by RichDavey on 2015-10-13
Can any one help me with a full system re-set / re-install / just wipe the whole fecking thing and start again? I know it's a "nuclear" option, but there's nothing worth keeping on hd so I don't mind losing anything - I can't use the laptop at the moment so am desperate to get it back into some semblance of working order. 
Many thanks,
Rich

---

### Post by Bashing-om on 2015-10-13
RichDavey; Welp;

Regrets there is no advisement to effect resolution to your situation.
To (RE-)install is no big deal .
Boot the install medium and choose "erase disk and install ubuntu" for a standard default install . The installer will do just that for a system running only 'buntu .
If I may .. IF you have no need of encryption ,... do not choose LVM and/or encryption options in this installer as it adds a level of complexity that in times of trouble may not be overcome.

You will be back up and operational in about 30 minutes.

[INDENT][INDENT]sometimes, it is the better course
[/INDENT][/INDENT]

---

### Post by RichDavey on 2015-10-16
Hi there, my next problem  that I've just discovered is that I cant get my laptop to boot from the usb - I've changed the boot options but it still does nothing

---

### Post by Bashing-om on 2015-10-16
RichDavey; Well ...

In that case, I would try and boot the liveUSB in a different box . Isolate to a problem with the liveUSB or in the boot configurations of this system.

[INDENT][INDENT]which way did he go, George
[/INDENT][/INDENT]

---

### Post by Jasper_HD on 2016-04-14
I also had this problem (could login as guest, not my regular sudoer user which just looped)

Here's how I fixed it (Ubuntu 15.10):
[LIST]
[*]At the login screen I switched to the terminal (CTRL + ALT + F1) (BTW: CTRL + ALT + F6 takes you back)
[*]I went down the avenue of trying to manually decrypt the home directory as all I could see was (Access-Your-Private-Data.desktop) and a readme.txt file.
[*]Using the command (ecryptfs-mount-private) I realised ecryptfs wasn't installed
[*]I suspected some libraries I installed to try and see a Windows network share, so I found recently packages installed ([http://askubuntu.com/questions/17012/is-it-possible-to-get-a-list-of-most-recently-installed-packages)sudo](http://askubuntu.com/questions/17012/is-it-possible-to-get-a-list-of-most-recently-installed-packages)sudo) awk '$3~/^install$/ {print $4;}' /var/log/dpkg.log
[*]I removed those packages - [http://askubuntu.com/questions/151941/how-can-you-completely-remove-a-package](http://askubuntu.com/questions/151941/how-can-you-completely-remove-a-package)
[*]I then created a new user via the terminal: [http://mixeduperic.com/ubuntu/how-to-add-a-new-user-in-ubuntu-using-the-command-line.html](http://mixeduperic.com/ubuntu/how-to-add-a-new-user-in-ubuntu-using-the-command-line.html)
[*]And added them to the root/sudo users: [http://mixeduperic.com/ubuntu/how-to-setup-a-user-or-group-with-sudo-privileges-on-ubuntu.html](http://mixeduperic.com/ubuntu/how-to-setup-a-user-or-group-with-sudo-privileges-on-ubuntu.html)
[*]I then rebooted and successfully logged into the GUI with the new root-level user.
[*]This enabled me to install the ecrypt library: *[COLOR=blue]sudo apt-get install ecryptfs-utils ([http://linuxpoison.blogspot.co.uk/2010/10/how-to-use-ecryptfs-cryptographic.html](http://linuxpoison.blogspot.co.uk/2010/10/how-to-use-ecryptfs-cryptographic.html))[/COLOR]*
[*]*[COLOR=blue][/COLOR]*[COLOR=blue][/COLOR]One reboot later and I could login to the GUI with my original user
[/LIST]

---

### Post by ruym on 2016-12-17
Hello had very similar problem with a new install, I was able to resolve as follows:
- At the login screen I switched to the terminal (CTRL + ALT + F1)
- Then created a new user via the terminal ->[https://goo.gl/YjAQPK](https://goo.gl/YjAQPK)
- Added user to the root/sudo users: -> [https://goo.gl/dGcfSb](https://goo.gl/dGcfSb)
- Then rebooted and successfully logged into the GUI with the new root-level user.
- Once logged in, clicked on the top right corner drop menu arrow.  
- Click on user drop down/account settings.
- Proceed it to create a new account with Administrator rights.
- Upon completion, reboot.

Everything works great after...  I hope it helps. Many thanks @mixeduperic.com for the great explanation on steps 1-3.

---

### Post by RichDavey on 2017-01-05
HI there,

Thanks for your suggestions.

I've tried booting into terminal and trying to add a new user but when I press ctrl alt F1 and get to a terminal from login screen, it just asks me for a login and password and then i can get no further.

Tried logging into the guest user and opening terminal there, but couldn't do anything there either.

Any other thoughts?

kind regards,
Rich

---

