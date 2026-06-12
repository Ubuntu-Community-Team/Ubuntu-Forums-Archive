---
title: "Unziping to the apache folder?"
date: 2005-09-30
forum: General Help
---

### Post by hansoffate on 2005-09-30
How do i unzip (its php-nuke.zip) to my var/www/ folder. It is password protected. What do i do?

---

### Post by Leif on 2005-09-30
if you mean you can't write to /var/www, preface the command with sudo.

---

### Post by hansoffate on 2005-09-30
i tried,  it doesn't work

hans@hans:~/Internet_downloads$ sudo unzip PHP-Nuke-7.8.zip /var/www/ Archive: PHP-Nuke-7.8.zip
caution: filename not matched: /var/www/

Thats what i get.

---

### Post by PMO6022 on 2005-09-30
See man unzip...

> SYNOPSIS
       unzip      [-Z]     [-cflptuvz[abjnoqsCLMVX$/:]]     file[.zip]     [file(s) ...]
       [-x xfile(s) ...] [-d exdir]

[-d exdir]
              An  optional  directory  to which to extract files.  By default, all files
              and subdirectories are recreated in the current directory; the  -d  option
              allows  extraction in an arbitrary directory (always assuming one has per&#8208;
              mission to write to the directory).  This option need not  appear  at  the
              end of the command line; it is also accepted before the zipfile specifica&#8208;
              tion (with the normal options), immediately after the  zipfile  specifica&#8208;
              tion,  or between the file(s) and the -x option.  The option and directory
              may be concatenated without any white space between them,  but  note  that
              this  may  cause  normal  shell behavior to be suppressed.  In particular,
              ‘‘-d ~’’ (tilde) is expanded by Unix C shells into the name of the  user’s
              home  directory, but ‘‘-d~’’ is treated as a literal subdirectory ‘‘~’’ of
              the current directory.
 
In other words you need "sudo unzip PHP-Nuke-7.8.zip -d /var/www"

---

### Post by hansoffate on 2005-09-30
How do i also removedirectory with files in it?
hans@hans:/var/www$ sudo rmdir apache2-default/
rmdir: `apache2-default/': Directory not empty

Another question is how do i do the same thing as you helped me do with the .zip file but with a  with a .tar.gz?

Thanks for your help

---

### Post by PMO6022 on 2005-09-30
To remove a directory you typically do rm -r <directory_to_remove>.  -r means to remove recursively, so this will remove all subdirectories as well.  However, this will ask you about removing every file, so it is typically coupled with -f, or force.  This is an _extremely_ powerful command.  It will remove everything with no questions, and with no way to get the removed files back.  Use it carefully.  See man rm

I'd suggest checking out [http://www.linuxcommand.org/learning_the_shell.php]("http://www.linuxcommand.org/learning_the_shell.php") for more info on shell commands.

for .tar.gz: tar -xzvf <file-to-untar> -C <path-to-extract-to>
see also: man tar

---

