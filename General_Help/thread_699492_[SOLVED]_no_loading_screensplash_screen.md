---
title: "[SOLVED] no loading screen/splash screen"
date: 2008-02-17
forum: General Help
---

### Post by JohnnyBoy022 on 2008-02-17
When I boot Ubuntu I see a loading... please wait message than a black screen for about a minute then the GNOME login screen. How can I see the progess bar / splash screen or text of what's going on? It's just a black screen. Thanks for any help.

---

### Post by y-lee on 2008-02-17
You may have a misconfigured resolution for usplash. This seems to happen sometimes on fresh Gutsy installs. To fix it, edit **/etc/usplash.conf **as root and set the **xres** and **yres** lines to the horizontal and vertical resolutions that your screen supports.

Then do

```
sudo update-usplash-theme usplash-theme-ubuntu
```

If you don't know how to edit a file as root:


```
sudo gedit
```

Open the file make the changes and save the file.

Post back and let us know if that works or not.

---

### Post by JohnnyBoy022 on 2008-02-17
Thanks, that worked perfectly. Is there any way that I can see the loading splash screen and see the text output of what is happening? I like to see what's going on when my computer boots.

---

### Post by y-lee on 2008-02-17
> **JohnnyBoy022 said:**
> Thanks, that worked perfectly. Is there any way that I can see the loading splash screen and see the text output of what is happening? I like to see what's going on when my computer boots.

I honestly don't know for sure. I'm running Dapper and I do get some textual output before my login screen as well as a usplash image. But I installed a latter version of ubuntu for a friend and in that case I didn't get the text, however I didn't investigate the issue as it didn't matter.

Perhaps you can edit the grub menu list, the file **menu.lst**,  found **/boot/grub** and If you remove the quiet option from the kernel line the messages should  appear in the splash.

Make a backup in case you mess up using a command like:

   ```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
```

And edit as superuser 

```
sudo gedit /boot/grub/menu.lst
```

Save your file after you are done try rebooting.

Note: I can't test this as I use Dapper and it may or may not work.

---

### Post by JohnnyBoy022 on 2008-02-18
Awesome, that worked.

---

### Post by y-lee on 2008-02-18
Great Glad to hear it. Thought it might but I wasn't sure.:)

---

