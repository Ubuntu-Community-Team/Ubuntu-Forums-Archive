---
title: "Can only open Thunderbird using sudo"
date: 2018-03-17
forum: General Help
---

### Post by PDA1 on 2018-03-17
For whatever reason I can now only open Thunderbird using the sudo thunderbird  (in Terminal)

Can someone please tell me how to fix this?

Thank you

PDA1

---

### Post by QIII on 2018-03-17
Hello!

My guess is that you may have accidentally opened the GUI using sudo at some point before -- and have now changed the ownership/permissions of the profile in your /home directory.

Would you please look at

```
ls -l ~/.thunderbird
```

and check to see that you are the owner?

Then go into the directory and find your profile, which should look something like 

```
/.thunderbird/<randomString>.default
```

Then also run 

```
ls -l ~/.thunderbird/<randomStringYouFound>.default
```

That will probably produce a pretty long list of items.  Check to make sure you are also the owner of those.

---

### Post by PDA1 on 2018-03-17
Ok....here's the result.  I hope that means something.


```
Distance@Distance-MM061:~/thunderbird$ ls -l ~/.thunderbird/hobart21r.default
total 94304
-rwxrwxr-x  1 Distance Distance    14491 Mar 15 15:44 abook.mab
drwx------  2 Distance Distance     4096 Mar 17 21:56 adblockplus
-rw-rw-r--  1 Distance Distance   365283 Jul 22  2013 adblockplus-rules.json
-rw-------  1 Distance Distance    93506 Mar 17 19:43 addons.json
-rw-rw-r--  1 Distance Distance   524288 Feb 21 20:59 addons.sqlite
-rw-rw-r--  1 Distance Distance        0 Mar 17 20:09 AlternateServices.txt
-rw-rw-r--  1 Distance Distance   425984 Feb 21 20:59 blist.sqlite
-rw-------  1 Distance Distance   266168 Mar 17 15:44 blocklist.xml
-rw-rw----  1 Distance Distance        1 Oct 14  2013 _CACHE_CLEAN_
drwx------  4 Distance Distance     4096 Nov 10  2012 Cache.Trash671977507
drwx------ 18 root root     4096 Nov  9  2012 Cache.Trash99983627
drwx------  3 Distance Distance     4096 Mar 17 19:34 calendar-data
-rwxrwxr-x  1 Distance Distance   409600 Mar 17 21:59 cert8.db
-rwxrwxr-x  1 Distance Distance    12948 Nov  7  2016 cert_override.txt
drwx------  2 Distance Distance     4096 Dec  5  2009 chrome
-rwxrwxr-x  1 Distance Distance    98304 Feb 21 20:59 chromeappsstore.sqlite
-rwxrwxr-x  1 Distance Distance      159 Mar 17 21:25 compatibility.ini
-rw-rw-r--  1 Distance Distance   176343 Apr 14  2012 compreg.dat
-rw-rw-r--  1 Distance Distance   229376 Feb 21 20:59 content-prefs.sqlite
-rw-r--r--  1 Distance Distance   524288 Feb 21 21:00 cookies.sqlite
drwx------  3 Distance Distance     4096 Mar 17 21:56 crashes
drwx------  2 Distance Distance     4096 Mar 17 21:56 datareporting
-rw-r--r--  1 root root       23 Mar 17 21:29 directoryTree.json
-rw-------  1 Distance Distance   159682 Mar 17 19:41 downloads.json
drwx------  5 Distance Distance    12288 Mar 17 20:04 extensions
-rw-r--r--  1 root root     1255 Mar 17 21:23 extensions.ini
-rw-------  1 root root    65270 Mar 17 21:23 extensions.json
-rwxrwxr-x  1 Distance Distance  1043242 Oct 22  2013 extensions.log
-rwxrwxr-x  1 Distance Distance    77301 Apr 16  2012 extensions.rdf
-rw-rw-r--  1 Distance Distance   524288 Feb 21 20:59 extensions.sqlite
-rwxrwxr-x  1 Distance Distance     2007 Nov 30  2010 filterlog.html
-rwxr-xr-x  1 Distance Distance      774 Oct  5 16:37 folderTree-1.json
-rwxr-xr-x  1 root root      798 Mar 17 21:59 folderTree.json
-rw-rw-r--  1 Distance Distance   196608 Feb 21 20:59 formhistory.sqlite
-rw-rw-r--  1 Distance Distance 17530880 Mar 17 21:59 global-messages-db.sqlite
drwx------  3 Distance Distance     4096 Mar 17 19:37 gmp
-rwxrwxr-x  1 Distance Distance   100602 Mar 17 21:30 history.mab
drwx------ 11 Distance Distance     4096 Nov  7  2016 ImapMail
-rwxrwxr-x  1 Distance Distance 66806195 Dec  1  2010 INBOX
drwx------  2 Distance Distance     4096 Nov 24  2012 INBOX.sbd
-rwxrwxr-x  1 Distance Distance     5216 Jan 11  2010 install.log
-rw-rw----  1 Distance Distance    72321 Mar 13 23:02 junklog.html
-rwxrwxr-x  1 Distance Distance    16384 Mar 17 21:59 key3.db
-rw-rw-r--  1 Distance Distance   262962 Feb  6  2017 lightweighttheme-footer
-rw-rw-r--  1 Distance Distance   720241 Feb  6  2017 lightweighttheme-header
-rwxrwxr-x  1 Distance Distance    83791 Nov 10  2015 localstore.rdf
-rw-rw-r--  1 Distance Distance     2093 Feb 22  2013 localstore-safe.rdf
-rw-------  1 Distance Distance     4623 Nov 18 21:39 logins.json
drwx------  3 Distance Distance     4096 Nov 20 18:01 logs
drwxr-xr-x  2 Distance Distance     4096 Feb  6  2017 lwtheme
drwx------  7 Distance Distance     4096 Apr  9  2016 Mail
-rwxrwxr-x  1 Distance Distance      108 Sep 20  2011 mailViews.dat
-rwxrwxr-x  1 Distance Distance    16500 Dec 22 21:01 mimeTypes.rdf
drwx------  2 Distance Distance    12288 Jan 16 20:25 minidumps
-rwxrwxr-x  1 Distance Distance     2676 Dec  1  2010 msgFilterRules.dat
drwx------  3 Distance Distance     4096 Apr  9  2016 News
-rwxrwxr-x  1 Distance Distance    24831 Mar 17 21:59 panacea.dat
-rwxrwxr-x  1 Distance Distance    17408 Mar 17 19:34 permissions.sqlite
-rwxrwxr-x  1 Distance Distance      146 Jul  7  2012 pgprules.xml
-rwxrwxr-x  1 Distance Distance  1671168 Mar 17 21:24 places.sqlite
-rw-------  1 root root     6880 Mar 17 21:23 pluginreg.dat
-rwxr-xr-x  1 root root    91014 Mar 17 21:59 prefs.js
-rw-r--r--  1 root root    32452 Mar 17 21:55 revocations.txt
drwx------  2 Distance Distance   380928 Mar 17 21:56 saved-telemetry-pings
-rw-------  1 Distance Distance    17134 May 21  2016 search.json
-rw-------  1 root root     5248 Mar 17 21:23 search.json.mozlz4
-rw-rw-r--  1 Distance Distance        2 Jul 19  2012 search-metadata.json
-rw-rw-r--  1 Distance Distance    65536 Feb 21 20:59 search.sqlite
-rwxrwxr-x  1 Distance Distance    16384 Apr 16  2012 secmod.db
-rw-rw-r--  1 Distance Distance        0 Mar 17 20:09 SecurityPreloadState.txt
-rw-------  1 root root      204 Mar 17 21:59 sessionCheckpoints.json
-rw-------  1 root root      368 Mar 17 21:59 session.json
-rwxrwxr-x  1 Distance Distance    25600 Feb 21 20:59 signons.sqlite
-rw-rw-r--  1 Distance Distance    98304 Feb 21 20:59 simple_storage.sqlite
-rw-rw-r--  1 Distance Distance     1333 Mar 17 21:59 SiteSecurityServiceState.txt
drwxr-xr-x  4 Distance Distance     4096 Sep 21  2016 storage
-rwxrwxr-x  1 Distance Distance    32768 Jan 12  2010 storage.sdb
-rw-rw-r--  1 Distance Distance   415741 Feb 28  2012 TestPilotErrorLog.log
drwx------  2 Distance Distance     4096 Jan 16  2012 TestPilotExperimentFiles
-rw-------  1 Distance Distance       25 Jul 20  2016 times.json
-rwxrwxr-x  1 Distance Distance  1717587 Mar 14 09:32 training.dat
-rwxrwxr-x  1 Distance Distance        8 Mar 14 09:32 traits.dat
-rwxrwxr-x  1 Distance Distance     1024 Feb 21 20:59 urlclassifier2.sqlite
-rwxrwxr-x  1 Distance Distance    32768 Feb 21 20:59 urlclassifier3.sqlite
-rw-rw-r--  1 Distance Distance       24 Dec 27  2011 urlclassifier.pset
drwx------  2 Distance Distance     4096 Dec  5  2009 US
-rwxrwxr-x  1 Distance Distance        0 Dec 31  2015 virtualFolders-1.dat
-rwxrwxr-x  1 Distance Distance     2395 May 12  2013 virtualFolders-2.dat
-rwxrwxr-x  1 Distance Distance     2395 May 13  2013 virtualFolders-3.dat
-rwxrwxr-x  1 Distance Distance     2395 Jun  5  2013 virtualFolders-4.dat
-rwxrwxr-x  1 Distance Distance     2395 Jun 11  2013 virtualFolders-5.dat
-rwxrwxr-x  1 Distance Distance        0 Jun 12  2013 virtualFolders-6.dat
-rwxrwxr-x  1 Distance Distance     2366 Jan 28  2014 virtualFolders-7.dat
-rwxr-xr-x  1 root root     1395 Mar 17 21:59 virtualFolders.dat
-rwxrwxr-x  1 Distance Distance     4096 Mar 17 21:24 webappsstore.sqlite
-rw-rw-r--  1 Distance Distance   120235 Apr 14  2012 xpti.dat
-rw-rw-r--  1 Distance Distance        0 Dec 16  2013 xpunge-extension-prefmigration-existing-new-prefs.txt
-rw-rw-r--  1 Distance Distance     1255 Dec 16  2013 xpunge-extension-prefmigration-old-prefs.txt
-rw-------  1 root root     8628 Mar 17 21:30 xulstore.json  
```

---

### Post by QIII on 2018-03-17
Hello again.

Please run those two commands separately.

Thanks.

---

### Post by PDA1 on 2018-03-17
I hope this is what you're looking for....

```
~$ ls -l ~/.thunderbird
 total 72
 -rwxr-xr-x  1 Distance Distance   335 Nov 29  2010 appreg
 -rw-r--r--  1 root root    48 Mar 17 20:52 C:\nppdf32Log\debuglog.txt
 drwx------  4 Distance Distance 12288 Mar 17 19:34 Crash Reports
 drwx------ 22 Distance Distance 20480 Mar 17 21:59 hobart21r.default
 -rw-------  1 root root    94 Dec 31  2015 profiles.ini
 
 
 Distance@Distance-MM061:~$ ls -l ~/.thunderbird/hobart21r.default
 total 94304
 -rwxrwxr-x  1 Distance Distance    14491 Mar 15 15:44 abook.mab
 drwx------  2 Distance Distance     4096 Mar 17 21:56 adblockplus
 -rw-rw-r--  1 Distance Distance   365283 Jul 22  2013 adblockplus-rules.json
 -rw-------  1 Distance Distance    93506 Mar 17 19:43 addons.json
 -rw-rw-r--  1 Distance Distance   524288 Feb 21 20:59 addons.sqlite
 -rw-rw-r--  1 Distance Distance        0 Mar 17 20:09 AlternateServices.txt
 -rw-rw-r--  1 Distance Distance   425984 Feb 21 20:59 blist.sqlite
 -rw-------  1 Distance Distance   266168 Mar 17 15:44 blocklist.xml
 -rw-rw----  1 Distance Distance        1 Oct 14  2013 _CACHE_CLEAN_
 drwx------  4 Distance Distance     4096 Nov 10  2012 Cache.Trash671977507
 drwx------ 18 root root     4096 Nov  9  2012 Cache.Trash99983627
 drwx------  3 Distance Distance     4096 Mar 17 19:34 calendar-data
 -rwxrwxr-x  1 Distance Distance   409600 Mar 17 21:59 cert8.db
 -rwxrwxr-x  1 Distance Distance    12948 Nov  7  2016 cert_override.txt
 drwx------  2 Distance Distance     4096 Dec  5  2009 chrome
 -rwxrwxr-x  1 Distance Distance    98304 Feb 21 20:59 chromeappsstore.sqlite
 -rwxrwxr-x  1 Distance Distance      159 Mar 17 21:25 compatibility.ini
 -rw-rw-r--  1 Distance Distance   176343 Apr 14  2012 compreg.dat
 -rw-rw-r--  1 Distance Distance   229376 Feb 21 20:59 content-prefs.sqlite
 -rw-r--r--  1 Distance Distance   524288 Feb 21 21:00 cookies.sqlite
 drwx------  3 Distance Distance     4096 Mar 17 21:56 crashes
 drwx------  2 Distance Distance     4096 Mar 17 21:56 datareporting
 -rw-r--r--  1 root root       23 Mar 17 21:29 directoryTree.json
 -rw-------  1 Distance Distance   159682 Mar 17 19:41 downloads.json
 drwx------  5 Distance Distance    12288 Mar 17 20:04 extensions
 -rw-r--r--  1 root root     1255 Mar 17 21:23 extensions.ini
 -rw-------  1 root root    65270 Mar 17 21:23 extensions.json
 -rwxrwxr-x  1 Distance Distance  1043242 Oct 22  2013 extensions.log
 -rwxrwxr-x  1 Distance Distance    77301 Apr 16  2012 extensions.rdf
 -rw-rw-r--  1 Distance Distance   524288 Feb 21 20:59 extensions.sqlite
 -rwxrwxr-x  1 Distance Distance     2007 Nov 30  2010 filterlog.html
 -rwxr-xr-x  1 Distance Distance      774 Oct  5 16:37 folderTree-1.json
 -rwxr-xr-x  1 root root      798 Mar 17 21:59 folderTree.json
 -rw-rw-r--  1 Distance Distance   196608 Feb 21 20:59 formhistory.sqlite
 -rw-rw-r--  1 Distance Distance 17530880 Mar 17 21:59 global-messages-db.sqlite
 drwx------  3 Distance Distance     4096 Mar 17 19:37 gmp
 -rwxrwxr-x  1 Distance Distance   100602 Mar 17 21:30 history.mab
 drwx------ 11 Distance Distance     4096 Nov  7  2016 ImapMail
 -rwxrwxr-x  1 Distance Distance 66806195 Dec  1  2010 INBOX
 drwx------  2 Distance Distance     4096 Nov 24  2012 INBOX.sbd
 -rwxrwxr-x  1 Distance Distance     5216 Jan 11  2010 install.log
 -rw-rw----  1 Distance Distance    72321 Mar 13 23:02 junklog.html
 -rwxrwxr-x  1 Distance Distance    16384 Mar 17 21:59 key3.db
 -rw-rw-r--  1 Distance Distance   262962 Feb  6  2017 lightweighttheme-footer
 -rw-rw-r--  1 Distance Distance   720241 Feb  6  2017 lightweighttheme-header
 -rwxrwxr-x  1 Distance Distance    83791 Nov 10  2015 localstore.rdf
 -rw-rw-r--  1 Distance Distance     2093 Feb 22  2013 localstore-safe.rdf
 -rw-------  1 Distance Distance     4623 Nov 18 21:39 logins.json
 drwx------  3 Distance Distance     4096 Nov 20 18:01 logs
 drwxr-xr-x  2 Distance Distance     4096 Feb  6  2017 lwtheme
 drwx------  7 Distance Distance     4096 Apr  9  2016 Mail
 -rwxrwxr-x  1 Distance Distance      108 Sep 20  2011 mailViews.dat
 -rwxrwxr-x  1 Distance Distance    16500 Dec 22 21:01 mimeTypes.rdf
 drwx------  2 Distance Distance    12288 Jan 16 20:25 minidumps
 -rwxrwxr-x  1 Distance Distance     2676 Dec  1  2010 msgFilterRules.dat
 drwx------  3 Distance Distance     4096 Apr  9  2016 News
 -rwxrwxr-x  1 Distance Distance    24831 Mar 17 21:59 panacea.dat
 -rwxrwxr-x  1 Distance Distance    17408 Mar 17 19:34 permissions.sqlite
 -rwxrwxr-x  1 Distance Distance      146 Jul  7  2012 pgprules.xml
 -rwxrwxr-x  1 Distance Distance  1671168 Mar 17 21:24 places.sqlite
 -rw-------  1 root root     6880 Mar 17 21:23 pluginreg.dat
 -rwxr-xr-x  1 root root    91014 Mar 17 21:59 prefs.js
 -rw-r--r--  1 root root    32452 Mar 17 21:55 revocations.txt
 drwx------  2 Distance Distance   380928 Mar 17 21:56 saved-telemetry-pings
 -rw-------  1 Distance Distance    17134 May 21  2016 search.json
 -rw-------  1 root root     5248 Mar 17 21:23 search.json.mozlz4
 -rw-rw-r--  1 Distance Distance        2 Jul 19  2012 search-metadata.json
 -rw-rw-r--  1 Distance Distance    65536 Feb 21 20:59 search.sqlite
 -rwxrwxr-x  1 Distance Distance    16384 Apr 16  2012 secmod.db
 -rw-rw-r--  1 Distance Distance        0 Mar 17 20:09 SecurityPreloadState.txt
 -rw-------  1 root root      204 Mar 17 21:59 sessionCheckpoints.json
 -rw-------  1 root root      368 Mar 17 21:59 session.json
 -rwxrwxr-x  1 Distance Distance    25600 Feb 21 20:59 signons.sqlite
 -rw-rw-r--  1 Distance Distance    98304 Feb 21 20:59 simple_storage.sqlite
 -rw-rw-r--  1 Distance Distance     1333 Mar 17 21:59 SiteSecurityServiceState.txt
 drwxr-xr-x  4 Distance Distance     4096 Sep 21  2016 storage
 -rwxrwxr-x  1 Distance Distance    32768 Jan 12  2010 storage.sdb
 -rw-rw-r--  1 Distance Distance   415741 Feb 28  2012 TestPilotErrorLog.log
 drwx------  2 Distance Distance     4096 Jan 16  2012 TestPilotExperimentFiles
 -rw-------  1 Distance Distance       25 Jul 20  2016 times.json
 -rwxrwxr-x  1 Distance Distance  1717587 Mar 14 09:32 training.dat
 -rwxrwxr-x  1 Distance Distance        8 Mar 14 09:32 traits.dat
 -rwxrwxr-x  1 Distance Distance     1024 Feb 21 20:59 urlclassifier2.sqlite
 -rwxrwxr-x  1 Distance Distance    32768 Feb 21 20:59 urlclassifier3.sqlite
 -rw-rw-r--  1 Distance Distance       24 Dec 27  2011 urlclassifier.pset
 drwx------  2 Distance Distance     4096 Dec  5  2009 US
 -rwxrwxr-x  1 Distance Distance        0 Dec 31  2015 virtualFolders-1.dat
 -rwxrwxr-x  1 Distance Distance     2395 May 12  2013 virtualFolders-2.dat
 -rwxrwxr-x  1 Distance Distance     2395 May 13  2013 virtualFolders-3.dat
 -rwxrwxr-x  1 Distance Distance     2395 Jun  5  2013 virtualFolders-4.dat
 -rwxrwxr-x  1 Distance Distance     2395 Jun 11  2013 virtualFolders-5.dat
 -rwxrwxr-x  1 Distance Distance        0 Jun 12  2013 virtualFolders-6.dat
 -rwxrwxr-x  1 Distance Distance     2366 Jan 28  2014 virtualFolders-7.dat
 -rwxr-xr-x  1 root root     1395 Mar 17 21:59 virtualFolders.dat
 -rwxrwxr-x  1 Distance Distance     4096 Mar 17 21:24 webappsstore.sqlite
 -rw-rw-r--  1 Distance Distance   120235 Apr 14  2012 xpti.dat
 -rw-rw-r--  1 Distance Distance        0 Dec 16  2013 xpunge-extension-prefmigration-existing-new-prefs.txt
 -rw-rw-r--  1 Distance Distance     1255 Dec 16  2013 xpunge-extension-prefmigration-old-prefs.txt
 -rw-------  1 root root     8628 Mar 17 21:30 xulstore.json
  
```

---

### Post by &amp;KyT$0P# on 2018-03-17
See if this fix it -
```
sudo chown -R Distance: ~/.thunderbird
```

---

### Post by QIII on 2018-03-17
Thanks.

OK, you have confirmed my suspicion.  At some point you almost certainly started Thunderbird from the command line using "sudo" alone.  The problem with starting GUI applications with sudo is that you may end up changing the ownership of configuration files -- even those in your /home -- to root.  This happens because sudo leaves the $HOME environment variable as root's, so all the config files are saved with root's ownership.

To make sure that the ownership of directories and files in your /home remain owned by you, you should not use "sudo" by itself.

Instead, use gksudo (if your release still supports it, but it is being deprecated) or "sudo -H " to make sure that the appropriate environment variable is used.  (kdesudo still works as expected in Kubuntu).

To fix this, you'll need to change the ownership of everything in /.thunderbird back to yourself recursively.  You can do that with 

```
sudo chown -R $LOGNAME ~/.thunderbird
```

or

```
sudo chown -R Distance:Distance ~/.thunderbird
```

Notice that this time you do use "sudo" alone because you have to be root to change ownership on files owned by root.

---

### Post by PDA1 on 2018-03-17
Halogen2....YOU ARE A SUPER HERO!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

It worked perfectly!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

Thank you so much!!!!!!!!!!!!!!!

---

### Post by &amp;KyT$0P# on 2018-03-17
You're welcome! :KS

---

### Post by PDA1 on 2018-03-17
....And QIII.....thank you so much for the help too!!!!

---

