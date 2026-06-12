---
title: "sudo mv /whatever/file * deleted directories"
date: 2007-05-28
forum: General Help
---

### Post by andrewsawyer on 2007-05-28
Hi All,

I think I've done something really stupid.

I was trying to copy a flash movieinto my /var/www directory and instead of typing sudo mv /mnt/tv/recordings/final.flv /var/www/final.flv I actually typed sudo /mnt/tv/recordings/final.flv * thinking it would just copy to the directory I was in.  It actually appears to have deleted most of the contents of the current directory though.  Here is my output:

```

andrew@myth-server:/var/www$ ls
apache2-default  mythweb  phpmyadmin
andrew@myth-server:/var/www$ sudo mv /mnt/tv/recordings/final.flv
Password:
Sorry, try again.
Password:
mv: missing destination file operand after `/mnt/tv/recordings/final.flv'
Try `mv --help' for more information.
andrew@myth-server:/var/www$ sudo mv /mnt/tv/recordings/final.flv *
andrew@myth-server:/var/www$ ls
phpmyadmin

```

Can anyone help me get mythweb back?  The system is setup as a mythtv so no Gnome or KDE.  I can ssh in which is how I was doing this 'transfer'.

Any help would be very much apreciated!  It would also be nice to get the flash movie back!

Regards,
Andy

---

### Post by fanatik on 2007-05-29
well since the syntax of the mv command is mv <source files/dirs> <destination file/dir>, and since you used the asterisk which expanded into everything in your directory, this is probably the command you ran:

```
$ sudo mv /mnt/tv/recordings/final.flv apache2-default  mythweb  phpmyadmin
```

now, I think you've been very lucky in that phpmyadmin is a directory, and therefore have probably just moved /mnt/tv/recordings/final.flv apache2-default  mythweb into phpmyadmin.

if phpmyadmin had been a file you would have overwritten it.

Now to get it all back just cd into phpmyadmin and mv the files back to the correct location, ie:

```
$ cd phpmyadmin
$ sudo mv final.flv apache2-default  mythweb ..
```

that should do it, let us know how you get on.

---

### Post by andrewsawyer on 2007-06-01
It worked - all is back.  Thank you for your help!

---

