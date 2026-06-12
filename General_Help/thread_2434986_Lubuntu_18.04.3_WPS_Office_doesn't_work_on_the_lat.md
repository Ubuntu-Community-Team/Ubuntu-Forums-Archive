---
title: "Lubuntu 18.04.3: WPS Office doesn't work on the latest version"
date: 2020-01-14
forum: General Help
---

### Post by stilnovo1 on 2020-01-14
Hi,

after several notifications, I have updated WPS Office to the latest version (11.1.0.9080).

During the installation, I haven't received any error message or I didn't notice any strange behaviour, apparently the process went smooth (like all the previous ones).

As usual, the first time I've clicked on Write, It has appeared the terms and conditions page, I've accepted but... nothing!

All the programs of this office suite don't start at all, no messages, it 'simply' happens... nothing.

They are present on the Lubuntu program list, but they don't start.

I have supposed that it could be a libgtk2 fault, I've found something about this but no results at all...

Any idea? 

ps: don't suggest to use LibreIOffice instead of WPS :):).  I already use LibreOffice, but I need also WPS

---

### Post by stilnovo1 on 2020-01-16
anyone could help me?

---

### Post by howefield on 2020-01-16
Thread moved to the "*General Help*" forum for a better fit.

Try opening from the terminal, you may get an idea with some verbose output.

---

### Post by guiverc on 2020-01-16
I don't know or use WPS Office (I never have so know almost nothing about it), but I'd (too) try running it from terminal, so you can hopefully see messages that give clues on what is happening and any problem encountered. Did you look in logs before & then after trying to start `writer`, ie. maybe clues went to `dmesg` or `journalctl` given you indicated none went to your screen.

You have alluded to it possibly being [COLOR=#000000]libgtk2[/COLOR] fault?  Why was that? I did note the following in the .deb which does refer to libgtk2.0

```
Package: wps-office
..
Depends: libc6(>= 2.15) | libc6.1, libfreetype6(>= 2.4),
         libcups2, libglib2.0-0, libglu1-mesa,
         libsm6, libxrender1, libfontconfig1,
         libxext6, libxcb1, libbz2-1.0 ,libgtk2.0-0
..
```

---

### Post by stilnovo1 on 2020-01-17
Ciao,

if I run this office suite via terminal I don't receive any feedback: after I have typed wps or wpspdf the terminal screen remains all black with a blocked cursor.
If I run via terminal in sudo mode typing 'wps' I have the same black screen with the blocked cursor. 
If I run via terminal in sudo mode typing 'wpspdf', then the program finally start (the main initial program, not the pdf module). From this point, I can load any file from the wps menu and it seems to normally work.
If I click on a .docx or .xlsx document, it happens nothing but in the tasks manager I see the wps module loaded.

Thanks in advance for your help!

---

### Post by CelticWarrior on 2020-01-17
You shouldn't run graphical software with sudo under any circumstance. If you did that before then very likely that was the root cause of your current problem.

---

### Post by stilnovo1 on 2020-01-17
Ciao,

I didn't run wps with sudo before, but I was curious to see the behaviour of the program... by the way, could you know why it works in this way?

---

### Post by CelticWarrior on 2020-01-17
I wasn't talking about WPS specifically. If you did that with other software before that may be the cause of your problem now with WPS.

---

### Post by ajgreeny on 2020-01-17
Just out of interest can you show us the output of command ```
ls -la
``` in terminal to check ownership of files and folders in your home which should all belong to you as user but can be transferred to root ownership if you use sudo to open a GUI application with root permissions.
If any of them are owned by root you will probably need to run command ```
sudo chown -R $USER:$USER /home/$USER
``` to return everything to your ownership, but let's see the ls output first to be sure.

---

### Post by stilnovo1 on 2020-01-20
ciao!

Well:

```
ls -la totale 184
drwxr-xr-x 29 zambo zambo 4096 gen 20 14:38 .
drwxr-xr-x  3 root  root  4096 set 28 20:11 ..
drwxr-xr-x  3 zambo zambo 4096 dic  9 18:33 .anydesk
-rw-------  1 zambo zambo 6391 gen 20 15:40 .bash_history
-rw-r--r--  1 zambo zambo  220 set 28 20:11 .bash_logout
-rw-r--r--  1 zambo zambo 3771 set 28 20:11 .bashrc
drwxrwxr-x 21 zambo zambo 4096 gen 17 15:17 .cache
drwx------ 31 zambo zambo 4096 gen 14 14:58 .config
drwx------  3 root  root  4096 nov  7 20:30 .dbus
drwx------  2 zambo zambo 4096 gen 14 14:58 Desktop
-rw-r--r--  1 zambo zambo   26 set 28 22:28 .dmrc
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Documenti
drwxrwxr-x  2 zambo zambo 4096 ott  7 15:32 Eseguibili
drwx------  3 zambo zambo 4096 set 28 22:28 .gnupg
drwxr-xr-x  2 zambo zambo 4096 ott  4 13:02 .hplip
drwxr-xr-x  2 zambo zambo 4096 ott 29 17:51 Immagini
-rw-rw-r--  1 zambo zambo   21 ott 14 19:24 .iscan_preference
drwxrwxr-x  3 zambo zambo 4096 gen 14 13:03 .kingsoft
drwxr-xr-x  3 zambo zambo 4096 set 28 22:28 .local
-rw-rw-r--  1 zambo zambo 8743 ott 17 18:34 log
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Modelli
drwx------  5 zambo zambo 4096 ott  4 10:36 .mozilla
-rw-rw-r--  1 zambo zambo   49 nov 11 18:58 .mtpaint
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Musica
drwx------  3 zambo zambo 4096 ott  7 15:33 .nv
-rw-rw-r--  1 zambo zambo  621 ott  4 11:41 .nvidia-settings-rc
drwxrwxr-x 12 zambo zambo 4096 ott 31 17:47 .openshot_qt
drwx------  3 zambo zambo 4096 ott  4 12:14 .pki
-rw-r--r--  1 zambo zambo  807 set 28 20:11 .profile
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Pubblici
drwxrwxr-x  8 zambo zambo 4096 ott  4 11:29 rtl8821ce
drwx------  4 zambo zambo 4096 ott 14 16:02 .sane
drwxr-xr-x  3 zambo zambo 4096 gen 14 14:59 Scaricati
drwxr-xr-x  2 zambo zambo 4096 gen 14 13:04 Scrivania
-rw-r--r--  1 zambo zambo    0 set 28 22:48 .sudo_as_admin_successful
drwx------  4 zambo zambo 4096 ott  4 12:12 .thumbnails
drwxrwxr-x  8 zambo zambo 4096 dic  2 16:17 .thunderbird
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Video
-rw-------  1 zambo zambo   57 gen 20 14:38 .Xauthority
-rw-rw-r--  1 zambo zambo  131 ott  4 10:50 .xinputrc
-rw-r--r--  1 zambo zambo   14 lug 25 10:21 .xscreensaver
-rw-------  1 zambo zambo 2501 gen 20 14:38 .xsession-errors
-rw-------  1 zambo zambo 2501 gen 17 14:30 .xsession-errors.old
drwxr-xr-x  2 root  root  4096 gen 14 14:58 &#27169;&#26495;



```

and the output of:

```
sudo chown -R $USER:$USER /home/$USER
```

is wholly empty... no output at all.

So, I see that kingsoft directory is not root...am I wrong?

---

### Post by CelticWarrior on 2020-01-20
You had some root owned folders indeed, including "template" (&#27169;&#26495;), vdery likely WPS related.
This should have been corrected by the chown command and it's normal it doesn't give feedback.

Confirm by running again ```
ls -la
```
It should now show all owned by you.

---

### Post by ajgreeny on 2020-01-20
More importantly, I think, the .dbus folder was also root owned which could possibly have given you bigger problems than simply WPS-Office not working.

This all probably stems from you using sudo to open WPS-Office.

As mentioned by CelticWarrior there was not meant to be any output from the chown command; [COLOR="#FF0000"]chown[/COLOR] stands for **[COLOR="#FF0000"]ch[/COLOR]**ange **[COLOR="#FF0000"]own[/COLOR]**er and the lack of output, as in most Linux commands, means simply that it was successful.

---

### Post by stilnovo1 on 2020-01-20
Ciao!

Now the output of ls -la command is effectively different:

```
ls -la totale 184
drwxr-xr-x 29 zambo zambo 4096 gen 20 14:38 .
drwxr-xr-x  3 root  root  4096 set 28 20:11 ..
drwxr-xr-x  3 zambo zambo 4096 dic  9 18:33 .anydesk
-rw-------  1 zambo zambo 6436 gen 20 16:01 .bash_history
-rw-r--r--  1 zambo zambo  220 set 28 20:11 .bash_logout
-rw-r--r--  1 zambo zambo 3771 set 28 20:11 .bashrc
drwxrwxr-x 21 zambo zambo 4096 gen 17 15:17 .cache
drwx------ 31 zambo zambo 4096 gen 14 14:58 .config
drwx------  3 zambo zambo 4096 nov  7 20:30 .dbus
drwx------  2 zambo zambo 4096 gen 14 14:58 Desktop
-rw-r--r--  1 zambo zambo   26 set 28 22:28 .dmrc
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Documenti
drwxrwxr-x  2 zambo zambo 4096 ott  7 15:32 Eseguibili
drwx------  3 zambo zambo 4096 set 28 22:28 .gnupg
drwxr-xr-x  2 zambo zambo 4096 ott  4 13:02 .hplip
drwxr-xr-x  2 zambo zambo 4096 ott 29 17:51 Immagini
-rw-rw-r--  1 zambo zambo   21 ott 14 19:24 .iscan_preference
drwxrwxr-x  3 zambo zambo 4096 gen 14 13:03 .kingsoft
drwxr-xr-x  3 zambo zambo 4096 set 28 22:28 .local
-rw-rw-r--  1 zambo zambo 8743 ott 17 18:34 log
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Modelli
drwx------  5 zambo zambo 4096 ott  4 10:36 .mozilla
-rw-rw-r--  1 zambo zambo   49 nov 11 18:58 .mtpaint
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Musica
drwx------  3 zambo zambo 4096 ott  7 15:33 .nv
-rw-rw-r--  1 zambo zambo  621 ott  4 11:41 .nvidia-settings-rc
drwxrwxr-x 12 zambo zambo 4096 ott 31 17:47 .openshot_qt
drwx------  3 zambo zambo 4096 ott  4 12:14 .pki
-rw-r--r--  1 zambo zambo  807 set 28 20:11 .profile
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Pubblici
drwxrwxr-x  8 zambo zambo 4096 ott  4 11:29 rtl8821ce
drwx------  4 zambo zambo 4096 ott 14 16:02 .sane
drwxr-xr-x  3 zambo zambo 4096 gen 14 14:59 Scaricati
drwxr-xr-x  2 zambo zambo 4096 gen 14 13:04 Scrivania
-rw-r--r--  1 zambo zambo    0 set 28 22:48 .sudo_as_admin_successful
drwx------  4 zambo zambo 4096 ott  4 12:12 .thumbnails
drwxrwxr-x  8 zambo zambo 4096 dic  2 16:17 .thunderbird
drwxr-xr-x  2 zambo zambo 4096 set 28 22:28 Video
-rw-------  1 zambo zambo   57 gen 20 14:38 .Xauthority
-rw-rw-r--  1 zambo zambo  131 ott  4 10:50 .xinputrc
-rw-r--r--  1 zambo zambo   14 lug 25 10:21 .xscreensaver
-rw-------  1 zambo zambo 2501 gen 20 14:38 .xsession-errors
-rw-------  1 zambo zambo 2501 gen 17 14:30 .xsession-errors.old
drwxr-xr-x  2 zambo zambo 4096 gen 14 14:58 &#27169;&#26495;



```

Only the second line I see it remains with root... all the rest has changed to user as you said (by the way: thank you both your very clear explanations) 

Now I've just tried to load wps (in terminal) but I still have no results... in task manager I see two wps modules loaded

---

### Post by CelticWarrior on 2020-01-20
Try this:

Open Files, the file manager and enable hidden files/folders with CTRL+H.

Now you should see a hidden .kingsoft folder. Delete it, log out and login again or reboot. Try opening WPS the usual way.

---

### Post by stilnovo1 on 2020-01-20
Ciao!

I've tried to delete the .kingsoft hidden folder, rebooted but... nothing...

---

### Post by stilnovo1 on 2020-01-24
Please, help me! Not solved...

---

### Post by kurt18947 on 2020-01-24
Something I've done in the past when having a similar problem. Create a new user and try opening WPS as a new user. This may not help but it may be worth a try. Do you have a user account in addition to the account created when installing Ubuntu? I create a normal user account and do as little from the original account as possible.

---

### Post by stilnovo1 on 2020-01-27
thanks, I will try it!

---

### Post by stilnovo1 on 2020-02-03
no, it still doesn't work....
The (very) strange thing is that it starts only from the terminal being root (so, with sudo command).
Then, it apparently properly works...

In task manager I can see two different situations:

- non root: two wps tasks loaded but no video output (it seems off, but it not so --> if I load a .doc file for example, I can see also the temporary one, but no output in the video, wps seems not loaded);

- root: I can open files, the program loads its first module screen --> in task manager no wps modules at all, there are two 'et' modules instead

boh??

---

### Post by CelticWarrior on 2020-02-03
> **stilnovo1 said:**
> The (very) strange thing is that it starts only from the terminal being root (so, with sudo command).
Then, it apparently properly works...

And, again, doing that only makes the situation worse.

---

### Post by stilnovo1 on 2020-02-03
Infact I have uninstalled wps... but I need sometimes a full compatibility with office docs, I am the only one in my Company that is using Linux... wps has been the best solution until now, LibreOffice unfortunately is not always a good solution for my problem

---

