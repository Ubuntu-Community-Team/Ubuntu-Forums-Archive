---
title: "Gnome Login Loop"
date: 2022-02-23
forum: General Help
---

### Post by dorpapst on 2022-02-23
Hello people,
I cannot start Gnome in Ubuntu anymore after I last time restarted my computer.
When I start my computer and login, nothing happens and I get back to the login screen again.
There are a lot of articles existing in the internet about that and I tried a lot of them.
I checked the permissions for /tmp as well as .Xauthority, those have been fine.
I also ran sudo dpkg-reconfigure gdm3 which did not return any error message.

However, when logging in, I get trapped in that login loop.

it seems like there are a lot of other window managers installed on that PC (they have been there for years).
If I try to login into „Ubuntu“ or „Ubuntu Wayland“, I get into that loop.
If I start into LXDE, everything is alright, but I would like to use Gnome, I don‘t like LXDE.

Is there any trick I haven’t seen yet which could help me?
Thanks for any help!

---

### Post by TheFu on 2022-02-23
Did you happen to use sudo with any GUI program?

---

### Post by dorpapst on 2022-02-23
> **TheFu said:**
> Did you happen to use sudo with any GUI program?

Not that I remember

---

### Post by TheFu on 2022-02-23
Is GDM the default login manager? I think Gnome mandates it.

Also, you can create another account and see if you can login to that one. That would tell us whether this is system-wide or just the settings for 1 account. Using a different account is a very useful troubleshooting technique for all sorts of things.

---

### Post by #&amp;thj^% on 2022-02-23
> **TheFu said:**
> Is GDM the default login manager? I think Gnome mandates it.

Also, you can create another account and see if you can login to that one. That would tell us whether this is system-wide or just the settings for 1 account. Using a different account is a very useful troubleshooting technique for all sorts of things.

+1
I was also wondering if Nvidia Drivers are installed?
Wouldn't hurt to check ownership with:
```
stat /home/username ####your user name
```

---

### Post by ActionParsnip on 2022-02-23
+1 for a new test user. See if its account specific

---

### Post by dorpapst on 2022-02-23
Thank you for all replies.
I just created a new user and I also end up within a loop, so it is probably a system wide problem.

gdm is the default window manager.
The output of systemctl status display-manager.service is:
```
&#9679; gdm.service - GNOME Display Manager
     Loaded: loaded (/lib/systemd/system/gdm.service; static; vendor preset: enabled)
     Active: active (running) since Wed 2022-02-23 15:00:16 CET; 3h 45min ago
    Process: 1203 ExecStartPre=/usr/share/gdm/generate-config (code=exited, status=0/SUCCESS)
    Process: 1215 ExecStartPre=/usr/lib/gdm3/gdm-wait-for-drm (code=exited, status=0/SUCCESS)
   Main PID: 1221 (gdm3)
      Tasks: 3 (limit: 18944)
     Memory: 5.4M
     CGroup: /system.slice/gdm.service
             &#9492;&#9472;1221 /usr/sbin/gdm3

Feb 23 18:44:35 lukas-ubuntuknecht gdm-password][20120]: gkr-pam: unable to locate daemon control file
Feb 23 18:44:35 lukas-ubuntuknecht gdm-password][20120]: gkr-pam: stashed password to try later in open session
Feb 23 18:44:35 lukas-ubuntuknecht gdm-password][20120]: pam_unix(gdm-password:session): session opened for user testus>
Feb 23 18:44:35 lukas-ubuntuknecht gdm-password][20120]: gkr-pam: gnome-keyring-daemon started properly and unlocked ke>
Feb 23 18:44:37 lukas-ubuntuknecht gdm3[1221]: GdmDisplay: Session never registered, failing
Feb 23 18:44:45 lukas-ubuntuknecht gdm-password][20488]: gkr-pam: unable to locate daemon control file
Feb 23 18:44:45 lukas-ubuntuknecht gdm-password][20488]: gkr-pam: stashed password to try later in open session
Feb 23 18:44:45 lukas-ubuntuknecht gdm-password][20488]: pam_unix(gdm-password:session): session opened for user lukas >
Feb 23 18:44:45 lukas-ubuntuknecht gdm-password][20488]: gkr-pam: gnome-keyring-daemon started properly and unlocked ke>
Feb 23 18:44:56 lukas-ubuntuknecht gdm3[1221]: Child process -19364 was already dead.
```

nvidia-drivers are not installed (I guess), but I am running Ubuntu on a MacBook Pro. I guess it has an internal GPU.
The command
```
lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
```
outputed:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Iris Graphics 6100 [8086:162b] (rev 09) (prog-if 00 [VGA controller])
```

The output of the stat command from 1fallen is:
```
  File: /home/lukas
  Size: 2194          Blocks: 0          IO Block: 4096   directory
Device: 37h/55d    Inode: 257         Links: 1
Access: (0755/drwxr-xr-x)  Uid: ( 1000/   lukas)   Gid: ( 1000/   lukas)
Access: 2022-02-22 18:26:37.920848538 +0100
Modify: 2022-02-23 18:50:53.085158807 +0100
Change: 2022-02-23 18:50:53.085158807 +0100
 Birth: -
```

---

### Post by #&amp;thj^% on 2022-02-23
Interesting I was expecting something like:
```
File: /home/me
  Size: 4096            Blocks: 8          IO Block: 4096   directory
Device: 803h/2051d      Inode: 803571      Links: 18
Access: (0750/drwxr-x---)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2022-02-23 11:12:24.850838312 -0700
Modify: 2022-02-23 11:07:27.356000000 -0700
Change: 2022-02-23 11:07:27.356000000 -0700
**[COLOR="#FF0000"] Birth: 2022-01-31 09:31:47.443419716 -0700[/COLOR]**

```
I find it odd that there is no reported data on "**_Birth: -_**"
EDIT: One other to point to in your replys>>>"Feb 23 18:44:37 lukas-ubuntuknecht gdm3[1221]: GdmDisplay: Session never registered, failing"
Maybe try to re-install desktop
```
sudo apt install --reinstall gnome-shell ubuntu-gnome-desktop
```

---

### Post by dorpapst on 2022-02-23
Thank you for your answer. That actually does not help.

i reinstalled it and started newly, still cannot come in.

What is weird though is which window managers I can choose at login:
- LXDE
- Cinnamon
- Cinnamon (software rendering)
- GNOME
- GNOME on Xorg
- Openbox
- Plasma
- Ubuntu
- Ubuntu on Wayland
- XFCE Session

Before my system broke I was always using Ubuntu. Now, neither Ubuntu nor Ubuntu on Wayland work.

what&#8217;s interesting though is that GNOME and GNOME on Xorg haven&#8217;t been there before I did the reinstall gnome shell command.
so it now seems like it is double there. Anyway, none of them works either

currently, I am using Xfce, which is &#8222;ok&#8220;, but I want my gnome back :)

---

### Post by #&amp;thj^% on 2022-02-23
Well you certainly are adventurous with that many DE's installed, I'll give you that. ;)
Gnome and Plasma known issues with a mix. 
Gnome and Cinnamon known issues with a mix.
Ubuntu on Wayland I just don't have any interest there, so can't say here.

---

### Post by dorpapst on 2022-02-23
Yeah, I have no idea why there are there, there have been for ages.

So I honestly cannot believe this is the reason now what causes my problems

---

### Post by ajgreeny on 2022-02-23
I think it is worth seeing if you are owner of all your home files and folders so please run command```
ls -l | grep -v $USER
``` from whichever DE version you are able to log into.

I wonder if some files or folders are no longer owned by you as your username, and if that is the case there will be more than the one expected single line of output which is ```
ls -l | grep -v $USER
1:total 642M
```

However, like 1fallen, I think you are asking for problems with those 10 available sessions, and in future I would strongly recommend that you choose the DE you like best and install just that single one when you install the OS, ie Kubuntu for KDE, Xubuntu for Xfce, Ubuntu-Mate for Mate, etc, etc.

---

### Post by dorpapst on 2022-02-23
Yeah. I collected those over years sometimes trying something new, that was a bad decision. I might reinstall everything for Ubuntu 22.04.

Anyway folks, I just decided to play in a backup from one week ago (only losing like 3 folders which are all on GitHub and can be pulled back), because it seems like finding the error is purely random.
It is now working again,and I hope that it doesnt break down again (since I do not know how it broke down...)

Thank you everybody for all of your help!

---

### Post by #&amp;thj^% on 2022-02-23
> **dorpapst said:**
> Yeah, I have no idea why there are there, there have been for ages.

So I honestly cannot believe this is the reason now what causes my problems
All I can do is point to problems, the rest is up to you. :p

> **ajgreeny said:**
> 

However, like 1fallen, I think you are asking for problems with those 10 available sessions, and in future I would strongly recommend that you choose the DE you like best and install just that single one when you install the OS, ie Kubuntu for KDE, Xubuntu for Xfce, Ubuntu-Mate for Mate, etc, etc.

Yep and +1

---

### Post by TheFu on 2022-02-23
Having lots of DEs installed shouldn't be an issue, except if one of them mandates a specific login manager.
The risk is that old settings for 'related' DEs will have different meanings. The solution for that is to always create a new account for each DE used. Don't cross those streams.

Relations come from the libraries used to build the DE and programs.  There are 2 major libraries, Qt and GTK+.  KDE and LXQt use ... Qt.  All the others use different versions of GTK+.  Again, having mixed libraries on the system isn't the issue. It is about the personal settings having conflicts, usually between Gnome2/Gnome3 DEs and all the other GTK+ v2, v3, and v4 libraries. They all want to write your personal settings to the same places based on the user's HOME.  The solution for these conflicts isn't hard, the developers just need to have version specific settings for each application, copying over the most recent settings on the first run to the new settings DB.  In the old days, we had .rc files and fixing issues was trivial.  Then someone decided to copy MSFT's "registry" idea, badly and started putting settings into a DB (dconf or gconf).  Yuck, but it does reduce the number drive sectors used - like that matters anymore.

---

