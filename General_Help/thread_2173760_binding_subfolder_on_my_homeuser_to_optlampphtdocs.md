---
title: "binding subfolder on my /home/user/ to /opt/lampp/htdocs/newfolder help"
date: 2013-09-11
forum: General Help
---

### Post by jhay2 on 2013-09-11
hello to all

im really new in linux .. and i really need your help about binding folder on bootups..


itry this .

sudo leafpad /etc/fstab

and add this line 

/home/user/subfolder /opt/lampp/htdocs/newfolder none bind 0 0

and reboot my laptop 


and when it bootup .. errors appear 


mount: special device /home/user/subfolder does not exist 

So binding folders failed 


so i remove the lines that ive added.

i also try 
sudo leafpad /etc/rc.local

and add this line 

mount -o bind /home/user/subfolder /opt/lampp/htdocs/newfolder

and reboot 


but it gives me  same result 

mount:special device /home/user/subfolder does not exist


itry to manual recover and try to cd /home

but the errors still the same 

special device /home does not exist.. 


please help .. 

sorry if some of my grammar are wrote incorrectly .. 

by the way im using ubuntu 13.04 with lxde

---

### Post by jhay2 on 2013-10-01
no one wants to help me :(

---

### Post by Lars Noodén on 2013-10-01
Two things are here.  One is that fstab is for mounting filesystems.  It won't influence individual directories, just filesystems (partitions, etc).  Second is that some how you've ended up with XAMPP on your computer.  If you are just starting out, I would recomend removing XAMPP and doing things the Linux (Ubuntu) way.  After removing XAMPP, the correct way to get Apache2 would be to install it from the Software Center or Synaptic.  Or you could install it via the shell:

```

sudo apt-get update
sudo apt-get install apache2

```

XAMPP puts all kinds of things in strange places and makes it hard for you to help yourself and even harder for others to help you.

A third thing would be the actual configuration of Apache2.  It looks like you might be trying to set up [user directories](http://httpd.apache.org/docs/2.4/howto/public_html.html).

---

### Post by bab1 on 2013-10-02
> **jhay2 said:**
> hello to all

im really new in linux .. and i really need your help about binding folder on bootups..


itry this .

sudo leafpad /etc/fstab

and add this line 

/home/user/subfolder /opt/lampp/htdocs/newfolder none bind 0 0

and reboot my laptop 


and when it bootup .. errors appear 


mount: special device /home/user/subfolder does not exist 

So binding folders failed 


The fstab entry appears to be correct.  See bind section of the man pages for *mount*```

man mount...

     The bind mounts.
              Since  Linux  2.4.0  it is possible to remount part of the file hierarchy somewhere
              else. The call is
                     mount --bind olddir newdir
              or shortoption
                     mount -B olddir newdir
              or [COLOR="#FF0000"]fstab entry is:
                     /olddir /newdir none bind
[/COLOR]
              After this call the same contents is  accessible  in  two  places.   One  can  also
              remount  a single file (on a single file). It's also possible to use the bind mount
              to create a mountpoint from a regular directory, for example:

                     mount --bind foo foo

              The bind mount call attaches only (part of) a single filesystem, not possible  sub&#8208;
              mounts.  The  entire  file hierarchy including submounts is attached a second place
              using

                     mount --rbind olddir newdir

              or shortoption

                     mount -R olddir newdir

              Note that the filesystem mount options will remain the same as those on the  origi&#8208;
              nal  mount  point,  and  cannot  be  changed  by  passing  the -o option along with
              --bind/--rbind. The mount options can be changed by a separate remount command, for
              example:
                     mount --bind olddir newdir
                     mount -o remount,ro newdir

              Note  that  behavior  of  the  remount operation depends on the /etc/mtab file. The
              first command stores the 'bind' flag to the /etc/mtab file and the  second  command
              reads  the  flag from the file.  If you have a system without the /etc/mtab file or
              if you explicitly define source and target for the remount command  (then  mount(8)
              does  not  read  /etc/mtab),  then  you  have  to use bind flag (or option) for the
              remount command too. For example:

                     mount --bind olddir newdir
                     mount -o remount,ro,bind olddir newdir

```...but this is very relevant> mount: special device /home/user/subfolder **does not exist **
So binding folders failed 

Was the subdirectory there or, as I suspect, not?
> 


so i remove the lines that ive added.

i also try 
sudo leafpad /etc/rc.local

and add this line 

mount -o bind /home/user/subfolder /opt/lampp/htdocs/newfolder

and reboot 


but it gives me  same result 

mount:s[COLOR="#FF0000"]pecial device /home/user/subfolder ***does not exist***[/COLOR]
Same here (above in red).> 

itry to manual recover and try to cd /home

but the errors still the same 

special device /home does not exist.. 


please help .. 

sorry if some of my grammar are wrote incorrectly .. 

by the way im using ubuntu 13.04 with lxde
Check your subdirectories that you are using in the mount bind.

---

### Post by jhay2 on 2013-10-05
> **bab1 said:**
> The fstab entry appears to be correct.  See bind section of the man pages for *mount*```

man mount...

     The bind mounts.
              Since  Linux  2.4.0  it is possible to remount part of the file hierarchy somewhere
              else. The call is
                     mount --bind olddir newdir
              or shortoption
                     mount -B olddir newdir
              or [COLOR=#FF0000]fstab entry is:
                     /olddir /newdir none bind
[/COLOR]
              After this call the same contents is  accessible  in  two  places.   One  can  also
              remount  a single file (on a single file). It's also possible to use the bind mount
              to create a mountpoint from a regular directory, for example:

                     mount --bind foo foo

              The bind mount call attaches only (part of) a single filesystem, not possible  sub&#8208;
              mounts.  The  entire  file hierarchy including submounts is attached a second place
              using

                     mount --rbind olddir newdir

              or shortoption

                     mount -R olddir newdir

              Note that the filesystem mount options will remain the same as those on the  origi&#8208;
              nal  mount  point,  and  cannot  be  changed  by  passing  the -o option along with
              --bind/--rbind. The mount options can be changed by a separate remount command, for
              example:
                     mount --bind olddir newdir
                     mount -o remount,ro newdir

              Note  that  behavior  of  the  remount operation depends on the /etc/mtab file. The
              first command stores the 'bind' flag to the /etc/mtab file and the  second  command
              reads  the  flag from the file.  If you have a system without the /etc/mtab file or
              if you explicitly define source and target for the remount command  (then  mount(8)
              does  not  read  /etc/mtab),  then  you  have  to use bind flag (or option) for the
              remount command too. For example:

                     mount --bind olddir newdir
                     mount -o remount,ro,bind olddir newdir

```...but this is very relevant
Was the subdirectory there or, as I suspect, not?
Same here (above in red).
Check your subdirectories that you are using in the mount bind.

the subdirectory is in my /home/user folder .. but i dont know why i get this error on boot .. :(

i think its because i'd choose to encrypt my home folder when i fresh install ubuntu? i dont know yet if thats the reason ... 


any suggestion sir ?

---

### Post by bab1 on 2013-10-05
> **jhay2 said:**
> the subdirectory is in my /home/user folder .. but i dont know why i get this error on boot .. :(

i think its because i'd choose to encrypt my home folder when i fresh install ubuntu? i dont know yet if thats the reason ... 


any suggestion sir ?
Yes, the encryption is the is the problem.  If the /home directories are on a separate partition then you can backup the data and reformat the partition.  If /home is not on a separate partition then you will have to reinstall.  I don't encrypt the entire /home/$user directory.  There is too much chance of of the problem you are running up against.

A hack might be to move your home directory to something like /home/test/$user.  You will have to modify the user settings for the home dir.  i do that directly in the /etc/passwd file.  But I assume you can do it with the tool *usermod*.  This means you will still have the encrypted space while not using it for anything.  I'm a stickler for details so that would bug me until I cleaned it up, but it might work for your needs.

---

### Post by Bucky Ball on 2013-10-05
Just a note:

```
**gksudo** leafpad
```

Not 'sudo'. Whenever opening a GUI as root you use 'gksudo'. 

Just thought I'd mention.

---

### Post by SeijiSensei on 2013-10-05
> **Bucky Ball said:**
> Whenever opening a GUI as root you use 'gksudo'.

Unless, like me, you are not using a GNOME-based desktop environment.  The equivalent KDE command is "kdesudo".

---

### Post by Bucky Ball on 2013-10-06
> **SeijiSensei said:**
> Unless, like me, you are not using a GNOME-based desktop environment.  The equivalent KDE command is "kdesudo".

;)

---

### Post by jhay2 on 2013-10-06
Thanks for the reply for all you .. 


@bab1 

So i need  to reinstall? Awts..  is there any other suggestion that no need to reinstall .. ? or is there any solution that can i make my home folder unencrypted without reinstalling?




@bucky 

What is the difference between sudo and gksudo?

---

### Post by bab1 on 2013-10-07
> **jhay2 said:**
> Thanks for the reply for all you .. 


@bab1 

So i need  to reinstall? Awts..  is there any other suggestion that no need to reinstall .. ? or is there any solution that can i make my home folder unencrypted without reinstalling?

In my previous post I gave you both alternative strategies.  Reinstall or replace the encrypted directory with a non-encrypted one.  No magic bullets.  If you reinstall you don't have to worry about mucking up your new unencrypted home directory location.  This makes it the least amount of mental work on your part.  If you know how to substitute one home directory for another this is the overall easiest method.  All of this you have to do this as the root user.  I would make all the changes using the terminal.  The commands are direct and you can check your work easily.  Every once in a while there are little inconsistencies when using GUI file managers. 

These are the only choices I know of.  Make sure you have[COLOR="#FF0000"] backed up ALL OF YOUR DATA to a remote location[/COLOR] (flash drive or external drive) ***before*** you do anything.  This way if it all goes horribly wrong you still have the data and can reinstall everything 
> 
@bucky 
What is the difference between sudo and gksudo?
I'll answer this also.  The difference is in the variables that are set for running a GUI application as root.  Calling gksudo (or gksu) invokes sudo with GUI variables.  Most of the time the user won't see the difference.  But the bottom line is: you you should use the gksudo command when running a GUI app as the root user from the command line (CLI).

---

### Post by btindie on 2013-10-07
What's the contents of your /etc/fstab file? - make sure the bind line comes after any entry to mount /home as otherwise the source of the mount won't exist when it tries to mount it!

Re the encrypted partition - have you tried manually mounting it from the command line? If that works then encryption isn't an issue.

---

