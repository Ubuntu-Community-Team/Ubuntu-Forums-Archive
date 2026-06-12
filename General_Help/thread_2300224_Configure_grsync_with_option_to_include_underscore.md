---
title: "Configure grsync with option to include underscores in directories/files names"
date: 2015-10-24
forum: General Help
---

### Post by dragonfly41 on 2015-10-24
I'm using grsync GUI tool in Ubuntu 14.04 to backup partitions (ext4 and ntfs formats) from local drive to external USB drive.

I've noticed that the contents of directories prefixed with underscore "_" do not get copied into the destination directories. 
The directories are copied with the correct underscore prefix name .. but not their contents.

(I sometimes rename directories or files with underscore as a quick means of disabling applications under test rather than uninstalling them).

I guess that I need to configure Advanced Options > Additional Options field.

But what option should I place in this Additional Options field?

---

### Post by dragonfly41 on 2015-10-24
I've now found this ..  [http://serverfault.com/questions/414358/rsync-filter-file-rules-for-subpath](http://serverfault.com/questions/414358/rsync-filter-file-rules-for-subpath) ..
which gives some example of using filter.txt to filter underscore in names

rsync -a --include-from=filter.txt /path/to/source/ /path/to/dest

I'll try this  filter rule .. [COLOR=#0000ff]+**/_*[/COLOR] .. later when I've finished a grsync session which is now running.

---

### Post by dragonfly41 on 2015-10-24
I have now completed my (48GB) grsync session and I see that the contents of  /_directoryname has in fact been copied without need for filter rule.

I'm not understanding how the rsync process works since on first posting my question above I could see an empty "/_development" folder which was created as first folder at top of target .. but the contents of this folder were only copied at the _completion_ of the grsync session.  It seems that folders are created first and then their contents follow out of sequence. Puzzling.

I also noticed that all copying of assets is done in reverse alphabetical order and so "_" (at top of tree) comes at end of this process.

Anyway first session is ended. Now for several more partitions to follow.

---

