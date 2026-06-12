---
title: "Problem with DVD"
date: 2008-05-25
forum: General Help
---

### Post by j0hnj0hn on 2008-05-25
Hello i have a problem trying to use my DVD device.

i have a Asus DVD-CD but it's not working since i have ubuntu 7.10, now i have ubuntu 8.04 and still not working.

first my dvd device is not mounted at start up my PC so i have to try mounting manualy, i have tried a thousand ways to mount it but i think its all the same...

```

j0hn@anger:/media$ sudo mount /dev/cdrom1 cdrom0/
[sudo] password for j0hn: 
mount: dispositivo de bloques /dev/scd0 está protegido contra escritura; se monta como sólo lectura
mount: debe especificar el tipo de sistema de ficheros
j0hn@anger:/media$ 

```

it's in spanish but it says that /dev/scd0 is write protected and that it's mounted read only. also says that i have to especify the file type

here's another way:
```

j0hn@anger:/media$ sudo mount -t udf /dev/sr0 cdrom0/
mount: dispositivo de bloques /dev/scd0 está protegido contra escritura; se monta como sólo lectura
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido

j0hn@anger:/media$ 

```

other:

```

j0hn@anger:/media$ sudo mount -t iso9660 /dev/sr0 /media/cdrom0/
mount: dispositivo de bloques /dev/scd0 está protegido contra escritura; se monta como sólo lectura
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido

j0hn@anger:/media$ 

```

it's all like that...

i don't know what to do, maybe someone can help.

here's my fstab:

```

j0hn@anger:/media$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=17f1b6a2-c2fa-48d4-b6e8-c33bf2b6563d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=32ffcb1f-a03b-4b8d-a0d5-e5ad3aca6f79 /home           ext3    defaults        0       2
# /dev/sda1
UUID=c67ff48f-6d4e-4e4c-b4ab-ddb2882828d6 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
j0hn@anger:/media$

```

and my dmesg it's here [http://pastebin.org/38436](http://pastebin.org/38436)

i hope you can help me, sorry if someone else posted this problem but i couldn't find a way to solve this...

Thanks.

---

### Post by ibuclaw on 2008-05-25
Firstly, can you post the output of the command "**df**"?
Just type in```
df
```in the terminal.

Secondly, append **utf8** your cdrom line in the fstab file.
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec**,utf8** 0       0
```

Also, maybe adding the read-only option may help.
```
sudo mount -o r -t udf /dev/scd0 /cdrom0
```

Regards
Iain

---

### Post by j0hnj0hn on 2008-05-25
here's my "df" output:

```

j0hn@anger:~$ df
S.ficheros         Bloques de 1K   Usado    Dispon Uso% Montado en
/dev/sda3             15567620   5024668   9752156  35% /
varrun                  257804       124    257680   1% /var/run
varlock                 257804         0    257804   0% /var/lock
udev                    257804        52    257752   1% /dev
devshm                  257804        12    257792   1% /dev/shm
lrm                     257804     38176    219628  15% /lib/modules/2.6.24-16-generic/volatile
/dev/sda2             60317472  41981596  15271880  74% /home
j0hn@anger:~$ 

```

i have add utf8 to my fstab and here's the output again:

```

j0hn@anger:~$ sudo mount -o r -t udf /dev/scd0 /media/cdrom0/
mount: dispositivo de bloques /dev/scd0 está protegido contra escritura; se monta como sólo lectura
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       En algunos casos se encuentra información en syslog, pruebe
   dmesg | tail   o algo parecido

j0hn@anger:~$ 

```

---

### Post by j0hnj0hn on 2008-05-26
anything else i can try? plz help

thanks...

---

