---
title: "Browser File Upload default paths"
date: 2007-10-24
forum: General Help
---

### Post by SCS on 2007-10-24
Hello All,

I have just converted a 20 station customer service center to Xubuntu stations from windows 2000/xp.  Everything is working smoothly and I am at the point of adding the stations to some sort of LDAP/Kerberos network and moving the users from ies4linux/wine to native firefox.

My problem is as follows:  The users are using catfish to search a repository of up to 200,000 files stored in a flat folder hierarchy.  Once the requested file is located, it is reviewed and then attached via firefox to a web application.  

The issue I am having is that when the user browses for the file in the webApp (Thunar is being used as the file manager), it defaults to the last place a file was browsed within the browser.  This is not only a linux attribute but happens in almost every OS with every browser.  

What the users do on the first file browse for the session (the path seems to default to the users home dir) is click the search in Thunar and catfish takes over and finds the file.  Then you can click the result and it will go in to the webapp's uploader box and then the file can be uploaded.  But on the second file browse, Thunar will automatically open up the path where the last file was uploaded from.  That directory may have 20,000-30,000 files in it by itself so at this point things get quite slow. Once it loads you can go back to the search or change directories if needed.  Again all very slow.

I cannot organize thise files any better due to the nature of their usage.

Ideally, I would like to be able to force this dialog to default to the users home dir if it can and alternately use the last file location as a secondary option if the home dir path doesn't exist.  That way the users can just use the search to quickly find the files they need since the file browser will open on a directory with only a handful of files and folders to index.

I hope this makes sense and I hope someone can help me with this.

Thanks,

SCS

---

