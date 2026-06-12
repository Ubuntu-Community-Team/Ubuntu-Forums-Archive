---
title: "Trying to play files from Bookmarked folder, cannot see or cannot open"
date: 2013-10-18
forum: General Help
---

### Post by Micheal_Morrow on 2013-10-18
I am somewhat new at this.  Running 12.04 LTS.  Have read some in books and have been working with other computers and systems since 1966.  So not totally new, just new to Ubuntu and *nix.

I have read that the file system is one whole thing in *nix.  That does not seem to be true.  I have noticed it over and over.  Here are some examples of my problems with that not being true.

I am trying to use VLC and Pitivi and have too much trouble with both.  VLC will not open any file from a bookmarked folder.  Complains about not being able to open the MRL.  The hits I can find on this are all talking about streaming files from the internet.  I am trying to open a local file from a bookmarked (mounted) folder from a server running (probably) Debian under the covers running a Samba server.  It is a Synology NAS.

Pitivi does not even offer bookmarked folders in the Open File dialog.  It simply ignores them.  So why it is ignoring part of the "unified" file system?  Not supposed to happen as it is written and I read it.

In VLC, when I drag any file from a bookmarked Samba share to VLC, it cannot open it.  I get an error message but there is no log file being produced, even though I set it.  Nothing comes out.  There is no file.  Not sure why it does not like opening files from bookmarked (mounted) shares or writing the log file.  They should all appear local if, in fact, the entire file system all comes from /.

So what is the problem here?  How do I make VLC play movies?

Yes, there is Movie Player but it seems to have little to none of the features that VLC has.  It will play the files from the same bookmarked folders so this is not an access issue.  I have proper access to these folders.  But VLC refuses to play from them and Pitivi refuses to even show them.

And a third variation.  GIMP image editor does show the bookmarked folders in its File Open dialog so they are there for all to see and use but am having a lot of trouble making programs see them and use them.

Mike Morrow

---

