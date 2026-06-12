---
title: "Please help me to copy a file on to a USB stick"
date: 2016-05-30
forum: General Help
---

### Post by Gins on 2016-05-30
I am using ' Ubuntu 14.04.4 LTS '


I am struggling to copy a file from my 'Downloads' folder to a USB stick.



The name of the file is ' T-CRLPEUHC_2009.0.exe '
 

I must copy the above file onto a USB stick.

**Please help me to copy the file in question.**
--------------------------------------------------
The location of the USB stick is /media.

The name is usb0
**[ When right clicking the USB stick, I got the above details.]**
--------------------------------------------------

&#8230;....................................................................................................
ni@Ni:~/Downloads$ ls -a
.                                       021 - 2016-05-10 - ARN- Skrivelse.pdf
..                                      DriverDownloader.exe
018 - 2016-04-19 - ARN- Meddelande.pdf  ls
019 - Missiv fr mp.pdf                  
020 - SVAROMÅL (1).pdf                  
**T-CRLPEUHC_2009.0.exe**
020 - SVAROMÅL.pdf
ni@Ni:~/Downloads$ 


&#8230;.....................................................................................................
ni@Ni:~/Downloads$ sudo cp /T-CRLPEUHC_2009.0.exe /media/usb0
[sudo] password for ni: 
cp: cannot stat &#8216;/T-CRLPEUHC_2009.0.exe&#8217;: No such file or directory
ni@Ni:~/Downloads$ ls
&#8230;.....................................................................................................

ni@Ni:~/Downloads$ sudo cp /'T-CRLPEUHC_2009.0.exe' /media/usb0
**cp: cannot stat &#8216;/T-CRLPEUHC_2009.0.exe&#8217;: No such file or directory**
ni@Ni:~/Downloads$ 
&#8230;................................................................................

ni@Ni:~/Downloads$ sudo cp /'T-CRLPEUHC_2009.0.exe' /dev/sdb1
**cp: cannot stat &#8216;/T-CRLPEUHC_2009.0.exe&#8217;: No such file or directory**
ni@Ni:~/Downloads$ 

&#8230;..........................................................................................................

ni@Ni:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 931,5G  0 disk 
&#9500;&#9472;sda1   8:1    0   309G  0 part 
&#9500;&#9472;sda2   8:2    0 165,4G  0 part 
&#9500;&#9472;sda3   8:3    0 146,5G  0 part 
&#9500;&#9472;sda4   8:4    0    18M  0 part 
&#9500;&#9472;sda5   8:5    0     2G  0 part [SWAP]
&#9500;&#9472;sda6   8:6    0    10G  0 part 
&#9500;&#9472;sda7   8:7    0   134G  0 part 
&#9492;&#9472;sda8   8:8    0 164,7G  0 part /

[B]
sdb      8:16   1 480,5M  0 disk 
&#9492;&#9472;sdb1   8:17   1 480,5M  0 part /media/usb0[/B]
sr0     11:0    1  1024M  0 rom  
ni@Ni:~$ 

( The hard drive is 'sda'. And I have several partitions on my hard drive.)
( The above shows 'sdb' as the USB stick. )

&#8230;......................................


ni@Ni:~$ cd Downloads
ni@Ni:~/Downloads$ pwd
/home/ni/Downloads
ni@Ni:~/Downloads$ 

**The above shows that I am in the 'Downloads' folder'.**

---

### Post by Impavidus on 2016-05-30
> **Gins said:**
> ```

ni@Ni:~/Downloads$ [COLOR=#008800]**sudo**[/COLOR] cp [COLOR=#ff0000]**/**[/COLOR]T-CRLPEUHC_2009.0.exe /media/usb0
[sudo] password for ni: 
cp: cannot stat ‘/T-CRLPEUHC_2009.0.exe’: No such file or directory
```

Drop the leading / from the filename. The leading slash indicates this is an absolute path, starting at the root directory. You use a relative path, so you should not use the leading /.

Depending on how you mounted you may not need root permissions to copy the file. Is this a server (no gui)? Because Ubuntu desktop systems would automount the usb drive somewhere else, where you wouldn't need root permissions to write.

---

### Post by Gins on 2016-05-30
Thanks for the reply.
It did not work.

Please read the following output.


ni@Ni:~$ sudo cp T-CRLPEUHC_2009.0.exe /media/usb0
[sudo] password for ni: 
**cp: cannot stat &#8216;T-CRLPEUHC_2009.0.exe&#8217;: No such file or directory**
ni@Ni:~$

........................................................................................................................
I have a desktop computer. I don't have a server.

Maybe the path is incorrect. I am not good at this things.
( dev/sdb1 is mounted at /media/usb0 )

---

### Post by steeldriver on 2016-05-30
You originally posted
```

ni@Ni:[COLOR=#0000ff]~/Downloads[/COLOR]$ ls -a
.                                       021 - 2016-05-10 - ARN- Skrivelse.pdf
..                                      DriverDownloader.exe
018 - 2016-04-19 - ARN- Meddelande.pdf  ls
019 - Missiv fr mp.pdf                  
020 - SVAROMÅL (1).pdf                  
**T-CRLPEUHC_2009.0.exe**
020 - SVAROMÅL.pdf
ni@Ni:~/Downloads$

```
indicating that you were in your Downloads directory when you issued the ls command. Now you have 
```

ni@Ni:[COLOR=#0000ff]~[/COLOR]$ sudo cp T-CRLPEUHC_2009.0.exe /media/usb0
[sudo] password for ni: 
**cp: cannot stat ‘T-CRLPEUHC_2009.0.exe’: No such file or directory**
ni@Ni:~$

```
showing that you are in your ~ (HOME) directory, so the command would need to be

```

cp Downloads/T-CRLPEUHC_2009.0.exe /media/usb0

```
or
```

cd Downloads

cp T-CRLPEUHC_2009.0.exe /media/usb0

```

---

### Post by dave238 on 2016-05-31
You could be trying to copy it to the wrong place.

The usb has a "device name" of usb0 but that will actually be mounted under a different name in /media/USER/name_of_device

For instance on my machine i have a USB hard drive with name sdb, and partitions sdb1 and sdb2. This is actually mounted to /media/dave/4TBHDD

If you type: 
cd /media/USERNAME/
ls

It will show the names of attacted devices to copy your file to.

---

### Post by Gins on 2016-05-31
Thanks everybody for the help.
**It did not work.**

ni@Ni:~$ cp Downloads/T-CRLPEUHC_2009.0.exe /media/usb0
cp: cannot create regular file &#8216;/media/usb0/T-CRLPEUHC_2009.0.exe&#8217;: Permission denied
ni@Ni:~$ 

&#8230;..................................

ni@Ni:~/Downloads$ cp T-CRLPEUHC_2009.0.exe /media/usb0
cp: cannot create regular file &#8216;/media/usb0/T-CRLPEUHC_2009.0.exe&#8217;: Permission denied
ni@Ni:~/Downloads$ 

&#8230;......................................................................................

ni@Ni:~$ cd/media/ni ls
bash: cd/media/Ni: No such file or directory
ni@Ni:~$ 

&#8230;.............................................................................................
ni@Ni:/media$ ls
ni  usb  usb0  usb1  usb2  usb3  usb4  usb5  usb6  usb7

&#8230;........................................................................................

ni@Ni:/media$ cd ni
ni@Ni:/media/ni$ ls
............................................................................................

Inside 'ni' directory has not got anything.
Because the output of the command ' ls ' was empty.


[B]( I have not tried as a root user. Because it did not ask.)

For some reason the command ' cd/media ' worked.

The command ' cd/media/ni ' did not work.[/B]

The command  ' cd ni ' worked.

---

### Post by howefield on 2016-05-31
What is the output of 

```
ls -al /media/ni/
```

---

### Post by Gins on 2016-05-31
Hi

The following worked. Thanks everybody

sudo cp Downloads/T-CRLPEUHC_2009.0.exe /media/usb0

---

