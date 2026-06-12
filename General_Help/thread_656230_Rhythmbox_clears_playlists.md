---
title: "Rhythmbox clears playlists"
date: 2008-01-02
forum: General Help
---

### Post by crazybeard on 2008-01-02
Started up Rhythmbox this morning and a number of my playlists were cleared of any music.  Just empty playlists.  The music is still there (in their directories) and I haven't changed anything that I am aware off.  I haven't even done any upgrades to any of my software since I last used it.

I am using Ubuntu 7.10 and Rhythmbox 0.11.2

What could have happened?

brian

---

### Post by Nunu on 2008-01-02
Is your music on a different partition, for instance a ntfs file system maybe. you need to open the NTFS partition before starting Rhythmbox else it will clear the play list because it can't see the files.

---

### Post by crazybeard on 2008-01-03
Thanks for the reply.

My music is indeed on a ntfs partition.  However, it mounts at start up and it was mounted when I started Rhythmbox.       The interesting part is that some playlists cleared and some did not.  All the music is located in subdirectories which in turn are contained in the same single directory on the same partition.   

Something else interesting:
I have one large list made up of the same music in several other play lists.   All the music that disappeared in the individual play lists also disappeared in the large play list.  However, the music that didn't disappear, that was also added to the large play list, is still there (in the large list).    The music files haven't moved and are still on that partition.   Go figure.  This is really strange.

b--

---

### Post by crazybeard on 2008-01-03
I am such an dumb dumb!   I just figured out the problem.   Somewhere in the past I had added a link to my docs folder on the ntfs to my desktop.  The other day I deleted it.  Some of my playlists were built through that link, some were built directly through the mount point.   Sorry to waste everyone's time.

b--

---

