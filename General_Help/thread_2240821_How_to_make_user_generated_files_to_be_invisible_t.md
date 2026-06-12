---
title: "How to make user generated files to be invisible to other users?"
date: 2014-08-22
forum: General Help
---

### Post by bjngchn on 2014-08-22
I was thinking in k/ubuntu if a user creates some files either by browsing or using an editor etc. those files remain under home directory of that user and becomes invisible to other users if chmod 700'ed. ... Then I realized while experimenting, tmp folder is shared by all users and files created by one user can be seen by any other user... This is a very bad thing, because tmp folder is being used outside user control.  In principle any activity or file belonging to one user can be seen by other users, because users can't control which files are created without user control and becomes public unintentionally.... Why are things done this way? Is it really very difficult to make those folders separate? Are there any other such folders? Is it possible to block such possibility, say, for example by chmodding tmp folder, so nothing can be written onto it?  When installing this system I required home folder encryption in addition to global encryption. It looks like at least home folder encryption is completely useless.

---

### Post by bjngchn on 2014-08-22
One more question: if a user is deleted together with its files, are associated files in tmp and other root folders also deleted?

---

### Post by ian-weisser on 2014-08-22
> **bjngchn said:**
> tmp folder is shared by all users and files created by one user can be seen by any other user... This is a very bad thing, because tmp folder is being used outside user control.  In principle any activity or file belonging to one user can be seen by other users, because users can't control which files are created without user control and becomes public unintentionally.... Why are things done this way?

Users are not supposed to be creating private files in /tmp for precisely that reason. It's not their directory, it's publicly readable, and it's flushed at times that they cannot discover or control. User data belongs in /home. You can enforce this easily.

Applications can (and do) create session files in /tmp for various reasons. Many applications store lockfiles, temporary databases, working files, and various session references in /tmp.


> **bjngchn said:**
> Is it possible to block such possibility, say, for example by chmodding tmp folder, so nothing can be written onto it?

Chmodding or Chowning /tmp will thoroughly break your system. Applications expect to be able to read/write to it.


> **bjngchn said:**
> One more question: if a user is deleted together with its files, are associated files in tmp and other root folders also deleted?

No. Because user-associated files should only be in /home. Users do not have permission to wander the system placing files anywhere they please. If you discover a user doing that, lock them out immediately.

---

### Post by bjngchn on 2014-08-22
I wonder why are things done this way. Are all linux' like this? Why are tmp's not different for different users? This is an obvious antisecurity/antiprivacy thing forced on users. ... Are there other such folders? It looks like, for downloads, tmp  folder have  to be used. So probably most files are copied to /tmp at some point. Since files are not really deleted, any activity belonging to a user may remain on computer forever. Why are all other people not angry about such a thing (violation of security/privacy). It is impossible to understand.

---

### Post by ian-weisser on 2014-08-22
> **bjngchn said:**
> Are all linux' like this?

Yes, with a few exceptions irrelevant to this discussion.
> **bjngchn said:**
> Why are tmp's not different for different users?

They can be.
Users can put anything they want in /home. Including their tempfiles.
/tmp is the SYSTEM temp directory.


 > **bjngchn said:**
>  This is an obvious antisecurity/antiprivacy thing forced on users.

No, it's an obvious place to put temporary files. Please explain clearly why you believe that to be a security issue.


 > **bjngchn said:**
> Are there other such folders? It looks like, for downloads, tmp  folder have  to be used.

No. Depends upon the application you use to download. The wget application, for example, uses any directory you wish.


> **bjngchn said:**
> So probably most files are copied to /tmp at some point. Since files are not really deleted, any activity belonging to a user may remain on computer forever.

Yes /tmp files are deleted. Either by the application itself (most applications *do* clean up after themselves), or by reboot, or on some servers by a cron job.


Do you have an example of an application the stores user data in /tmp?
Looking at my /tmp, there are merely status files and lockfiles.  Oh look, I'm running PulseAudio and an SSH session...but you can't tell what music I am listening to; nor gather any clues to my ssh keys or connections from those files in /tmp.

---

### Post by bjngchn on 2014-08-23
Firefox stores opened documents in /tmp sometimes... Maybe firefox forced file to be opened by something which stores files in /tmp.  If all files go through /tmp, even if they are deleted, they can be recovered with a recovery tool. So obviously there is zero privacy between users, and there is a security risk.  What can happen: I create two users. One of them I use only myself. I let others use the other account. Then although I have a stong pw, most of my files can be stolen easily. What a shame. What is the point of having a pw, if all files by one user can be seen by other users.     Can users create alternative tmp folders under their home directory?  Can users prevent their data from being stored outside their home directory?

---

### Post by sotiris2 on 2014-08-23
If you really need to have users use different temp folders you 'll have to set the **TMPDIR** enviroment variable. Check [this]("https://help.ubuntu.com/community/EnvironmentVariables") out. Do note however that this is an advanced function and requires you to properly understand what you are doing. So I recommend you backup your system before you try to make the system work as you want.


EDIT: Deleted files usually are recovered by programs searching the actual disk for data. Those won't respect any kind of file permissions and are usually run via a live enviroment. If run on an installed system they 'd probably require root priviledge to access the disk device directly. That is if /tmp is an actual on disk filesystem. I think that is the case in ubuntu but it is also possible to have it as a ram filesystem (you should have a lot of ram and some experience)

---

