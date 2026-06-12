---
title: "Understanding user and group permissions - reciprocal?"
date: 2019-08-14
forum: General Help
---

### Post by 5circles on 2019-08-14
I know there is a lot of information online about user and group permissions, but I'm having a tough time deciphering the symptoms I've been seeing, and the apparent resolution.  I'd love to find some sort of comprehensive tutorial with explanations and best practices - and not just responses of "already answered".  This post is based on experiences with PhpStorm, both Windows and Ubuntu, with deployment on a dedicated Ubuntu box, or Ubuntu running on VirtualBox.  The most recent experience which stimulated the post is setting up Laravel.  I'll try to minimize any comments or questions related directly to PhpStorm or Laravel.  I'll clarify any differences between the two deployment servers - actually I don't think there are any.

I always deploy to a Ubuntu box, whether it's for testing/development, staging, or (eventually) actual deployment.  The username I want to use is mine - mikep.  I can't use www-data because Windows only allows a single set of credentials to be connected to a single network device.  (That's a stupid limitation IMO - claimed to be for security reasons - but I can't do anything about it, so I can either connect as mikep or www-data.

Files created on either server by uploading with PhpStorm, when connected as mikep (which is the only way I've connected to the dedicated box), are all owned by mikep with group mikep.

mikep is part of the www-data group, but I guess this is a Secondary group membership when the add to a new group is done with adduser user group.  Is this correct?

_**What is a Secondary group anyway (and is it the same as Supplemental group - both terms are used in help for programs that manipulate users)?**_

The problem I was having with Laravel is that permissions for the 'storage' directory and subdirectories was incorrect.  The result was that the first access to the Laravel directory gave an error about not being able to open the log file - "*The stream or file "/var/www/../../storage/logs/laravel.log" could not be opened: failed to open stream: Permission denied*" .  This actually means that the file could not be created.  

So what does it mean that "mikep" is a member of the "www-data" group that runs the webserver?  Not much, it appears.  I don't know if Laravel is checking for ownership, not just permissions.  But at this stage of experiments, something was preventing the file from being created.  

Here's what I tried:

1. Made www-data part of the mikep group with "sudo adduser www-data mikep"  .  I was then able to touch files in the storage and storage/logs folder, but Laravel still generated the same error.
2. ran "sudo chown -R :www-data /var/www/../../Laravel_1".  This allowed the Laravel page to be displayed without error, suggesting that permissions for files and directories in the hierarchy were incorrectly set earlier.  The problem with this - it seems to me - is that new files or directories created by PhpStorm and uploaded would still have ownership as "mikep:mikep" which is likely to cause problems.
3. ran "sudo chmod -R g+s /var/www/../../Laravel_1" per something I found online to set the setgid bit.  This appears to work as far as Laravel is concerned, and probably including new files, but it looks messy with owner:group for new files and also for the ls output after the  setgid bit.
4. Finally, which I think is the right approach  - "sudo usermod -g www-data mikep" to change the primary group for my user to www-data.  Logging out and back in didn't have the right effect, but restarting did the trick. Now files created by user mikep - whether on the machine or through a mapped drive - are mikep:www-data.

I think this last approach is the best because it only means making the change once, and having www-data group ownership makes sense.

Am I correct, or is there a better way?  And, as I wondered at the beginning, why does Primary group seem to be a mystery?  I've been using Ubuntu for a long time, and I've never really been exposed to explanations.

Thanks
Mike

---

### Post by wildmanne39 on 2019-08-15
Thread closed. Please do not post duplicates, it dilutes community effort.

---

