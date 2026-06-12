---
title: "Problem accessing samba share from Windows"
date: 2008-05-17
forum: General Help
---

### Post by 9x0 on 2008-05-17
Hi,

I have encountered a really strange problem with my Samba share on Hoary. I can't access it from Windows using the path \\server\share. After trying to do this, Windows correctly prompts me for password, but after entering the credentials, an error message appears saying something like "\\server\share is not accessible. You might not have permissions to access this network resource...".

However, when I try mounting the share as a network drive, it works (note that I am using the same share name and the same credentials). I was using Gutsy before Hoary and both access methods did work, but after upgrading I am only able to mount it.

Was there a substantial change in the Samba versions in Gutsy and Hoary that could influence this behavior? Any help appreciated :).

---

