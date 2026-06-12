---
title: "Firefox 3.0 Broken"
date: 2008-06-27
forum: General Help
---

### Post by gwinston99 on 2008-06-27
I am running Kubuntu Hardy Heron.  Recently Firefox 3.0 started behaving strangely.  When I start it it takes forever to open, and then freezes completely.  I am able to run as root ("sudo firefox").

I have tried the following:

sudo chmod -R 777 /home/gregg

I have also uninstalled firefox, deleted the ~/.mozilla directory to delete the profile, deleted /usr/lib/firefox /usr/lib/firefox-3.0 and /usr/lib/firefox-addons,  and then reinstalled.

None of this has helped or had any effect that I can see.

The problem started after I installed citadel server (which seems to be running OK).  Nothing else on my system is messed up.

Please help.

Thanks in advance,

Gregg

---

### Post by firsttimeuser on 2008-06-27
Do you mean when run as root, FF does not have this issue?

> **gwinston99 said:**
>  I am able to run as root ("sudo firefox").



---

### Post by Daddyo-613 on 2008-06-27
I had a similar problem when I upgraded from firefox 2.0.0.14 to 3.0 this thread might be helpful to you.

[http://ubuntuforums.org/showthread.php?t=835626]("http://ubuntuforums.org/showthread.php?t=835626")

I hope it helps.

---

### Post by gwinston99 on 2008-06-27
That's right.  If I run firefox as root, it works fine.

Gregg

---

### Post by jimv on 2008-06-27
> **gwinston99 said:**
> That's right.  If I run firefox as root, it works fine.

Gregg

Then the obvious answer is that it just doesn't like you.  The reason it works when you use root is because it doesn't know it's really you.

Maybe if you buy it some flowers or write a poem...

---

### Post by gwinston99 on 2008-06-27
Daddyo-613 - tried your suggestion - still no joy :confused:

I'll try the flowers, but somehow I don't think this will help!

---

### Post by firsttimeuser on 2008-06-27
so do you get anything when runing it using command line?

---

### Post by gwinston99 on 2008-06-27
> **firsttimeuser said:**
> so do you get anything when runing it using command line?

Nothing in the terminal.  After a VERY long time it may open and then hang.

When I run as root, it opens right up, as expected.

Gregg

---

### Post by firsttimeuser on 2008-06-27
I had this issue before (but I did not test running it as root), it took about 1 minute to load and after that most probably it just hang there with very slow response to mouse click. And later I did some modification with my /etc/hosts, /etc/resolv.conf and /etc/network/interfaces, and then the issue cleared. 

So you might want to check these 3 files?

> **gwinston99 said:**
> Nothing in the terminal.  After a VERY long time it may open and then hang.

When I run as root, it opens right up, as expected.

Gregg

---

### Post by jimv on 2008-06-27
What if, just for kicks, you create a new user, log in as that user, and try firefox?  If it's fast, it's something odd in your profile.

---

### Post by Daddyo-613 on 2008-06-28
If you pay particular attention to page 2 of the link I provided above you may yet find a solution. In efforts to solve my problem I backed up several times and used the purge commands. Eventually I overwrote the directory that contained the files that were incompatible with Firefox 3.0. It may be a bit long winded but I have set out the steps I followed. If it helps you great. If not...it was worth a shot.

What I believe happened in the end was that I overwote my backup files with files from a clean install. What I discovered was that some versions of plugins that I used in 2.0.0.14 were not compatible with 3.0. In particular "adblock plus". There is an updated version that does work with 3.0 but the old plugins were not removed in the install of 3.0.

Here is the sequence used in my original effort to install:

```
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

As you can see the plugins were preserved.

I tried uninstalling firefox using the Synaptic Package Manager and I tried using the purge command for firefox 2.0 and 3.0 and tried to reinstall the package a couple of times to test it. No joy. 

But, with the help of friends in the forum I was able to generate this error message:

```
~$ ls /usr/bin/firefox -l
lrwxrwxrwx 1 root root 20 2008-04-18 13:39 /usr/bin/firefox -> /opt/firefox/firefox

~$ ls /opt/firefox/plugins -l
lrwxrwxrwx 1 root root 24 2008-06-20 15:10 /opt/firefox/plugins -> /usr/lib/firefox/plugins

~$ mv ~/.mozilla ~/.mozilla.notworking
~$ /opt/firefox/firefox &
[1] 6236
~$ (crashreporter:6262): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(crashreporter:6288): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

[1]+  Exit 1                  /opt/firefox/firefox
```

Note the different locations of the plugins.

I then went back to basics and removed firefox using the following code:

```
sudo rm /usr/bin/firefox
sudo dpkg-divert --rename --remove /usr/bin/firefox
sudo rm -r /opt/firefox
```

As you can see, the directories containing the plugins were removed. I then went to the directory containing the tar I had downloaded and reinstalled as follows:

```
sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt
rm firefox-3.0.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

and peace was returned to the land.

Your issue may not be with that particular plugin but it should give you something to try. Good luck and good hunting.

---

