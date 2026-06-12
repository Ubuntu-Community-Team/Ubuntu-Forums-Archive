---
title: "Problems recovering Bzip2 files"
date: 2016-09-12
forum: General Help
---

### Post by guilherme9 on 2016-09-12
Long story short: I deleted bzip2 files from a ntfs partition and lost the $DATA records, so I had to manually carve it using Scalpel, using different footers at a time (once the footer of a bzip2 file is bit aligned, and not byte aligned, so it was kind of hard to work around).

But I finally managed to carve out the files I wanted, they're about the size they were, but bzip2 says they're corrupted. So i used bzip2recover to take out the blocks from them.

Each one of them were an big tarball before compressing, a single file. So i expected to stitch all of the files back in a single file after bzip2recover did its work (and after decompressing the blocks, of course).

But, there's a problem: While most of the recovered blocks are 900kb, as expected, about 40 of them are bigger than that, and are corrupt themselves too. 

What should I do now?

Do ignore them and stitch the rest?

Do I fill the gap with a 900kb file full of zeros?

One of the things i thought about is:

Ex.: I have this 3 blocks:

rec1.bz2 -> 900kb
rec2.bz2 -> Corrupt
rec3.bz2 -> 900kb

So I decompress the non-corrupt ones and move the corrupt to another folder:

rec1.bz2 -> rec1.tar
rec2.bz2 -> move to /folder/
rec3.bz2 -> rec3.tar

And so, in that folder, i use bzip2recover to extract the blocks from the corrupt one, then I decompress them, and stitch them into rec2.tar.

After doing that, i move that rec2.tar back into the previous folder:

rec1.tar
rec2.tar <- Stitched back from the decompressed recovered blocks
rec3.tar

And then, finally, I stitch those 3 files into the final tarball. 

What do you think?

Thanks for your help!

---

