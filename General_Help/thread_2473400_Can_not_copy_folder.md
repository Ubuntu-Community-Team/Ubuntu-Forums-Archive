---
title: "Can not copy folder"
date: 2022-04-03
forum: General Help
---

### Post by coolricksanchez on 2022-04-03
Hi

I am trying to copy a folder to an SMB share using the following command:

```
cp -r -u /var/snap/plexmediaserver/common/Library/'Application Support'/'Plex Media Server' /mnt/PlexMetadataBackup
```

but then I receive lots of messages like this one:

```
cp: cannot create symbolic link '/mnt/PlexMetadataBackup/Plex Media Server/Metadata/Albums/0/82b061f4ac86407f1928bb0137b85f547fd7f78.bundle/Contents/_combined/tracks/a44de8f662a6af0c6ceb7fb6f6b18a7b8197dd51/lyrics/com.plexapp.agents.lyricfind_8a00a92097f7e634f6fd8838d5a988f0a4996a27': Operation not supported
```

Why am I getting those messages and how can I copy that folder?

I made share the share is mounted, I have also access and permissions to add and delete files from it.

---

### Post by TheFu on 2022-04-03
Use rsync:
$ rsync -avz  "/var/snap/plexmediaserver/common/Library/Application Support/Plex Media Server" /mnt/PlexMetadataBackup

Symbolic links will be copied, but they will not be followed.

---

### Post by coolricksanchez on 2022-04-05
> **TheFu said:**
> Use rsync:
$ rsync -avz  "/var/snap/plexmediaserver/common/Library/Application Support/Plex Media Server" /mnt/PlexMetadataBackup

Symbolic links will be copied, but they will not be followed.

Thanks, it seems like it's working. What do you mean exactly with Symbolic links will be copied, but they will not be followed?

---

### Post by ActionParsnip on 2022-04-05
Can you SSH to the media server? If so then mount the remote file system using SSHFS and you'll have an easier time

---

### Post by TheFu on 2022-04-05
> **coolricksanchez said:**
> Thanks, it seems like it's working. What do you mean exactly with Symbolic links will be copied, but they will not be followed?

I mean that the file system object for a symbolic link will be copied on, but that where it points will not be followed, so if that location is outside the area being backed up, then it won't be included.  That's what 'not followed' means.

---

### Post by TheFu on 2022-04-05
> **ActionParsnip said:**
> Can you SSH to the media server? If so then mount the remote file system using SSHFS and you'll have an easier time

He's doing local copies.  rsync is easier than sshfs AND 100x faster over remote connections, but that doesn't apply here.

---

