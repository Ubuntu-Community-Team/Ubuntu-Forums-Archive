---
title: "F-Spot Facebook export howto add a diff .."
date: 2007-05-30
forum: General Help
---

### Post by trippinnik on 2007-05-30
Hopefully this is the best place to post this.  I am having trouble importing a diff into the f-spot svn source.  I've never done it before and couldn't find anything relevant (or anything that worked on the net).

First a little background. Now that Facebook as it's APIs published I was hoping to use F-Spot to upload photos like I do to flickr and Picasa.  I checked and it wasn't in the official build but it is on the upcoming features.  Looking here [http://f-spot.org/How_To_Build_from_HEAD](http://f-spot.org/How_To_Build_from_HEAD) I followed the instructions to get the svn version, then tried to add in the diff, but it was rejected.  

Anyone have any ideas?

---

### Post by trippinnik on 2007-05-30
OK, maybe I've put this in the wrong place.  I guess it's more of a development question.  I think this Facebook feature could use some more attention, especially from Mugshot people out there.

---

### Post by fuoco on 2007-09-04
Hi, dies this work now?

---

### Post by trippinnik on 2007-09-04
No, I wish it did.  I've been looking all over for this....

---

### Post by kroiz on 2008-04-11
Are we there yet?

---

### Post by trippinnik on 2008-04-11
I think so.  Last I looked F-spot had this in the plugins you could install from the default repository or F-spot plugins.  I didn't test it since I haven't needed to upload any pictures recently (I used conduit last time).  Also can't check now since mono is foobared on my pc from trying to build mono from svn to get Moonlight...

---

### Post by kroiz on 2008-04-11
Indeed I found it in the F-Spot "Manage Extensions" but its installation failed.
)-:

---

### Post by trippinnik on 2008-04-11
well i guess you can try conduit instead. It's purpose is basically syncing with various internet services or other folders.  it works pretty well and it's in the repos.

---

### Post by kroiz on 2008-04-12
based on your recommendation I installed conduit but I can not get it to do anything.
once it loads I drag a "Data Provider" to the right pane but I am not able to configure anything.
I right click configure and nothing seems to happen.
what version are you using?

I did not find any documentation on their site nor does the built-in help works.

---

### Post by trippinnik on 2008-04-12
I just looked at it again.  you need to drag 2 data providers over to the canvas onto the same line.  For facebook that Facebook and F-spot.  Right click to configure, then click file - syncronize.  I think with Gutsy I had to build from source, but now I have version .36  If you are running Hardy you'll have it in the repo.  If you are running Gutsy just add the backports repo.

---

### Post by kroiz on 2008-04-13
> you need to drag 2 data providers over to the canvas onto the same line. For facebook that Facebook and F-spot. Right click to configure, then click file - syncronize.
The right click configure part does nothing hence the synchronization to follow does nothing.

The version I used is 0.3.9 which is the what I get from synaptic after I added to the sources.list the repo suggested in conduit site.
If I remove that line from the sources.list I can get from synaptic version 0.3.2 which does not have facebook as a "Data Provider".

oh well I guess I will have to wait until this application mature or the f-spot facebook export plugin mature.
In the mean time I will use the simple uploader.
Thanks anyway.

---

### Post by trippinnik on 2008-04-13
No, this one really does work.  Maybe my instructions aren't that clear.  Drag Facebook connection over to the canvas on the right, then place the F-spot connection over it.  The two should be linked up now.  Then right click Facebook, a browser window opens, enter you password and username, then right click F-spot and choose which tags/albumns to sync. then right click and Refresh Item.

---

### Post by kroiz on 2008-04-14
trippinnik, you are a dear and your explanations are crystal clear. (-:
It is the configure part that does not work, no dialog is opened.

---

