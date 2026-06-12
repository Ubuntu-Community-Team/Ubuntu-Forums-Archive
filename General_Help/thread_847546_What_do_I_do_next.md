---
title: "What do I do next"
date: 2008-07-02
forum: General Help
---

### Post by tomytech on 2008-07-02
Ubuntu Studio asks me for my login name and password, then it just sits there with this dollar sign thing. What do I do next. How can I get to the Desktop to start using some programs.:confused:

---

### Post by soccerboy on 2008-07-02
did you enter in the user name and password?  If so, try hitting Ctrl+Alt+F7 for a gui

---

### Post by tomytech on 2008-07-02
yes, entered correct username and password. Will CTRL - ALT - F7 take me to the desktop or the Windows equivalent?

---

### Post by ibutho on 2008-07-02
The dollar sign is a command prompt. Enter the command "startx" (minus the quotes). Does the GUI startup?

---

### Post by tomytech on 2008-07-02
not infron of Ubuntu machine, will try later. Are there any other possibilites? (Seems like a loaded question, but I really wanna know)

---

### Post by tomytech on 2008-07-02
sorry "in front of"

---

### Post by soccerboy on 2008-07-02
there are many possibilities.  X could not be installed or errors in the boot process etc.  We'll only know as you try stuff and post debugging info.

---

### Post by tomytech on 2008-07-02
Thanks

---

### Post by roaldz on 2008-07-02
> **tomytech said:**
> Thanks

It looks like your X server (graphical GUI) is not starting. This can be due to problems with your video hardware/driver. Please post the output of the command ```
cat /var/log/Xorg.0.log
```. I know this is hard, since you can´t use a web browser on you ubuntu. A little trick:

```
tail -n 300 /var/log/Xorg.0.log > ~/xorg.0.log
```
This command outputs the last 300 lines from the file ¨/var/log/Xorg.0.log¨ and stores it in the home directory of your user account.

Now install ssh:

```
sudo apt-get install openssh-server
```
This will download and install the Secure Shell Server (SSH). This is usefull for logging in remotely.

Now get a FTP client which can handle the SFTP protocol (windows, linux, doesn´t matter). Then login to your machine and get the file ¨xorg.0.log¨ from your homedir (/home/<USERNAME>/) and post the output.

---

