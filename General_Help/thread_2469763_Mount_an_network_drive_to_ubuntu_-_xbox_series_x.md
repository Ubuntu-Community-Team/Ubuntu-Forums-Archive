---
title: "Mount an network drive to ubuntu - xbox series x"
date: 2021-12-08
forum: General Help
---

### Post by Kusho on 2021-12-08
Ok I am trying to do a walkthru for Windows on a Ubuntu pc.  That is making it rather difficult.

I know a little about Ubuntu but by far am not an expert.
The walkthru I am doing is here
[https://www.youtube.com/watch?v=BdQJVUvlG3A](https://www.youtube.com/watch?v=BdQJVUvlG3A)

I am trying to mount my Xbox Series X as a network drive so I can copy files into it.  
The walktrhu for that on Ubuntu I found was here

[https://askubuntu.com/questions/46183/how-to-map-a-network-drive](https://askubuntu.com/questions/46183/how-to-map-a-network-drive)

My Xbox says this

Instructions

Open a file explorer and go to:

\\192.168.0.35\DevelopmentFiles

Username: 192.168.0.35\DevToolsUser

Password: password

If you don't want to enter credentials, you can run this command from a command prompt, then browse to \\192.168.0.35\DevelopmentFiles:

cmdkey.exe /add:192.168.0.35 /user:192.168.0.35\DevToolsUser /pass:"password"


The command I am trying to run is this in terminal

tom@tom-Inspiron-5755:~$ sudo mount -t cifs -o username=192.168.0.35\DevToolsUser //192.168.0.35/DevelopmentFiles /media/Data/
[sudo] password for tom: password
mount: /media/Data/: mount point does not exist.
tom@tom-Inspiron-5755:~$ 

What am I doing wrong?  And be gentle.

---

### Post by TheFu on 2021-12-09
I don't have any clue. Never seen or touched any Xbox. They were too loud.

'\' is an escape character on Unix systems.  IF you want a '\' character, then use '\\'

The error,*  /media/Data/ mount point does not exist.* tells me that the directory hasn't been created.  You should create it.  
**sudo mkdir -o /media/Data** and try again.  Mount commands expect the directory to pre-exist where they are mounted.

I think that's it.  Good job using //IP/remote-loocation.  That is correct.

I don't know what cmdkey.exe does. That's a new program to me. According to the MSFT documentation, that program is for Windows Server products. [https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/cmdkey](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/cmdkey) has examples.

---

### Post by Kusho on 2021-12-10
tom@tom-Inspiron-5755:~$ sudo mkdir /Xbox/
tom@tom-Inspiron-5755:~$ sudo mount -t cifs -o username=192.168.0.35\DevToolsUser //192.168.0.35/DevelopmentFiles /Xbox/
mount: /Xbox: mount(2) system call failed: Operation now in progress.
tom@tom-Inspiron-5755:~$ 


I changed the dir name to Xbox.  but still it didn't seem to work.

And yes the cmdkey.exe was for Windows.  I just included all that the Xbox told me.

---

### Post by Kusho on 2021-12-10
tom@tom-Inspiron-5755:~$ sudo mount -t cifs -o username=192.168.0.35\DevToolsUser //192.168.0.35/DevelopmentFiles /Xbox/
mount: /Xbox: cannot mount //192.168.0.35/DevelopmentFiles read-only.
tom@tom-Inspiron-5755:~$ 


I logged back into Development Mode in my Xbox.  But still it doesnt work.  Seems the command is correct for Ubuntu thou.  now I have to figure out how to enable Read Write access on my Xbox.  I watched this section further in the Walkthru but it just says to map the drive then you can make folders in the Xbox.  It has to be both read and write to do this.  They don't say I need to do anything other than run that cmdkey.exe comandlet in Windows and then map a network drive.  I am stumped.
Is there a way to enter both my username and my password in with the mount command?  In windows it logged in.  As it now all it has in the command is the username.

---

### Post by TheFu on 2021-12-10
Yes, you can use the "credentials" file mount option.  That is spelled out in the manpage for mount.cifs.  The relevant part:
```
       credentials=filename|cred=filename
                 specifies  a  file  that contains a username and/or password and
                 optionally the name of the workgroup. The format of the file is:

                     username=value
                     password=value
                     domain=value

              This is preferred over having passwords in plaintext  in  a  shared
              file,  such as /etc/fstab . Be sure to protect any credentials file
```
Probably best to check the exact manpage ON-YOUR-SYSTEM, since these things change and the version on-your-system will be for the version of the mount.cifs command there. Don't trust googled results. There are specific examples in these forums and a few caveats (for security), if you need it.

---

