---
title: "I want to move /var to a new partition"
date: 2006-08-17
forum: General Help
---

### Post by Elephantium on 2006-08-17
I installed Dapper (server disc) on a 18 gig HD, and now I'd like to put /var on a second 60 gig drive.

I've successfully moved my /home to the first partition on the new drive - I mounted the new drive at /mnt/home, copied everything from /home to /mnt/home, then deleted /home and added a symlink to /mnt/home

I'm not sure whether that will work for /var - I have the idea that currently-running programs could cause problems.

So, does anyone have any tips?

---

### Post by aysiu on 2006-08-17
I think you can do the same thing as moving /home, but you'll need to use a live CD if you don't want to interfere with currently running programs.

Here's a tutorial on moving /home with a live CD:
[http://www.psychocats.net/ubuntu/separatehome.html](http://www.psychocats.net/ubuntu/separatehome.html)

---

### Post by Irony on 2006-08-17
This should work - I've used the gentoo documentation to move my home directory so it looks like /var is similar but with the addition of symlinks;

[http://www.gentoo.org/doc/en/articles/partitioning-p2.xml](http://www.gentoo.org/doc/en/articles/partitioning-p2.xml)

Note you don't need a live CD for this. Instead you boot up as normal into Ubuntu but then do *sudo init 1* to take you to a root shell. Be patient as at first *ubuntu login* pops up but wait a bit longer until *root@ubuntu* pops up.

If you are puzzled as to what the * means in the instruction;

[PHP]# cd /var 
# cp -ax * /mnt/rwstorage/var[/PHP]

It means copy the *contents* of var to the new folder var.

---

### Post by Stewori on 2006-08-19
I have installed Dapper and Hoary parallel on two partitions and everything is working fine.
Since my Dapper-partition is nearly full, I'm trying to move /usr to another partition (have more than the two system-partitions), cause usr takes more space than any other system folder.

As mentioned above I planned to copy /usr to another partition and then create a symbolic link. First I tried to copy using nautilus - of course that didn't work - as mentioned before one should use a life CD or something.

So I re-tried it with my Hoary usr-folder (so if something goes wrong my Dapper-Installation would not be harmed), performing copy-process from Dapper. Nautilus didn't work again. So I tried a tar-command I found in some thread:
change to /usr, then (of course with root-rights)
tar cfpl - --atime-preserve . | ( cd destpath/usr; tar xfp - --atime-preserve )

Several errors arised during copy process and more then 1000 files were not copied, so I didnt't try out to replace usr with a symlinkt to destpath/usr.

Errors typically said:

Kann Datei-Eigentümer nicht zu uid 0, gid 0 ändern.: Operation not permitted

or

Verzeichnis umbenannt bevor sein Status ermittelt werden konnte
tar: .: Kann Datei-Eigentümer nicht zu uid 0, gid 0 ändern.: Operation not permitted
tar: Fehler beim Beenden, verursacht durch vorhergehende Fehler.

Since this Forum is in english I try a translation of tars error messages:

Can't change File owner to uid 0, gid 0.: Operation not permitted

or

tar: ./X11: Directory renamed before its state could be determined


These errors arised many-thousand times, nearly on every file in usr.
Finally tar exited with (message translated to english):

tar: Error on exit: Caused by previous errors.


So why does this not work? The folder I try to copy should not be used by the running system, is even on another partition and of course I did everything with root-rights. Why is Operation not permitted? I have root-rights!
Is there a chance this works better using a life CD?  Where is a difference between using a life CD or a parallel Ubuntu-Installation?

I hope for fast replies since I can't do much with a full root partition.

---

### Post by mlind on 2006-08-19
You should use **sudo** while doing the tarball. If you had a LVM setup, you could dynamically resize partitions.

---

### Post by Stewori on 2006-08-23
Hello again.
I tried the tarball using sudo, but exactly the same errors arised like before. Didn't know why sudo should make a difference to entering su and *PASSWORD* anyway.
I also processed the tarball from a Knoppix-Live-DVD - with the same unlucky result. In addition tar was unable to create several symlinks. ](*,) 

So any ideas?

How can I find out, whether I have an LVM setup? Dapper says something about LVM-Volumes during startup.

How should I go on for rezising my partitions? Which program should I use?

---

### Post by Irony on 2006-08-23
Follow the link I provided - it also leads to /usr copying.

---

### Post by Elephantium on 2006-08-23
I followed the directions on the link that you posted, Irony, but it didn't work properly.  I ended up with a /var/var symlink pointing to /mnt/var, and nothing worked.

After a reboot into rescue mode from the install CD and some fiddling, I got /var to be a symlink to /mnt/var, but now mysql doesn't work.  When I try to start it up, it complains about not being able to bind to port 3306.  If I try to start it up using sudo, it complains that it can't find a log file
/var/log/mysql/mysql-bin.000031

Got any hints on this one?

Edit:  After further investigation, it seems that the problem is with resolvconf and /var being a symlink to /dev/hda2.

---

### Post by Stewori on 2006-08-24
Thanks for your reply, but the cp command from the guide you linked to produced the same errors like tar.
I finally found out, why:
I tried to copy usr to a fat32 partition. Using an ext3 partition copying works fine.
Unfortunately my huge partition, to which I wanna move, is fat32 cause I'm sharing it with windows.
Is there any way to settle usr on a fat32 partition?
Or is it possible to split usr on more than one partition (don't have really much space on any partition but my huge fat32)? For instance by moving some subfolders of usr to one partition and some others to another partition, providing correct symlinks?

---

### Post by Jonie on 2007-01-28
This makes really a pain in a$$. /var/run is mounted as tmpfs and therefore must not be mounted on a mountable parttion. In fact it's being mounted even before root is rw, so that network init has no access to /var/run and fails. Simply create a directory run under /var on the root partition and chmod it to 755. Don't worry that initial /var/run will be superimposed by mounted i.e. empty content - init scripts should handle the moving.

More reading

[http://utcc.utoronto.ca/~cks/space/blog/linux/](http://utcc.utoronto.ca/~cks/space/blog/linux/)

---

