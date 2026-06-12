---
title: "Opera not working"
date: 2007-04-28
forum: General Help
---

### Post by glx5667 on 2007-04-28
hi; looks like I'm not the only one with opera problems.  I've been using Opera/Ubuntu 6 for at least one year without any difficulties, and last week it stopped loading.  The error message I get is:

glx@glx-desktop:~$ opera
ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault

I purged Opera, renamed the Opera file in the archive, redownloaded a new version, and it still does not work.
I like Opera, used it for years with Windows (even when you had to buy it).
Help and thanks

---

### Post by hyperair on 2007-04-28
if you downloaded the Opera debs and installed them, don't. I did that and had your problem. 

Solution: add "deb [http://deb.opera.com/opera](http://deb.opera.com/opera) etch non-free" (without quotations of course) to your /etc/apt/sources.list file. Then run these commands in the terminal:

```

sudo apt-get update
sudo apt-get install opera

```

Alternatively, you could go into Synaptic Package Manager and do a search for Opera and install it.

P.s. Don't forget to remove the locally installed Opera.

---

### Post by Goliath! on 2007-05-12
I had to do a few extra things.

First when trying to do the install I got:
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: You may want to run apt-get update to correct these problems

So then I found this article: [http://forums.debian.net/viewtopic.php?p=68795&sid=09f2c7b2f7a6cd2a783d05c309841b52](http://forums.debian.net/viewtopic.php?p=68795&sid=09f2c7b2f7a6cd2a783d05c309841b52)

which told me to do this:
```
sudo gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 033431536A423791
```

and I got:
gpg: WARNING: unsafe ownership on configuration file `/home/john/.gnupg/gpg.conf'
gpg: keyring `/home/me/.gnupg/secring.gpg' created
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error

The configuration file was:
-rw------- 1 me me 9231 2007-03-15 20:03 /home/me/.gnupg/gpg.conf

So then I found [http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-gnupg-warnings.html](http://www.redhat.com/docs/manuals/linux/RHL-9-Manual/custom-guide/s1-gnupg-warnings.html) from which I learned I had to do this:

```
sudo chown root /home/john/.gnupg/gpg.conf
sudo chown root /home/john/.gnupg
chmod 700 ~/.gnupg

```

When I re-tried to get the key I got:

gpg: requesting key 6A423791 from hkp server wwwkeys.eu.pgp.net
gpg: /home/john/.gnupg/trustdb.gpg: trustdb created
gpg: key 6A423791: public key "Opera Software Archive Automatic Signing Key <hostmaster@opera.com>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1

This concerned me a bit, but then on [http://wiki.debian.org/SecureApt](http://wiki.debian.org/SecureApt) if found:

> What does the "gpg: no ultimately trusted keys found" warning mean? --> The Warning: "no ultimately trusted keys found" means that gpg was not configured to ultimately trust a specific key. Trust settings are part of OpenPGPs Web-of-Trust which does not apply here. So there is no problem with this warning. In usual setups the users own key is ultimately trusted.

So I figured I could just trust myself.

Then I did the:
```
sudo gpg --armor --export 033431536A423791 | sudo apt-key add -
```

[INDENT](NOTE: I had to add the two "sudo"s because I am not root.  When I tried to run that as root I got some other error because it tried to create the key for root, not me.)[/INDENT]

And I got a terse "OK".

OK, fine.

Finally I did:
```
sudo apt-get install opera

```

And voila, I have Opera running.

---

