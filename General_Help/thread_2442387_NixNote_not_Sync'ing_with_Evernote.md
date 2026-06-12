---
title: "NixNote not Sync'ing with Evernote"
date: 2020-05-03
forum: General Help
---

### Post by webmanoffesto on 2020-05-03
I've been using Evernote (web interface) and occasionally syncing it to NixNote, I then backup Nixnote2 by "exporting database".
Recently NixNote2 stopped sync'ing with Evernote.
NixNote2 Message Log says
[FONT=courier new]Error:  INFO 2020-05-03 01:00:04.551 ( nixnote.cpp @ 1900 ) "Internal Error: Error downloading [https://www.evernote.com/edam/user](https://www.evernote.com/edam/user) - server replied: OK"
[/FONT]But that doesn't give me any helpful information.


I uninstalled and reinstalled Nixnote2. I'm still getting the error message
[FONT=courier new]sudo add-apt-repository ppa:nixnote/nixnote2-stable -y
sudo apt update
sudo apt install nixnote2 -y
[/FONT]
I can see that Nixnote is an updated version, Help/About says Version: 202003110020~2.1.5~ubuntu16.04.1

How can I resolve this sync problem?

Then I got this, which includes some more details, but is repetitive. 
This could be a "corrupted database" but then what do I do about that?

[FONT=courier new]ERROR 2020-05-03 10:55:49.372 ( sql/tagtable.cpp @ 395 ) Unknown Tag record key: 1004 
ERROR 2020-05-03 10:55:49.372 ( sql/tagtable.cpp @ 395 ) Unknown Tag record key: 1004 
ERROR 2020-05-03 10:55:49.373 ( sql/tagtable.cpp @ 395 ) Unknown Tag record key: 1004 
 INFO 2020-05-03 10:55:51.965 ( nixnote.cpp @ 1900 ) "Internal Error: Error downloading [https://www.evernote.com/edam/user](https://www.evernote.com/edam/user) - server replied: OK" 
ERROR 2020-05-03 10:55:52.219 ( sql/tagtable.cpp @ 395 ) Unknown Tag record key: 1004 
ERROR 2020-05-03 10:55:52.229 ( sql/tagtable.cpp @ 395 ) Unknown Tag record key: 1004 
ERROR 2020-05-03 10:55:52.229 ( sql/tagtable.cpp @ 395 ) Unknown Tag record key: 1004[/FONT]

---

### Post by mashaku on 2020-05-04
I am getting the same error since 01 May 2020. it is very annoying and I still cannot fix it. Any help will be much appreciated.

---

