---
title: "HOWTO: Recompile Nautilus without Tracker integration aka fix search in Gutsy"
date: 2008-03-16
forum: General Help
---

### Post by ryanhaigh on 2008-03-16
This post details how to recompile nautilus, the default file manager for gnome/ubuntu to remove tracker integration and restore the default search function. 

These are a couple of places where people including myself have commented on the problems with tracker integration, there are many others where people do not realise that the cause of search not working is the tracker integration, this is particularly true for people searching in a directory outside trackers indexed areas and getting results from tracker which are independant of the directory from which the search takes place.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150379](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/150379)
[http://brainstorm.ubuntu.com/idea/476/](http://brainstorm.ubuntu.com/idea/476/)
[http://ubuntuforums.org/showthread.php?t=719363](http://ubuntuforums.org/showthread.php?t=719363)
[http://ubuntuforums.org/showthread.php?t=675322](http://ubuntuforums.org/showthread.php?t=675322)

I understand that the next release of ubuntu will address this issue, this is a fix for those running Gutsy and like me not wanting to wait to fix the search function.

**Step 1: Get the source.**
You will need to download the source code for nautilus but first you will need to make sure you have enabled source repositories. The easiest way to do this is go to System > Administration > Software Sources and mark the box Source code as in the attached image. When you press close another window will appear, click reload to download the updated package lists. Once that is finished we can download the source for nautilus. 

Open a terminal by going to Applications > Accessories > Terminal. We will now change directory to the Desktop for convenience and download the source code. 

**NOTE: Do note close the terminal after any step, until you have your new packages installed in step 5.**
```

cd Desktop
apt-get source nautilus

```
You will now have a folder on the desktop called nautilus-2.20.0 (the version number may change, this is the version at the time of writing).

**Step 2: Change the rules**
We will now change the options used when compiling nautilus to disable tracker integration. I am doing this in the terminal as it is easier to explain and you should be able to just copy and paste each line.
```

cd nautilus-2.20.0/debian/
gedit rules

```
This will open the rules file in the text editor, change the line that says
> 
DEB_CONFIGURE_EXTRA_FLAGS += --libexecdir=/usr/lib/nautilus
to 
> DEB_CONFIGURE_EXTRA_FLAGS += --libexecdir=/usr/lib/nautilus --disable-tracker
Close gedit and save the changes when prompted. 

**Step 3: Get the essentials**
In order to compile any software you need, among other things a compiler, fortunately installing these requirements on Ubuntu is ridiculously easy thanks to the package management system used.
```

sudo apt-get install devscripts build-essential

```
Alternately you can simply click the links below, which takes advantage of the apt:// protocol handler to install software, unfortunately it doesn't work for source or build-dep
[apt://devscripts]("apt://devscripts")
[apt://build-essential]("apt://build-essential")

As well as these generic packages nautilus also requires some additional libraries, those who have compiled from source may know that working out exactly what libraries are required can be a pain, once again apt-get to the rescue.
```

sudo apt-get build-dep nautilus

```

**Step 4: Build it and they will...search**
We now have everything we need to compile or custom de-trackerised nautilus. We will need to change directory back into nautilus-2.20.0, thats what the first command does, the second is some super-cool voodoo magic that takes a bunch of text files (thats all source code is after all) and converts them to installable deb packages. 
```

cd ..
sudo debuild -us -uc

```
This magic may take a while to happen depending on how fast your computer is but once it is done you should end up with some deb packages on your desktop. 
> 
libnautilus-extension1_2.20.0-0ubuntu7.1_i386.deb
libnautilus-extension-dev_2.20.0-0ubuntu7.1_i386.deb
nautilus_2.20.0-0ubuntu7.1_i386.deb
nautilus-data_2.20.0-0ubuntu7.1_all.deb
nautilus-dbg_2.20.0-0ubuntu7.1_i386.deb

You can install these easily using dpkg...apt-gets older brother. 
```

cd ..
sudo dpkg -i nautilus*.deb libnautilus*.deb

```

**Step 5: Cross your fingers**
Congratulations you have just compiled and installed a new version of nautilus without tracker integration, now its time to test out your shiny new file manager. To do that we need to quit the current instance, so once again in the terminal:
```

nautilus -q

```
Nautilus will quit and you will be left with an empty desktop...don't panic just breathe... to start nautilus again simply go to places and open your home directory (or anything else) and after a short delay nautilus will start again. (Note: alternately you can restart nautilus by pressing Alt+F2 to bring up the Run Application dialog where you can enter nautilus and click run.)

If all has gone well you can now press the Search button on the toolbar or hit Ctrl+F and search for files the old fashioned way, search will not only work if you don't have tracker but will return results based on the directory you searched in. At this point I cried with joy, feel free to do the same! You can now go ahead and delete the files on your desktop created during this process, I personally kept the debs but you don't have to. For reference here is a complete list of files created during the process.

> libnautilus-extension1_2.20.0-0ubuntu7.1_i386.deb
libnautilus-extension-dev_2.20.0-0ubuntu7.1_i386.deb
nautilus-2.20.0
nautilus_2.20.0-0ubuntu7.1.diff.gz
nautilus_2.20.0-0ubuntu7.1.dsc
nautilus_2.20.0-0ubuntu7.1_i386.build
nautilus_2.20.0-0ubuntu7.1_i386.deb
nautilus_2.20.0.orig.tar.gz
nautilus-data_2.20.0-0ubuntu7.1_all.deb
nautilus-dbg_2.20.0-0ubuntu7.1_i386.deb

**Step 6: Why would I need a step 6 you say?**
Well if everything worked out for you and you are enjoying your tracker free file searching then you don't this step is for all those mind changeras out there who want a big Ctrl+Z(aka undo). So what do you do if you decide you want to rejoin the dark side, you open the terminal and do this:
```
sudo apt-get install --reinstall nautilus nautilus-data nautilus-dbg libnautilus-extension1 libnautilus-extension-dev
```
This command will download and install the packages from the ubuntu repositories which are of course compiled with tracker support. You will then need to restart nautilus as documented in Step 5.

[B]
Step 7: Just kidding...enjoy your new nautilus![/B]
And of course feel free to leave comments/suggestions/thanks.

---

### Post by ShodanjoDM on 2008-03-16
I wonder, could the search function in Nautilus integrated with slocate?

---

### Post by ryanhaigh on 2008-03-16
ShodanjoDM I am not sure if that would be any better a solution than tracker currently is. From my breif read of the manual page for slocate it seems you would still need to have your files indexed. This may work for local files but will have the same pitfalls as tracker for removable media and network shares and of course you have the overhead of indexing.

In my opinion what is needed is the ability to choose the backend used for a search, searches within the areas indexed should use tracker and searches outside those areas fall back to the builtin search. You should also be able to choose the backend on either a per-search basis or permanently. For those like myself indexing is an uneccessary use of resources, and can be crippling on older machines. I have used the indexed search on Vista at work and while I find it useful in that environment it has often failed to find newly created files. Perhaps a hybrid search with indexed results appearing first and normal results that are not in the indexed results added as they are found. There are of course many other ways indexed search could be integrated this is however beyond the scope of my abilities and this howto.

---

### Post by ShodanjoDM on 2008-03-16
Understood, and thanks for explaining.

I've been using slocate for few months now and I like the way it works. I may be mistaken though, but file indexing must/can be triggered manually - just the way I like it.

Agree about the ability to choose the backend.

---

### Post by pt123 on 2008-03-16
Thanks Ryan, even if you are a Queenslander.;)

---

### Post by nemoinis on 2008-03-22
Works great - good to have a no-nonsense search back.
Thanks, Ryan.

---

### Post by ryanhaigh on 2008-04-12
You may have noticed that there are new nautilus packages available (I have all repos enabled so maybe not for some of you), I haven't bothered upgrading to the new version so that I don't have to redo the compile but it should still be the same procedure. It may be a good idea to change the version number of the packages if you don't want to upgrade but I don't know how to do this yet for the moment I have just locked the version in synaptic.

---

### Post by drs305 on 2008-04-12
ryanhaigh,

I have to admit I got a bit nervous as I watched about 3 minutes of stuff scroll across a full-screen terminal. But in the end it worked well. :)

One question: do I need to lock anything in synaptic to prevent a newer version of nautilus from undoing your script?

Thanks for your efforts.

---

### Post by imtheguru on 2008-04-13
This is a good intentioned thread, but it is quite unnecessary to recompile nautilus from scratch.

Simply disable Tracker and pull Beagle from the repositories. Give Beagle an hour or so to index your data and then proceed to use the search button in Nautilus, or the Beagle search tool (keybinding F12).

Edit: Catfish (package from repo) provides a gui for searching with 'find', '(s)locate' and Beagle.

Cheers.

---

### Post by ryanhaigh on 2008-04-13
I can't attest to the functionality of beagle search integration with nautilus as for me the reason that I initially had to investigate this issue is that I had removed tracker and nautilus search wasn't working. I keep track of my files with an organised heirachy of directories and neither needed or wanted my files being indexed. This remains true and is the reason why beagle is no better an alternative for my own needs than tracker was. That said if this solution allows searching outside the areas of the filesystem currently indexed it could be worth investigating for those who would prefer indexed search.

---

### Post by imtheguru on 2008-04-13
> **ryanhaigh said:**
> I keep track of my files with an organised heirachy of directories and neither needed or wanted my files being indexed. This remains true and is the reason why beagle is no better an alternative for my own needs than tracker was. That said _if this solution allows searching outside the areas of the filesystem currently indexed_ it could be worth investigating for those who would prefer indexed search.It does not. And this is a great feature of Beagle and other indexing tools. Some directories may contain sensitive information, system data, or just be completely irrelevant to items entered by the user.

Full disk searches have their uses and can be accomplished with 'find' and 'slocate'. Catfish can provide users with a functional GUI to search using 'find' and 'slocate'.

You've posted a good set of instructions, i'm just pointing out that there's a reliable replacement for tracker.

Cheers.

---

### Post by ryanhaigh on 2008-04-13
The idea that not everything should be indexed is quite valid which is why I believe a hybrid approach is needed as mentioned above. Unfortunately we are not yet at this stage. 

At the moment using the integrated search while browsing a removable drive/cd/network share that isn't indexed will return results from your home directory (and anywhere else indexed). Returning search results independant of the directory where the search takes place just does not make sense which is why the normal search mechanism will be used in hardy (last I checked anyway). 

Until the developers of nautilus address this issue I think it would be better to have a separate search mechanism for tracker(deskbar)/beagle(beagle has its own I believe) etc. rather than forcing 'normal' directory dependant searches to be carried out outside the file manager.

Thanks for the positive feedback regarding the howto.

---

### Post by bigbrovar on 2008-05-01
thanks dude ... just downgraded from hardy and was looking for sumtin that would fix the broken nautilus search function that works fine in hardy .. goodle broght me to u .. i tried ur guide and it worked like a charm .. open source rock.. :guitar:

---

### Post by gsiliceo on 2008-05-03
Will i get wildcard support with the nautilus integrated search recompiling it?
ie: *coldplay*.mp3

---

### Post by ryanhaigh on 2008-05-03
> **gsiliceo said:**
> Will i get wildcard support with the nautilus integrated search recompiling it?
ie: *coldplay*.mp3


I just did a quick test and it looks like nautilus interprets the wildcard characters literally. That said if you just use spaces instead the search will return the desired results. For example I have a directory of mp3 files with names 10 Years - title.mp3, searching for the following brings up all the files. The last shows that the search is case insensitive.

Searches:
10 mp3
Years mp3
years mp3

10* - no results


Hope this helps

---

### Post by gsiliceo on 2008-05-03
It does, thank you i will recompile it right now.

---

### Post by alecz20 on 2008-07-20
Well, thanks for the HOWTO. It fixes the Search function 80%.

Things the Search function still can't do:

Search for *.extension, for example Search for *.avi returns nothing.
Serch for *whatever, for example search for *cat should return catwoman.avi
Searching for cat does that.

I suppose these are not related to the Tracker thing but searching via Places->Search for files works 100%

One more thing, after restarting I got the update notice to update nautilus, what's this about?

Thanks again!

EDIT: One more thing my desktop is empty and i can't even do Right-click, how do I get it back how it was?

EDIT2: NVM, the desktop stuff appeared after a few minutes...

---

### Post by ryanhaigh on 2008-07-20
I'm pretty sure the wildcard issue is another bug separate to this one but as ou point out searching without it returns the desired result.

Regarding the update notice, I don't know what causes this as you are obviously compiling the same version as what is in the repos (thats where you got the source after all). What I do is lock the version in the synaptic package manager and it no longer bugs me.

---

### Post by alecz20 on 2008-07-21
For some reason, locking the version does not help.
It is locked, but it still bugs me every time I log in.

---

### Post by ryanhaigh on 2008-07-21
Ahh sorry forgot about the update manager as I don't use it myself. Not sure how you would avoid the notifications, perhaps if you lock the package using apt/dpkg (haven't done this for some time so can't help sorry). The other thing you could do is figure out how to change the version of the compiled nautilus. I'll ask on IRC for a way to do this as I am not on my ubuntu machine at the moment to try it myself.

---

