---
title: "Subversion: Commit as a different user?"
date: 2008-04-04
forum: General Help
---

### Post by HautingLu on 2008-04-04
I have an interesting situation with Subversion I'm trying to figure, but I'm not 100% sure this is even possible.....

User1 checks out some files from a remote server via ssh and creates a workspace. User1 has the same login on the remote server.

User2, who has access to User1's workspace, edits some files and wants to commit back to the server. User2 has the same login on the remote server.

**Is it possible to User2 to commit as User2 so that the log history correctly shows that User2 made the commit?**


I currently have several WS's I'm trying to test this on. I edited User2's subversion config file to read: 

*ssh = $SVN_SSH ssh -l User2*

But when I go commit, it still asks for User1's password.


Thanks.

---

