---
title: "Hardlinks and &quot;mount --bind&quot;"
date: 2014-01-29
forum: General Help
---

### Post by enf0 on 2014-01-29
Hello everyone,

I've followed the wiki article on [how to set up an NFSv4 server]("https://help.ubuntu.com/community/NFSv4Howto") using a pseudo filesystem under */export/* to present to the NFS client.

This is how my setup looks so far:

**SERVER1**
```

/mnt/storage/
          - folder1/
          - folder2/
          - folder3/ # [I](i.e. private folder which I do not want to export to NFS!)
[/I]          - etc..

$ mount --bind /mnt/storage/folder1 /export/CLIENT1/folder1
$ mount --bind /mnt/storage/folder2 /export/CLIENT1/folder2

/export/CLIENT1/
          - folder1/
          - folder2/

```

[B]CLIENT1
[/B]```

$ mount -t nfs4 SERVER1:/ /mnt/SERVER1

/mnt/SERVER1
          - folder1/
          - folder2/

```

Now, trying to create a hardlink between *folder1 *and *folder2* on the client gives me this error:
```

$ ln /mnt/SERVER1/folder1/test.txt /mnt/SERVER1/folder2/test.txt

ln: creating hard link `/mnt/SERVER1/folder1/test.txt' => `/mnt/SERVER1/folder2/test.txt': Invalid cross-device link


```

I assume this is because the two folders are actually seen as two different filesystems and as such won't allow hardlinks between them. I understand that.

** What I'm really asking is if there is another way of presenting certain sub-directories to a client while keeping them inside the same "filesystem" in order for things like hardlinks to work?**


Thanks in advance for any assistance!

---

