---
title: "Creating Samba share for MS Access"
date: 2014-09-10
forum: General Help
---

### Post by nathanb2 on 2014-09-10
I work for a hospital and we would like to use an Ubuntu 12 server to collect form responses (csv format) that will be referenced by a MS Access file on a Windows 2008 R2 Server to do reporting.

I [created a Samba share]("https://help.ubuntu.com/community/How%20to%20Create%20a%20Network%20Share%20Via%20Samba%20Via%20CLI%20%28Command-line%20interface/Linux%20Terminal%29%20-%20Uncomplicated,%20Simple%20and%20Brief%20Way!") on Ubuntu but I'm not sure how to configure the Windows share / mapping to make that work. I tried accessing the file directly via a hyperlink but MS Access can't read csv files via URL.

Bonus: It would be extra helpful if I could limit access to the share to only particular Windows domain users. For security, I'd also like to limit access to the share to be internal to our hospital (maybe it is by default even if listed public when behind a firewall; I'm new to Ubuntu and Samba.)

Any suggestions?

---

### Post by lukeiamyourfather on 2014-09-10
See this if you haven't already. Samba can be configured to use credentials from a Windows domain.

[https://help.ubuntu.com/12.04/serverguide/windows-networking.html](https://help.ubuntu.com/12.04/serverguide/windows-networking.html)

---

### Post by SeijiSensei on 2014-09-11
Let me ask a couple of questions.  There may be a better approach entirely.

How are you collecting the form responses on the Ubuntu server?  Did you write a PHP application so the data is entered via a web form?  If so, I suggest rather than compiling them to .csv files, you store them in PostgreSQL or MySQL on the Ubuntu server, then use ODBC with Access to connect to the SQL data from Access.  Access can reference remote tables if you install the appropriate ODBC driver for the SQL database you choose.  I use PostgreSQL myself, but both programs make their corresponding ODBC drivers available freely.

Any PHI here?  If so, you might need to consider encrypting the records.  I built a web-based appointments system for patients at a local community health center.  I had to write routines to encrypt all the patient data with AES256 before storing them in the database to comply with HIPAA requirements.

---

### Post by nathanb2 on 2014-09-11
SeijiSensei, Thanks for your helpful comments.

I'm using  CoffeeCup Web Form builder, which only gives us a csv/email option. It's  quick and simple and anyone can create the forms that way.

As  for PHI, we don't think so presently but there may come a time when some  confidential info appears. It's behind our main firewall on an intranet  virtual server, but encryption would still be a question if we used  PHI, though addressable. Any easy ways to do this? I could maybe move  the csv file systematically from the folder and append it to our Windows  server file via coreftp and powershell, which is another possibility in  place of sharing the folder...

Wait! Web form builder does  indeed have a MySQL database option... but that means I would need to  figure out how to set one up on Ubuntu and enable access from Windows to  that... I'm getting a headache!

---

### Post by SeijiSensei on 2014-09-11
```
sudo apt-get install mysql-server
``` for starters.  Maybe the CoffeCup app will build the tables for you or guide you through the process.  There are lots of guides on the Internet for MySQL.

[https://help.ubuntu.com/12.04/serverguide/mysql.html](https://help.ubuntu.com/12.04/serverguide/mysql.html)  - Setting up and tuning the server; I doubt you need to worry about tuning.

[http://dev.mysql.com/doc/refman/5.5/en/](http://dev.mysql.com/doc/refman/5.5/en/) - the main documentation for version 5.5 which ships with Ubuntu 12.04

[http://blogs.sakienvirotech.com/index.php/random/2011/09/05/mysql-101-creating-your-first](http://blogs.sakienvirotech.com/index.php/random/2011/09/05/mysql-101-creating-your-first) - a nice overview for creating your first database

As for protecting the data, I'd probably create a task in Access that reads the remote data into a local table, then deletes it from MySQL.  You probably want to do the same if you use CSV files.

Another option to consider is [mounting a Windows directory on Ubuntu]("https://wiki.ubuntu.com/MountWindowsSharesPermanently") and running a cron job on the Ubuntu server to copy the CSV files to a place where the machine running Access can see them.  So rather than exporting the directory from Ubuntu to Windows, you'd do the reverse. The cron job could delete the file from the Ubuntu server when the copy is complete.

---

### Post by nathanb2 on 2014-09-16
We actually already use MySQL for a Moodle install... But how would I link up to MySQL in Ubuntu from Access on a Windows server when Moodle is on the Ubuntu server?

---

