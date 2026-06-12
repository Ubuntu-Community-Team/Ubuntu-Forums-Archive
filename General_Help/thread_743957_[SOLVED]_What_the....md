---
title: "[SOLVED] What the..."
date: 2008-04-03
forum: General Help
---

### Post by Kemono on 2008-04-03
I booted into Ubuntu today and all of the folders and files in my Home folder were on the desktop. I thought they were just links (shortcuts) and [COLOR="Red"]Shift+Delete[/COLOR]d them (bad habit. I know). I saw all kinds of files being deleted and canceled the process. Now I'm left with only 2 folders.

Is there a way to recover my folders and files?

Why did this happen?

---

### Post by erginemr on 2008-04-03
For the undelete, please refer to:
[http://ubuntuforums.org/showpost.php?p=4009745&postcount=7](http://ubuntuforums.org/showpost.php?p=4009745&postcount=7)
(I am sorry...)

---

### Post by erginemr on 2008-04-03
For the reason of your home folders showing up at desktop, please run: Alt F2 -> gconf-editor
and check that the key shown in the attached screenshot has not been enabled.

---

### Post by fela on 2008-04-03
unfortunately, files accidentally deleted on a ext3 partition are unrecoverable...:(

maybe this'll get you out of that bad habit though

---

### Post by Kemono on 2008-04-03
@erginemr, don't be. Most of the important data was in those remaining 2 folders.

@erginemr, it's unchecked.

@fela, hardly. I always delete the files I don't and won't need. I was just caught unprepared.

I was messing around with the .Trash folder yesterday. Could it be related to that?

EDIT: Oh yeah, I forgot. They're still on the desktop. How do I remove them without deleting them?

---

### Post by Delkster on 2008-04-03
Out of curiousity, if you go to a terminal, are those folders directly in your home folder (try "ls -l" or only in your desktop folder (try "ls -l Desktop")? Is there anything except Desktop in your home folder?

---

### Post by Kemono on 2008-04-03
> **Delkster said:**
> Out of curiousity, if you go to a terminal, are those folders directly in your home folder (try "ls -l" or only in your desktop folder (try "ls -l Desktop")? Is there anything except Desktop in your home folder?

```
narrator@NAPALM:~$ ls -l
total 12
drwxr-xr-x 5 narrator narrator 4096 2008-03-08 01:39 All Downloads
drwx------ 2 narrator narrator 4096 2008-04-03 12:24 amsn_received
drwxr-xr-x 4 narrator narrator 4096 2008-04-03 12:17 Documents
narrator@NAPALM:~$ ls -l Desktop
ls: Desktop: No such file or directory
narrator@NAPALM:~$ 
```

I don't know if that's what you mean?

---

### Post by danwood76 on 2008-04-03
create the Desktop directory again.
It wont be able to load your destkop without that folder.

```

mkdir ~/Desktop

```

---

### Post by Kemono on 2008-04-03
> **danwood76 said:**
> create the Desktop directory again.
It wont be able to load your destkop without that folder.

```

mkdir ~/Desktop

```

That's funny. The [COLOR="Blue"]Desktop[/COLOR] folder was the reason I was messing with [COLOR="Blue"].Trash[/COLOR]. I deleted the [COLOR="Blue"]Desktop[/COLOR] folder in my [COLOR="Blue"]Home[/COLOR] and every time I tried to empty the trash, it just kept coming back.

---

### Post by danwood76 on 2008-04-03
So you deleted the Desktop folder and wondered why your desktop suddenly became your home directory?
Hehe. ;)

That folder is necessary if you want a desktop seperate to your home dir.

---

### Post by Kemono on 2008-04-03
That's odd. I'm sure I created another [COLOR="Blue"]Desktop[/COLOR] folder. After I couldn't empty the trash or restore the folder, I figured it was important and created a new one.

EDT: The folders still won't go away.

---

### Post by erginemr on 2008-04-03
Did you try logging out and back logging in? Also checking that key in gconf-editor and unchecking it, followed by a logout/login may also have some effect.

---

### Post by Kemono on 2008-04-03
> **erginemr said:**
> Did you try logging out and back logging in? Also checking that key in gconf-editor and unchecking it, followed by a logout/login may also have some effect.

Nope. No effect. It isn't really that big of a deal. The new release is 21 days away. I can wait for it and reinstall my system (I'm a patient guy). I just wanted to know how to fix it in case it happens again (which I doubt since I'm not planning to delete any of the default folders again). There should be a notification message to warn users of such consequences (unless there is one and I missed it).

---

### Post by erginemr on 2008-04-03
> I can wait for it and reinstall my system (I'm a patient guy).
So am I persistent guy. ;) Before you let go of this, could you please post the output of the following two commands from the terminal? To give you an example, I have posted mine:

```
**cat ~/.config/user-dirs.dirs**

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/.Templates"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```


```
**echo $HOME**

/home/my_user_name
```

---

### Post by Kemono on 2008-04-03
```
narrator@NAPALM:~$ cat ~/ .config/user-dirs.dirs
cat: /home/narrator/: Is a directory
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"
```


```
narrator@NAPALM:~$ echo $HOME
/home/narrator
```

Well, uuumm...have fun?

---

### Post by erginemr on 2008-04-03
So, I guess you should first copy that file:
```
cp ~/.config/user-dirs.dirs ~/.config/user-dirs.dirs.mybackup
```
then edit it:
```
gedit  ~/.config/user-dirs.dirs
```
and replace the corresponding lines with the ones existing in mine:
```
...
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Desktop"
XDG_TEMPLATES_DIR="$HOME/.Templates"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

Logout and back in and see what happens. (Make sure that you have already created Desktop, .Templates, Documents, etc.)

---

### Post by Kemono on 2008-04-03
Sorry to take so long but I had to boot into Windows. Skype for Linux has been a pain in the *ss (the video disappears).

Well, **erginemr**...it worked. The folders are gone. Good to know where the paths are. Now I can hide the folders I don't want in my [COLOR="Blue"]Home[/COLOR] and point to their location in the **user-dirs.dirs** file. Unless I shouldn't?

---

### Post by erginemr on 2008-04-03
Great! Now, I am happy! :D

Yet I suggest you not to mess with the "user-dirs.dirs" file anymore, which is kind of important for the Gnome system.

Besides, you can hide files and folders easily by putting a dot (.) before their name. This is actually the way Linux hides config files in your home folder. You can check this case with:
```
ls ~
ls -a ~
```
where the second command will show all hidden files in your home directory. And inside Nautilus (Gnome's file manager), you can press Ctrl+H to show / hide hidden files and folders (i.e. those with a preceding dot.)

That's all I guess. So, have fun! ;)

---

### Post by erginemr on 2008-04-03
Ahh, one more thing... Please change the line for public share directory to:
```
XDG_PUBLICSHARE_DIR="$HOME/Public"
```

after creating the folder itself. I am not sure but the line:
```
XDG_PUBLICSHARE_DIR="$HOME/"
```
might compromise your security / privacy when you use file sharing programs such as amule, frostwire, etc. It is better to be safe than be sorry... ;)

---

### Post by Kemono on 2008-04-03
Yes, I know about the hiding stuff. But when I, for example, hide the [COLOR="Blue"]Desktop[/COLOR] folder by putting a "." in front of it, I have to let the system know where it is by putting a "." in front of "Desktop" in the **user-dirs.dirs** file. Isn't that right? Or am I wrong?

---

### Post by Kemono on 2008-04-03
> **erginemr said:**
> Ahh, one more thing... Please change the line for public share directory to:
```
XDG_PUBLICSHARE_DIR="$HOME/Public"
```

after creating the folder itself. I am not sure but the line:
```
XDG_PUBLICSHARE_DIR="$HOME/"
```
might compromise your security / privacy when you use file sharing programs such as amule, frostwire, etc. It is better to be safe than be sorry... ;)

Yeah, I thought something was missing.

---

### Post by erginemr on 2008-04-03
Hmm, this is correct on paper. Indeed, it will be a good experiment to hide ".Desktop" whereas it is supposed to show up on your desktop. :-k I'd say knock yourself out and keep us updated...

---

### Post by Kemono on 2008-04-03
Well, I made 2 launchers on the desktop and then put a "." in the [COLOR="Blue"]Desktop[/COLOR] folder. I didn't even have to update the **user-dirs.dirs** file. It updated itself automaticly. When I rebooted the icons were there (although not where I left them). So I guess it works.

Also, a new folder called "[COLOR="Blue"]file:[/COLOR]" was created in my [COLOR="Blue"]Home[/COLOR]. What's it for, anyway?

```
file:/home/narrator/Desktop
```

the [COLOR="Blue"]Desktop[/COLOR] folder is empty.

---

### Post by Delkster on 2008-04-05
If the only thing you want is to have specific folders hidden in Nautilus, you don't really even need to change their name to begin with a dot.

In each folder you can create a plain text file called .hidden and list the folders you don't want to appear in Nautilus there. I do that sometimes when some clueless applications want to add a visible (non-dotted) configuration file directly in the user home directory or something.
```

$ cat .hidden
Desktop
Mail
mbox
LightZone
properties.cfg
Fake Windows

```
Sort of like that.

Anyway, what happened with the original problem? Did you get your files back? Are you now just trying to understand things to prevent this from happening again?

---

### Post by Delkster on 2008-04-05
> **Kemono said:**
> Also, a new folder called "[COLOR="Blue"]file:[/COLOR]" was created in my [COLOR="Blue"]Home[/COLOR]. What's it for, anyway?

```
file:/home/narrator/Desktop
```

Sounds a little like something was trying to access your now non-existing Desktop folder by a full URL (beginning with file: to indicate the protocol to use, which in this case would be just reading the filesystem). file:///home/narrator/Desktop would refer to the file /home/narrator/Desktop in your local filesystem. Why the strangely named file appeared I don't know -- that kind of a URL should refer to the aforementioned folder anyway, so if anything, that folder should have been re-created rather than a file with a name beginning with "file:" or something.

---

### Post by Kemono on 2008-04-07
Sorry to reply so late. Delkster, I'm afraid they can't be recovered. Fortunately most of the important data was intact. I can't pick up from where I left, but I don't have to start from the beginning neither. 

Yes, I've learned that I shouldn't delete system default folders.
 
It'll be a long road before I gain the knowledge of properly operating a Linux box...but I'm willing to walk it. Like I said, I'm a patient guy.

---

