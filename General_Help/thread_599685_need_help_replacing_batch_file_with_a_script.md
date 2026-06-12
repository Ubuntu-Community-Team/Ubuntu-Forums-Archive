---
title: "need help replacing batch file with a script"
date: 2007-11-01
forum: General Help
---

### Post by 1d2n on 2007-11-01
I need to replace a very simple batch file

```
move \\192.168.1.8\faxes\*.* \\192.168.1.3\faxes
```

it moves received faxes to a file server. I have been trying to do this with a bash script and have not gotten it to work. the only way I seem to be able to get it to work is if I mount the shares and mv from one directory to the other. I would rather not do that on every machine I need to run this from. is there any way to copy the files directly from the shares without mapping them. any ideas ?
thanks

---

### Post by cwaldbieser on 2007-11-01
> **1d2n said:**
> I need to replace a very simple batch file

```
move \\192.168.1.8\faxes\*.* \\192.168.1.3\faxes
```

it moves received faxes to a file server. I have been trying to do this with a bash script and have not gotten it to work. the only way I seem to be able to get it to work is if I mount the shares and mv from one directory to the other. I would rather not do that on every machine I need to run this from. is there any way to copy the files directly from the shares without mapping them. any ideas ?
thanks

If the samba package is installed, you can use the "smbclient" command.

---

### Post by 1d2n on 2007-11-01
> **cwaldbieser said:**
> If the samba package is installed, you can use the "smbclient" command.

I tried that but couldn't get the syntax right and kept getting errors. The man page was not much help I don't know if I had the right number of //// or if the command was completely wrong.
thanks

---

### Post by kast on 2007-11-01
To connect to a Windows computer try

**smbclient //cholera/C$ -U username -W workgroup **

or

 **   smbclient //cholera/C -U Administrator -W workgroup **

---

### Post by kast on 2007-11-01
Source

[http://brneurosci.org/linuxsetup38b.html](http://brneurosci.org/linuxsetup38b.html)

---

### Post by 1d2n on 2007-11-02
ok heres the script I ended up with. I am running it as a cron job every 5 minutes on the server, its bsd thats why the path to bash is different. thanks for your help

```

#!/usr/local/bin/bash
cd /usr/data/faxes
smbclient //192.168.1.8/faxes -U username%password -W workgroup -c "cd inv;prompt;mget *;exit"
smbclient //192.168.1.8/faxes -U username%password -W workgroup -c "cd inv;prompt;del *;exit

```

---

### Post by kast on 2007-11-02
Your welcome! hey your missing your closing " on the second line in cron

---

