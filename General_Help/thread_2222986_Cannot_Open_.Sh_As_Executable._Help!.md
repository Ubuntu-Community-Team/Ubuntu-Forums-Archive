---
title: "Cannot Open .Sh As Executable. Help!"
date: 2014-05-08
forum: General Help
---

### Post by spencer9 on 2014-05-08
I really need help. I'm trying to open a .Sh file, but when I do, it opens gedit
I've already checked allow executing file as program.
No luck.

I've tried this command in Terminal
cd /home/administrator/Downloads/Folder/<FILENAME>.sh
$ chmod ugo+x ./<FILENAME>.sh

Then it just says command not found.

Also tried
# sh ./<FILENAME>.sh
That command seems to have no effect 

What am I doing wrong?? :(

Thanks in advance

---

### Post by papibe on 2014-05-08
Hi spencer9. Welcome to the forum ):P

I believe you are trying to 'run', or 'execute' a bash script (.sh).

The fact that when you run it it appears to have no effect, it doesn't mean it did not run.

Could you post the content of the script?

Regards.

---

### Post by monkeybrain20122 on 2014-05-09
Open Nautilus (the file manager), go to Preferences > Behaviour > Executable Text Files and choose "Ask Each Time" instead of "Display", then next time when you click it will offer an option to run (provided you have set permission for it to run, right click file, Properties > Permission or "chmod + x ..." in terminal). 

Of course you can always run it from the terminal.You have to change directory to the place where the script is or use the full path if you run from the terminal (and either "./filename" or "sh filename", not "sh ./filename") Why are you running as root?

---

### Post by deadflowr on 2014-05-09
Learned a fun one today
This will show the setting
```
gsettings get org.gnome.nautilus.preferences executable-text-activation

```
This will show what you can set it as
```
gsettings range org.gnome.nautilus.preferences executable-text-activation

```
In 14.04 it's set to 'display', or in the GUI "view",
to change
```
gsettings set org.gnome.nautilus.preferences executable-text-activation ask
```
or set to launch, if you want.
Fun stuff, in any case.

---

