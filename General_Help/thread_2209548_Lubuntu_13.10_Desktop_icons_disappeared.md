---
title: "Lubuntu 13.10: Desktop icons disappeared"
date: 2014-03-06
forum: General Help
---

### Post by eliezer2 on 2014-03-06
I am a new user of Lubuntu running lubuntu 13.10.
I have used lubuntu only for about 1 month.
Suddenly yesterday after lubuntu booted up, all my icons disappeared and I got the message "the specified directory is not valid.(attached)

[ATTACH=CONFIG]250889[/ATTACH]

When I open the PCManFM file manager and I clicked on desktop, the folder name looks wiered. 
[ATTACH=CONFIG]250892[/ATTACH]
I tried restarting the computer and then I had the contents of my home folder on the desktop (i.e Documents, Downloads, Pictures etc.)
I restarted again and now again there was nothing on the desktop(just like the first image)
Even if I add a new shortcut to my desktop, it disappears on the next reboot.
I can runn all the softwares without any problems.

---

### Post by pixel2 on 2014-03-06
1. Reinstall lubuntu, or
2. issue apt-get clean. or
3. go to /etc/lightdm/lightdm.conf and add sth like:

X: <path_to_X> ignore DTT /dev/usb01,

or
4. Switch to Debian.

I'd recommend last one.

---

### Post by mörgæs on 2014-03-06
When giving advice please keep focus on the problem in question. 

1) is last resort
2) does not change anything on the desktop environment
3) something about USB - why?
4) your personal preference is not what original poster is requesting.

If you don't know the problem it's better to wait for someone who does.

---

### Post by eliezer2 on 2014-03-06
Hi [**[COLOR=#000000]pixel2[/COLOR]**]("http://ubuntuforums.org/member.php?u=1908952"),
I love lubuntu and plan to stick to it.
I would prefer a solution to my problem so that if something like this happens again, I can fix it without depending on the community. 
Reinstalling will be my last resort because I might have to face broblems like this again and I cant keep reinstalling always. 
I believe there might be a fix to this.

---

### Post by Rex Bouwense on 2014-03-06
This is indeed weird.  Would you please check the log-in page to insure that you are booting into Lubuntu (and not Openbox, LXDE, or some other option).  It is unlikely but just check to see that Lubuntu is checked for log-in.  It can be found by clicking the icon in the upper right hand corner of the screen.

---

### Post by eliezer2 on 2014-03-07
When I installed lubuntu I set it not to ask password at startup so I don't have an option to check it that way.  But when I logged out then I got the log-in screen and lubuntu was the selected option.

Also sometimes I get this error.
[ATTACH=CONFIG]250927[/ATTACH]

I wonder if it has something to do with the desktop folder's permissions.
Thanks.

---

### Post by Rex Bouwense on 2014-03-07
Could you share the details with us?  They might lead to the crux of the problem.

---

### Post by eliezer2 on 2014-03-08
Can you please tell me what details you want. Is it the details in the error window? I'llgive those details the next time I get the error. I should have copied it when I got the error erlier.
Also whant to add something to the first post. Actually I found that when I add a new shortcut to the desktop, it doesn't disappear but it makes a shortcut in the "/home/user" folder. 
Also now when I click on desktop in the file manager, the name has changed to this:
[ATTACH=CONFIG]250950[/ATTACH]
What is the actual name that should have been instead of these characters?

---

### Post by bapoumba on 2014-03-08
Would you be using any particular desktop theme or fonts ? If so, please try with the default ones.

---

### Post by eliezer2 on 2014-03-08
> **bapoumba said:**
> Would you be using any particular desktop theme or fonts ? If so, please try with the default ones.

No I havent changed any fonts or themes.

---

### Post by bapoumba on 2014-03-08
Please hit **Alt-F2** and run **lxterminal**, you'll be in your /home. Then run **ls**. Are the folder names, and the Desktop one in particular, displaying correct names or not ?

---

### Post by eliezer2 on 2014-03-08
I did that and it showed me only these folders:

Documents, Downloads, Music, Pictures, proxy, Public, Templates, thumbs, titles, Videos, VirtualBox VMs

The last one I think was created by VirtualBox.

There is no desktop folder.

Thanks for the help all of you.

---

### Post by eliezer2 on 2014-03-08
Today I got an error saying"Sorry, Ubuntu 13.10 has experienced an internal error" And it has a huge list of details. I dont know how to copy them.
And like before in the first post, all the icons in the home directory appeared on the desktop after the error

---

### Post by bapoumba on 2014-03-08
What you could try :

1- Make a new desktop folder. Open lxterminal, make sure you are in your /home folder (prompt should be something like <your_user>@<your_machine>:~$) and run :
```
mkdir Desktop
```
When you run **ls**, the Desktop folder should be in blue (a directory).

2- Now open .config/user-dirs.dirs :
```
nano .config/user-dirs.dirs
```

and make sure it looks like this :
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

You can edit the file accordingly, save it with <ctrl-o> (letter o) and exit with <ctrl-x>. If your file is ok, just exit nano.

3- Log out and log back in.

---

### Post by eliezer2 on 2014-03-08
@**bapoumba**,
It worked perfecly. Thank you very much.
I lost all my previous files that were there on my desktop but thats fine. I didn't lose anything very important except a text file containing some simple terminal commands that I was learning to use.
I am very happy to have my lubuntu back in shape.

**@Rex Bouwense**
 Thank you very much for your support.

I have marked this thread as solved.

---

### Post by bapoumba on 2014-03-09
Thanks for marking the thread solved and glad to see you fixed it.

If you can navigate to the borked Desktop file, you may be able to move your files to the new one. No sure the old Desktop is browsable if the ls command you ran yesterday did not show it up.
Not sure either how and why it got renamed to something the system could not see, even as a regular file. Looks to me like a borked character encoding, not UTF-8, thus my first question about fonts or themes :)

Cheers!

---

### Post by eliezer2 on 2014-03-16
Hi bapoumba,
Today I found my old "Desktop" folder in the "Pictures" folder. I somehow didn't notice it before. Maybe I accidentally dragged the desktop folder into the pictures folder. I didn't lose anything anyway. All my old files are there.

---

### Post by bapoumba on 2014-03-16
Ah, that is possible. Good you did not loose anything :)

---

### Post by Theuinpo on 2014-04-12
Hi -- found this post after searching for solution to my problem. I am running Lubuntu and my desktop icons have disappeared also. But I have not lost the desktop folder -- all my files are there in File Manager but the icons just don't show on the desktop. I was playing around with trying to sort and snap to grid my desktop icons...all of a sudden most of them disappeared. I am not a veteran Linux user. Can anyone offer any suggestions? Thanks.

---

