---
title: "cat folderlist.txt | xargs mkdir dealing with spaces and special chars"
date: 2014-02-05
forum: General Help
---

### Post by norjms on 2014-02-05
Hello all,
    I made a directory list using ls > folderlist.txt and I thought I would be able to just cat folderlist.txt | xargs mkdir to recreate the structure. However I ran into problems. Some of the folders have spaces and special chars that need escaped through. Anyone have suggestions on how to fix the issue?

Example

John
Jim's Taxes (2013)
Jake Smith
ect
I have several hundred folders to recreate but, I still have access to the original structure to recreate the duplicate folder structure ie I just moved the files to a new directory and want to recreate the directory tree.

---

### Post by norjms on 2014-02-05
Sorry for the post seems as soon as I posted I found a solution
 find . -type d -exec mkdir ../targetdir/{} \;

---

### Post by Lars Noodén on 2014-02-05
Does that handle the names with spaces ok?  I would think that you would need quotes "{}"

---

