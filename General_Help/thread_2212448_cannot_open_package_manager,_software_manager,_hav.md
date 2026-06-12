---
title: "cannot open package manager, software manager, have drmc error on boot"
date: 2014-03-21
forum: General Help
---

### Post by capo1949 on 2014-03-21
Hi all
[COLOR="#FF0000"]**PLEASE DONT SPEND TIME ON THIS DECIDED TO REINSTAL**[/COLOR]

Yesterday I reformatted my 3Tb USB HDD and on completion I found the preferences was root for the drive.
Foolishly I changed the preverences using the recursive option, and now have the above problems.

 $ sudo chmod -Rfv ugo+rwx  /media/graham/4b25d238-ee7f-4ef7-addb-1a1f03d14a35 /

Is there some way I can correct this or is it easier to do a reinstall?

---

### Post by Dreamer Fithp Apprentice on 2014-03-21
Answering because an answer takes it out of the unanswered list which many people check to see if they can help. I suggest in the future ANSWERING your own post when this happens rather than editing it. 

I don't think there is an out of the box solution. I have contemplated making a script that would recursively check the ownership and permissions of all files on a newly installed system and for each file append lines with chown and chmod commands to restore that file to its original condition to a file "/restore-ownership-perms-defaults.sh". So that in this sort of circumstance one could simply run the script as root and have a good chance of recovery.  But I haven't gotten around to it and you'd have to run the first script on a new installation before borking it anyway.

---

