---
title: "Howto ignore an update"
date: 2008-06-25
forum: General Help
---

### Post by yagee on 2008-06-25
Hi,

I followed the [[COLOR="Blue"]howto on how to install vpnc with openssl[/COLOR]]("http://ubuntuforums.org/showthread.php?t=812381") support.

It all went fine but since then the update manager allways tries to overwrite my custom build vpnc with the one from the central repository of the same version.

I rather would like to prefer to keep my self built version that just gets updated if a newer version is available.

How can I do this?

---

### Post by iaculallad on 2008-06-25
Try using the "Lock Version" under "Package" menu in your Synaptics Package Manager.

---

### Post by yagee on 2008-06-25
> **iaculallad said:**
> Try using the "Lock Version" under "Package" menu in your Synaptics Package Manager.

I tried that but after that there is still one update available. Both vpnc have the same version number so this trick seems not to work here.

---

### Post by yagee on 2008-07-03
> **yagee said:**
> Hi,

I followed the [[COLOR="Blue"]howto on how to install vpnc with openssl[/COLOR]]("http://ubuntuforums.org/showthread.php?t=812381") support.

It all went fine but since then the update manager allways tries to overwrite my custom build vpnc with the one from the central repository of the same version.

I rather would like to prefer to keep my self built version that just gets updated if a newer version is available.

How can I do this?

OK here is a working solution

I created a directory for the vpnc package:
```
sudo mkdir /var/packages
```

After copying it there I run the following command to create a local repository (current directory has to be writable by the current user):
```
sudo dpkg-scanpackages ./ /dev/null | gzip > Packages.gz

```

The next step was to add the local repository to [FONT="Courier New"]/etc/apt/sources.list[/FONT]

```

deb file:///var/packages ./

```

And finally I had to add this repository with high priority to [FONT="Courier New"]/etc/apt/preferences
[/FONT]
```

Package: vpnc
Pin: origin "file:///var/packages"
Pin-Priority: 999

```

For more infos see [FONT="Courier New"]man apt_preferences[/FONT]

Maybe this solution can help someone other, too.

---

### Post by Cuchaz on 2008-10-13
Or, alternatively, you can change the version number in your custom .deb. That should get the lock version trick to work.

run dpkg-buildpackage as in the howto:
[http://ubuntuforums.org/showthread.php?t=812381](http://ubuntuforums.org/showthread.php?t=812381)

Then find your debian folder. It's probably somewhere near here:
```
cd vpnc-0.5.1r275/debian
```

edit the .deb control file:
```
gedit vpnc/DEBIAN/control
```

find the line that says "Version:" and add a -1 onto the end
My version line looks like this:

Version: 0.5.1r275-1-1

Then repackage the .deb and install
```

sudo dpkg-deb -b vpnc vpnc.deb
sudo dkpg -i vpnc.deb

```

---

