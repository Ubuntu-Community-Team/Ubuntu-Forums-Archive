---
title: "Ubuntu 22.04 - Change the color, font and background of files and folders in terminal"
date: 2024-06-29
forum: General Help
---

### Post by mdragu8126 on 2024-06-29
Hi,

I want to change the color, font and background of files and folders in terminal (see attachment).
In the first picture for instance, bash_cmd is a folder.
I want to change the background, but I don't know how.

Thank you in advance.

---

### Post by Holger_Gehrke on 2024-06-29
The colouring of the output of the 'ls' command is controlled by the environment variable LS_COLORS. There is a command named 'dircolors' for setting up that variable. The default ~/.bashrc is set up to load a file ~/.dircolors into that command. To create such a file you can use 'dircolors --print-database>~/.dircolors'. You can use any text editor to change that file. The generated file has comments that describe what value you can set.

Holger

---

### Post by Dennis N on 2024-06-29
The terminal has lots of settings in it's preferences dialog, including theme and colors. You can change those in that dialog. See screenshot. Under profiles, the default is just called "unnamed" here. Click that and use the appropriate tab to make changes to the default. Or make a new profile.

---

### Post by &amp;KyT$0P# on 2024-06-29
Is the problem actually that you're mounting a NTFS or other non-Unix filesystem with more permissive permissions than you're using?  Does [FONT=monospace]ls -la[/FONT] show those files and folders having the exact permissions you need/want?

---

### Post by mdragu8126 on 2024-07-02
In Screenshot_001, the folders are the ones with blue color. They are the folders in the home directory.


In Screenshot_002 and Screenshot_003, the folders are on a green background. I would like that background to be gone.
Indeed, those folders may be NTFS folders since they are shared Windows folders.
Is it possible to remove that background?
Thank you. All the best!

---

### Post by Holger_Gehrke on 2024-07-02
That pattern of colours (blue text on green background) in 'ls' with the standard LS_COLORS settings means 'directory writable by others' and is meant to draw your attention to the question of whether or not those permissions are what you want. So you can either change the way you mount that NTFS-Volume (give the options uid=, gid=, and fmask= with appropriate values so the mounted device is not by default writable by anyone and everyone; see 'man mount.ntfs' for details) or if you only want to change the way it's presented you can change the colours produced by 'ls' in the way I mentioned in Post #2.

Holger

---

