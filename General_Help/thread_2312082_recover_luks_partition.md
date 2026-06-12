---
title: "recover luks partition"
date: 2016-02-01
forum: General Help
---

### Post by soomon on 2016-02-01
I recently scewed up my raid and now I am trying to find a way to get the data from my luks partition (on that raid back) back.
in the end I recreated the array with mdadm --create which probably was a big mistake...
Now it starts but it sais that /dev/md0 is not a valid LUKS device.
I think the problem is a wrong offset as the LUKS header doesnt begin at the offset 0, which it should from what I read

```
# grep -a -b -P --only-matching 'LUKS' /dev/md0
# 1048576:LUKS
```

so I created a loopback device to test the LUKS header:
```
# losetup -o 1048576 -r -f /dev/md0
# losetup -a
# /dev/loop1: [0005]:31035 (/dev/md0), offset 1048576
```

I then tried to open it: cryptsetup luksOpen /dev/loop1 loop1
And it seemed to work. I have the mapper device. But when I try to mount it, it wants me to specify a filesystem type:

```
# mount /dev/mapper/loop1 /media/raid
# mount: block device /dev/mapper/loop1 is write-protected, mounting read-only
# mount: you must specify the filesystem type
```

It WAS ext4, when I try to mount it:
```
# mount /dev/mapper/loop1 /media/raid -t ext4
# mount: block device /dev/mapper/loop1 is write-protected, mounting read-only
# mount: wrong fs type, bad option, bad superblock on /dev/mapper/loop1,
#        missing codepage or helper program, or other error
#        In some cases useful info is found in syslog - try
#       dmesg | tail  or so

```


I ran testdisk on the device and it shows strange stuff. I only had 1 big partition there (ext4, full size of the disk)

```

Disk /dev/mapper/loop1 - 9001 GB / 8383 GiB - 17580794880 sectors (RO)
Current partition structure:
     Partition                  Start        End    Size in sectors

Bad GPT partition, invalid signature.
Trying alternate GPT
Bad GPT partition, invalid signature.

```


When I do a search:

```

  MS Data                        0 17580799999 17580800000
check_FAT: Unusual media descriptor (0xf0!=0xf8)
Warning: number of heads/cylinder mismatches 2 (FAT) != 1 (HD)
Warning: number of sectors per track mismatches 18 (FAT) != 1 (HD)
  MS Data                 15491476   15494355       2880 [EFISECTOR]
  Mac HFS                 30754963   43337876   12582914
  Mac HFS                 50531792 1132894364 1082362573 [`x ~Wo~QM-9PT~V~R ~]:M-Z~I~G^K]

```



does anyone have an idea how I can get my data back? :O



thanks!!!

---

### Post by Nuno_Abreu on 2016-02-02
Probably the filesystem is corrupted. Try to check for errors with this command - again, I'm not responsible if you permanently cannot access it.
```
sudo fsck /dev/mapper/loop1
```

Then tell me the output or if it did work.

---

### Post by soomon on 2016-02-02
sadly it cannot find a filesystem. Also the backup superblocks dont work :/

I found a script that tries to mount the filesystem with different offsets, as I had to use a different offset for luks aswell:

```
sz=512 # or 1024, 2048, 4096 higher = faster

for i in {2..10000000}; do
    echo "--->$i<---"
    mount -o offset=$(($bsz*$i)) -t ext4 /dev/whatever /mnt/foo
    if [ $? == 0 ]; then # whahoo!
        echo Eureka
        break
    fi
done
```

It didnt find anything for hours :/


testdisk sais: invalid GPT and backup GPT table, but when I do a quickscan it shows: 

```
Disk /dev/mapper/loop1 - 9001 GB / 8383 GiB - 17580794880 sectors (RO)
Analyse cylinder 2177662976/400925695: 12%


  MS Data                        0 17580799999 17580800000
check_FAT: Unusual media descriptor (0xf0!=0xf8)
Warning: number of heads/cylinder mismatches 2 (FAT) != 1 (HD)
Warning: number of sectors per track mismatches 18 (FAT) != 1 (HD)
  MS Data                 15491476   15494355       2880 [EFISECTOR]
  Mac HFS                 30754963   43337876   12582914
  Mac HFS                 50531792 1132894364 1082362573 [`x ~Wo~QM-9PT~V~R ~]:M-Z~I~G^K]
  Mac HFS               1263448322 1970188547  706740226
  Unknown               1987919486 40172261555837 40170273636352 [kM-9M-n^X]

```





no idea why it sais mac HFS or MS data...
for whatever reason it does show an efi sector, but shouldnt that show up earlier?
also that first partition should be it. right?
not sure if it can be recovered though...

when i stop testdisk, it shows:

```
Disk /dev/mapper/loop1 - 9001 GB / 8383 GiB - 17580794880 sectors (RO)

     Partition                  Start        End    Size in sectors

 1 P MS Data                 15491476   15494355       2880 [EFISECTOR]
 2 P Mac HFS                 30754963   43337876   12582914
 3 P Mac HFS                 50531792 1132894364 1082362573 [`x ~Wo~QM-9PT~V~R ~]:M-Z~I~G^K]
 4 P Mac HFS               1263448322 1970188547  706740226
 5 P Mac HFS               2267560288 2296527713   28967426 [9]
```


but i was only able to write the changes, do a deeper search or quit. the big partition didnt show up any more... do I need to wait until testdisk scans the whole 9TB? or does it meen it cannot recover the partition?
I can only brows the EFISECTOR thingy, it lists a /efi/boot/bootx64.efi
Cannot browse the others

after LUKS was able to mount the encrypted device, I was hoping to get the data back. Is there any other way to scan for an ext4 filesystem or do you think any of the partitions shown by testdisk are worth a shot?

---

### Post by soomon on 2016-02-06
anyone?

---

### Post by soomon on 2016-02-14
alright I managed to find out that I should select intel instead of EFI. still the problem remains the same.  
when testdisk starts it directly finds one big partition:

Disk /dev/mapper/loop0 - 9001 GB / 8383 GiB - 17580794880 sectors
Analyse cylinder 399540224/400925695: 26%


  Linux                          0 17580799999 17580800000

which shoudl be the one I want because it starts at the beginning of the device and goes all the way to the end. 
sadly, when testdisk finishes, I neither see the partition on the "not recoverable" partitions nor on the ones I can recover.
shouldnt it still be there or am I missing something?

---

