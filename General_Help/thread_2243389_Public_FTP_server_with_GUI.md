---
title: "Public FTP server with GUI"
date: 2014-09-08
forum: General Help
---

### Post by charlo66 on 2014-09-08
Hey Guys,


I bough a little devboard recently and I'm interested in making a public FTP server for me and some of my friends. The problem is that I don't want them to have to download an FTP client to upload files. I want them to be able to do it from their browser (dropbox like). I've look into options like Seafile and Owncloud but I'm looking at something really basic. Here are the thing I need:

- No authentication required 
- Able to lock certain folders to people (Read but not write)

Is there something that I could use that could achieve those kind of things ? In the options I check they seemed overloaded with features that I don't need. I want to keep the interface with minimal stuff (no share button for example).

Thanks !

---

### Post by nerdtron on 2014-09-08
> I want to keep the interface with minimal stuff

Actually setup for an SFTP server will a LOT be easier on your end, then just let the users download and install FileZilla to download files from your server.
Or even easier is to have a dropbox share folder and let them access it.

Problem with the setup you want is mainly security. You don't know who the public internet is and how the internet users around the world are capable of. If you just leave your ftp server open and let anyone download from a web browser, you can be attacked by anyone on the internet causing your bandwidth to fill up and you server to stop responding.

Just my opinion though as many newbies fail to understand some of these pointers.

---

### Post by Lars Noodén on 2014-09-08
You probably mean SFTP instead of [FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp), I hope?  FTP is not secure at all.  But, if your friends are using Linux then they already have file managers which support SFTP.  For example, in Nautilus, press ctrl-L and then enter the URL of the server: sftp://user@xx.yy.zz.aa/  That will then connect to the server and allow file transfers via the normal, graphical file manger just as if the remote files and directories were local.   Same goes for the others, not just Nautilus.  

If you really want a web upload / download service, there are at least a few of those, but they are more work to set up and keep up to date.

---

### Post by ian-weisser on 2014-09-08
Read-only in a web browser using Python2.7 and Python 3.x, and already included with the default install of Ubuntu:

```
cd /path/to/directory-to-serve
python -m SimpleHTTPServer    # Or python3 -m http.server
```

Not secure. Any web browser with access to your net can see it.
No uploading. Only users with a login and appropriate permission can add files.
As Nerdtron quite correctly pointed out, this method is a Bad Idea on the open internet or for more than limited use.
It is very handy to share a few files at a meeting.

As others have said, long-term file hosting requires security and maintenance.
Your solution will depend on the kind of security you want, and how you want to maintain it.
Happily, it's free. You can try lots of methods.

Personally, I use SSHFS and SCP. Secure, easy to use. Requires initial key setup, and maintenance when users change.

---

