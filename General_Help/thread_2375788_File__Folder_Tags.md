---
title: "File / Folder Tags"
date: 2017-10-27
forum: General Help
---

### Post by LHammonds on 2017-10-27
Is there anything that will allow various people to assign "tags" to files or folders (of any type) and work for multiple operating systems (Linux and Windows)?

Organizing files by folder containers can only work to a point.  We need something like tags (for lack of better word) that can help describe the contents especially if it really fits in more than one category.

A couple examples to describe the problem:

```
\Games\Strategy
\Games\RPG
\Games\Shooter
\Pictures\Family\JohnDoe\Birthday
\Pictures\Family\JaneDoe\Birthday
```

There might be strategy games that can also be categorized as Indie, Role-Playing, SinglePlayer, Multiplayer, Survival, etc.  It can be problematic to find all "survival" games if they can be found under various categories like Strategy, RPG, Shooter, etc.

Pictures can contain many people which makes it impossible to place pictures into each person's folder unless you duplicate which would be a bad thing to do.

I'd like to setup an Ubuntu file server and use OpenLDAP for authentication.  Most client devices will be Windows, iPads and such.

Once this central repository is setup, I'd like to have a mechanism in place that will allow finding items no matter the directory structure.

Having this tag/search mechanism work now and in the future through newer OS versions is a must.

Placing files on the Internet (cloud) is not a desirable option due to limited bandwidth...let alone security/privacy issues.

All suggestions welcome.

Thanks,
LHammonds

---

### Post by LHammonds on 2017-10-30
Potential solutions found so far:

1. Include the keywords in the filename.  Example:
```
file001 [LHammonds Certificate MySQL].xml
file002 [Birthday John Doe 2017].idm
file003 [Dog Cat Mouse 2016].abc
```

[LIST]
[*]Not exactly a good idea since there are limitations on filename lengths and thus the amount of keywords that can be used. 
[/LIST]


2. Include a metafile that matches the filename.  Example:
```

file001.xml
file001.xml.json
file002.idm
file002.idm.json
file003.abc
file003.abc.json

```
 
[LIST]
[*]If the file is moved, copied, renamed or deleted, there is nothing that will automatically handle the meta file which may leave it orphaned and useless. 
[/LIST]


3. Use an application with a meta database.


[LIST]
[*]This might become problematic if the application does not work on multiple systems or is not designed to work in a network environment...such as multiple people contributing and using the same database. 
[*]If the application becomes defunct, all the time spent maintaining the potentially huge database will become useless and stuck back at square one but with much time wasted. 
[/LIST]


4. Use of a cloud service like OneDrive.

 
[LIST]
[*]Files have to be stored on an external server not under your control and accessible from the Internet 
[*]Once files are no longer on your server/device, they are no longer under your control.  A security breach could render your private files public.  There are no amount of words that can be said to convince me otherwise. 
[/LIST]


NOTE: I will edit this post to update my findings as I have time to do so.

---

### Post by dragonfly41 on 2017-10-30
Currently I am using CherryTree editor as my main asset indexer.

In any node in an xml node tree I can record notes, code snippets to run, links to websites, files, folders .

Tags can be added to nodes for indexing.

I am exploring other uses of this powerful editor which can also import legacy notes from Tomboy and a host of other editors.

CherryTree is found in Ubuntu software centre.

[http://www.giuspen.com/cherrytree/](http://www.giuspen.com/cherrytree/)


[p.s.] I should add that this is for local desktop use. Next step will be to integrate with an XML database - eXist-db. Xml documents can be uploaded to server - or the eXist-db server can run locally.

[https://exist-db.org/exist/apps/dashboard/index.html](https://exist-db.org/exist/apps/dashboard/index.html)

---

### Post by LHammonds on 2017-10-30
> **dragonfly41 said:**
> Currently I am using CherryTree editor as my main asset indexer.
That looks interesting but I'm not sure my family or regular employees would be able to make good use of it....or even understand it.  ;-)

---

### Post by dragonfly41 on 2017-10-30
It's easy peasy.

---

### Post by dragonfly41 on 2017-11-02
Further notes from my own research .. since I would find tag searching to be useful ..

Assuming that users are familiar with Nautilus (or Nemo) to access folders/files then python extensions can add further options to the Nautilus (or Nemo) context menu (right click on folder/file).

We can extend our experiments by going to the site which developed CherryTree (mentioned earlier in post #3).

[http://www.giuspen.com/nautilus-pyextensions/](http://www.giuspen.com/nautilus-pyextensions/)


Download

[http://www.giuspen.com/software/nautilus-pyextensions_3.4.1-1_all.deb](http://www.giuspen.com/software/nautilus-pyextensions_3.4.1-1_all.deb)


Install with GDebi Package Installer (make sure that Synaptic window is not open which locks out GDebi).

nautilus-pyextensions_3.4.1-1_all.deb

After installation the list of installed python extensions show in ..

Applications > Accessories > Nautilus PyExtensions



Go through same process to install Nemo PyExtensions


Now the task is to create a python extension which can add searchable tags to any selected Folder/File.
 

Whether you use Nautilus or Nemo is a matter of choice. Nemo does offer a richer interface.   I have both installed for testing pyextensions.

For Nautilus PyExtensions the dependency python-nautilus needs to be installed.

For Nemo PyExtensions the dependency python-nemo is required but I could not find it in Ubuntu 16.04.

I found python-nemo here ...

[https://www.ubuntuupdates.org/package/mint_main/rosa/main/base/python-nemo](https://www.ubuntuupdates.org/package/mint_main/rosa/main/base/python-nemo)

...

I found one thread which suggests using **tracker** with Nautilus..

open terminal ...

```
sudo add-apt-repository ppa:tracker-team/tracker
sudo apt-get install tracker tracker-gui
```

Next step, launch Nautilus through ..
Applications > Accessories > Files

Navigate to any folder or file and right click.

Choose properties at bottom of context menu.
Popup window shows ...

Basic | Permissions | Local Network Share | **Tags**

Click on Tags tab.

Now you can attach a tag or multiple tags to this resource.

Next step, is to setup &#8220;tag search&#8221;.

Go to Applications > Accessories > Desktop Search
and launch.

Desktop Search can search by filename but we are interested in searching by **tags**.

Note that the top menu bar changes layout depending on your search profile.

Clear any search term which might remain in search field (from a previous search session).

Click on the second button from left with tooltip:

"Display results by files found in a list"

Click on the sixth button from left with tooltip:

&#8220;Find search criteria in **file tags** only (separated by a comma)&#8221;

In the search field type the tag or tags you wish to locate, separating multiple tags by commas.

You can see a list of registered tags by clicking on the star button with tooltip:

&#8220;Show tagging panel which allows editing tags of selected results&#8221;

After inserting one or more tags in the search criteria field hit enter button and search shows all tagged resources.

...

Experiments are continuing ... I feel that the above process might be automated further.

...

References:

[https://askubuntu.com/questions/827701/how-can-i-tag-files-and-search-them-later-based-on-the-tag](https://askubuntu.com/questions/827701/how-can-i-tag-files-and-search-them-later-based-on-the-tag)

[http://www.omgubuntu.co.uk/2017/07/tags-tab-restore-features-coming-to-nautilus](http://www.omgubuntu.co.uk/2017/07/tags-tab-restore-features-coming-to-nautilus)

---

