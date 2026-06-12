---
title: "Help with FSLint"
date: 2016-08-17
forum: General Help
---

### Post by DWRZ on 2016-08-17
Hello,

I am using FSLint to clean up a mess left over after attempting to use insync (Google Drive alternative). Insync left me with tens of thousands of duplicate files, which I am trying to delete.

Basically, this is what I am trying to do:

If a file is in Folder A and the duplicate is in any other folder, then delete the file in Folder A.

However, if both of the duplicates are in Folder A, then don't delete either file.

For example, if the file test.txt is located in Folder A and Folder B, then delete test.txt in Folder A, but keep it in Folder B.

If the file test.txt and the file text-2.txt are both located in Folder A, then keep both files.

FSLint says it can accept regular expressions, and it can also output the list of duplicates to a file.

I am slowly teaching myself the command line and regular expressions, but I think this is a bit beyond me at the moment (and I'm not sure if it's even possible to use regular expressions here).

I am guessing that the easiest way would be to export the FSLint duplicates file, run a script on it and determine the files to be deleted, then create another file to feed into rm.

I'm really not sure though. Any help in the meantime would be much appreciated!

---

