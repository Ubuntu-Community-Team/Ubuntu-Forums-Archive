---
title: "SCP command"
date: 2013-04-02
forum: General Help
---

### Post by saande on 2013-04-02
The content of my script is:

cp -b /home/ionadmin/my_script5.sh [\\192.168.0.174\pgm]("file://192.168.0.174/pgm")
cp -b /home/ionadmin/my_script5.sh [\\192.168.0.174\proton]("file://192.168.0.174/proton")
 
 
echo
echo "Done!"
date
echo
 
I've done the following 3 tests :
 
Test1
I first copied a local file from the Ubuntu server to another folder within the ubuntu server and that worked fine.
 
Test2
Second, I tried to copie a local file from the Ubuntu server (Ubuntu 10.04.2 LTS) to a Windows server (192.168.0.174). The Windows is freely accessible, there is no proxy, firewall or any acces restriction. Anyone can go on it. Does it work? Well, it depends how we interpret the feedback: I do not get any error message on screen but after 30min still nothing is copied. 

Test3
I try to do the same in command line but all tentatives failed: 

If I execute the command : « ssh sudo cp my_script5.sh //192.168.0.174 »

[LIST]
[*]I get the error message : « ssh: Could not resolve hostname sudo: Temporary failure in name resolution »
[/LIST]
 
Althought I'm at the root, I execute the csame command with the full path of the file to be copied, 

[LIST]
[*]I get the same error message
[/LIST]
 
If I do a normal transfer, I use the command « sudo cp my_script5.sh //192.168.0.174 »

[LIST]
[*]I get an invitation to type in my Ubuntu password and that's what I do.
[*]The system brings me back to the root and no further message.
[/LIST]
 
I've done a ping, from the Ubuntu server to the Windows server and it was successfull.

Is there a way to complete the script or get to know where it blocks? To complete you with some usefull information: The Ubuntu server is managed by another department and they have granted me (Network Administrator) with full access to some specific folders so I'd be able to copy the requested files. The fact is that I have no acces to create a CRON or create a cache file.

Any idea?

---

### Post by CaptainMark on 2013-04-02
I'm no expert on scp but when I have used it, the command should look something like this ```
scp /home/mark/somefile otheruser@192.168.0.174:/home/otheruser/somefile
```

---

### Post by btindie on 2013-04-02
From your description it's not particularly clear what it is you're trying to achieve.

The below won't work as you're specifying what would be a command, sudo, where you're supposed to specify the hostname. But as this is a windows box you're trying to connect to it more than likely doesn't support SSH/SCP.
> **saande said:**
> 
If I execute the command : « ssh sudo cp my_script5.sh //192.168.0.174 »

[LIST]
[*]I get the error message : « ssh: Could not resolve hostname sudo: Temporary failure in name resolution »
[/LIST]

 
You're probably better off first [mounting]("http://www.thatsquality.com/articles/mounting-windows-smb-file-shares-using-cifs") the windows share locally and then copying the files. I've never tried copying the files directly to a windows share (//192.168.0.174/rubbish/) and doubt it works with the cp command.

When it prompts you for your Ubuntu password, that would be because you're using the sudo command which depending on your sudoers config is required.

---

### Post by Lars Noodén on 2013-04-02
Also mind that Linux uses slashes (/) in paths, not backslashes (\)

You might want to use sftp instead.  That can be used interactively or in batch mode.

---

### Post by saande on 2013-04-08
Hi,

Thanks for your advice but the windows server has no SFTP or FTP activated/functioning.

---

### Post by saande on 2013-04-08
Indeed, copying it to any Windows share does not work at all. If I copy it to another location/folder on that LInux system it works without any problem. When trying to copy it to a windows share I always get "is not a directory". 
I can ping the windows share, which has a specific IP, but I cannot copy anything on it.

---

### Post by saande on 2013-04-08
When using this or even bashto verify command, I always get cp: target [EMAIL="`@19.168.0.174:/pgm'"]`@19.168.0.174:/pgm'[/EMAIL] is not a directory

---

### Post by Lars Noodén on 2013-04-08
> **saande said:**
> Hi,

Thanks for your advice but the windows server has no SFTP or FTP activated/functioning.

If you have SSH, then you also have SFTP.   It is built into OpenSSH server.  It would be possible to turn it off, but it is on by default.

---

