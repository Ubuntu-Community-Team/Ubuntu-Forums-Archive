---
title: "locate external disk on the windows 10 ubuntu bash"
date: 2018-02-26
forum: General Help
---

### Post by bask185 on 2018-02-26
I have a question. It is a bout the bash on ubuntu on windows. So I don't know if this is the right place to ask.

If I need to navigate to my windows folders on the C: disk I do: cd /mnt/c/Users/bask185/Documents/   and there I am.

When I plug in my card reader with a CF card it appears in windows under the D: disk. 

The reason I am using this bash is to get the hex2bin program to work and I am using a shellscript to move and name some files (I've really no clue how to do this in Windows). The script turns a .hex in a .bin and it has to be stored on the CF card. I cannot find it, so I am using my Document folder instead at the moment.

Can I acces the files on the CF card? and if so, how?

---

### Post by dragonfly41 on 2018-02-26
I have Windows 10 + Ubuntu 16.04 dual-boot.
I did experiment with Windows bash some weeks ago but my primary OS is Ubuntu.
I located the user path here .. C:\%localappdata%\lxss\home\{myusername}\
I foilowed the notes from here ...

[https://askubuntu.com/questions/759880/where-is-the-ubuntu-file-system-root-directory-in-windows-nt-subsystem-and-vice](https://askubuntu.com/questions/759880/where-is-the-ubuntu-file-system-root-directory-in-windows-nt-subsystem-and-vice)

Take note of warning ..

> [COLOR=#111111][FONT=Ubuntu]**PLEASE NOTE We (the WSL team) [STRONGLY recommend you do NOT spelunk into the Linux distro data folders]("https://blogs.msdn.microsoft.com/commandline/2016/11/17/do-not-change-linux-files-using-windows-apps-and-tools/") ). If you do, data loss and/or corruption is VERY likely We are working to improve this interop scenario and will announce any progress on our blog: [blogs.msdn.microsoft.com/commandline]("https://blogs.msdn.microsoft.com/commandline/")**[/FONT][/COLOR]**[COLOR=#111111][FONT=Ubuntu]&#8211; [/FONT][/COLOR][Rich Turner]("https://askubuntu.com/users/381841/rich-turner")[COLOR=#111111][FONT=Ubuntu] [/FONT][/COLOR][COLOR=#9199A1][FONT=Ubuntu][[FONT=inherit]Nov 14 '17 at 18:34[/FONT]]("https://askubuntu.com/questions/759880/where-is-the-ubuntu-file-system-root-directory-in-windows-nt-subsystem-and-vice#comment1567071_759880")[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] [/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu][/FONT][/COLOR]**

---

### Post by bask185 on 2018-02-27
That is not what I am asking, I already know where I can find the Linux folder structure. I need acces to the D: drive (CF card) not the C: drive.

---

### Post by ubname on 2018-02-27
> **bask185 said:**
> That is not what I am asking, I already know where I can find the Linux folder structure. I need acces to the D: drive (CF card) not the C: drive.


Hi, I would try 

```
cd /mnt/d
```

HTH.

---

### Post by bask185 on 2018-02-27
c is the only drive present in the /mnt folder. That's the problem

---

### Post by dragonfly41 on 2018-02-27
So perhaps /d needs to be mounted?

---

