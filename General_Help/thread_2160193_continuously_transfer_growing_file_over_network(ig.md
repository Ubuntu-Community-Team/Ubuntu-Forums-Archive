---
title: "continuously transfer growing file over network(ignoring temporary end-of-buffer's)"
date: 2013-07-06
forum: General Help
---

### Post by buntuyu on 2013-07-06
Hi.

I realize this may not be ubuntu-specific/exclusive, but I thought it may be somewhat justifiable to post it here.

Say you have a continuously growing log file on system A.  Is there a way to issue some single file transfer command, to start transferring the file to System B, across the network, such that the utility does not exit when the supply buffer (from A) is depleted, but rather anticipates the buffer to become non-empty again, waits for that to happen, then resumes transfer, continuing to append to the file copy to the remote system B.

I have checked ncftp, rsync, and others.  Everything seems to be exiting on empty-buffer. Unless I am wrong.

Thanks in advance

---

### Post by Kujua on 2013-07-07
I think with off-the-shelf applications it might not be possible to do exactly what you want - that is, to have an endless file-transfer connection which waits and sends more data as it becomes available. If you really need it, you might have to write your own client and server programs to achieve this. But I think there are simpler alternatives:

First, why exactly do you need it to be one continuous transfer? Is it because you do not want to send the whole file again if there is a minor update? If so you can run rsync periodically in delta-transfer mode. Only the newly added log messages will be sent to B.

With the above method the log file on B can be out-of-sync during the intervals between rsync runs. If this is a concern then another option is to use NFS to export the logs directory on A. That way when an application on B accesses the log file, it will always get the up-to-date version.

There might be other options besides these. In any case I think you are complicating the matter by trying to have a single endless transfer.

---

