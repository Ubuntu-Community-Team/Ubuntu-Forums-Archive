---
title: "A quick question about using dd for system backup"
date: 2022-12-09
forum: General Help
---

### Post by DVD-R on 2022-12-09
Hello All,
I'm curious about using dd from the terminal for system backup/restore functionality.

I've traditionally used a live thumbdrive with CloneZilla as a backup/restore utility.
And if I'm not mistaken - it uses dd as its backup and restore function.

The image file sizes CloneZilla generally creates for a full system backup are approximately 5 Gig in size.
So CloneZilla is obviously creating a compressed file.

When using dd from the terminal - does it also compress like CloneZilla does?
Or does it create a backup file the same exact size as what is being backed up?

Sincere thanks

---

### Post by ian-weisser on 2022-12-10
dd does not compress. Many applications that use dd under the hood do add compression.

Standard warning about dd:

Using dd casually from the terminal is unwise.
The command is utterly unforgiving of human typos and errors. There are no safety features, no guardrails, no protection from folly.

---

### Post by HermanAB on 2022-12-10
Contrary to popular perception, there is no difference between dd and cat and a few others when it comes to making low level device copies.

It is also usual to run it through gzip to compress all the empty space:

# cat /dev/sda | gzip -9 > image.gz
(Provided that you are running from a USB widget and not sda!)

You can also pipe the data over a network with netcat to another machine with a huge disk drive.

---

### Post by Impavidus on 2022-12-10
```
cat /dev/sda | gzip -9 > image.gz
```
That will compress empty space that was filled with zeros or ones, but not empty space that was filled with random data from deleted files. Clonezilla is smarter than that. On supported filesystems, it skips the empty space, even if filled with random data. After restoring the backup, the remnants of deleted files will be gone. Clonezilla does use dd under the hood (at least, that's what wikipedia tells me), but only on filesystems it doesn't understand.

---

### Post by mIk3_08 on 2022-12-10
> **ian-weisser said:**
> dd does not compress. Many applications that use dd under the hood do add compression.

Standard warning about dd:

Using dd casually from the terminal is unwise.
The command is utterly unforgiving of human typos and errors. There are no safety features, no guardrails, no protection from folly.
Now I know about this DD tool. Thanks for sharing ian-weisser. Regards and cheers.

---

