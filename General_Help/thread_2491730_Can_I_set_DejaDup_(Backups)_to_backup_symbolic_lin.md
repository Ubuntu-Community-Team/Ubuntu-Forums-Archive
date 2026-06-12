---
title: "Can I set DejaDup (Backups) to backup symbolic links (22.04)"
date: 2023-10-19
forum: General Help
---

### Post by ittayd on 2023-10-19
My use case is that I want to backup files strawn in folders like .local that are otherwise huge. So I thought of creating a folder 'backups' and whenever I have such a file, create a symlink to it from backups. But will 'backups' be backedup?

---

### Post by TheFu on 2023-10-20
I bet the links are backed up, but not followed. This is the expected behavior.

I don't use Deja Dup or any Duplicity-based backup tools. They didn't meet my needs when I tested them. Anyway, this just means I don't have any recent, relevant knowledge, but wanted you to see that someone actually read your post.

Before selecting any backup tool, it is always a good idea to also search for how it fails according to other people.  Deja Dup has a number of posts about corrupted backups, which are worth considering.  After all, a backup that can't be restored is a complete waste of time, effort and storage.

What is a "files strawn in folders"?

If the file is on the same file system, just use a hardlink, not a symbolic link.  [https://en.wikipedia.org/wiki/Hard_link](https://en.wikipedia.org/wiki/Hard_link)

Or better, add the directory where the file is actually stored to your backup list of directories to be included.  Storage design for me is mostly about backups, but also about security. I split up different parts of the file system to ensure I can backup at the file system level and each file system can have different mount options to increase security.  YMMV, of course.

---

### Post by ittayd on 2023-10-20
Thanks for the hardlinks tip. What backup solution do you use?

---

### Post by TheFu on 2023-10-20
"solution" isn't the right term. I use a number of different tools and processes to script before, during and after the backups. I've posted lots of backups and restores in these forums. Do some searching and reading. Note the dates, so you can tell which is newer and which are older. There have been subtle improvements to my method over the last 13 yrs as I run into minor issues or decide more data would be useful for error correction, not just restores.

The tools that actually does the "backup" is rdiff-backup.  But I use LVM snapshots, and run about 15 commands to capture needed, useful, data, pre-backup.  Running the backup command is kinda anti-climactic. Then the cleanup afterwards is also good. I don't leave snapshots lying around, for example.  There are many subtle reasons for _why_ I do things the way I do. Far too many to explain.

I wouldn't use hardlinks, BTW. Just because something is possible, that doesn't mean it is a good idea.

---

