---
title: "Issues with Filezilla and FTP command line... ?"
date: 2020-05-29
forum: General Help
---

### Post by dbee on 2020-05-29
I can't seem to open a persistent connection with FTP cli in emacs. The connection keeps timing out making it useless.

When i use Filezilla UI it keeps missing whole folders in the download path.

What's the story with that ? For instance, it downloads the whole directory but misses wp-content and wp-admin. I have to re-queue them and then they seem to download fine.

Can anyone solve either or both of these issues pls ?

Who uses bash to ftp to a remote shared server that doesn't support SSH but uses FTP over TLS ... ?

Thanks,

---

### Post by dbee on 2020-05-29
I could have sworn years ago there was an emacs script that would ping the FTP server regularly to keep the connection alive.

Maybe a LISP script perhaps ? Can't find anything suitable on Google ...

---

### Post by sdsurfer on 2020-05-29
I have had nightmares with FileZilla in the Windows days, but seems to be working fine in Ubuntu.

A couple things to suggest: first is that for whatever reason FileZilla is losing the connection during the times that directories go missing. This could be due to a connection issue, by that I mean connection speed, a timeout error, or possibly your provider is metering out the data transfers? The last is a wild guess, don't blame the provider without checking it out. :-D

A good place to look is that log window at the bottom of the FileZilla screen. scroll through to the point at which it skips files or directories. Any errors there?

Also the way FileZilla queues transfers causes some files to transfer before others, it's not exactly in sequential order at times. I don't know why, but I have seen it. Make sure the queues are complete before thinking it's skipped something.

---

### Post by dbee on 2020-06-03
Haven't noticed any connection issues in other applications. Only filezilla.

Besides isn't that what the 'Failed Transfers' or whatever tab is all about ? To flag missing folders ?

I requeue all the failed transfer files - but filezilla still misses out on whole directories in WP. eg. wp-admin, wp-content etc...

---

