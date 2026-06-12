---
title: "File Question"
date: 2006-11-01
forum: General Help
---

### Post by Ringil on 2006-11-01
Hi Everyone,

Currently I am running Windows XP on my computer, and have two partitions. One partition has my OS on it, and the other has all my files, such as pictures, text documents, and music. That partition is of course, encoded so that it will work on Windows.

When I install Ubuntu, will I still be able to access the files that are on the second partition? If not, is there a way I can make it so I can access them on both Ubuntu and XP?

I'd really appreciate some help with this.

---

### Post by John.Michael.Kane on 2006-11-01
Have look over this
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Joe_CoT on 2006-11-01
As for whether you can access it, and whether you can write to it, it depends entirely on the filesystem. [this guide](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows) pretty much tells you how to deal with any of them.

Most likely, your second drive is NTFS. In that case, you can read the files from Ubuntu, but you can't write or modify them from ubuntu, unless you install a beta module such as fuse (mentioned in the guide). If it were FAT32, linux would have native read and write support for it. I generally make my data drive FAT32 for this reason, but it has many limitations -- mostly a max 4gb file size (doesn't work too well with dvd isos :-/ )

---

### Post by jpkotta on 2006-11-01
> **Joe_CoT said:**
> As for whether you can access it, and whether you can write to it, it depends entirely on the filesystem. [this guide](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows) pretty much tells you how to deal with any of them.

Most likely, your second drive is NTFS. In that case, you can read the files from Ubuntu, but you can't write or modify them from ubuntu, unless you install a beta module such as fuse (mentioned in the guide). If it were FAT32, linux would have native read and write support for it. I generally make my data drive FAT32 for this reason, but it has many limitations -- mostly a max 4gb file size (doesn't work too well with dvd isos :-/ )

You can make FAT file systems bigger than 4 GB.  I have one that is 5.1 GB.  It doesn't make too much sense for a 32 bit fs, though...

---

### Post by Joe_CoT on 2006-11-01
> You can make FAT file systems bigger than 4 GB. I have one that is 5.1 GB. It doesn't make too much sense for a 32 bit fs, though...

No, I said **file sizes** over 4GB, not **file systems** over 4gb. My fat32 partition is 200GB, and fat32 partitions have a maximum size in the terabytes; a single file can't be bigger than 4gb. So I can have my entire mp3 collection on there just fine, but I can't save a dvd ISO file to it.

---

### Post by Ringil on 2006-11-02
Cool. Thanks for the help everyone. I'm just starting to read one of the guides now.

I don't really mind not being able to have files over 4GB. I never burn DVDs on this computer (don't have a DVD burner), and I don't do video stuff, so that should be fine.

---

### Post by Joe_CoT on 2006-11-02
> I don't really mind not being able to have files over 4GB. I never burn DVDs on this computer (don't have a DVD burner), and I don't do video stuff, so that should be fine.

Good choice. There's modules for linux that let it write ntfs, and there's drivers for Windows that let it use ext3, but I've never gone wrong with Fat32 for the data partition 8)

Keep in mind, however, that Windows will not let you format large partitions (i think the limit is 20GB?) as fat32 -- not because that's the maximum it supports, but because they want you to use ntfs. You can use Partition Tragic or something like that to format it, or you can install the ubuntu package 'dosfstools' (comes with Dapper/Edgy standard I believe) and the command mkdosfs to format the partition

```
sudo mkdosfs -F 32 /dev/hda2
```

With your fat32 partition path, obviously. It'll show up in windows just fine once it's formatted.

---

### Post by Ringil on 2006-11-02
> **Joe_CoT said:**
> Good choice. There's modules for linux that let it write ntfs, and there's drivers for Windows that let it use ext3, but I've never gone wrong with Fat32 for the data partition 8)

Keep in mind, however, that Windows will not let you format large partitions (i think the limit is 20GB?) as fat32 -- not because that's the maximum it supports, but because they want you to use ntfs. You can use Partition Tragic or something like that to format it, or you can install the ubuntu package 'dosfstools' (comes with Dapper/Edgy standard I believe) and the command mkdosfs to format the partition

```
sudo mkdosfs -F 32 /dev/hda2
```

With your fat32 partition path, obviously. It'll show up in windows just fine once it's formatted.
I'm using Partition Magic, but the partition is only 15GB so it wouldn't be a problem any way.

I'm guessing to change the partition to FAT32 I'm going to have to format it. Oh well, I'm just happy that Dad's got a DVD burner.

---

