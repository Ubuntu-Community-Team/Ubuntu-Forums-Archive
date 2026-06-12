---
title: "Help me patch davfs2 so it will work with Cubby.com"
date: 2013-03-30
forum: General Help
---

### Post by cr45h on 2013-03-30
Hi,

I'm very new to Ubuntu/Linux and am having a hard time trying to get my Cubby.com account working properly through WebDav (davfs2). Some more info:

I found a guide that helped me set up WebDav (through davfs2) and set up mount points in fstab. I set this up for my Box.com account and it worked PERFECTLY!. Then, I tried to do the same for my Cubby.com account. I can get the account mounted properly but the problem is that folder names that contain spaces are not displayed. I did a lot of research and might have found a solution but I'm stuck trying to implement it.

What I've already done:
- Checked multiple webdav servers. All servers other than Cubby.com work fine in davfs2. Box.com mounts and displays folder names with and without spaces. No problem.
- Checked the Nautilus ("Files") webdav implementation. This loads up Cubby just fine and displays all folders. But I cannot "mount" through Nautilus. So I have to find a way to use davfs2.
- Updated davfs2. Removed the version available through apt-get (1.4.6) and installed 1.4.7-2. This is supposed to be a bug fix version but it did not help with this particular issue.
- Found possible solution here:  [http://savannah.nongnu.org/support/?107114](http://savannah.nongnu.org/support/?107114) (this is for the sharepoint webdav implementation but it is the exact same issue I am having with Cubby.com)
  -- Downloaded Patch file: [http://savannah.nongnu.org/support/download.php?file_id=23697](http://savannah.nongnu.org/support/download.php?file_id=23697)
  -- Found possible way to apply patch here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=311286](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=311286) (note that this was a patch for a different problem but I got the command from here)
 - So I should need to apply the patch by using the command "[COLOR=#000000]patch -p1 < [/COLOR]neon-fix-davfs-spaces-issue.patch"

What I can't figure out:
 - Where do I go to apply the patch?
  -- I've read all the man pages I could think of but this hasn't been useful.
 - I guess I don't understand the Ubuntu directory structure. Where is the file I need to patch? Also, can I apply this to the binary file or do I need to download source, patch, re-compile, and re-install. I really don't have a clue how to do any of this so ANY help will be greatly appreciated!

[Running 13.04 nightly, x64 on a Dell XPS 13]

Thanks!
-cr45h

---

### Post by algonquinn on 2014-02-09
Hi cr45h, I was wondering if you ever got this working. I am experiencing similar issues to you (running 13.10, davfs2 1.4.6).

---

### Post by oldos2er on 2014-02-09
cr45h hasn't visited the forum since April 2013; you're much more likely to get help if you create a new thread rather than posting in someone else's old one.

---

### Post by algonquinn on 2014-02-09
Done and done. Thanks for the tip - new thread posted here.

[http://ubuntuforums.org/showthread.php?t=2204610&p=12924484#post12924484](http://ubuntuforums.org/showthread.php?t=2204610&p=12924484#post12924484)

---

