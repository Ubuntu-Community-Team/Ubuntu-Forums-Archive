---
title: "Ubuntu 16.04.5 mounting cifs from Freenas unable to write"
date: 2019-08-15
forum: General Help
---

### Post by morphius1971 on 2019-08-15
Hello Everyone,
I'm struggling with permissions.

I have a windows share mounted in fstab like this:
```
//10.10.10.2/Download /download3 cifs credentials=/home/morphius/.smbcredentials,vers=3.0,rw,user,exec,umask=0022,uid=1000 0 0
```

.smbcredentials content: 
```
username=morphius.local/morphius
password=XXXXXXX

```

The share is mounted
```
drwxr-xr-x  2 morphius morphius        0 Aug 15 11:21 .
drwxr-xr-x 27 root     root         4096 Aug 15 11:20 ..
-rwxr-xr-x  1 morphius morphius    20771 Mar 13  2017 Bestellen.docx
drwxr-xr-x  2 morphius morphius        0 Nov  4  2018 Dropbox
-rwxr-xr-x  1 morphius morphius      355 Aug 14 20:44 _password.txt
drwxr-xr-x  2 morphius morphius        0 Aug 15 00:28 processed
drwxr-xr-x  2 morphius morphius        0 Jul 14 23:10 temps
-rwxr-xr-x  1 morphius morphius        0 Aug 15 11:21 test.txt

```


The mount point has the following settings:
```
drwxr-xr-x   2 morphius morphius     0 Aug 15 10:46 download3

```
And when i mount there are no errors:
```
morphius@sabnzb:/$ sudo mount -av
/                        : ignored
/boot                    : already mounted
none                     : ignored
/download3               : already mounted
/plex                    : already mounted

```

But when i want to create a folder i don't have the permissions
```
morphius@sabnzb:/$ sudo mkdir /download3/test
mkdir: cannot create directory ‘/download3/test’: Permission denied

```
On the Freenas i've set the permissions like this
[https://drive.google.com/file/d/1O8hi-T3qBs5xajW0b2WpXC1e4JolilB_/view?usp=sharing](https://drive.google.com/file/d/1O8hi-T3qBs5xajW0b2WpXC1e4JolilB_/view?usp=sharing)[IMG]https://drive.google.com/file/d/1O8hi-T3qBs5xajW0b2WpXC1e4JolilB_/view?usp=sharing[/IMG]

I've been at it for over 3 days and look at all different post i found on google.
But still it will no work.

Please someone help me so i can get some sleep again.......
I'm pulling out my hair :?

---

### Post by Morbius1 on 2019-08-15
What happens when you add [COLOR=#0000cd]**nounix**[/COLOR] to the list of options.

---

### Post by morphius1971 on 2019-08-15
Hay Mobius1,

Tried it and nope, doesn't do a thing.

Also something strange, I have already a folder download and download2.
These folders are not just for mounting.
But still all files are there can not been remove (sudo rm -Rf /download) 
```
morphius@sabnzb:/download$ sudo rm -rf Bestellen.docx
rm: cannot remove 'Bestellen.docx': Permission denied
```

Content folder
```
morphius@sabnzb:/download$ ls -al
total 23556
drwxr-xr-x  2 root root        0 Aug 15 11:21 .
drwxr-xr-x 27 root root     4096 Aug 15 11:20 ..
-rwxr-xr-x  1 root root    20771 Mar 13  2017 Bestellen.docx
drwxr-xr-x  2 root root        0 Nov  4  2018 Dropbox
-rwxr-xr-x  1 root root      355 Aug 14 20:44 _password.txt
drwxr-xr-x  2 root root        0 Aug 15 00:28 processed
drwxr-xr-x  2 root root        0 Jul 14 23:10 temps
-rwxr-xr-x  1 root root        0 Aug 15 11:21 test.txt
-rwxr-xr-x  1 root root  1139147 May 31  2018 VBCABLE_Driver_Pack43.zip
-rwxr-xr-x  1 root root 18239000 May 31  2018 VoicemeeterProSetup.exe

```

the same for the folder dowlnoad2

---

### Post by freedombacon on 2019-08-15
Try using the noperm option. It prevents the client from checking the permissions, leaving it to the server. It can help if there's a mismatch between UIDs. You might need to remove uid and umask options, too.

---

### Post by morphius1971 on 2019-08-15
nope fails
```
//10.10.10.2/Download /download3 cifs credentials=/home/morphius/.smbcredentials,vers=3.0,rw,user,exec,noprem,umask=0022,uid=1000 0 0
```

---

### Post by Morbius1 on 2019-08-15
Well, without actually installing FreeNAS I don't know how to proceed. 

I would just like to note that all of the permissions you posted are the permissions on the client not the server. A cifs mount is virtual so the permissions correctly reflect your cifs mount statement: on the client system uid=1000 has write access and everyone else - on the client - has read only access ( 755 ).

On the server it's set to allow the owner ( morphius ) and group ( nogroup ) write access and everyone else read access ( 775 ).

All of that should still work but it almost looks like you have an ACL set on the /mnt/Tank/Download folder on the server. Is there any way you can run an ls on the server to determine it's true permissions:
```
ls -dl /mnt/Tank/Download
```

---

### Post by morphius1971 on 2019-08-15
This is straight from the server
```

[root@freenas /mnt/Tank]# ls -al Download/                                      total 37979                                                                     
-rwxrwxr-x+  1 MORPHIUS\morphius  nogroup       355 Aug 14 20:44 _password.txt  
drwxrwxr-x+  5 MORPHIUS\morphius  nogroup        11 Aug 15 11:21 .              
drwxrwxrwx   7 Morphius           nogroup         7 Jul 23 19:56 ..             
-rwxrwxr-x+  1 MORPHIUS\morphius  nogroup         0 Aug 14 23:10 .windows       
-rwxrwxr-x+  1 MORPHIUS\morphius  nogroup     20771 Mar 13  2017 Bestellen.docx 
drwxrwxr-x+  2 MORPHIUS\morphius  nogroup         2 Nov  4  2018 Dropbox        
drwxrwxr-x+ 11 MORPHIUS\morphius  nogroup        11 Aug 15 00:28 processed      
drwxrwxr-x+ 49 MORPHIUS\morphius  nogroup        49 Jul 14 23:10 temps          
-rwxrwxr-x+  1 MORPHIUS\morphius  nogroup         0 Aug 15 11:21 test.txt       
-rwxrwxr-x+  1 MORPHIUS\morphius  nogroup   1139147 May 31  2018 VBCABLE_Driver_
Pack43.zip                                                                      
-rwxrwxr-x+  1 MORPHIUS\morphius  nogroup  18239000 May 31  2018 VoicemeeterProSetup.exe

```

---

### Post by Morbius1 on 2019-08-15
> drwxrwxr-x+  5 MORPHIUS\morphius  nogroup        11 Aug 15 11:21 . 
That "+" at the end is an extended permissions flag - usually an acl.

Can you run the following next please to confirm if morphius really does have write access:
```
getfacl /mnt/Tank/Download
```

---

### Post by morphius1971 on 2019-08-15
output:
```
[root@freenas ~]# getfacl /mnt/Tank/Download                                    
# file: /mnt/Tank/Download                                                      
# owner: MORPHIUS\morphius                                                      
# group: nogroup                                                                
            owner@:rwxpDdaARWcCos:fd-----:allow                                 
            group@:rwxpDdaARWcCos:fd-----:allow                                           
       everyone@:r-x---a-R-c---:fd-----:allow   
```

I do have to note i'm using active directory.

---

### Post by Morbius1 on 2019-08-15
> I do have to note i'm using active directory.		
You're killin' me. This isn't an ext4 filesystem either is it? This has become above my pay grade. 

From what I can understand it looks like morphius has write access but ...

---

### Post by morphius1971 on 2019-08-15
Nope it's ntfs windows file system 
and yes [EMAIL="morphius@morphius.local"]morphius@morphius.local[/EMAIL] has read/write permissions and it work with my windows pc
and it did work before, but after a restart of the nas it failed

i got this error
```

mount.cifs kernel mount options: ip=10.10.10.2,unc=\\10.10.10.2\Download,noprem,umask=0022,uid=1000,user=morphius.local/morphius,pass=********
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```
and after adding vers=3.0...even vers=2.0
removed the error and the connecting was made

---

### Post by Morbius1 on 2019-08-15
There is one thing that I don't think actually matters at this point - and I'm embarrassed I didn't see it before - but there is no such parameter as **umask** in mount.cifs. It's [B]dir_mode=0755

[COLOR=#0000cd]EDIT[/COLOR][/B]: It's the opposite of a umask. It represents the permissions you want to have on the client side.It's usually followed by the corresponding file_mode for files:
file_mode=0644 - or file_mode=0755.

---

### Post by morphius1971 on 2019-08-15
nope still nothing

---

### Post by morphius1971 on 2019-08-15
Don't really know how but this works now
```

//10.10.10.2/Download /download cifs rw,user=Morphius,password=XXXXXXXXX,vers=3.0,uid=1000,iocharset=utf8,sec=ntlm       0       0
//10.10.10.2/Media /plex cifs username=morphius,password=XXXXXXXXX,vers=3.0,uid=1000,iocharset=utf8,sec=ntlm     0       0

```

Just added my AD user to the permissions of the root of the share and it magically worked.

Men i can get some sleep again :popcorn:

---

