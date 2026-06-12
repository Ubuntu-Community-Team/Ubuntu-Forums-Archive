---
title: "Ftp Filezilla"
date: 2007-11-06
forum: General Help
---

### Post by Elena678 on 2007-11-06
hello, i need to find a good ftp client that is easy to use, i tried filezilla but when i try to connect is tels me it has no HTTP-protocol. can i fix this???

greetings

---

### Post by x1a4 on 2007-11-06
To access http servers use an http client like Firefox or Epiphany.  

For ftp, Have you tried gFTP?  It's a very good ftp client but many people complain that the UI isn't very user friendly (I disagree).
[ftpcube]("http://ftpcube.sourceforge.net/") is another good client but it's not in the repositories and requires you to have [wxPython]("http://www.wxpython.org/") installed which also is not in the repositories.  

Or use a two-pane file manager that supports ftp like FileRunner.  

On the command line your best bet is probably ncftp.

---

### Post by michaelzap on 2007-11-06
The best FTP app that I've found for Ubuntu is actually the FireFTP add-on for Firefox. I've tried a **LOT** of FTP clients, but I haven't really been happy with any of them. I'm generally happy with FireFTP, but I'd prefer a stand-alone program.

---

### Post by RTrev on 2007-11-06
> **Elena678 said:**
> hello, i need to find a good ftp client that is easy to use, i tried filezilla but when i try to connect is tels me it has no HTTP-protocol. can i fix this???

greetings

I second the vote for gFTP.  Nothing else comes close.  You can edit files right on the server, and do all kinds of things that are handy.  I used to use the FireFTP Firefox extension until an old veteran showed me the error of my ways.  :)

---

### Post by michaelzap on 2007-11-06
> **RTrev said:**
> I second the vote for gFTP.  Nothing else comes close.  You can edit files right on the server, and do all kinds of things that are handy.  I used to use the FireFTP Firefox extension until an old veteran showed me the error of my ways.  :)

Actually, you can edit files on the server using FireFTP as well. And it also has some features that gFTP does not. For example, it auto-detects ascii/binary file types, you can have the local and remote directories stay in sync when you navigate either, and the site manager is much better, too.

---

### Post by RTrev on 2007-11-06
> **michaelzap said:**
> Actually, you can edit files on the server using FireFTP as well. And it also has some features that gFTP does not. For example, it auto-detects ascii/binary file types, you can have the local and remote directories stay in sync when you navigate either, and the site manager is much better, too.

Thanks.. maybe it's changed since I last tried it?  I'll look at it again.  It's nice that it's available on any platform that can run Firefox.

Bob

---

### Post by HermanAB on 2007-11-06
You should try konqueror (in the kde-base package).  It can do any protocol imaginable including ftp, fish, ldap, smb and a zoo of others.  It can even browse the web too, though I never use it for that...

---

### Post by Elena678 on 2007-11-13
i tryed to put some zip files on a server with konqueror, but when i try to download them again i have FORBIDDEN on my page, please help me ASAP

greetings

---

### Post by rpascual on 2007-11-27
In gFTP, is there a way to instruct it to skip existing files so that it does not have to ask? When you're resuming a failed upload, you just want to skip thru the files that are already there. It takes a while for gFTP to produce a list of exiting files in a huge directory - so i'm looking for a way to skip this dialogue. TIA

---

### Post by morningboat on 2007-11-27
You can try [CrossFTP]("http://www.gnomefiles.org/app.php/CrossFTP_Client") for your task. It has the overwrite rules settings and filters to skip certain files. Other choices are FilieZilla and FireFTP, while I prefer CrossFTP's functionality and reliable.

---

### Post by RTrev on 2007-11-27
> **rpascual said:**
> In gFTP, is there a way to instruct it to skip existing files so that it does not have to ask? When you're resuming a failed upload, you just want to skip thru the files that are already there. It takes a while for gFTP to produce a list of exiting files in a huge directory - so i'm looking for a way to skip this dialogue. TIA

The closest I've been able to find is in the gftprc file there's an option for overwrite_default, which you can set to either 0 or 1.  I believe you still have to click okay, but the proper choice will already be selected for you when you do.

Bob

---

