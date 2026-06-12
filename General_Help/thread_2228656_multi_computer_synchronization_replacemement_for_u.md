---
title: "multi computer synchronization replacemement for ubuntuone?"
date: 2014-06-08
forum: General Help
---

### Post by yoshimitsuspeed on 2014-06-08
I have searched a lot and found a lot of threads discussing the alternatives to ubuntuone but everything I found focussed on just syncing to the cloud. 

I had ubuntuone syncing to the cloud and keeping all my computers synced as well. 

Insync seems to think their software can do this but it involves a bit of work and it changes the look of my folders, seems really slow and is a bit of a PITA. I haven't tried this yet since I just switched my desktop back to Windows. 
> 1. On the Computer 1; right click "Documents" and select the account to sync it with Insync. Allow sync to finish.
2. On the Computer 2; rename "Documents" to something else. We'll get back to this later.
3. Type in: Ln -s ~/Insync/Documents ~/Documents. This creates a symlink from Insync's Documents directory to a non-existing ~/Documents on your Laptop. (note** non-existing because you have renamed the ~/Documents folder on step #2.
5. Move the files from the renamed (and original) Documents directory on the laptop to the new symlink "Documents".
6. Any changes on the Computer 1 or Computer 2 "Documents" folder should be in sync with this setup to whichever external directories changes happen.


Insync also wrecks my internet. It takes my ping from 20-30ms to 200-400 ms and can interfere with streaming music and things like that. 

I know there are some programs that sync between computers but I have really been hoping for an all in one setup that takes minimal setup, works cross platform and basically just does what ubuntuone did.

---

### Post by Frogs Hair on 2014-06-08
Own Cloud seems to offer file sync. [http://owncloud.org/sync-clients/](http://owncloud.org/sync-clients/)

---

