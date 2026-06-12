---
title: "sudoers is owned by uid 1000, should be 0"
date: 2007-09-27
forum: General Help
---

### Post by neonl on 2007-09-27
If heard this is a typical and difficult problem but... is it solvable?

What I did is simple: changed the owner of the entire /etc folder (with sub folders and files) to "Rui" (my user). Now I realize what I did :( :( :(

---

### Post by gaussian on 2007-09-27
> **neonl said:**
> If heard this is a typical and difficult problem but... is it solvable?

What I did is simple: changed the owner of the entire /etc folder (with sub folders and files) to "Rui" (my user). Now I realize what I did :( :( :(


Try 
sudo chown 0.0 /etc/sudoers

If this does not work (i.e. you are facing chicken and egg problem: you need to fix sudo to fix sudo), boot in recovery mode and try the same thing. If that does not work, boot with any linux live cd, mount your drive and do sudo chown 0.0 /MOUNTPOINT/etc/sudoers, where you need to replace MOUNTPOINT with actual mount point where your mounted your hard drive.

---

### Post by ruibernardo on 2007-09-27
Hi neol,

all the files there should owned by root. It should be easy to put the right file owner back. 

If you can't make "sudo" again, simply reboot the computer and on the GRUB menu on boot select the first "recovery" kernel (usually the second choice). This will put you on a shell as root. If you don't see a menu at boot, keep pressing [Esc] right after the reboot.

On that console/terminal run:

```
 chown -R root.root /etc/
```

This will make all files and directories on /etc/ owned by root again. 

Reboot again to login as usual.

Cheers fellow :popcorn:

---

### Post by bodhi.zazen on 2007-09-27
OUCH ...

It is usually easier to re-install rather then to try to set the correct ownerships in /etc :(

---

### Post by neonl on 2007-09-27
> **epimeteo said:**
> Hi neol,

all the files there should owned by root. It should be easy to put the right file owner back. 

If you can't make "sudo" again, simply reboot the computer and on the GRUB menu on boot select the first "recovery" kernel (usually the second choice). This will put you on a shell as root. If you don't see a menu at boot, keep pressing [Esc] right after the reboot.

On that console/terminal run:

```
 chown -R root.root /etc/
```

This will make all files and directories on /etc/ owned by root again. 

Reboot again to login as usual.

Cheers fellow :popcorn:

Thanks a lot. It worked.

Cheers "Compatriota" Fellow :)

---

### Post by bodhi.zazen on 2007-09-27
LOL

Not everything in /etc has a group of root (ie not everything is root.root)

---

### Post by ruibernardo on 2007-09-27
Aaargh, sorry neonl. #-o

bodhi.zazen is right, it shouldn't have been "root.root", but only "root". ](*,) 

I usually use "user.group" on chown on other cases and wasn't concentrated when I typed "root.root". My bad. :sad:

root owns everything, but the group of many files is different. Supposing that you only did "chown -R Rui /etc/" before, now it would be:

```
chown -R root /etc/
```

Now it's too late. No way back. Sorry fellow.

Please do a new install. Feel free to ask for any help to backup you /home directory, if needed.

---

### Post by pointone on 2007-09-27
root doesn't own everything, either. /etc/cups, for example is owned by cupsys:lp.

On my rather new install, my non-root-owned files and directories are:

/etc/at.deny owned by root:daemon
/etc/chatscripts owned by root:dip
/etc/gshadow owned by root:shadow
/etc/ppp owned by root:dip
/etc/shadow owned by root:shadow
/etc/wvdial.conf owned by root:dialout

Although if you've installed a lot of additional software, your /etc/ directory might look completely different.

---

### Post by neonl on 2007-09-28
I got it done a litle bit before watching your answers...

What I did was: Restart PC, in GRUB enter in recovery, not login (he putted me as root automatically) run:

```
chown root:root /etc/sudoers
```

Rebooted, logged in and tried SUDO. It was ok!

---

### Post by ruibernardo on 2007-09-28
neonl, 

after reading the post of pointone, I've checked all the group owners of the files in all the directories inside /etc/ that I have here (Gnome Ubuntu, desktop computer, almost fresh install).

Even if your system is still running, there are errors that might/will happen over the time because of those group owners. They allow some services to change the configurations without being root for security reasons. If you don't change them back, those services wont be able to change the configuration files when needed and the errors will occur.

Here is a solution to correct what I said you to do. Please paste this in gedit and save it on your home folder with the name "restore_groups.sh".

```
sudo chown root.daemon /etc/at.deny
sudo chown root.dialout /etc/wvdial.conf
sudo chown root.shadow /etc/shadow
sudo chown root.dip /etc/ppp
sudo chown root.dip /etc/ppp/peers/provider
sudo chown root.shadow /etc/gshadow
sudo chown root.lp /etc/cups
sudo chown root.lp /etc/cups/ppd
sudo chown root.dip /etc/chatscripts
sudo chown root.dip /etc/chatscripts/provider
sudo chown root.ssl-cert /etc/ssl/private
sudo chown root.lp /etc/cups/ssl
```Since you can make "sudo" again, open a console/terminal and type:

```
sudo sh /home/Rui/restore_groups.sh
```This should restore the right group owners of the files and directories.

Fica bem e desculpa ter-te induzido em erro, compatriota. :mrgreen:

---

### Post by bodhi.zazen on 2007-09-28
If you are running that script as root, you do not need sudo.

also, this script is insufficient for the directories :

Here is a listing on non root.root in /etc :> -rw-r-----  1 root daemon      144 2007-02-20 06:41 at.deny
drwxr-s---  2 root dip        4096 2007-08-08 18:04 chatscripts
drwxr-xr-x  4 root lp         4096 2007-09-16 08:50 cups
-rw-r-----  1 root fuse        216 2007-08-10 16:04 fuse.conf
-rw-r-----  1 root shadow      745 2007-08-20 22:46 gshadow
drwxr-xr-x  8 root dip        4096 2007-08-08 18:04 ppp
-rw-r-----  1 root shadow      966 2007-09-13 00:50 shadow
-rw-r-----  1 root dialout      66 2007-08-08 18:07 wvdial.conf

Here is a listing of :

**/etc/chatscripts**

> drwxr-s---   2 root dip  4.0K 2007-08-12 16:31 .
drwxr-xr-x 123 root root  12K 2007-09-28 06:33 ..
-rw-r--r--   1 root root  653 2007-08-12 16:13 pap
[color=red]-rw-r-----   1 root dip   656 2007-08-12 16:13 provider[/color]

**/etc/cups**
> drwxr-xr-x   4 root lp   4.0K 2007-09-16 08:50 .
drwxr-xr-x 123 root root  12K 2007-09-28 06:33 ..
-rw-r--r--   1 root root 2.4K 2007-08-22 21:47 cupsd.conf
-rw-r--r--   1 root root 2.5K 2007-08-22 21:47 cupsd.conf.default
-rw-r--r--   1 root root 8.7K 2007-08-22 21:47 cups-pdf.conf
-rw-r--r--   1 root root 4.4K 2007-08-22 21:47 mime.convs
-rw-r--r--   1 root root 6.1K 2007-08-22 21:47 mime.types
[color=red]drwxr-xr-x   2 root lp   4.0K 2007-08-22 21:47 ppd[/color]
[color=red]-rw-------   1 root lp    289 2007-09-16 08:47 printers.conf[/color]
[color=red]-rw-------   1 root lp    290 2007-08-22 21:47 printers.conf.O[/color]
-rw-r--r--   1 root root  242 2007-08-22 21:47 raw.convs
-rw-r--r--   1 root root  213 2007-08-22 21:47 raw.types
-rw-r--r--   1 root root  181 2007-08-22 21:47 snmp.conf
[color=red]drwx------   2 root lp   4.0K 2007-08-22 21:47 ssl[/color]

[color=blue]Note, ssl and ppd are also directories ... Everything in those is indeed root.root[/color]

Everything in /etc/ppp, including directories and their contents is root.root **EXCEPT** :

/etc/ppp/peers is a directory and is root.dip

/etc/ppp/peers/provider is also root.dip

* this is a listing of the non root.root stuff in /etc for a default gutsy install. You /etc will vary depending on what else you may have installed.

_Note_: for the record, **everything in /etc is owned by root**, what we are changing is group ownership.

Every file/directory has user(owner), group, and other permissions.

---

### Post by ruibernardo on 2007-09-29
bodhi.zazen, the script only doesn't have the /etc/cups/printers.conf* files because I still didn't connected mine at this time (almost fresh install, Feisty). Thanks for referring it.

I've looked at cups directory. I was listing the files without owner, just group too, so I've missed some files not owned by root. :o But cupsys seems to be the only exception.

```
[FONT=Fixedsys]drwx------ 2 [COLOR=Red]cupsys[/COLOR] [COLOR=Blue]lp[/COLOR]     40 2007-04-15 12:59 ssl
-rw-r--r-- 1 root   root  213 2007-04-15 12:59 raw.types
-rw-r--r-- 1 root   root  242 2007-04-15 12:59 raw.convs
drwxr-xr-x 2 [COLOR=Red]cupsys[/COLOR] [COLOR=Blue]lp[/COLOR]      6 2007-04-04 09:32 ppd
-rw-r--r-- 1 root   root 6109 2007-04-04 09:32 mime.types
-rw-r--r-- 1 root   root 4461 2007-04-04 09:32 mime.convs
drwxr-xr-x 2 root   root    6 2007-04-04 09:32 interfaces
-rw-r--r-- 1 [COLOR=Red]cupsys[/COLOR] **root** 2981 2007-04-04 09:32 cupsd.conf
[/FONT]
```So, after all there are files not owned by root. Making those files owned by root could break CUPS when trying to create or change printers. If nobody find more files (I didn't), then script to restore the owners and groups should look this (without the sudos too):

```
chown root.daemon /etc/at.deny
chown root.dialout /etc/wvdial.conf
chown root.shadow /etc/shadow
chown root.dip /etc/ppp
chown root.dip /etc/ppp/peers/provider
chown root.shadow /etc/gshadow
chown cupsys.lp /etc/cups
chown cupsys.lp /etc/cups/ppd
chown cupsys.root /etc/cupsd.conf
# if the next command fails, you don't have a printer.
chown cupsys.lp /etc/cups/printers.conf*
chown root.dip /etc/chatscripts
chown root.dip /etc/chatscripts/provider
chown root.ssl-cert /etc/ssl/private
chown root.lp /etc/cups/ssl

```Paste it on gedit and proceed as I said on the post [#10]("http://ubuntuforums.org/showpost.php?p=3441713&postcount=10").

---

### Post by bodhi.zazen on 2007-09-29
Nice script. I always want to shorten my scritps :

> chown root.daemon /etc/at.deny
chown root.dialout /etc/wvdial.conf
chown root.shadow /etc/shadow /etc/gshadow
# if the next command fails, you don't have a printer.
chown root.dip /etc/ppp /etc/ppp/peers/provider /etc/chatscripts /etc/chatscripts/provider
chown cupsys.lp /etc/cups /etc/cups/ppd /etc/cups/printers.conf*
chown cupsys.root /etc/cupsd.conf
chown root.ssl-cert /etc/ssl/private
chown root.lp /etc/cups/ssl

woo hoo 6 lines shorter

[indent]I know, I know, geekus maximus ...[/indent]

The problem being, however, that as you point out re your comment and the differences between your /etc it is *hard to restore all the permissions in /etc ; the longer one has been running a system, the harder it is.

The second problem is one might not notice the error right away, but rather have a problem down the line when say a new printer is added. One may well spend hours wondering why they can not add a printer ...

---

