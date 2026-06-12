---
title: "apache will not allow me to change my web root folder"
date: 2008-06-06
forum: General Help
---

### Post by djrobthaman on 2008-06-06
Hi,

Anyone know why my config file in the sites-available folder (for apache2) which is below, should give me a permissions error when I try to view "localhost" with firefox?

Error:
"[error] [client 127.0.0.1] (13)Permission denied: access to / denied"

Config file:
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /media/Other/www/vhosts/localhost/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/Other/www/vhosts/localhost/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>

```

Thanks

---

### Post by wdaniels on 2008-06-06
The config looks OK to me. Did you give access for the user www-data to read /media/Other/www/vhosts/localhost/?

---

### Post by djrobthaman on 2008-06-06
I thought that too, but am not sure how to do that.  (Also I've done similar apache edits before and never needed to).  Could you tell me how I could give www-data those priveleges though?

Thanks

---

### Post by wdaniels on 2008-06-06
You can do recursive chown and chmod commands to set the permissions. You may want to have the webserver own the files itself, or just give it read permissions, or some other combination...it depends on who/what needs to modify which files. I suggest you try something like this initially:

```
sudo chown -R <your user>:www-data /media/Other/www/vhosts/localhost
sudo chmod -R 770 /media/Other/www/vhosts/localhost
```

The chown should set your user as the owner and the webserver as the group for all files in that directory, then the chmod sets full permissions to both your user and the webserver (that's the 77 part, the final 0 means no public permission).

If that works OK, have a think then about whether you do actually want the webserver to have full permissions on all those files and read up on chmod to learn what the numbers mean so that you can lower the permissions to the minimum required (unless of course this is for personal and you're not too bothered about the security).

---

### Post by wdaniels on 2008-06-06
This does assume that /media/Other is a proper Linux filesystem, not something like FAT - if that is not the case you will have to do something slightly different.

---

### Post by djrobthaman on 2008-06-06
yeah... it's ntfs :(

---

### Post by wdaniels on 2008-06-06
OK, what you'll have to do then is set the user/group IDs (or umask) in the mount options. Post me your /etc/fstab file and I'll tell you what to do.

---

### Post by djrobthaman on 2008-06-06
Here it is:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=15c78977-ab67-4d86-8301-de76d95fa59b /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f078a176-16e9-4a01-87c1-1dbdc8d59ca0 /media/Fedora   ext3    defaults        0       2
# /dev/sdd1
UUID=702450DB2450A5BE /media/Movies   ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdc1
UUID=E47CDB527CDB1DDC /media/Music    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=EEF4E51BF4E4E735 /media/Other    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=A448BBA548BB74A0 /media/Windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=74666780-9974-4ab6-877b-278ae2c75d6e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by wdaniels on 2008-06-06
OK, probably the simplest thing to do here is change the umask option to 000, which should cause all files on this mount to be fully accessible by anyone. If you are OK with that then change the line:

```
UUID=EEF4E51BF4E4E735 /media/Other    ntfs    defaults,umask=007,gid=46 0       1
```

to:

```
UUID=EEF4E51BF4E4E735 /media/Other    ntfs    defaults,umask=000,gid=46 0       1
```

Alternatively, if the webserver only needs read access you could use a umask of 002.

You will need to remount the partition for the changes to take effect.

---

### Post by djrobthaman on 2008-06-07
It worked.  Thanks a bunch.

I wonder why I've never had to do this before.

Anyway, I just had one question.  When you say that all the info is fully accessible to everyone, did you mean everyone who uses this computer or everyone on my network?

---

### Post by wdaniels on 2008-06-08
> **djrobthaman said:**
> Anyway, I just had one question.  When you say that all the info is fully accessible to everyone, did you mean everyone who uses this computer or everyone on my network?

Just any user/process on the machine. How much that translates to anyone on the network depends on what mechanisms there may be for others on the network to connect to the machine (e.g. remote shell logins).

By default with Ubuntu there are no open ports, other than for DNS,DHCP and avahi which you don't really need to worry about. Obviously you have since opened ports at least for Apache, so to use that as an example, if somebody were to compromise Apache such that they cause it to run some code, it would potentially be able to write to anywhere on that partition. There is some level of restrictions built into Apache (like the Directory directives in the configuration) that help to constrain this, but if this server will be sitting on the internet, it's perhaps a risk you would want to avoid.

On a LAN it's not so much of an issue, unless you have sensitive data on that partition and highly technical users, or potential hackers compromising the LAN through weaker nodes etc... but generally, no, it's not going to magically create a network share for that partition or anything.

---

