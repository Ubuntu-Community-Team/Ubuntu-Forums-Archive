---
title: "specialist software in WINE"
date: 2007-08-31
forum: General Help
---

### Post by dcmarsh on 2007-08-31
I'm trying to install a specialist piece of software for work, it's a windows
helpdesk application made by Numara software called Trackit. 

I've managed to get the installer to run within WINE but now I'm stuck. As it works with a
central SQL database a part of the install asks for the network location of the database. It
won't accept a standard UNC path, or the ip address.

Works perfectly with the standard settings in Windows and it isn't a DNS issue.

can ubuntu use standard UNC paths or is there a specialist one to use?

If I can get this going I may be able to almost stop using XP completely.

---

### Post by anaconda on 2007-08-31
Cant help you with the specific problem, but if you have a dualboot system, does the program work if you try to run it with wine from the windows partition? 

I mean you would boot to ubuntu, mount the windows partition, and then run the program with wine straight from your windows partition. 

If it works this way then you just need to copy the installed program from windows to ubuntu..

---

### Post by soyezu on 2007-10-22
I'm sorry to hear that you're saddled with TrackIt (I'm not a fan). 

The simple solution to your problem is that you need to mount the Windows share from your SQL server onto your ubuntu desktop. 

<servername> = the dns name of your SQL server
<username> = your username on your local ubuntu system
<sharename> = the name of the Windows share that holds the database on your SQL server
<winusername> = your Windows domain username
<winpassword> = your Windows domain password

```
sudo apt-get install smbfs
sudo mkdir /mnt/<servername>
sudo chown <username> /mnt/<servername>
sudo mount -t cifs //<servername>/<sharename> /mnt/<servername> -o username=<winusername>,password=<winpassword>

```

You would then enter /mnt/<servername> as the UNC path for TrackIt. You should then be able to connect to the TrackIt database. You might also consider further research regarding mounting Windows shares because of the prevalence of Windows in your environment. Good luck.

---

