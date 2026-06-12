---
title: "Need help with the following..."
date: 2007-10-05
forum: General Help
---

### Post by Punk Boi 8 on 2007-10-05
Hello. I am looking for some help for the following.

[LIST=1]
[*]How do I compile the source for GtkPod
[*]Ditto Above - But for Amarok
[*]How do I enable MP3 playback and the like
[/LIST]

I am using Xubuntu Feisty Fawn, and the computer it is on does not have a Internet Connection. Thanks.

---

### Post by tgalati4 on 2007-10-05
You're going to need an internet connection to grab the necessary packages.  I don't know how you would do it otherwise since Ubuntu is distributed as a piecemeal system.

When you do get a connection:

>sudo apt-get build-essential

Then download the latest gtkpod from:

[http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=66245&release_id=519243](http://sourceforge.net/project/showfiles.php?group_id=67873&package_id=66245&release_id=519243)

Uncompress it and run the configuration and make in the gtkpod directory:

>./configure
>make
>sudo make install

Amarok follows a similar path.

Although you may be happy with:

>sudo apt-get install amarok

For the mp3 codecs you need to install the restricted gstreamer codecs.  Do a search in Synaptic for gstream and click away.  Be sure to enable the extra repositories so that the latest gstreamer shows up (version 0.10.0 I think)

Without an internet connection, it's a challenge to get these packages since they are constantly changing and are not packaged in a convenient way.

There may be an Ubuntu DVD available.  You will have to search around.

---

