---
title: "Problems to install GenealogyJ - Permission denied"
date: 2015-05-04
forum: General Help
---

### Post by Constantinopolitan on 2015-05-04
Dear users,

I try to install GenealogyJ, but it doesn't work. I cannot save it under "Home", and the system denies me permission to install it from another folder. I tried to install it via sudo but get again some instructions I unfortunately cannot understand (what is a destination file operand?). Here is what the Konsole says:

constantinopolitana@Constantinopolitana:~$ ./Documentos/Kunst/genj_install-6755.jar
bash: ./Documentos/Kunst/genj_install-6755.jar: Permission denied
constantinopolitana@Constantinopolitana:~$ ^C
constantinopolitana@Constantinopolitana:~$ sudo mv /home/constantinopolitana/Documentos/Kunst/genj_install-6755.jar
[sudo] password for constantinopolitana: 
mv: missing destination file operand after '/home/constantinopolitana/Documentos/Kunst/genj_install-6755.jar'
Try 'mv --help' for more information.
constantinopolitana@Constantinopolitana:~$ mv --help
Usage: mv [OPTION]... [-T] SOURCE DEST
  or:  mv [OPTION]... SOURCE... DIRECTORY
  or:  mv [OPTION]... -t DIRECTORY SOURCE...
Rename SOURCE to DEST, or move SOURCE(s) to DIRECTORY.

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL]       make a backup of each existing destination file
  -b                           like --backup but does not accept an argument
  -f, --force                  do not prompt before overwriting
  -i, --interactive            prompt before overwrite
  -n, --no-clobber             do not overwrite an existing file
If you specify more than one of -i, -f, -n, only the final one takes effect.
      --strip-trailing-slashes  remove any trailing slashes from each SOURCE
                                 argument
  -S, --suffix=SUFFIX          override the usual backup suffix
  -t, --target-directory=DIRECTORY  move all SOURCE arguments into DIRECTORY
  -T, --no-target-directory    treat DEST as a normal file
  -u, --update                 move only when the SOURCE file is newer
                                 than the destination file or when the
                                 destination file is missing
  -v, --verbose                explain what is being done
      --help     display this help and exit
      --version  output version information and exit

The backup suffix is '~', unless set with --suffix or SIMPLE_BACKUP_SUFFIX.
The version control method may be selected via the --backup option or through
the VERSION_CONTROL environment variable.  Here are the values:

  none, off       never make backups (even if --backup is given)
  numbered, t     make numbered backups
  existing, nil   numbered if numbered backups exist, simple otherwise
  simple, never   always make simple backups

If anyone can enlighten me, many thanks already in advance!

Best regards,

Eva (computer un-affine newbie)

---

### Post by CantankRus on 2015-05-04
You downloaded a java archive file.
Do you have java installed?(terminal)...
```
java -version
```
You can install the open source version of java with (terminal)...
```
sudo apt-get install openjdk-7-jre
```

When java is installed, you need to open a terminal and change directory (cd) to where **genj_install-6755.jar** is.
From your previous posts the command would be...
```
cd /home/constantinopolitana/Documentos/Kunst
```

Then run the java installer with...
```
java -jar genj_install-6755.jar
```

---

### Post by Constantinopolitan on 2015-05-04
Fantastic, it worked!
Thanks a LOT, CantankRus!!!!!
Eva

---

### Post by CantankRus on 2015-05-04
> **Constantinopolitan said:**
> Fantastic, it worked!
Thanks a LOT, CantankRus!!!!!
Eva
OK goodluck.
I installed here to test and the genealogy application starts up fine.

---

