---
title: "Can't delete empty files"
date: 2008-01-13
forum: General Help
---

### Post by RagingOcelot on 2008-01-13
I'm having trouble installing PHP 5 on a remote server.  When I try to install 

libapache2-mod-php5

I get this error: 

```
dpkg: error processing libapache2-mod-php5 (--configure):
 unable to install `/etc/apache2/mods-available/php5.load.dpkg-new' as `/etc/apache2/mods-available/php5.load': No such file or directory
```

It seems that dpkg is trying to overwrite the php5.load file but can't.  I know full well I'm root, so it's not a permissions issue.  The php5.conf file is not right either.  

Both of these files appear to be empty.

When I try to delete either of these files, I get:

```
rm: cannot remove `php5.load': No such file or directory
```

...just like the files don't exist.  Do I have some file corruption?  I forced a reboot with fsck but to no avail.

I have a screenshot of the two files in Konqueror (notice the lack of info pertaining to creation dates and ownership).

---

### Post by sumguy231 on 2008-01-13
That's really weird, and maybe there is something wrong with your filesystem, but have you tried overwriting them yourself, e.g. echoing some nonsense text to them? It seems like if it thinks that the file doesn't exist it would have no problem with trying to create it properly.

---

### Post by RagingOcelot on 2008-01-13
```
echo "blah" >> php5.load
-bash: php5: No such file or directory
```

when I try to echo some text to it.  Really baffled...

---

### Post by sageb1 on 2008-01-15
my guess is those particular files are links to files that were never installed.

---

### Post by geirha on 2008-01-15
Could you paste the output of this? ```
 ls -l /etc/apache2/mods-available/php5.*
```
Just curious how ls outputs it. My guess is that the filesystem has errors. Any chance of getting physical access to the box, so you can reboot into recovery mode and run fsck?

If not, you could try to rename the directory, create a new, and then copy all the "good" files to the new one. That would just be a workaround though, until you can have the filesystem checked
```
sudo mv /etc/apache2/mods-available /etc/apache2/mods-available.backup
sudo mkdir /etc/apache2/mods-available
# copy files ...

```

---

