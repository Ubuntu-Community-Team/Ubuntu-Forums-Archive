---
title: "Swap not being autmatically turned on in gutsy anymore"
date: 2007-12-28
forum: General Help
---

### Post by sefs on 2007-12-28
Hi  I have a small problem with my swap...its not being turned on at boot up ... I now have to go into gparted and swapon.

To tell you the truth i don't know how long this has been.


in my fstab is
```

proc /proc proc defaults 0 0
# Entry for /dev/hda1 :
UUID=471906a1-3aa4-4c6c-b378-4ba1b95b82c3 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/hda5 :
UUID=d8a6a7d3-6b4f-42b3-b72d-1db2b966900c /home ext3 defaults 0 2
# Entry for /dev/hda6 :
UUID=bed1ebc5-dd71-49cb-b046-edeb6547abe3 /media/hda6 ext3 defaults 0 2
# Entry for /dev/hdb1 :
#UUID=0ffa9991-ad8d-4c6d-ae90-eb177119dcfb /media/hdb1 ext3 defaults 0 2
# Entry for /dev/hda7 :
UUID=341eab80-ecfc-4ec7-a19d-a4381f441780 none swap sw 0 0
# Entry for /dev/hdb5 :
#UUID=97f5e36c-3b56-4389-9395-3d0c40dafcef none swap sw 0 0

```

blkid gives me 

```

/dev/hda1: UUID="471906a1-3aa4-4c6c-b378-4ba1b95b82c3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: LABEL="data1" UUID="d8a6a7d3-6b4f-42b3-b72d-1db2b966900c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda6: LABEL="data2" UUID="bed1ebc5-dd71-49cb-b046-edeb6547abe3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda7: TYPE="swap" UUID="2c5fdb00-c0e8-4ab7-a0c0-0b23d13072ec" 

```

The uuid seems to differ between the two

should they report the same thing? and should i change the fstab to what the blkid says?

---

### Post by taurus on 2007-12-28
Yes, the UUID needs to be the same.  Is the UUID in /etc/fstab was before you changed or moved your partitions around?  If it is, then you need to replace it with the new one.

---

### Post by sefs on 2007-12-28
I didnt really change anything that i can recall ... i just noticed the difference.

---

### Post by taurus on 2007-12-28
Didn't you move your partitions around with gparted?  Whatever happened to /dev/hdb5?

---

### Post by sefs on 2007-12-29
hdb5 was swap i had created on a second hard drive but i took it out to save power...so just commented out all the hdb entries.  So you think I should just change it to what blkid said right?

---

