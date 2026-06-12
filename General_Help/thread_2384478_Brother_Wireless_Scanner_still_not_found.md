---
title: "Brother Wireless Scanner still not found"
date: 2018-02-07
forum: General Help
---

### Post by DAB4970 on 2018-02-07
I've copied 3 files from */usr/lib64* and */usr/lib64/sane* to */usr/lib*.  I am not able to create the directory */usr/lib/sane* for the 3 files in the *lib64/sane* directory, even with using *sudo*.  System replies with *File Already Exists*.  I want to create the directory to copy 3 files into.  Is it because the file exists that I can't create a directory with the same name?

I still am having the issue of *SCANNER NOT FOUND*.  If I'm not mistaken, 16.04's SANE was finding the scanner at some point.  Now it's not.  Has there been any system file changes to make the scanner not found this time?  I'm kinda getting irritated with this issue.

Any help would be greatly appreciated.  Thanks.

Update:  2/8/18
I used admin priveledges to delete the file and create the directory.  Then I was able to copy the 3 files from */usr/lib64/sane* to */usr/lib/sane*.  And walla, scanner is found.  Brother email support hasn't replied to my request about the file named *sane* if it was ok to delete it.  So I just did it anyway and I now have access to the scanner via wifi.

Update: 11/21/18
I also installed libsane-extras, because with Ubuntu 18.04, copying the files noted in this post, other posts and on Brother's support site, my scanner wasn't found until the extra-backends was installed.  So that helped.

---

