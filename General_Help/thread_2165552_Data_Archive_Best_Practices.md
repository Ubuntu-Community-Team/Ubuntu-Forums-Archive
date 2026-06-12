---
title: "Data Archive Best Practices?"
date: 2013-08-05
forum: General Help
---

### Post by drmrgd on 2013-08-05
I've got a data server that we're running here, which has two main functions: collect and analyze data from a scientific instrument, and publish this data to a web based application where users can work with the data.  These data sets are rather large, and it necessary to archive these data for long term storage.  After some discussion we have decided the critical subset of the data that should be archived, paring it down to ~12GB per dataset (~ 2500 files ), and I have put together a script to create the tarball and move it to our cold storage drives.  As these data are quite critical, I want to make sure that I'm doing everything in the best way possible without, of course, spending days worth of compute time over analyzing and checking the data.

Where is the most likely place for data corruption to occur, during the tarball creation or while moving the archive to the network storage drive?  I feel like the tarball creation is more suspect, but it certainly would be way easier to md5sum the tarball before and after moving it rather than checking all of the files prior to and after creating the tarball.  Maybe it is necessary to do both, though, or is that overkill?

What other considerations should I take into account for this task?  Beyond just tarballing the data and moving it, should I consider some other check or method to be sure that the data is intact and able to be resurrected should the need arise?

---

### Post by Dave_L on 2013-08-05
> Where is the most likely place for data corruption to occur, during the tarball creation or while moving the archive to the network storage drive? I feel like the tarball creation is more suspect, but it certainly would be way easier to md5sum the tarball before and after moving it rather than checking all of the files prior to and after creating the tarball. Maybe it is necessary to do both, though, or is that overkill?

Personally, I would do both checks, especially since the data is critical, on the "better safe than sorry" philosophy.

Checking all the files is not necessarily that difficult. You can use a simple script to recursively compute the md5sums, or use a package such as "md5deep". An alternate tool could be the package "par2" (Parity Archive Volume Set, for checking and repair of files).

---

### Post by drmrgd on 2013-08-05
> **Dave_L said:**
> Personally, I would do both checks, especially since the data is critical, on the "better safe than sorry" philosophy.

Checking all the files is not necessarily that difficult. You can use a simple script to recursively compute the md5sums, or use a package such as "md5deep". An alternate tool could be the package "par2" (Parity Archive Volume Set, for checking and repair of files).

Yeah, from a panicky perspective, I feel like I need to do that.  But, again, with 12 - 16GB worth of data per dataset (of which there are currently ~135 runs and will be several per week coming), that's a lot of compute time, and I'm a little concerned about the resources required; a normal data analysis to generate the data does take up quite a bit of resources.  

As there are a couple other things I needed to do, I've written the archive script in Perl and have an unimplemented sub built in to handle this, though, and I would agree that it should be easy to go through the file list to generate the md5sums for each file.  But, the question is how to check after?  So, would the idea be to:

 
[LIST=1]
[*]Create a file with the md5sum values for each file in the archive
[*]Tarball the data and then get an md5sum for that tarball
[*]Untar the data in a temp location and check that the reconstituted files are not corrupt.
[*]Move the tarball to the cold storage drive and check the md5sum matches
[/LIST]

Or with md5deep (which I'll have to read up on a bit), is there a way to get the file MD5sum without having to untar the archive?

---

### Post by Cheesemill on 2013-08-05
If the data is important then I'd think about using ZFS as a filesystem, for both the archiving and the live data as it prevents many of the silent corruption issues that all other filesystems suffer from. If you cant trust your disks to correctly store the data you ask them to then you're not building on a solid foundation.

[http://en.wikipedia.org/wiki/ZFS#Data_integrity](http://en.wikipedia.org/wiki/ZFS#Data_integrity)

---

### Post by drmrgd on 2013-08-05
> **Cheesemill said:**
> If the data is important then I'd think about using ZFS as a filesystem, for both the archiving and the live data as it prevents many of the silent corruption issues that all other filesystems suffer from. If you cant trust your disks to correctly store the data you ask them to then you're not building on a solid foundation.

[http://en.wikipedia.org/wiki/ZFS#Data_integrity](http://en.wikipedia.org/wiki/ZFS#Data_integrity)

Very interesting.  I had no idea that existed.  Unfortunately, I'm not sure that's going to be an option for our setup, although I will have a look into it.  For sure, the final archive location is set as a CIFS storage drive, and I have no control over that.  This does give me some ideas, though, and definitely something to consider in the future if at all possible.  Thanks!

---

