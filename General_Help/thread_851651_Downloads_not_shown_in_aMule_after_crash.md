---
title: "Downloads not shown in aMule after crash"
date: 2008-07-06
forum: General Help
---

### Post by DMurray on 2008-07-06
Hi everybody.
First of all, sorry if this is not the correct area for posting about aMule. I did a search and found most of aMule-related threads here.

I had like 6 or 7 downloads in aMule. Computer crashed, had to restart.
When I opened aMule again, the files being downloaded are not shown in the download list, but they are in the "Incoming" directory.
What do we do to get the stuff back?

Thanks in advance.

---

### Post by Vivaldi Gloria on 2008-07-06
> **DMurray said:**
> I had like 6 or 7 downloads in aMule. Computer crashed, had to restart. When I opened aMule again, the files being downloaded are not shown in the download list, but they are in the "Incoming" directory. What do we do to get the stuff back?


This happened to me too. The funny thing is that eventhough the files being downloaded were not shown i could see them when selecting them with mouse and the downloads continued. So I waited the downloads to finish and then uninstall & reinstalled it. So check if your downloads are continuing despite they don't show.

---

### Post by DMurray on 2008-07-09
Hello, Vivaldi.

I didn't understand what you meant with "i could see them when selecting them with mouse".
The download list is empty and there is no action regarding downloads, only uploads. After 2 hours, I took a look at the statistics and nothing was downloaded at all.

---

### Post by Vivaldi Gloria on 2008-07-09
> **DMurray said:**
> The download list is empty and there is no action regarding downloads, only uploads. After 2 hours, I took a look at the statistics and nothing was downloaded at all.

I have two suggestions A and B.

---------------------------------------------------------

A. Only replace 

```
 ~/.aMule/amule.conf 
```

It may be corrupted. Before you do this open amule and write down all your preferences. Then delete the amule.conf file. Then put a fresh amule.conf file in its place (see below). Then start amule and re-do your preferences. Then restart amule. That's it.

To find a fresh amule.conf file look at the page

[http://www.amule.org/wiki/index.php/Amule.conf_file](http://www.amule.org/wiki/index.php/Amule.conf_file)

There is an example amule.conf file there. It starts with

```

[eMule]
AppVersion=aMule 2.1.0
Nick=http://www.aMule.org
...
```

Yes, it writes [eMule] at the top, not [aMule]. Copy those lines to gedit and save as amule.conf.

The only problem is that that page does not say if that example is for the latest amule. I think so, but I'm not sure. May be ask in amule forums for a fresh amule.conf.

---------------------------------------------------------

B. If A doesn't work then I don't know what you can do other than reinstalling.

1) Make a backup copy of your ~/.aMule folder. Then start amule and right down all the preferences. Close it.

2) From synaptic right click on amule and choose completely remove.

3) delete ~/.aMule folder if it is still there.

4) Install amule using synaptic.

5) From your backup of .aMule copy and paste the important configuration files to the new .aMule (see below).

6) Start amule and goto preferences and re-do your preferences. Restart amule. That's all.

The page

[http://www.amule.org/wiki/index.php/AMule_files](http://www.amule.org/wiki/index.php/AMule_files)

contains the list of files in ~/.aMule. See it for more info.

At least copy server.met and the files ones about downloaded files (.part files etc.) from old .amule folder to the new one. If you also connect to KAD then preserve nodes.dat also.

Have a look at the list and decide if there are other files you want to preserve. Keep minimum.

I wouldn't keep amule.conf and start with a fresh one. Since you will have written down the prefs before you uninstall, you can quickly re-do your prefs.

If you have uploaded more than 100 MB then it may be a good idea to preserve also the files which keep your identity. I forgot which are those - look at the list. This is useful since the other clients which owe you can recognize you and you'll go up the waiting list faster.

---------------------------------------------------------

If none of these restore your downloads then you'll have to start them from the beginning.

---

### Post by DMurray on 2008-07-10
Hi there, Vivaldi.

Aparently there is nothing wrong with ~/aMule/amule.conf. I can edit it with no problems and no garbage in the file.
I would proceed with "B", but there were only 3 (large) files being downloaded, but nothing that I can't restart. I also can't imagine how a reinstall would solve it.
By the way, I thank you very much for your support. This may just be an inconvenience of aMule. This is not the first time ir crashes (including windows and linux), but I never saw the downloads vanishing.
It's obvious that I'm not the only one to experience this issue, the devs are probably aware of that.
Thank you very much for your effort. It may just be a bug and no matter how skilled a user is... it could be a bug without solution at the moment.

Thanks a lot.

---

### Post by Vivaldi Gloria on 2008-07-11
> **DMurray said:**
> nothing that I can't restart. ...

That' good. Then just completely remove and reinstall.

>  Thanks a lot.

You're welcome.

---

