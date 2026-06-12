---
title: "Can't complete updates.."
date: 2008-06-15
forum: General Help
---

### Post by Maelgwyn on 2008-06-15
Hey guys,

I get the following when I try to update:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://nz.archive.ubuntu.com hardy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Running 8.04 x64.

---

### Post by ppl on 2008-06-20
Same problems here for quite a few days now in both of my laptops, must be some problems in the server side as I am using the same server.

> **Maelgwyn said:**
> Hey guys,

I get the following when I try to update:
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://nz.archive.ubuntu.com hardy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Running 8.04 x64.

---

### Post by Bubba64 on 2008-06-20
Make sure the apt source is up to date, make sure you have what you want ticked in the software sources, and change the server.

---

### Post by Maelgwyn on 2008-06-23
I've done that - I'm running off the Main servers now, and I still get it =/

---

### Post by Maelgwyn on 2008-06-24
ok, so if I use the Main servers, I get this error:
```
W: GPG error: http://archive.ubuntu.com hardy-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

If I use the NZ servers instead, I get a different one!
```
Failed to fetch http://nz.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-amd64/Packages.bz2  Hash Sum mismatch
Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by rpimn on 2008-11-09
I am currently using Hardy Heron and also got this error message.
To solve the problem with the signature update, I opened "Synaptic Package Manager, deactivated the "Third Party Software" options in the Repositories setting, and finally press the "Reload" button in the toolbar.
Hope, this can help.

---

### Post by Sef on 2008-11-10
Moved to General Help.

---

### Post by jmate24 on 2008-11-10
+1 Here. Seem to be unable to update or download from the repositories with error in synaptic E: Method gave invalid 400 URI Failure message Method gave invalid 400 URI Failure message. it all started 1-2 days ago when i reinstalled Ubuntu Ibex and Battle for Wesnoth 1.4.2 and i went to install the addons from their server add-ons.wesnoth.org the game kept closing directly before and after i went to install the addon(s). I have since uninstalled BfW 1.4.2 and have installed BfW 1.4.6 to see if installing addons still gives me trouble. 

I think that this might be a DoS attack, It does seem very likely with Ibex just coming out and Feisty EOL. But they could be totally unrelated, It is probably just that the servers went down so that they could delete the Feisty OS and all of the related packages.

---

### Post by arnaudj on 2008-11-10
here i get:
```
W: Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/pool/main/d/dpkg/dpkg-dev_1.14.20ubuntu6_all.deb
  Hash Sum mismatch
```

do I ave to add so;ethig in the Software source or the Synaptic sofware manager? I got fonfused...

---

### Post by idzuna on 2008-12-08
I had this problem for the last few months, only when upgrading to Intrepid did I try to fix it.

To fix my problem (I was using NZ servers as well) I went to 
System > Administration > Software Sources

Then to the Authentication tab and deleted EVERY key, and restored the default keys.

Hopefully this helps other people as it seemed to work for me.

---

