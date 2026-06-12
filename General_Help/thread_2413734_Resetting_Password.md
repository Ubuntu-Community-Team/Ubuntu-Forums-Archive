---
title: "Resetting Password"
date: 2019-03-01
forum: General Help
---

### Post by Stob on 2019-03-01
I have forgotten my password. I attempted to rest using the link below, but failed in each try. Is there a better/easier way? I have not used this laptop for some time and it needs updating, prompting for the password. 

 [URL="https://help.ubuntu.com/community/LostPassword"]https://help.ubuntu.com/community/LostPassword



[/URL]

---

### Post by Impavidus on 2019-03-01
There's this guide that I usually direct people to: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Instead of exiting the root shell and resuming normal boot, you can also reboot. Just use the **reboot** command. It may make a difference if you use a proprietary graphics driver.

If it doesn't work, could you tell how far you get?

---

### Post by Stob on 2019-03-02
Sir, thank you for the link. I followed it and I thought I was successful. Once I entered my password twice it said it was successful. However when I tried to install an upgrade and entered the password, it didn't authenticate it. Don't know why.

---

### Post by sisco311 on 2019-03-02
Did you try to do the upgrade via the GUI or the terminal?

---

### Post by Stob on 2019-03-02
I downloaded the update, which was an update for Firefox, then did a search on how to load it. It gave me things to type in the terminal, but I'm not very familiar with doing that. Somewhere in doing that I was asked for the password, and that's when I found out the password reset didn't work.

---

### Post by sisco311 on 2019-03-02
Is your password accepted when you try to log in?

Did you get any error messages when you changed your password?

Please post a link to the instructions you have followed and the exact error message you get.

Also check if your user is in the admin and/or sudo group. The following command will print the groups:```
id
```

You can also test if you can run commands as root with sudo or via the gui (polkit) by running a harmless command like echo.

echo will simply displays a line of text: 
```
sudo echo "foo"
```
and
```
pkexec echo "bar"
```

---

### Post by Impavidus on 2019-03-03
From a PM:[QUOTE=Stob]Sir, I replied to the thread about the password. I thought it was complete but evidently not.

Aside from that issue, if I get that resolved, I was trying to download  an update to Firefox. I downloaded the update and it is in the archive  manager, but how do I install the update? I am more familiar with  windows based systems, and you get a prompt to install updates, but not  with this. If I can get my password issue resolved, how do I install the  update?

Thank you so much for your help.[/QUOTE]The proper way to install updates to Firefox (or any other software known to the package mananger) does not involve the archive manager. I always wait for the update manager to pop up, then click install, but you can also use two terminal commands.

(And please, don't use PMs that way. Just post on the forum.)

---

### Post by oldos2er on 2019-03-03
> **Stob said:**
> I have forgotten my password. I attempted to rest using the link below, but failed in each try. 

Failed how, exactly? The more information you provide, the better the answer.

---

### Post by flyn633 on 2019-03-17
You can simply use *passwd * command to change the password in terminal. During the login screen open terminal in rescue mode and change it through the command([Follow this guide]("https://help.ubuntu.com/community/LostPassword")). You can also [change the root password]("https://linuxflips.com/change-user-root-password-in-ubuntu-linux/") as well.

---

