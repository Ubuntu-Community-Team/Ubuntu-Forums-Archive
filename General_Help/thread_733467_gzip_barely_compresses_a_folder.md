---
title: "gzip barely compresses a folder"
date: 2008-03-23
forum: General Help
---

### Post by Gerlads Mod on 2008-03-23
I tried to compress a directory with gzip that was 28.4 MB. with 74 files in it, into a tar.gz with the following command:
**gzip -r directory**
And it gave me a directory.tar.gz that was 27.8 MB.

27.9 Megs!
I thought it would *at least* go down to 10 MB. but it only compressed it down a half of a MB.


Is there I way I can get it to compress a little more?
Thanks.

---

### Post by LaRoza on 2008-03-23
Why did you expect it to go down?

That is a reasonable compression. Remember, some files are already compressed, and compressing further will not do anything. The archives have to be extractable :-)

(Many movie, image, and multimedia formats are already compressed)

---

### Post by Gerlads Mod on 2008-03-23
Oh. 
So thats actually good for tar compression?

What would be a good way to compress a large directory into a smaller compressed achive?

I was thinking RAR but...

---

### Post by LaRoza on 2008-03-23
> **Gerlads Mod said:**
> Oh. 
So thats actually good for tar compression?

What would be a good way to compress a large directory into a smaller compressed achive?

I was thinking RAR but...

tar is an archive format, it doesn't compress anything.

There is a limit to this. You are likely at that limit.

---

### Post by kevdog on 2008-03-23
bzip2 is a much more efficient (although slightly slower) compression engine.  I would try that!

---

### Post by accatagon on 2008-03-24
EDIT:I figure I should mention this at the beginning, so you actually see it: if you want something closer to RAR in performance, try LZMA. IT beats out gzip and bzip2 a lot as far as performance (with maximum compression) I got the bitmap I mention later in this post down to 420.9 KB with that, so you might actually see significant compression instead of basically nothing. It might also take forever. . . though I was using maximum compression. Just make sure you tar the file first.   

If you want an interesting comparison of compression algorithms, go to [http://tukaani.org/lzma/benchmarks]("http://tukaani.org/lzma/benchmarks"). Seriously though, if gzip isn't compressing much, then you probably don't have something that lends itself to compression. 

Generally speaking, if you have compressed media files such as jpegs or mp3 files, there isn't much you can do to compress them. 

Gzip is far more effective in the right circumstances. For example, the Linux kernel source gzipped tarball is 50 megs, while the uncompressed tarball is 250 megs. The thing to remember is that the linux source is mostly a bunch of text files, with the same constructs repeated over and over again (for loops, while loops, structs etc.) 

As far as I know, every lossless compression algorithm relies on repetition in the data so that it can list the item that is being repeated once, and then simply specify where that item gets repeated again. This is essentially what gzip does. Since gzip has no idea what kind of data it is compressing (unlike algorithms such as those for FLAC or for PNGs), it basically just looks for repetitions of strings in the code. 

This works great for anything written largely in a human-readable language, since human readable languages tend to contain a lot of oversized, frequently repeated strings (words). It works decently for multimedia too, except for the fact that most media are already compressed, and, as I mentioned before, most compression algorithms (including the lossy ones) try to annihilate repetition. Once there is no more repetition left, trying to compress it more won't do anything. 

Here's an example from my computer. I have a file called Screenshot.png. It is 615.9 KB. if I compress it using the maximum possible compression (gzip -N9 Screenshot.png), then it goes down in size to 611.8 KB. Not a huge difference, right? If I take the file and save it as a .bmp file, it ends up being 5.0 megabytes. Then, if I compress it, again using the maximum compression, I get a file of 688.5 KB. Clearly, this is a huge compression ratio. The reason the second compression ratio was so great was because it was compressing something that was very repetitive, whereas the first time I was compressing something that had had everything repetitive removed by the PNG compression algorithm. Also worth noting is that the PNG is smaller than the gzipped bitmap. This is because PNG was designed with images in mind, and thus (surprise!) does better when compressing images. 

So I would check what kinds of files you have in that folder before you go yelling at the gzip compression algorithms. If they're all jpegs or mp3s or some other compressed file format, then no compression algorithm, no matter how good (including rar), will be able to do much more. Remember that at some point you shouldn't be able to compress it any more, or else that would mean that you don't actually have any data. You can try bzip2, but it will only do a little better.

---

