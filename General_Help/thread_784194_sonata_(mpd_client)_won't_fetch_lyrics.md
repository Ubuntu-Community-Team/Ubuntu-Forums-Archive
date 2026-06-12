---
title: "sonata (mpd client) won't fetch lyrics"
date: 2008-05-06
forum: General Help
---

### Post by kaiju on 2008-05-06
in ubuntu hardy, sonata only gives a "Fetching lyrics failed" message, even though python-zsi is installed.
perhaps anyone knows what the problem might be and how to fix this?

---

### Post by Malcolm on 2008-05-09
I had the same issue. It seems that the problem is with the python-xml module, and limited to Ubuntu/Debian systems. This is not a straightforward solution, and it is just the product of my trial-and-error, so use it at your own risk. ;)

Thanks to some very helpful messages in the Sonata users mailing list archives ([https://lists.berlios.de/pipermail/sonata-users/2008-April/000626.html]("https://lists.berlios.de/pipermail/sonata-users/2008-April/000626.html")), I solved it this way: I uninstalled the Sonata version from the repositories, downloaded the Sonata source (version 1.5.1), unpacked it and modified main.py adding the line:

```
sys.path.append('/usr/lib/python%s/site-packages/oldxml' % sys.version[:3])
```

after line 30. After adding this line, that section of code should look like this:

```
import getopt, sys, gettext, os, ConfigParser, misc
import mpdhelper as mpdh
from socket import getdefaulttimeout as socketgettimeout
from socket import setdefaulttimeout as socketsettimeout
sys.path.append('/usr/lib/python%s/site-packages/oldxml' % sys.version[:3])
```

To install Sonata 1.5.1, you also need python-mpd. This doesn't seem to be in the Ubuntu repositories, or if it is, I couldn't find it. I downloaded the source from

[http://www.musicpd.org/~jat/python-mpd/]("http://www.musicpd.org/~jat/python-mpd/")

and installed it unpacking it and typing:

```
sudo python setup.py install
```

After this, I installed Sonata using the same command.

I hope this helps, let me know if you need more details.

---

### Post by DJ_Peng on 2008-08-13
I tried following Malcolm's instructions, but I ended up in dependency hell with pygtk-2.0. I just ended up installing 1.5.2 from the Debian sid repo. Is there something I'm missing, other than the ability to fetch lyrics?

---

### Post by DJ_Peng on 2008-08-18
I found something that worked for me. I found [this post]("https://lists.berlios.de/pipermail/sonata-users/2008-July/000671.html") on the sonata-users list which recommended getting [http://switch.dl.sourceforge.net/sourceforge/pywebsvcs/ZSI-2.0-py2.5.egg](http://switch.dl.sourceforge.net/sourceforge/pywebsvcs/ZSI-2.0-py2.5.egg), but it didn't work Instead I got the newer version, [http://downloads.sourceforge.net/pywebsvcs/ZSI-2.1_a1-py2.5.egg](http://downloads.sourceforge.net/pywebsvcs/ZSI-2.1_a1-py2.5.egg) and extracted it to /usr/local/lib/python2.5/site-packages. Once it was extracted I used sudo nautilus to move the ZSI folder from where it was extracted to /usr/local/lib/python2.5/site-packages. Once that was there and I fired up Sonata I was finally able to fetch lyrics without having to fight my way through dependency hell.

---

### Post by adam_kimber on 2008-08-18
> **DJ_Peng said:**
>  I was finally able to fetch lyrics .

Holy COW it works! You are a star. :guitar:

---

### Post by DJ_Peng on 2008-08-18
Heh. I simply refused to take no for an answer this time. I can be such a stubborn SOB some times. Glad it works for you too.

---

### Post by luisneto on 2008-08-19
> **DJ_Peng said:**
> I found something that worked for me. I found [this post]("https://lists.berlios.de/pipermail/sonata-users/2008-July/000671.html") on the sonata-users list which recommended getting [http://switch.dl.sourceforge.net/sourceforge/pywebsvcs/ZSI-2.0-py2.5.egg](http://switch.dl.sourceforge.net/sourceforge/pywebsvcs/ZSI-2.0-py2.5.egg), but it didn't work Instead I got the newer version, [http://downloads.sourceforge.net/pywebsvcs/ZSI-2.1_a1-py2.5.egg](http://downloads.sourceforge.net/pywebsvcs/ZSI-2.1_a1-py2.5.egg) and extracted it to /usr/local/lib/python2.5/site-packages. Once it was extracted I used sudo nautilus to move the ZSI folder from where it was extracted to /usr/local/lib/python2.5/site-packages. Once that was there and I fired up Sonata I was finally able to fetch lyrics without having to fight my way through dependency hell.

That's just what i was looking for, thank you very much:)

---

### Post by DJ_Peng on 2008-08-20
You're welcome. I ended up [blogging it]("http://nancib.wordpress.com/2008/08/18/getting-lyrics-in-sonata-under-ubuntu/") because I had a feeling others were going to need to be able to find it easily.

---

### Post by niller on 2008-10-16
Thanks a million :-D

Works here too !!

---

### Post by Czar on 2008-12-29
> **DJ_Peng said:**
> I got the newer version, [http://downloads.sourceforge.net/pywebsvcs/ZSI-2.1_a1-py2.5.egg](http://downloads.sourceforge.net/pywebsvcs/ZSI-2.1_a1-py2.5.egg) and extracted it to /usr/local/lib/python2.5/site-packages. Once it was extracted I used sudo nautilus to move the ZSI folder from where it was extracted to /usr/local/lib/python2.5/site-packages. Once that was there and I fired up Sonata I was finally able to fetch lyrics without having to fight my way through dependency hell.

@DJ_Peng `ZSI-2.1_a1-py2.5.egg` fixed the sonata lyric issue.  Thanks for the tip!

---

### Post by DJ_Peng on 2008-12-29
Glad I could help, Czar. I feel like I'm beating my head against the wall sometimes, especially with some thing I post on my blog, and it's nice to know my posts are helping people. :)

---

### Post by vanadium on 2008-12-29
I found this thread a few days ago, but I could not thank you, probably because the message is too old. I took the opportunity now ;)

---

### Post by xcesarfrancox on 2009-03-27
It may be a little late but thank you peng, this worked very well, but I have a question, I found sonata under arch, but now I can't find the edit lyrics option that was beside of the search option, and there are some lyrics that I'd like to edit, and I'm too lazy to manually open the browser and go to the wiki and edit them this way >.<

Do you know why there isn't such option (edit)?

---

### Post by mcduck on 2009-03-27
Great tip, thanks.

By the way, assuming you are running Intrepid, you don't need to bother with compiling new Sonata versions or anything. Just install the version from repositories and then edit /usr/share/pyshared/sonata/main.py ;)

---

### Post by InspirationDate on 2009-04-17
Thanks DJ_Peng!  I wanted to post on your blog post but comments are disabled.

---

### Post by DJ_Peng on 2009-04-18
No problem, Inspiration_Date. The only reason I had closed the comments on it was because the post was so old and I was trying to steer comments to the newer posts. I'll see about reenabling them but I have a bit of things to do before I can really do that.

[I]ETA: It turns out my sister closed the comments on that post because of all the spam it was attracting. (It's her blog, I just write the tech posts for it.) On closer examination it turns out the comments were automatically closed because the post was over 90 days old. She disabled that setting so comments are now reopened. Thanks for pointing out that we needed to reopen the comments on that post. It is one of the more popular posts on our blog.
[/I]

---

### Post by stargazer3 on 2011-04-20
[INDENT]hi everybody!

I'm using sonata 1.6.2.1 on Ubuntu 11.04 Natty Narwal, have python-zsi installed, and tried both
[http://downloads.sourceforge.net/pywebsvcs/ZSI-2.1_a1-py2.5.egg](http://downloads.sourceforge.net/pywebsvcs/ZSI-2.1_a1-py2.5.egg)
[http://switch.dl.sourceforge.net/sourceforge/pywebsvcs/ZSI-2.0-py2.5.egg](http://switch.dl.sourceforge.net/sourceforge/pywebsvcs/ZSI-2.0-py2.5.egg)
solutions in a way described earlier, but I'm still getting the "lyrics fetcing failed" error every time!

I'm so frustrated. I sovled the problem some other distro (hm, could even be Ubuntu) several years ago, but this time - no luck.

edit: and hey, I know that it's bad to be such a necromancer (it's been over two years sine the last post), but I think this thread is really good, so I didn't want to start a new one; after all, it's my first post, cut me some slack:P
[/INDENT]

---

### Post by furiat on 2011-05-04
Hi @stargazer,

I have red somewhere that the website from which Sonata fetched lyrics, has changed. Maybe you can check that. I am sorry I can't provide any links, but I have no idea where did I come across this information.

If I will find more I will let you know.

---

### Post by vmsda on 2011-09-03
> **stargazer3 said:**
> [indent]... But i'm still getting the "lyrics fetcing failed" error every time! ... I'm so frustrated ...
[/indent]

+ 1 :(

---

