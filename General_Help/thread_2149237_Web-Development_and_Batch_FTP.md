---
title: "Web-Development and Batch FTP"
date: 2013-05-28
forum: General Help
---

### Post by asearle on 2013-05-28
Hi Everyone,

I am working on a set of HTML files for a web-site that I am building and currently use Filezilla and/or FireFTP to upload these to the web-server.  That works fine.

The HTML-Editor that I am using is "BlueFish" which is a good tool and I notice that it has the option (under the File Menu) to "Upload" and "Download" and so I was hoping that I could set it up so that I could upload these files to the web-server with the click of a button (as I edit them).  But this option did not accept FTP-Syntax and seemed to demand a standard, local directory.

So my question here is ...
a.) Whether anyone can help me with the uploading syntax/functionality of BlueFish.
... or (even better) ...
b.) Somebody knows of an FTP tool or an FTP script that would copy all my files up to the server at the click of a button.

I do hope that someone has a tip or a snippet of script-code that might help me.

Many thanks,
Alan Searle

---

### Post by HermanAB on 2013-05-28
Two words:
wget
wput

---

### Post by Lars Noodén on 2013-05-28
I'm not even a novice with Bluefish but looking at it a little it seems that it finds the remote server only when fed a URI.  That looks like it precludes more complicate methods like batch mode.

On a regular SFTP client, you have [batch mode (-b)](http://manpages.ubuntu.com/manpages/raring/en/man1/sftp.1.html).  Though if I understand correctly the [prerequisite for batch mode is using key-based authentication](https://en.wikibooks.org/wiki/OpenSSH/Cookbook/SFTP#Automated_SFTP).  Anyway, once you have that, you can specify a file containing your sftp commands (put, get, and so on) and launch sftp pointed at the batch file.

---

### Post by asearle on 2013-06-10
Hallo Lars,
Many thanks:  It looks like sftp is exactly what I need.
I will post feedback once I have got things working.
Regards and many thanks,
Alan

---

