---
title: "installed and setup proftpd and gproftpd.. having issues.. please help"
date: 2007-05-06
forum: General Help
---

### Post by billdotson on 2007-05-06
I have installed and setup proftpd and gproftpd.  I can login to the server and upload files (with an FTP client) and afaik can also download using an FTP client.  Although if I sign in through a web browser (I am assuming you cannot upload through a browser so that is not an issue) and I click on the link to a file on the server it says 500/name_of_file is not a directory or something very similar.  If I do right-click save link target as I get a really small file of 1KB.  The file is ~340KB.  How do I set it up so that I can download from a browser (given that I have logged into the server) ?  I gave the user write access..

---

### Post by asipi on 2007-05-07
what url you use in the browser? user&pw included? if not, guest account in ftpd config allowed?

---

### Post by billdotson on 2007-05-09
I fixed it.  The account I was trying to use did not have the RETR ftp command as allowed

---

