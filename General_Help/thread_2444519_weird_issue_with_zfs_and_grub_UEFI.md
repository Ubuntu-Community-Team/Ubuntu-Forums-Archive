---
title: "weird issue with zfs and grub UEFI"
date: 2020-05-31
forum: General Help
---

### Post by darksidedude on 2020-05-31
hello all,

I'm having some weird issues with ZFS and grub the updates from apt will install including kernel updates zsys will take its snapshots as intended and they will show up in grub (didn't test if they work) but new kernels installed do not show in grub. 

curious about this I ran 
```
sudo update-grub
```

and got a giant wall of text but these snippets are what I find confusing
 

```
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_au1fuu@autozsys_iy5deu
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_au1fuu@autozsys_iy5deu
cannot open 'bpool/BOOT/ubuntu_au1fuu@autozsys_fi34nf': dataset does not exist
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_au1fuu@autozsys_fi34nf
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_au1fuu@autozsys_fi34nf
/usr/sbin/grub-probe: error: unknown filesystem.
device-mapper: reload ioctl on osprober-linux-sdb4  failed: Device or resource busy
Command failed.
Adding boot menu entry for UEFI Firmware Settings
done

```

and running 
```
uname -r
```
shows 
```
5.4.0-31-generic
```

thanks in advance, I promise I didn't go out of my way to break anything on this install... yet...:lolflag:

---

### Post by DuckHook on 2020-05-31
I don't like the looks of:```
cannot open 'bpool/BOOT/ubuntu_au1fuu@autozsys_fi34nf': dataset does not exist
…
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_au1fuu@autozsys_fi34nf
/usr/sbin/grub-probe: error: unknown filesystem.

```
Did this happen right after a routine update &#8594; upgrade?

Please post: ```
df -hT -x squashfs -x tmpfs -x devtmpfs
``` ```
sudo zpool list
``` ```
sudo zpool status
``` ```
sudo zfs list
``` ```
dpkg --get-selections 5.4.0-33
``` ```
apt policy linux-generic
```Output will be lengthy so please be prepared.

---

### Post by sideburnie on 2020-06-08
I came across a similar issue when running update-grub after deleting "quiet splash" from /etc/default/grub so that I can see boot messages. 

```

&#10140;  ~ sudo update-grub2
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
grub-probe: error: unknown filesystem.
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_3py78c
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_3py78c
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_3py78c
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_3py78c
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_zgbzhk
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_zgbzhk
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_zgbzhk
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_zgbzhk
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_wpiqsu
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_wpiqsu
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_wpiqsu
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_wpiqsu
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_gcf84h
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_gcf84h
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_gcf84h
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_gcf84h
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_rr8o1q
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_rr8o1q
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_rr8o1q
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_rr8o1q
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_b5j7q5
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_b5j7q5
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_b5j7q5
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_b5j7q5
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_q83aau
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_q83aau
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_q83aau
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_q83aau
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_6ji45k
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_6ji45k
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_6ji45k
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_6ji45k
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_if2igp
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_if2igp
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_if2igp
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_if2igp
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_kdpqft
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_kdpqft
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_kdpqft
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_kdpqft
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_6ym59c
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_6ym59c
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_6ym59c
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_6ym59c
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_74nvnw
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_74nvnw
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_74nvnw
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_74nvnw
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_g100ql
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_g100ql
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_g100ql
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_g100ql
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_ngr5lx
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_ngr5lx
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_ngr5lx
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_ngr5lx
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_pxdopb
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_pxdopb
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_pxdopb
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_pxdopb
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_aeroka
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_aeroka
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_aeroka
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_aeroka
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_s20vf2
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_s20vf2
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_s20vf2
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_s20vf2
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_pddx5x
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_pddx5x
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_pddx5x
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_pddx5x
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_opyyb1
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_opyyb1
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_opyyb1
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_opyyb1
Found linux image: vmlinuz-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_73avjh
Found initrd image: initrd.img-5.4.0-26-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_73avjh
Found linux image: vmlinuz-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_73avjh
Found initrd image: initrd.img-5.4.0-33-generic in rpool/ROOT/ubuntu_82f6sx@autozsys_73avjh
device-mapper: reload ioctl on osprober-linux-sdb4  failed: Device or resource busy
Command failed.
device-mapper: reload ioctl on osprober-linux-sdc1  failed: Device or resource busy
Command failed.
device-mapper: reload ioctl on osprober-linux-sdd1  failed: Device or resource busy
Command failed.
device-mapper: reload ioctl on osprober-linux-sde1  failed: Device or resource busy
Command failed.
device-mapper: reload ioctl on osprober-linux-sdf1  failed: Device or resource busy
Command failed.
device-mapper: reload ioctl on osprober-linux-sdg1  failed: Device or resource busy
Command failed.
device-mapper: reload ioctl on osprober-linux-sdh1  failed: Device or resource busy
Command failed.
Adding boot menu entry for UEFI Firmware Settings
done

```


I noticed that my bpool seems to have disappeared? (There was a bpool at some point I think?)

```

&#10140;  ~ zpool status
  pool: raid
 state: ONLINE
  scan: none requested
config:

	NAME                                    STATE     READ WRITE CKSUM
	raid                                    ONLINE       0     0     0
	  raidz2-0                              ONLINE       0     0     0
	    ata-WDC_WD100EMAZ-00WJTA0_2YKGWVUD  ONLINE       0     0     0
	    ata-WDC_WD100EMAZ-00WJTA0_JEHMV0EM  ONLINE       0     0     0
	    ata-WDC_WD100EMAZ-00WJTA0_JEHWP98M  ONLINE       0     0     0
	    ata-WDC_WD100EZAZ-11TDBA0_JEKGZGNZ  ONLINE       0     0     0
	    ata-WDC_WD120EMAZ-11BLFA0_5PGJ37MD  ONLINE       0     0     0
	    ata-WDC_WD120EMAZ-11BLFA0_5PGL520C  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: none requested
config:

	NAME        STATE     READ WRITE CKSUM
	rpool       ONLINE       0     0     0
	  sdb4      ONLINE       0     0     0

errors: No known data errors

```

---

### Post by kneutron on 2020-06-10
--What happens when (as root) you issue ' zpool import ' ?  If your bpool got completely trashed, you may have to reinstall

---

### Post by marcosestevesbarbosa on 2020-06-10
I updated my system last night and now I have the same problem. After a zpool import bpool my bpool came back, but a grub-probe --device /dev/sdb4 keeps showing the same error of unknown filesystem.

---

### Post by sideburnie on 2020-06-15
> **kneutron said:**
> --What happens when (as root) you issue ' zpool import ' ?  If your bpool got completely trashed, you may have to reinstall

```

&#10140;  ~ zpool status
  pool: raid
 state: ONLINE
  scan: scrub repaired 0B in 0 days 04:05:38 with 0 errors on Sun Jun 14 04:29:39 2020
config:

	NAME                                    STATE     READ WRITE CKSUM
	raid                                    ONLINE       0     0     0
	  raidz2-0                              ONLINE       0     0     0
	    ata-WDC_WD100EMAZ-00WJTA0_2YKGWVUD  ONLINE       0     0     0
	    ata-WDC_WD100EMAZ-00WJTA0_JEHMV0EM  ONLINE       0     0     0
	    ata-WDC_WD100EMAZ-00WJTA0_JEHWP98M  ONLINE       0     0     0
	    ata-WDC_WD100EZAZ-11TDBA0_JEKGZGNZ  ONLINE       0     0     0
	    ata-WDC_WD120EMAZ-11BLFA0_5PGJ37MD  ONLINE       0     0     0
	    ata-WDC_WD120EMAZ-11BLFA0_5PGL520C  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 0 days 00:03:37 with 0 errors on Sun Jun 14 00:27:40 2020
config:

	NAME        STATE     READ WRITE CKSUM
	rpool       ONLINE       0     0     0
	  sda4      ONLINE       0     0     0

errors: No known data errors

```

```

&#10140;  ~ sudo zpool import
   pool: bpool
     id: 2033780025970084274
  state: ONLINE
 status: Some supported features are not enabled on the pool.
 action: The pool can be imported using its name or numeric identifier, though
	some features will not be available without an explicit 'zpool upgrade'.
 config:

	bpool       ONLINE
	  sda3      ONLINE

```

```

&#10140;  ~ zpool status     
  pool: raid
 state: ONLINE
  scan: scrub repaired 0B in 0 days 04:05:38 with 0 errors on Sun Jun 14 04:29:39 2020
config:

	NAME                                    STATE     READ WRITE CKSUM
	raid                                    ONLINE       0     0     0
	  raidz2-0                              ONLINE       0     0     0
	    ata-WDC_WD100EMAZ-00WJTA0_2YKGWVUD  ONLINE       0     0     0
	    ata-WDC_WD100EMAZ-00WJTA0_JEHMV0EM  ONLINE       0     0     0
	    ata-WDC_WD100EMAZ-00WJTA0_JEHWP98M  ONLINE       0     0     0
	    ata-WDC_WD100EZAZ-11TDBA0_JEKGZGNZ  ONLINE       0     0     0
	    ata-WDC_WD120EMAZ-11BLFA0_5PGJ37MD  ONLINE       0     0     0
	    ata-WDC_WD120EMAZ-11BLFA0_5PGL520C  ONLINE       0     0     0

errors: No known data errors

  pool: rpool
 state: ONLINE
  scan: scrub repaired 0B in 0 days 00:03:37 with 0 errors on Sun Jun 14 00:27:40 2020
config:

	NAME        STATE     READ WRITE CKSUM
	rpool       ONLINE       0     0     0
	  sda4      ONLINE       0     0     0

errors: No known data errors

```

---

### Post by sideburnie on 2020-06-17
I'd really like to disable the 20.04 splash screen so I can see boot messages, but it seems I'm stuck not being able to update grub in my current situation? 

I'm assuming I'm in a situation somewhat close to this: [https://askubuntu.com/questions/1245549/ubuntu-20-04-on-zfs-cant-update-kernel-bpool-missing](https://askubuntu.com/questions/1245549/ubuntu-20-04-on-zfs-cant-update-kernel-bpool-missing)

But I don't think my vdevs ever changed... all I did was update grub after removing "quiet splash"...

---

