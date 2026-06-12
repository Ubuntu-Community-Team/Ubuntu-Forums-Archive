---
title: "What hard drive transfer speeds should I be getting?"
date: 2007-09-02
forum: General Help
---

### Post by juxtaposed on 2007-09-02
Ok, i've got one internal hard drive. I think it's sata. I have a root partition that is XFS and a data partition that is EXT3. I tried transfering a 4.3GB file over from the EXT3 partition and it took awhile, on average 5MBps. I tries transfering the same file from that partition to an encrypted xfs truecrypt container on the xfs partition and it went at 3MBps.

Now,  that seems awfully slow to me. Arn't hard drives supposed to get like 50MBps?

I'm running Debian Etch (I dont have an account on the debian forums that I know of, so I decided to ask here since I go here often and ubuntu is pretty close to debian ;D).

---

### Post by juxtaposed on 2007-09-08
I thought this would be an easy question for people, I guess not :P

---

### Post by atlfalcons866 on 2007-09-17
ext3 is not good with large files

---

### Post by juxtaposed on 2007-10-07
It's now XFS and it isn't much faster :(

---

### Post by fjgaude on 2007-10-07
I use ext3 on raid5 and JBODs and get from 70 to 114 MB/sec. All drives are latest technology. Drives two or more years old got 20 to 40 MB/sec. All measurements using hd -tT /dev/sd[n] or Gkrellm. Many files are 7 GB in length, most are not.

How old are your drives?

---

### Post by juxtaposed on 2007-10-07
The external is about a year old, the internal is probably two years old.

Now transferring from the external to an internal gives me 700KBps. That's like... USB1 speeds. Odd, and annoying :(

EDIT: I am very suprised. Instead of starting up my computer and turning on and mounting the external (which sets it to /dev/sdf1), I turn it on and then turn on the computer (which sets it to be /dev/sdb1), it does 15-18MBps instead of 700KBps!

EDIT: And I unmount it, turn it back on and mount it. Now it's back. I guess I have to restart the computer all the time to use it :P

---

### Post by atlfalcons866 on 2007-10-09
i always have problems with ext3. I use because it is the default fs in ubuntu. 

My hard drive says it has a bandwidth of 100MB/s but i only get 19mb/s.

---

