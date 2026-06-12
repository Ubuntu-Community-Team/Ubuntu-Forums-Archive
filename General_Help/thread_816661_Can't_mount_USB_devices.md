---
title: "Can't mount USB devices"
date: 2008-06-02
forum: General Help
---

### Post by Phonan on 2008-06-02
A couple disclaimers first: I am using PPC Ubuntu, and I started with a CLI install. Then I installed FVWM-Crystal, Rox-filer, and Thunar, with thunar-volman so Thunar can manage mounting, etc. I have mounting of CDs working fine. When I tried to mount a flash drive, at first I received a message that "a policy in place prevented" mounting or some such. But that's over now. Now when I try to mount my flash drive, I get: 

"Failed to mount *insertdrivenamehere.* org.freedesktop.hal.storage.mount-removable no <-- (action, result)." 

Now, I've looked this up online, and the most useful thread I found was here: 

[http://www.suseforums.net/index.php?showtopic=47757&st=0&p=235769&#entry235769](http://www.suseforums.net/index.php?showtopic=47757&st=0&p=235769&#entry235769)

I've done three things: changed /etc/dbus-1/system.d/hal.conf like crazy to allow volume, power management, etc. access for all users. No luck. Also, I edited /etc/PolicyKit/PolicyKit.conf to add this:

```
<match action="org.freedesktop.hal.storage.mount-removable">
		<return result="yes" />
	</match>
```

Finally, I doubt that this is needed, but it's something I saw (on SUSE forums, which is why I doubt it's helping): I made /etc/PolicyKit/privilege.d/hal-storage-removable-mount-all-options.privilege which contains this: 

```
[Privilege]
RequiredPrivileges=
SufficientPrivileges=
Allow=uid:__all__
Deny=
CanObtain=False
CanGrant=False
ObtainRequireRoot=True
```

Now, so far, all this has done is remove the first error message. I still get: 

"Failed to mount *insertdrivenamehere.* org.freedesktop.hal.storage.mount-removable no <-- (action, result)."

I'd really like this machine to be able to mount flash drives, etc. without being root (which does work.) If anyone needs clarification or more information, I'll do my best. Can anyone help here? Thanks.

---

### Post by Phonan on 2008-06-06
Bump?

---

### Post by Scheater5 on 2008-06-06
Well, you could try it the "old school" way, skipping any sort of automatic mounting.  It's why the /mnt/ folder is still there.  ```
sudo mkdir /mnt/mountpoint
sudo mount /dev/*da# /mnt/moundpoint
```
where * is the type of drive as Ubuntu sees it (s or h, most likely) and # is the partition number as ubuntu sees it.

---

### Post by Phonan on 2008-06-06
Man, normally I would, but I'm trying to get this to be usable for the other people who are going to be on this computer. Sorry...

---

### Post by Scheater5 on 2008-06-07
hmmm...over my head then.  Sorry I couldn't be of help.  Good luck.

---

### Post by Phonan on 2008-06-07
Thanks though for the idea of manually mounting.

---

### Post by Phonan on 2008-06-19
Well I did a different install of Ubuntu, reformatting etc and mounting works great now. Perhaps it was because I started with the SERVER disc.... I'm not sure why, it was probably just some random bug that showed up by accident, but now my problem's gone. Thanks everyone who tried to help.

---

### Post by aquavitae on 2008-06-19
Probably too late for you now, but the gentoo wiki if a good place to look for low level stuff like that.  You have to adapt the instructions slightly (e.g. sudo apt-get instead of su emerge) but they can really help with setting up hal and such like.

---

