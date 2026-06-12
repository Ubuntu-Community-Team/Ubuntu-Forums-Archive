---
title: "Ubuntu 17.10 Authentication Error on Login"
date: 2017-12-16
forum: General Help
---

### Post by dhersam1 on 2017-12-16
Hello Ubuntu forums,

I just upgraded from 17.04 to 17.10. This was on my Dell xps13 laptop, partitioned between win10 and ubuntu. I am able to boot Ubuntu as normal and now see the 17.10 login screen, but when I click my username the password box pops up with text stating "authentication error" and immediately jumps to the following page which I've taken a picture of. 

[ATTACH=CONFIG]277858[/ATTACH]

I am still able to access recovery mode but have not been able to successfully boot console mode from the Ubuntu login screen. Maybe this is a root user or permissions related issue? Has anyone faced this issue before? Thanks

---

### Post by hansdown on 2017-12-17
Welcome to the forum, 
dhersam1.

Does the screen progress past the point in the picture you have submitted?

How did you upgrade?

---

### Post by dhersam1 on 2017-12-17
I upgraded to 17.10 from 17.04 just by using the graphical system updater.

And no, the screen does not progress past the point that is imaged. I am able to click on my username at the very first screen on startup, but on the next screen I am unable to add a password, the authentication error is onscreen, and the system quickly jumps to what I have imaged. I am also unable to enter console mode at that point, I believe it's ctrl-alt-F1

---

### Post by dhersam1 on 2017-12-20
Update: I have been accessing the root shell in recovery mode to try to diagnose this problem. When running any command in that shell I get the "authentication token manipulation error". I can fix that by entering [I]mount -o remount,rw / 

[/I]After that I can reset my password with* passwd <username>, *but ultimately am unable to login to the 17.10 home screen.

---

### Post by #&amp;thj^% on 2017-12-20
"Sometimes" this works for login loops.
When you get to the login screen....Don't Login>>> try to access a TTY2 console by using the keyboard combo **<ctrl+alt+F2>**
Enter your user name and password....Then run
```
startx
```
If it dose not work, try to remember the errors from the output. Or take a picture.(Not the best method to show errors though)

---

### Post by gabev on 2018-02-03
I've got exactly the same error.I was unable to fix it with above solutions. In what /var/log/ file here should we look for errors ?

---

### Post by rahulmawari on 2018-02-26
I am also facing the same problem.
When it was upgrading .... It asked me to remove phpmyadmin and i don't want it .So,I stopped removing phpmyadmin.
Other than this i didn't interrupt upgrading process.

---

### Post by #&amp;thj^% on 2018-02-26
This will sound and very well might be overkill, but with the handful of users having the same in-ability to reach a desktop session, I decided to install 17.10 again and leaving the software repository's just the way they were when installed.**(No Changes were made.)**
**And NOTE:** NO Graphic Drivers installed yet. (Only what was installed with the installation.)
I finally was greeted with the same problem of not reaching a Desktop session.
And this is what worked for my setup. **(Your Mileage may vary)**

```
sudo add-apt-repository "deb http://archive.ubuntu.com/ubuntu $(lsb_release -sc) universe"
```

```
sudo apt purge --auto-remove gdm3
sudo apt purge --auto-remove gnome-shell
sudo apt purge --auto-remove gnome-software
sudo apt purge --auto-remove lightdm
sudo apt purge --auto-remove gnome-session-bin 
sudo apt purge --auto-remove gnome-session-common 
sudo apt purge --auto-remove ubuntu-session
sudo apt purge --auto-remove ubuntu-desktop
```
**Might be wise to take note of what else is being removed.**
Now I ran:

```
sudo apt update
sudo apt upgrade 
sudo apt install ubuntu-desktop
```

Rebooted, Bam! back to a working Desktop! 
May the Force be with you! ;)

---

### Post by rahulmawari on 2018-02-27
Thanks for your help.
I did the same as you explained.
But when i tried to install ubuntu-desktop
 I get the message



```

The following packages have unmet dependencies:
ubuntu-desktop : Depends: ubuntu-session but it is not going to installed

E:Unable to correct problems, you have held broken packages
```

and then when i reboot 
i get 
```

/dev/sda7: recovering journal
/dev/sda7: clean , 491291/5234688 files,4726990/20911616 blocks
```

---

### Post by #&amp;thj^% on 2018-02-27
> **rahulmawari said:**
> Thanks for your help.
I did the same as you explained.
But when i tried to install ubuntu-desktop
 I get the message



```

The following packages have unmet dependencies:
ubuntu-desktop : Depends: ubuntu-session but it is not going to installed

E:Unable to correct problems, you have held broken packages
```

and then when i reboot 
i get 
```

/dev/sda7: recovering journal
/dev/sda7: clean , 491291/5234688 files,4726990/20911616 blocks
```

Post the return of:
```
sudo apt -f install
```

---

### Post by rahulmawari on 2018-02-27
I tried that too but no good result.
Still showing the same when try to install ubuntu-desktop.

Should not I install ubuntu-session ?

After running command

```

sudo apt -f install

```

I got message 

0 upgrade ,0 newly installed,0 to remove ,and 0 not upgraded

---

### Post by #&amp;thj^% on 2018-02-27
Yep that was next:
```
sudo apt install ubuntu-session
```

---

### Post by rahulmawari on 2018-02-27
After running   install ubuntu-session
I got this error


After running 
sudo apt update --fix-missing 
I got this



I am doing this from my mobile phone 
So,sorry for any mistake.

---

### Post by #&amp;thj^% on 2018-02-27
> **rahulmawari said:**
> After running   install ubuntu-session
I got this error


After running 
sudo apt update --fix-missing 
I got this



I am doing this from my mobile phone 
So,sorry for any mistake.

No worries! :)
You have to clean up your sources you have at least one configured multiple times, but that should not stop progress on what we are working on.
I have no solution right now, I need to test some things, give me some time here.:)

---

### Post by deadflowr on 2018-02-27
Are you trying from Recovery Mode?

---

### Post by rahulmawari on 2018-02-27
Ok and thanks for your help.

---

### Post by rahulmawari on 2018-02-27
Yes ,I am doing all of this from recovery mode.

---

### Post by deadflowr on 2018-02-27
Then you need to choose the recovery mode option Enable Networking.
This not only allows you to download the packages, but also resets the file system to read/write.
The default recovery mode is set as read-only.

---

### Post by rahulmawari on 2018-02-28
I chose enable networking.
I got error message
```

grep: /etc/resolv.conf: No such file or directory 

```

There is a resolv.conf file in etc but in red color.

I tried to solve this by reading other ubuntu forms .I got one ,But to solve this i need DNS and i don't know what is my DNS .
Command like nm-tool and ifconfigure didn't work.

I am reading other ubuntu forms  . I will let you know if i could find anything.

---

### Post by deadflowr on 2018-02-28
Did you try guber2's thread: [https://ubuntuforums.org/showthread.php?t=2378817]("https://ubuntuforums.org/showthread.php?t=2378817")

Note you need to put your own device in the line so use 
```
ifconfig
```
To find it.
Yours should be listed at the top.

---

### Post by divyab on 2018-04-17
Thanks for your help
I had a same problem.
I did as per your description and now ubuntu login issue has been resolved.

---

