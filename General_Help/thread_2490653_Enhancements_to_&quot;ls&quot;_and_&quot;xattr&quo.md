---
title: "Enhancements to &quot;ls&quot; and &quot;xattr&quot;"
date: 2023-09-11
forum: General Help
---

### Post by happy-hobo on 2023-09-11
There's probably a better forum for this, but I don't know where.

It's been at least a decade since I used Ubuntu regularly, but this suggestion I made to Apple applies to any Linux or BSD distro (except for #1 which is Apple-unique)

Below is an excerpt of a directory listing.  Suggestions:

(1. Add com.apple.metadata:kMD* to EVERY download, not merely on MP3 files &#8212; Apple only)

2. Add an option to "ls -l@" that displays the VALUES of all extended attributes instead of their sizes.
   (or in addition to size)

3. Add to xattr a way to use wildcards in the name of the extended attribute

4. Add options to xattr and ls to put the fields in the value on separate lines instead of semicolon-delimited.
   (Even better, interpret the values instead of showing raw)

5. Pass these ideas on to the maintainers of ls & xattr on any other Unix variant.


WGroleau@MBP ~ % ls -late@O Downloads | more
total 1735720
-rw-r--r--@   1 WGroleau  staff  -         148582 Sep 11 06:31 from_DDG.jpg
        com.apple.quarantine           61 
-rw-r--r--@   1 WGroleau  staff  -         148582 Sep 11 06:31 from_Safari.jpg
        com.apple.quarantine           85 
-rw-r--r--@   1 WGroleau  staff  -      219070316 Sep  8 23:06 Sint_Maarten_dload_hi.mp4
        com.apple.avkit.thumbnailCacheEncryptionKey            16 
        com.apple.avkit.thumbnailCacheIdentifier               16 
        com.apple.lastuseddate#PS              16 
        com.apple.quarantine           61 
-rw-r--r--@   1 WGroleau  staff  -        1497234 Sep  7 07:38 FPB.mp3
        com.apple.macl         72 
        com.apple.metadata:kMDItemDownloadedDate               53 
        com.apple.metadata:kMDItemWhereFroms          154 
        com.apple.quarantine           57

---

### Post by TheFu on 2023-09-11
So ... **ls** is part of the GNU Core Utils.  Take it up with GNU.  [https://www.gnu.org/software/coreutils/](https://www.gnu.org/software/coreutils/)

I don't see Canonical touching this code, since every Linux distro would need to be involved.

---

### Post by coffeecat on 2023-09-12
> **happy-hobo said:**
> There's probably a better forum for this

Without a doubt, there will be. You posted in our General Help sub-forum whose strapline clearly states, "All your general support questions for Ubuntu, Kubuntu, Edubuntu, Xubuntu, Lubuntu, Ubuntu Mate, Ubuntu Budgie, Ubuntu Studio and Ubuntu Kylin." If there is a support question about Ubuntu in your post, it has escaped me. ***Thread closed***.

A couple of points:

This is a volunteer forum of end-users who help each other. We are neither developers or maintainers of Ubuntu. This is not the place to contact the developers of Ubuntu, and definitely not the place to contact developers of the gnu project. So...

> **happy-hobo said:**
> 
5. Pass these ideas on to the maintainers of ls & xattr on any other Unix variant.

Making peremptory demands of the forum membership is not polite. Making peremptory demands that cannot be fulfilled is both pointless and potentially counter-productive.

---

