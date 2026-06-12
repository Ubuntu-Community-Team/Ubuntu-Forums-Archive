---
title: "how to tell tar to skip .mp3?"
date: 2008-07-04
forum: General Help
---

### Post by logos34 on 2008-07-04
I run this command to make a gzipped tarball of my /home:

$ sudo tar cvzfp /media/hda3/homebackup_2008july4.tar.gz --exclude=/home/logos/.local/share/Trash --exclude=/home/logos/.thumbnails /home/logos

Problem is I have audio downloads (RealAudio, .mp3, some .ogg) in there, separate from my music folder (which is backed up/archived separately).  How do you tell it to NOT gzip the (already) compressed audio files, but still include them in the tarball?

---

### Post by ghostdog74 on 2008-07-05
check the tar man page. there should have options to exclude files.

---

### Post by logos34 on 2008-07-05
but I want the audio files INCLUDED in the tarball, I just don't want it to compress them (again).  And if I'm not mistaken, it gzips the files as it's building the tarball, not afterward.  I've checked the tar and gzip man pages already.

I'll probably end up just excluding the audio folder and making it into a separate tarball w/o gzip

---

### Post by ghostdog74 on 2008-07-05
tar won't compress them again. It only zip up the entire tarball, not individual files.

---

### Post by logos34 on 2008-07-05
> **ghostdog74 said:**
> tar won't compress them again. It only zip up the entire tarball, not individual files.

right, tar just grabs everything and rolls them into an archive, but I'm running it with the gzip option (tar c**z**vfp), so doesn't gzip compress everything in the tarball, including lossy audio files if present? How to tell it to include the audio files in the tarball but not to run the gzip part on those files?  I'm just assuming by watching my cpu activity that gzip works on the fly as the files are added to the archive rather than at the end.  Or does gzip only run at the end after the whole archive has been formed?

I guess it's not a big deal as I can do it separately as I said, but I curious

---

### Post by ghostdog74 on 2008-07-05
why don't you test it out.
use tar tvf and take a look inside your tar ball. are all the ordinary files in .gz format??

---

### Post by logos34 on 2008-07-05
ok, I see.  So then gzip compresses the entire tarball, not each individual file as it goes into the archive.
But it's confusing because it looks just like gzip is working on each file on the fly.

---

### Post by ghostdog74 on 2008-07-05
nothing confusing. just have to read carefully the man page.
> 

       -z, --gzip, --ungzip
              filter the archive through gzip




"filter the archive". It doesn't say otherwise.

---

### Post by logos34 on 2008-07-05
I saw that on the man page...sorry if I'm not overwhelmed by the information conveyed by that one line.

Here's the explanation I was looking for (FYI, [this is the link]("http://info2html.sourceforge.net/cgi-bin/info2html-demo/info2html?%28tar.info.gz%29gzip"))
> 
 `--gzip'
 `--ungzip'
      Filter the archive through `gzip'.
 
    Some format parameters must be taken into consideration when
 modifying an archive.  Compressed archives cannot be modified.
 
    You can use `--gzip' and `--gunzip' on physical devices (tape
 drives, etc.) and remote files as well as on normal files; data to or
 from such devices or remote files is reblocked by another copy of the
 `tar' program to enforce the specified (or default) record size.  The
 default compression parameters are used; if you need to override them,
 avoid the `--gzip' (`--gunzip', `--ungzip', `-z') option and run `gzip'
 explicitly.  (Or set the `GZIP' environment variable.)
 
    The `--gzip' (`--gunzip', `--ungzip', `-z') option does not work
 with the `--multi-volume' (`-M') option, or with the `--update' (`-u'),
 `--append' (`-r'), `--concatenate' (`--catenate', `-A'), or `--delete'
 operations.
 
    It is not exact to say that GNU `tar' is to work in concert with
 `gzip' in a way similar to `zip', say.  Surely, it is possible that
 `tar' and `gzip' be done with a single call, like in:
 
      $ tar cfz archive.tar.gz subdir
 
 to save all of `subdir' into a `gzip''ed archive.  Later you can do:
 
      $ tar xfz archive.tar.gz
 
 to explode and unpack.
 
    The difference is that the whole archive is compressed.  With `zip',
 archive members are archived individually.  `tar''s method yields
 better compression.  On the other hand, one can view the contents of a
 `zip' archive without having to decompress it.  As for the `tar' and
 `gzip' tandem, you need to decompress the archive to see its contents.
 However, this may be done without needing disk space, by using pipes
 internally:
 
      $ tar tfz archive.tar.gz
 
    About corrupted compressed archives: `gzip''ed files have no
 redundancy, for maximum compression.  The adaptive nature of the
 compression scheme means that the compression tables are implicitly
 spread all over the archive.  If you lose a few blocks, the dynamic
 construction of the compression tables becomes unsynchronized, and there
 is little chance that you could recover later in the archive.
 
    There are pending suggestions for having a per-volume or per-file
 compression in GNU `tar'.  This would allow for viewing the contents
 without decompression, and for resynchronizing decompression at every
 volume or file, in case of corrupted archives.  Doing so, we might lose
 some compressibility.  But this would have make recovering easier.  So,
 there are pros and cons.  We'll see!

---

