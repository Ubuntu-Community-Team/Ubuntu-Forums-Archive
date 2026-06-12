---
title: "Newb question regarding cURL"
date: 2012-12-13
forum: General Help
---

### Post by U2XS on 2012-12-13
I just installed cURL & I am using it to get a remote file from another server & then delete that file.  The part that surprises me is that I am able to delete a file on a different server without providing any sort of credentials!  I'm going to guess that it has to do with CHMOD, but it's really all I've got.  How is it possible?

---

### Post by Cheesehead on 2012-12-13
curl can ask to delete a remote file. Approval of that action will be based on the remote permissions.

curl also *does* include credentials...if you have told curl to include them.

---

