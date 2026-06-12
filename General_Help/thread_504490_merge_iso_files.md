---
title: "merge iso files"
date: 2007-07-19
forum: General Help
---

### Post by gertvdr on 2007-07-19
Hi,

Does anyone know of a way to merge cd iso files to one dvd iso? I downloaded the K12LTSP distro which comes in 6 cd images of 600MB each, I would like to merge them into 1 dvd image.

Thanks for your help.

---

### Post by mcduck on 2007-07-19
> **gertvdr said:**
> Hi,

Does anyone know of a way to merge cd iso files to one dvd iso? I downloaded the K12LTSP distro which comes in 6 cd images of 600MB each, I would like to merge them into 1 dvd image.

Thanks for your help.

You cannot do such thing. If it's 6 CDs, then it's 6 CDs, not a DVD.

---

### Post by king_rero on 2008-02-10
Hi,

I was looking for some thing like that, I found this:

> I hardly ever have to do this, so I can never remember precisely how to do it. Hopfully by noting it here, I won’t forget again.

Specifically, I want to do this so that I can create a single DVD image from the FreeBSD 6.3 CD images I have. Here’s more-or-less how it goes:

mount -t iso9660 -o loop disc1-mountpoint
mount -t iso9660 -o loop disc2-mountpoint
mkisofs -l -J -R -o dvd.iso disc1-mountpoint disc2-mountpoint

Don’t forget to unmount those mountpoints afterwards.

Here’s a shell script to do the work. It assumes it’s in a directory with a subdirectory called isos, which contains the source .iso images. It has no error handling, so the usual caveats apply:

> ```
#!/bin/sh

rm -rf mnt contents
mkdir mnt contents
for i in isos/*.iso; do
    mount -t iso9660 -o loop $i mnt
    cp -av mnt/* contents
    umount mnt
done

# This bit is specific to merging FreeBSD .isos.
sed -i -e 's/^CD_VOLUME = .$/CD_VOLUME = 1/' contents/cdrom.inf
sed -i -e 's/|.$/|1/' contents/packages/INDEX

mkisofs -l -J -R -o dvd.iso contents
rm -rf mnt contents
```

The site I've found on it is:
[http://talideon.com/weblog/2008/01/debian-merging-isos.cfm]("http://talideon.com/weblog/2008/01/debian-merging-isos.cfm")


By the way I didn't try it yet :popcorn:

---

