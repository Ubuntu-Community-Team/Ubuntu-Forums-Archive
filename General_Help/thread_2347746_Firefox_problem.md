---
title: "Firefox problem"
date: 2016-12-28
forum: General Help
---

### Post by satimis on 2016-12-28
Hi all,

Host - ubuntu 16.04
VM - ubuntu 16.04
Oracle VirtualBox
Web browser - Firegox 50.1.0

Godaddy share hosting

I encountered a strange problem.  After login the webmail account it only shows a blank page.  However there is no problem for the Firefox running on VM.  After login it shows the webmail.  Also It has no problem on Google chrome.

I have tried clearing the cached web contain.  Sometime it worked another failed still having the same problem.

Please shed me some light to fix this problem

Thanks

Regards
satimis

---

### Post by &amp;KyT$0P# on 2016-12-28
1) Create a new Firefox [profile]("http://kb.mozillazine.org/Profile") on your host machine.  Don't start Firefox with it just yet, just exit the profile manager for now.

2) Delete any files in the new profile folder.  Completely quit Firefox on both machines.  Then copy in the entire contents of your VM's Firefox profile into this new profile.

3) Start Firefox with this new (copied) profile.

Does it work?

---

### Post by satimis on 2016-12-28
> **halogen2 said:**
> 1) Create a new Firefox [profile]("http://kb.mozillazine.org/Profile") on your host machine.  Don't start Firefox with it just yet, just exit the profile manager for now.

2) Delete any files in the new profile folder.  Completely quit Firefox on both machines.  Then copy in the entire contents of your VM's Firefox profile into this new profile.

3) Start Firefox with this new (copied) profile.

Does it work?
Hi,

Thanks for your advice.  Performed following steps.

On Host terminal
&#10219; firefox -P
to start Profile Manager
-> [Create Profile..]
New_Profile
-> [Exit]

Again on Host terminal
&#10219; ls /home/satimis/.mozilla/firefox/vim3l7yy.New_Profile/```

times.json

```
Only one file

&#10219; rm /home/satimis/.mozilla/firefox/vim3l7yy.New_Profile/times.json 

On VM terminal
&#10219; ls /home/satimis/.mozilla/firefox/```

Crash Reports  ik7glgfy.default  profiles.ini

```

&#10219; ls /home/satimis/.mozilla/firefox/ik7glgfy.default/```

addons.json             extensions.ini      saved-telemetry-pings
blocklist-addons.json   extensions.json     search.json.mozlz4
blocklist-gfx.json      formhistory.sqlite  secmod.db
blocklist-plugins.json  gmp                 sessionCheckpoints.json
blocklist.xml           gmp-gmpopenh264     sessionstore-backups
bookmarkbackups         key3.db             SiteSecurityServiceState.txt
cert8.db                kinto.sqlite        storage
compatibility.ini       mimeTypes.rdf       storage.sqlite
containers.json         minidumps           times.json
content-prefs.sqlite    permissions.sqlite  webapps
cookies.sqlite          places.sqlite       webappsstore.sqlite
cookies.sqlite-shm      places.sqlite-shm   webappsstore.sqlite-shm
cookies.sqlite-wal      places.sqlite-wal   webappsstore.sqlite-wal
crashes                 pluginreg.dat       xulstore.json
datareporting           prefs.js
extensions              revocations.txt

```

Whether copy all files to Host /home/satimis/.mozilla/firefox/vim3l7yy.New_Profile/ ?

There are many files.  I'm stuck here.

Regards
satimis

---

### Post by Keith_Helms on 2016-12-28
Yes, copy all the files under the working profile directory to the newly created one.

---

### Post by satimis on 2016-12-29
> **Keith_Helms said:**
> Yes, copy all the files under the working profile directory to the newly created one.

On VM terminal run

Create a new folder "VM_Firefox_Profile"   on /media/sf_Transfer_Directory_PC1A/VM_Firefox_Profile

$ cp /home/satimis/.mozilla/firefox/ik7glgfy.default/* /media/sf_Transfer_Directory_PC1A/VM_Firefox_Profile/```

cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/bookmarkbackups'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/crashes'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/datareporting'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/extensions'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/gmp'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/gmp-gmpopenh264'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/minidumps'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/saved-telemetry-pings'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/sessionstore-backups'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/storage'
cp: omitting directory '/home/satimis/.mozilla/firefox/ik7glgfy.default/webapps'

```

$ ls /media/sf_Transfer_Directory_PC1A/VM_Firefox_Profile/```

addons.json             extensions.ini      revocations.txt
blocklist-addons.json   extensions.json     search.json.mozlz4
blocklist-gfx.json      formhistory.sqlite  secmod.db
blocklist-plugins.json  key3.db             sessionCheckpoints.json
blocklist.xml           kinto.sqlite        SiteSecurityServiceState.txt
cert8.db                mimeTypes.rdf       storage.sqlite
compatibility.ini       permissions.sqlite  times.json
containers.json         places.sqlite       webappsstore.sqlite
content-prefs.sqlite    places.sqlite-shm   webappsstore.sqlite-shm
cookies.sqlite          places.sqlite-wal   webappsstore.sqlite-wal
cookies.sqlite-shm      pluginreg.dat       xulstore.json
cookies.sqlite-wal      prefs.js

```

On Host terminal
&#10219; ls Transfer_Directory_PC1A/VM_Firefox_Profile/```

addons.json             extensions.ini      revocations.txt
blocklist-addons.json   extensions.json     search.json.mozlz4
blocklist-gfx.json      formhistory.sqlite  secmod.db
blocklist-plugins.json  key3.db             sessionCheckpoints.json
blocklist.xml           kinto.sqlite        SiteSecurityServiceState.txt
cert8.db                mimeTypes.rdf       storage.sqlite
compatibility.ini       permissions.sqlite  times.json
containers.json         places.sqlite       webappsstore.sqlite
content-prefs.sqlite    places.sqlite-shm   webappsstore.sqlite-shm
cookies.sqlite          places.sqlite-wal   webappsstore.sqlite-wal
cookies.sqlite-shm      pluginreg.dat       xulstore.json
cookies.sqlite-wal      prefs.js

```

&#10219; mv Transfer_Directory_PC1A/VM_Firefox_Profile/* /home/satimis/.mozilla/firefox/vim3l7yy.New_Profile/

&#10219; ls /home/satimis/.mozilla/firefox/vim3l7yy.New_Profile/```

addons.json             extensions.ini      revocations.txt
blocklist-addons.json   extensions.json     search.json.mozlz4
blocklist-gfx.json      formhistory.sqlite  secmod.db
blocklist-plugins.json  key3.db             sessionCheckpoints.json
blocklist.xml           kinto.sqlite        SiteSecurityServiceState.txt
cert8.db                mimeTypes.rdf       storage.sqlite
compatibility.ini       permissions.sqlite  times.json
containers.json         places.sqlite       webappsstore.sqlite
content-prefs.sqlite    places.sqlite-shm   webappsstore.sqlite-shm
cookies.sqlite          places.sqlite-wal   webappsstore.sqlite-wal
cookies.sqlite-shm      pluginreg.dat       xulstore.json
cookies.sqlite-wal      prefs.js

```

Then I have to start Firefox (the first time) with following steps (not clicking its icon on the left vertical bar)

On Host terminal run;
&#10219; firefox -P

select New_Profile
-> click [Start Firefox]

Now it works.

Thanks

Regards
satimis

---

