---
title: "Adding comments to files (naive question)"
date: 2022-11-07
forum: General Help
---

### Post by bjngchn on 2022-11-07
Is there a way to attach some text to any files (comment, especially on mp3's) , which can 
easily be read with something like mouse-over? (using dolphin)

An ugly way would be:  create a directory, move the file to directory, and create a text file
inside that directory.

---

### Post by dragonfly41 on 2022-11-07
[https://www.canto.com/blog/mp3-metadata-editor/](https://www.canto.com/blog/mp3-metadata-editor/)

---

### Post by TheFu on 2022-11-08
For mp3 and ogg files, I use 'easytag' to control the metadata. When I ripped the CDs, which I redid over the summer for the first time since the 1990s, the tool used, abcde, automatically filled in the data through an open CDDB connection.  
```
NAME
       abcde  -  Grab  an  entire  CD and compress it to Ogg/Vorbis, MP3, FLAC,
       Ogg/Speex, AAC, WavPack, Monkey's Audio (ape),  MPP/MP+(Musepack),  True
       Audio (tta) and/or MP2 format.
```

There is a 'comment' tag that can support a paragraph of added stuff, if you like.  Only a few fields have data validation, so almost anything can be put into the metadata for each file or all files. It is up to you.  There are tools which will let you script changing/updating the metadata too.  
```

NAME
       id3v2  -   Adds/Modifies/Removes/Views  id3v2 tags, converts/lists id3v1
       tags

```
I don't really use file managers, but music players all read these tags and display them based on how you configure the player program on your system. I wouldn't be surprised if an addon to some file manager did this too.

For other media files, most also have use a container format that supports text comments or even adding unlimited sized text files.  For example, it is possible to use the MKV tools to create an mka audio file for an audio book, then place the entire html and txt versions of the book into the same mka file.  Images, videos, captions, subtitles, text can all be added.  I'd almost bet that random binary data could be added too, but I've never tested that, so I don't really know.  mkv and mka are amazing media containers.

For other file types, many support metadata. All the ODF MSFT-Office files do.  Over the decades, it has been funny some of the metadata put into documents that were released .... sometimes the full change history of marketing material has been included, so we can see were the "worlds best" was changed to "market leading" to "pretty great", then back to "market leading" for a well known software company.

So, there are lots of file formats, many support metadata, but then there are some that don't.  For those, most linux file systems support something called **xattrs**.  These are added fields kept with the file as it is modified and moved around on file systems that support xattrs.  The problem with these is when a file get moved to a file system that doesn't support xattrs, all that data is lost.  I've never used xattrs for any reason besides to play with them, but I could see using them as a way to add "tags" to files to help searches later.  [https://manpages.ubuntu.com/manpages/bionic/man7/xattr.7.html](https://manpages.ubuntu.com/manpages/bionic/man7/xattr.7.html) 
[https://www.linuxtoday.com/blog/linux-extended-file-attributes/](https://www.linuxtoday.com/blog/linux-extended-file-attributes/) has a tutorial and explanation of the 4 namespaces for xattrs.  Security ACLs are part of xattrs.  For tagging, I'd use the "user" namespace. This allows name/value pairs.
```
$ setfattr -n user.comment -v "this is a comment" test.txt
```
A bit cumbersome to manually add to 1 file, but with a little scripting, anything can be added to any file, provided you are the owner or have write permissions to the file.  xattrs doesn't bypass the expected Unix security mandates for access.

By default, xattrs are enabled for ext4 file systems.  I'd expect them to be supported on most native Linux file systems, [https://en.wikipedia.org/wiki/Extended_file_attributes#Linux](https://en.wikipedia.org/wiki/Extended_file_attributes#Linux) has a list and confirms my beliefs.  I was shocked to see that NTFS, OS/2 have support and FAT are all supported, just with limited lengths. Pretty impressive.

Not a naive question at all.

---

### Post by HermanAB on 2022-11-08
This one of the reasons why Document Management systems exist.

---

### Post by Paddy Landau on 2022-11-08
> **TheFu said:**
> … most linux file systems support something called **xattrs**.
I don't use xattrs for two reasons. The first is that the file manager doesn't show them; you have to know that they're there, and use the CLI (or create your own GUI script) to see the values.

The second is that not all commands support it. E.g., commands such as [FONT=courier new]rsync[/FONT] and [FONT=courier new]cp[/FONT] support xattrs only if you remember to add the relevant options, while [FONT=courier new]rdiff-backup[/FONT], [FONT=courier new]mv[/FONT] and BorgBackup all support them by default. So, you have to be aware of xattrs when dealing with files!

It's a great question from the OP, and I wish that xattrs were better supported at the user level.

---

### Post by TheFu on 2022-11-08
> **HermanAB said:**
> This one of the reasons why Document Management systems exist.

I worked in DMS for a few years.  These things are extremely expensive, need a full-time librarian and fairly complex to setup. Perhaps the expensive aspect was because I was working at enterprise scales with companies of 6000-230K employees.  The more bare-bones, but good solution I've ever seen was DocuShare from Xerox [https://www.xerox.com/en-us/services/enterprise-content-management/docushare](https://www.xerox.com/en-us/services/enterprise-content-management/docushare) .  It was only $25K per server with a 250 concurrent user license, but that was decades ago. Compared to the competition, it was amazing, lite, simple to understand and use.  Their full text search and metadata management was excellent too.

In the F/LOSS world, there are just a few tools that come close to being DMS. Alfresco is one and it is a hog, bloated, and begs for a custom front-end to be created.  The built-in webapp was horrendous last time I looked about a decade ago.  OTOH, Alfresco was created by some DMS experts in the enterprise, multi-million $$$ per installation Documentum team.  Alfresco and Documentum have superpowers compared to DocuShare or FileAID solutions.  It isn't what we see in the interface, it is all the stuff we don't see, under the covers, below the sheets, under the padding.   Changes are that your insurance and broker and bank use Documentum to manage their documentation. Ever seen bar codes on each page from a monthly statement?  

The most famous Alfresco install was for Obama's "whitehouse.gov" ... which was $25K for the commercial version of Alfresco, but $250K+ for "consultants" to customize the Drupal front-end.  Of course, the next guy ripped all that out and paid millions for a MSFT solution instead. What a waste.  This ugly front-end is by design, part of their business model to ensure customization is required to use the core product.  It keeps the companies getting paid, which is 1 F/LOSS model, I suppose.  Anyone can become an Alfresco customizer. Be good with Java, but the front-end can be nearly any web toolkit you like.  

At my company, I stood up a raw Alfresco DMS for all document management. Held training so people would understand how to access it (web or CIFS or NFS), how to manage project folders, tagging, automation (when image assets are added to a specifically named folder, they get "web optimized", workflows for publishing, sharing with clients, stuff like that.  I'd setup about 10 workflows that could be reused and hooked it into a centralized LDAP for single credential use across all our enterprise webapps and Posix logins.   The PMs just wouldn't stop manually versioning files by creating different named versions like:   "document-v1.pdf" and  "document-v1.1.pdf"   "document-v1.2.pdf"   "document-v1.3.pdf"   "document-v1.4.pdf"   "document-v1.5-release.pdf". The system would automatically retain X number of versions. Just keep the same name. "document.pdf" ... each document could be set to unlimited versions, but the default of 25 was reasonable for our project-based work.   For their access, I also setup CIFS shares, which alfresco supports natively.  So they quickly started using it like any Windows NTFS shared storage and completely ignored the directory structures automatically created for each project to allow access to the client for their "public" documents, while keeping internal documents private.  It was a huge thing and after about 2 yrs of trying, we had a mess.  Oddly, the C-level people all "got it" and embraced the methods.   I ended up ripping out Alfresco and gave them direct shared storage.  It was easier for the PMs, I suppose, even if it made compliance with some legal mandates for our regulated clients.  Of course, I used the native NFS support from Alfresco all this time on my Linux clients.

Guess my take-away is that a full DMS is overkill in a house hold situation.  Calling owncloud or nextcloud a DMS is a bit of a stretch, but people do: [https://medevel.com/dms-cloud-file-sharing-opensource/](https://medevel.com/dms-cloud-file-sharing-opensource/)  

For my LAN, I use normal, structured directories with files. Each file has appropriate metadata, if the format supports that (most do), and recoll is the search and indexing tool used to quickly find anything from emails to specific PDFs, music, videos, or full text search of almost any other files.  recoll is based on the Lucene Apache project search engine.  Recoll is like having google for your own storage.  It is hard to explain. Indexing takes time.  Updating the index is much faster for modified files. Queries are instant, even complex soundex queries.  Recoll is a desktop search tool. That's the short version.
[https://youtu.be/kMoN-2Ef6kE](https://youtu.be/kMoN-2Ef6kE) - Linux Mint/Ubuntu how-to (3 min)
[https://youtu.be/uPbDySi-p2w](https://youtu.be/uPbDySi-p2w) - Finding information in huge data sets - DEF CON 25 talk from a security standpoint - (11 min)
If you only watch 1, do the DEFCON one. It is funny, short, complete enough and covers the things 99% of end-users want/need to know. The last half is about saving webpages and having them added to a local storage area that recoll knows about, so not really the core function of recoll.

BTW, recoll will index xattrs making those tags searchable too, just like any other document header metadata.  I use recoll perhaps 25 times a day.  More than Google/DDG/whatever.

I'd love to know about capable, F/LOSS, DMS solutions that aren't as ugly.  DocuShare was very light, fully indexed, and fast.

---

