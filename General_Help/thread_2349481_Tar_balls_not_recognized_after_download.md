---
title: "Tar balls not recognized after download"
date: 2017-01-15
forum: General Help
---

### Post by whitshade on 2017-01-15
I have prepared what I believe to be a cute Window Maker theme, featuring Amanda the Panda, the Window Maker mascot.  Anyway, I compress the file into a tarball and upload it to my site (christopherwhittum.com).  When I download the file via the link I've set up, it downloads without incident.  However, when I attempt to extract the rarball (using tar -xzvf Amanda_Theme.themed.tar.gz), I received this warning: 

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now

All I can think is that maybe there's some protocol for uploading tarballs that I'm unaware of.  Any suggestions or ideas are greatly appreciated.

---

### Post by TheFu on 2017-01-15
How is it downloaded? FTP?  binary mode?  Plain FTP should have been killed off in the mid-90s.

Extensions don't matter to Linux. Some GUI tools care about extensions. Many use the file's magic number as known by 'file' to do the expected thing.

---

### Post by efflandt on 2017-01-15
Are you using scp/sftp or ftp to upload it? Is **md5sum** the same before uploading and after downloading? If so does the original file properly extract before uploading?

---

### Post by whitshade on 2017-01-16
Thanks for the responses.  I've narrowed the problem down. The files  extract just fine prior to uploading.  The files extract while on the  Web server.  The files extract when downloaded via FileZilla.  For some  reason, they just don't download properly using a Web browser.  For  reference, FileZilla is set to "Auto" for transfer type.  Sorry I didn't  provide more info initially.  I was, and still am, a bit flustered by  this.  Again, suggestions are welcome.  Thanks.

---

### Post by whitshade on 2017-01-16
Interesting to note that when I attempted to download one of the files using Chromium, Chromium's Downloads lists the file as Failed -No file.  The files are there, but not downloading or not downloading properly.

---

### Post by TheFu on 2017-01-16
1 more idea - try renaming the file to .tgz. Doubt it will help, but never know what browsers think.  

For downloading large files, I tend to use either wget or sftp. Haven't had the plain FTP 'binary' issue in a very long time - over a decade at least. Is plain FTP running on the server and available at the same location?

---

### Post by whitshade on 2017-01-17
Thanks for the suggestion, TheFu.  You're right about  browser (a  perfect example of finicky software).  Plain FTP is running on the  server and at the location.  And you're right about wget and sftp.   That's the route to go.  I'll give your suggestions a try and get back  to you.  Thanks again.

---

### Post by whitshade on 2017-01-17
I just tried saving the tar ball as a .tgz file, The Fu, with no luck. However, wget did retrieve an extractable file, so I'll stick with that.  The only people who would download these files are Linux users, who will probably use sftp or wget to download them anyway.  This has been an interesting experience (for lack of a better term).  I think that I just got too focused on doing it one way and closed my mind to alternatives.  Thanks for the suggestions (especially mentioning wget, TheFu  That helped me resolve this issue).

---

### Post by TheFu on 2017-01-17
If these are anonymous users, then sftp won't work. wget will, but so should save-as from any web browser.  I fear it could just be YOUR SPECIFIC config in the browser.  I'd test by making a new userid, logout, login under the new userid, open the same browser, and grab the file. If it saves correctly, you've just determined that something is screwy with your browser config.

Also, try a different browser. Does that work?

For plain FTP (which really shouldn't be enabled anymore, anywhere), just make certain that binary mode is used, not ASCII mode. I would purge the FTP server myself, but I think plain FTP should never be used anywhere for a number of reasons. Google "stop using ftp" for reasons why.

---

