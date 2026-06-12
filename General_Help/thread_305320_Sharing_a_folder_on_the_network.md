---
title: "Sharing a folder on the network"
date: 2006-11-23
forum: General Help
---

### Post by johnny9794 on 2006-11-23
Ok I have just now started to use sharing a folder on my network "SMB Network" for my linux box. "I use shared files and folders off my XP boxs all the time and have no problem"

This is my first time using sharing a folder off my Ubuntu, Edgy box so i may access my Ubuntu, Edgy box shared folders and files from my other Windows, XP box.

When I try to access the shared folder that is on my Edgy box from my XP box I get prompt with a username and password login screen, I have tried my Edgy box login name and password, tried my network username and password, none of it works :(.

Is there a usernamer and password i must set for file sharing on Ubuntu? 

If my typing is bad, I am sorry i have been up for 20 hours or so.

Could someone help me out :)?
Here is a screenshot of the login prompt

---

### Post by awbassett on 2006-11-23
You need to make a samba user and password. You can do this by:

sudo smbpasswd -a system_username

sudo gedit /etc/samba/smbusers

Make sure the following line is in there.

    system_username = "network username"

---

### Post by Dr Small on 2006-11-23
I'm all new to linux, so I have no clue where you "do" that at.
I don't know where I'm supposed to type that in at.

Thanks

Dr Small

---

### Post by Keshyden on 2006-11-23
Dr Small, 

You type those commands into a terminal. For example, Applications > Accessories > Terminal.

---

### Post by Dr Small on 2006-11-23
> **Keshyden said:**
> Dr Small, 

You type those commands into a terminal. For example, Applications > Accessories > Terminal.

Ok. I tried the commands, in the terminal, and here's exactly as I typed, concerning the fist cmd.

sudo smbpasswd -a drsmall

And then it asks for a password, and it won't let me type anything in.
(See Screenshot)

---

### Post by awbassett on 2006-11-24
no characters are showing up, but you're still inputing text.

---

### Post by flameproof on 2006-11-28
>And then it asks for a password, and it won't let me type anything in.

The password is not echoed on the screen. You still type text.

One of the many strange things in linux....

---

