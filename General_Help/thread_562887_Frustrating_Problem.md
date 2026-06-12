---
title: "Frustrating Problem"
date: 2007-09-29
forum: General Help
---

### Post by troubl3dmind on 2007-09-29
I'm having a problem copying files to a disc in ubuntu.  I'm trying to copy  a uif file to a disc so i can extract it on my windows machine since linux makes it more difficult than it has to be to do this.  Every time i try to copy the file it says, "You do not have permissions to write to this folder."  Now, i'm logged in as root.  I don't know how much more permissions I can get.  Does anyone know the answer to this frustrating problem?

---

### Post by gnudoc on 2007-09-29
sounds like the folder you are trying to copy to is not writeable. if you are using ubuntu (not kubuntu etc), check this by opening the folder, right-clicking on some empty space in the window and going to properties. in the permissions tab, check what folder access is set to. make sure it's "create and delete files".

if you're not using ordinary ubuntu, or nautilus is not your file manager, then i'm not sure of the graphical steps you need.

however typing the following into a terminal should work. (but you'll need to go to the offending folder in the terminal first)
```
chmod u+w .
```

hope that helps.
gnudoc

---

### Post by wesleybailey on 2008-04-12
You can use UIF2ISO in Ubuntu, and use it to convert the .uif file to an .iso. Then you can burn it with k3b.

1. You need to install zlib and OpenSSL with apt-get.
```

sudo apt-get install zlib1g zlib1g-dev libssl-dev

```
2. You can download UIF2ISO with wget from a terminal, or from the author’s site here.
```

wget http://aluigi.altervista.org/mytoolz/uif2iso.zip

```

3. Unzip, make, and make install the file, and finally.
```

uif2iso example.uif output.iso

```

---

### Post by nowhere@cox.net on 2008-04-16
I have used this tool in the past tho I can't remember the details. I am again trying to use it with two errors. I downloaded, make, make install the latest version with no errors. When running on a 1.3GB uif file, it gets to 99% then gives error Invalid Argument.  I found a famous post by sharonz on the web claiming a fix by using fseeko etc. instead of fseek but this was for OSX. Also, it was supposed to be fixed in this version.

Next problem, I tried to test it on another uif file (this one 2.9 GB) and I get 
```
UIF2ISO 0.1.3
by Luigi Auriemma
e-mail: aluigi@autistici.org
web:    aluigi.org

- open test.uif
- create test.iso
- the output file already exists, do you want to overwrite it (y/N)? y
  an error here means that your exe has no full LARGE_FILES 64 bit support!

Error: Invalid argument

```

I don't know enough about the c file to try to make it compile with LARGE_FILE support. I have 7.10 i386 installed by the way. 

Any help?

Thanks,
Eric

---

### Post by nowhere@cox.net on 2008-04-16
Luigi wrote me and provided a solution. In case you need it see this thread:

[http://ubuntuforums.org/showthread.php?t=757084]("http://ubuntuforums.org/showthread.php?t=757084")

Eric

---

