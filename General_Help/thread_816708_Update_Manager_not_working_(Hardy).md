---
title: "Update Manager not working (Hardy)"
date: 2008-06-02
forum: General Help
---

### Post by John0 on 2008-06-02
Software sources, Synaptic and Update manager are not working for me, and also the after trying to use these, the "Add/Remove" window freezes and won't close.

Got my courage in both hands. Tried "sudo apt-get update", this doesn't work either. Here is the result:

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Fetched 5779B in 46s (124B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

Also tried "$ sudo synaptic", this doesn't work either. Here is the result:

john@John:~$ sudo synaptic
sudo: unable to resolve host John
[sudo] password for john: 

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
john@John:~$ 


Hope someone can help, please bear in mind that I am a newbie and am still quite uncomfortable on the command line!!

---

### Post by buntunub on 2008-06-02
> **John0 said:**
> Software sources, Synaptic and Update manager are not working for me, and also the after trying to use these, the "Add/Remove" window freezes and won't close.

Got my courage in both hands. Tried "sudo apt-get update", this doesn't work either. Here is the result:

Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Fetched 5779B in 46s (124B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

Also tried "$ sudo synaptic", this doesn't work either. Here is the result:

john@John:~$ sudo synaptic
sudo: unable to resolve host John
[sudo] password for john: 

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed

(synaptic:5924): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
john@John:~$ 


Hope someone can help, please bear in mind that I am a newbie and am still quite uncomfortable on the command line!!

Yikes. You have two issues. Firstly, your /etc/hosts is probably messed up. Open up your Terminal (Applications > Accessories > Terminal) and type the following:```


$sudo gedit /etc/hosts
```

This should look like the following:

```
127.0.0.1 localhost
127.0.1.1 user

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Note: "user" should be your user account name. My guess is yours looks like the following:

```
127.0.0.1 localhost
127.0.1.1 user-DOMAIN

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

Where DOMAIN is your windows domain. This is a known bug with Hardy. Just erase the DOMAIN part, save, and exit out of that.

Next issue. You need to go into System > Administration > Software Sources, and uncheck the CD-Rom from the first tab.

You should be off to the races now!

---

### Post by iaculallad on 2008-06-02
Try to Navigate System->Administration->Software Sources, and select "Ubuntu Software" tab. Place a check mark on Main, Universe, Restricted, and Multiverse.

Choose "Main Server" under "Download from".

Uncheck "Installable from CD-ROM/DVD.

Click on close and open up terminal:

```
sudo apt-get update
```

---

### Post by John0 on 2008-06-03
Hi Buntunub, thanks for your quick reply. I did what you suggested and yes, now everything works just fine ... except my wireless connection, which now no longer works at all. Do you have any more magic for me to try?
thanks

---

### Post by buntunub on 2008-06-03
> **John0 said:**
> Hi Buntunub, thanks for your quick reply. I did what you suggested and yes, now everything works just fine ... except my wireless connection, which now no longer works at all. Do you have any more magic for me to try?
thanks

You need to identify what wifi card you have.

```
$sudo lspci
```

Look for the line that contains the info about your card. Then, do a search on these forums with that info and you will find a guide or "how to" to get you up and running. If your on Broadcom like me, then you will have to use Ndiswrapper most likely.

---

