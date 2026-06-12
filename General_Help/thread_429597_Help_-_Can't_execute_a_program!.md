---
title: "Help - Can't execute a program!"
date: 2007-05-01
forum: General Help
---

### Post by hypersire on 2007-05-01
Hi all - I just finished installing the Cisco VPN client on Xubuntu 7.04. I know that it installed OK because I am able to run the service via a startup script. After initiating the service, you are supposed to run the client by simply entering "vpnclient connect name_of_cfg_file". However, when I try that (by itself and also with the sudo option) this is what I get:

From within /usr/bin which contains a symlink (did an ls -l so you can see the file is there and the permissions):

```
hypersire@turion:/usr/bin$ ls -l vpnclient
lrwxrwxrwx 1 root root 34 2007-05-01 09:09 vpnclient -> /opt/cisco-vpnclient/bin/vpnclient
hypersire@turion:/usr/bin$ vpnclient connect gs
bash: /usr/bin/vpnclient: No such file or directory
hypersire@turion:/usr/bin$ 
```

From within the directory that holds the actual exe:

```
hypersire@turion:/opt/cisco-vpnclient/bin$ ls -l vpnclient
---x--x--x 1 root bin 666260 2007-05-01 09:09 vpnclient
hypersire@turion:/opt/cisco-vpnclient/bin$ vpnclient connect gs
bash: /usr/bin/vpnclient: No such file or directory
```

As I mentioned, I tried it as sudo and it doesn't make a difference - same error.

I don't think it has anything to do with the program or the install - it must be a linux thing (permissions, the way I am executing it, etc.) - I am new to linux so I wouldn't be surprised if it is something simple that I am overlooking.

Thanks in advance !!

hypersire

---

### Post by taurus on 2007-05-01
Try 

```
cd /opt/cisco-vpnclient/bin
./vpnclient connect gs
```
or
```
/opt/cisco-vpnclient/bin/vpnclient connect gs
```

---

### Post by hypersire on 2007-05-01
Thanks for the quick reply - unfortunately still no go - same no such file or directory error.

I did make an insteresting discovery:

In the File manager, the symbolic link found in /usr/bin says it is of the Type "link to vpnclient document". I went to the actual directory that is supposed to house the exe (/opt/cisco-vpnclient/bin) and here the File manager says that vpnclient is of the Type "vpnclient document". It does not list it as an executable. It is however the same file size as the actual exe found in the folder I used to install the program.

Just for kicks I tried running the exe from the install folder and even then, I still get the same no such file or folder error.

Does this help any?

Thanks a lot!

---

### Post by taurus on 2007-05-01
```
cd /opt/cisco-vpnclient/bin
file vpnclient
ls -la vpnclient
```
Post the output of the last two commands here.

---

### Post by hypersire on 2007-05-01
Thanks for your help Taurus - I really appreciate it. 

I just got called into a mtg - will post the results later this afternoon.

hypersire

---

### Post by hypersire on 2007-05-01
Here is the output from the commands:

hypersire@turion:~$ cd /opt/cisco-vpnclient/bin
hypersire@turion:/opt/cisco-vpnclient/bin$ file vpnclient
vpnclient: executable, regular file, no read permission
hypersire@turion:/opt/cisco-vpnclient/bin$ ls -la vpnclient
---x--x--x 1 root bin 666260 2007-05-01 09:09 vpnclient
hypersire@turion:/opt/cisco-vpnclient/bin$ 

I am stumped - it says it is an executable file, but as I mentioned before, using the File manager it lists it as Type="vpnclient document". When I browse to the original install files, there vpnclient is listed as an executable.

I know it is something specific to my system - I've searched on the net and no one else who has installed the Cisco VPN client is posting this problem. 

Thhanks for your help.

---

### Post by taurus on 2007-05-01
Try

```
cd /opt/cisco-vpnclient/bin
sudo chmod 755 vpnclient
file vpnclient
```

---

### Post by hypersire on 2007-05-01
Ok, here are the results:

```
vpnclient: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped
```

 I am running the 64-bit version of Xubuntu and I did install the 64-bit version of the Cisco client.

---

### Post by taurus on 2007-05-01
> **hypersire said:**
> Ok, here are the results:

```
vpnclient: **[COLOR="Red"]ELF 32-bit LSB executable[/COLOR]**, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped
```

 I am running the 64-bit version of Xubuntu and I did install the 64-bit version of the Cisco client.

Sorry but it is a 32-bit version of the software. So, you can go back and reinstall the 64bit version or you can install all the necessary 32bit libraries to run a 32bit binary in a 64bit environment.

---

### Post by hypersire on 2007-05-01
I am sure I installed the 64-bit version - this was the package I used:

vpnclient-linux-x86_64-4.8.00.0490-k9.tar.gz

So it must be that the client piece of the VPN is 32-bit and others that are able to run it have the necessary libraries and I don't.

I did notce that after forcing an install of the 32-bit Skype, I am also unable to run it - same error - no such file or directory.

Could you point me in the right direction on how to go about installing these 32-bit libraries?

Thanks a lot!

---

### Post by taurus on 2007-05-01
Post the output of the last command here.

```

cd /opt/cisco-vpnclient/bin
ldd vpnclient

```

---

### Post by hypersire on 2007-05-01
Here are the results (unexpected?):

```
hypersire@turion:~$ cd /opt/cisco-vpnclient/bin
hypersire@turion:/opt/cisco-vpnclient/bin$ ldd vpnclient
        not a dynamic executable
```

---

### Post by hypersire on 2007-05-02
After doing some browsing on these forums, turns out that the Cisco client is more trouble than it is worth. I am very happy to say I managed to get the open source VPNC working and no longer have a need for the Cisco client. Even better, now that I can connect to my work XP box through Linux, I can say goodbye to windoze forever!!

Thanks for your help on this. Quick question - why was I getting a "no such file or directory" error even though the file was clearly present? I assume that in Linux, you will get this error if the file is there but something is wrong (e.g. you do not have the associated libraries)??

---

