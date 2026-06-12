---
title: "Acer Chromebook - Automatically start Linux Ubuntu on boot up?"
date: 2014-11-20
forum: General Help
---

### Post by harry28 on 2014-11-20
Sorry if this is in the wrong area, didn't know where to put it.

I installed Linux Ubuntu along side ChromeOS on my Acer C720 a month or so ago. I was wondering, since I have to go into the terminal, type sudo startunity, enter the password and wait for it to boot up, if there is a way so that when the Chromebook is turned on, Linux is automatically started and I can switch to it with the keyboard shortcut (Crtl, Alt, Shift, F2)? Sorry if this has been asked before, I couldn't seem to find anything else on the forum

---

### Post by cal1j on 2014-11-20
Kinda a hack, but I'd write a bash script with the start-up sequence in it, and make it execute on start up. So, if your command that you need is ```
sudo startunity
``` then write the following and place it in /etc/init.d/

```
#!/binbash/

# save file in directory /etc/init.d/

sudo startunity

```

After writing that file and saving as restart.sh in the /etc/init.d file, run:
```
sudo chmod +x /etc/init.d/restart.sh
```

 Restart your computer. I'm gonna bet that will work. Let me know if it did.

---

### Post by harry28 on 2014-11-23
Sorry been busy the last few days. I haven't tried this yet, but I was wondering what I would have to do about the passwords that i have to enter (one for the user account and one for decrypting the installation, called precise), how would I go about putting the password in automatically if this is even possible. Normally, to boot up Linux I have to go into the terminal on ChromeOS, enter shell (press enter), enter sudo startunity (press enter), enter the password for the use (press enter) and then finally enter the password for the OS(known as precise). Is it even possible to write a bash script for this?

---

### Post by cal1j on 2014-11-24
Sorry for the delay harry. First of all, I do not know how what you are asking is possible. However you shouldn't have to enter a password for a script owned by root. Maybe I misunderstand you. Secondly, I am unclear why you would encrypt an installation and then want to have an automated script un-encrypt it. Seems like it ruins the security provided by encryption. If I misunderstand you, please advise. In the meantime write the script I suggested. I very much think that will solve your problem. I continue to look forward to hearing if it works for you, and am willing to continue to provide help if that script fails to solve your problem

---

### Post by mJayk on 2014-11-25
I think it sounds like you are using the crouton chroot method?

What it sounds like you want to do is actually install ubuntu and duel boot, have a look and a read around Chrubuntu. It can do what you are asking but is a bit more in depth than a crouton script.

---

