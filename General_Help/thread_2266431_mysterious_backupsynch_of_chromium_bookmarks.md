---
title: "mysterious backup/synch of chromium bookmarks"
date: 2015-02-22
forum: General Help
---

### Post by parminides on 2015-02-22
My desktop runs chromium-browser Version 37.0.2062.120 Ubuntu 12.04 (281580) (64-bit). Today I discovered that the bookmarks are being stored and backed up to an unknown location. That is, somewhere besides ~/.config/chromium/Default/Bookmarks (and Bookmarks.bak). Wherever it is, the bookmarks are being restored/merged/synched without my knowledge or intention. I don't know if this unknown location is on my machine or in a cloud server.

As a diagnostic test, I deleted the chromium bookmarks (without chromium running):

rm ~/.config/chromium/Default/Bookmark*

Then I restarted the browser. The bookmarks bar was empty, as expected. However, within 10 seconds or so, the bookmarks had been mysteriously restored! The Bookmarks file reappeared.

This is really strange and bothersome since I'm not signed in to chromium or gmail or anything Google. This weird behavior doesn't happen with my laptop, which is running Version 40.0.2214.111 Ubuntu 14.04 (64-bit).

I discovered this problem after I copied my laptop Bookmarks file to my desktop and saw that the result was a merging of the two. This is not what I want. I also don't want my bookmarks on a cloud server.

I tried uninstalling chromium-browser, deleting ~/.config/chromium, and reinstalling. It still restores bookmarks as described above, even though I never sign in to chromium!

Does anyone know what's going on? Are there more files on my computer besides Bookmarks and Bookmarks.bak that store chromium bookmarks. How I can stop this behavior?

---

### Post by parminides on 2015-02-22
This screenshot confirms that I'm not signed in to Chromium. It also indicates that nothing has been saved to the Chrome Cloud servers. What's going on?

---

### Post by parminides on 2015-02-23
I suspect that bookmark information is stored in another settings file on my desktop, and the bookmarks are automatically restored after the browser sees that they're missing.

Where are these restored bookmarks are coming from? This issue is important to me because I synch all my files between computers (not only browser bookmarks) over a local network. This strange bookmark behavior is merging different versions of the bookmarks and messing things up.

Does anyone know if I need to delete something else besides Bookmarks and Bookmarks.bak to get rid of the bookmarks?

---

### Post by parminides on 2015-02-24
I believe I understand what's happening with my chromium bookmarks. I'm running version 37.0.2062.120 on an old desktop. Back in those days the bookmarks were apparently also stored in a database on the computer, namely, ~/.config/chromium/Default/Sync Data Backup/SyncData.sqlite3. There's also a journal file in that directory.

It's unclear to me whether my bookmarks are also stored on a cloud server somewhere. I sure would like to know.

Anyway, when I deleted the Bookmarks file, the database would restore the bookmarks after starting chromium. Actually, what it does is to merge the database bookmarks with the ones from to Bookmarks file.

My original interest was sync'ing chromium bookmarks (and my other files) across my local network using rsync. My laptop has a later version of chromium in which the sqlite feature is apparently gone.

In case someone's interested in such a project for themselves, here's how I got around the bookmarks issue:

In computer 1 (the computer whose chromium uses the sqlite backup feature)...

1. Use chromium's bookmark manager to backup the bookmarks to an html file.
2. Remove all bookmarks with the bookmarks manager. (This will remove the bookmarks from the sqlite3 database.)

3. Copy .config/chromium/Default/Sync Data Backup directory to computer 2 (the machine whose chromium doesn't use sqlite). This directory contains the database with no bookmarks. 

In computer 2...

4. mv ~/.config/chromium/Default/Sync\ Data\ Backup ~/.config/chromium/Default/nulldatabase
(This is because new chromium versions will delete a directory named "Sync Data Backup.")
5. When it's time to rsync from computer 2 to computer 1, rsync the unchanged database files from computer 2 to computer 1. But direct them to the Sync Data Backup directory on computer 1. This will put the empty bookmark database back on computer 1. This is the key.
6. Also rsync the Bookmarks file from machine 2 to 1.

When you run chromium from machine 1, it will load bookmarks from the Bookmarks file. Since the database is empty and it merges with the other bookmarks, it won't have any effect.

You might think the database is already empty on computer 1, but that's only true at the beginning of this process. In general, it's full of bookmarks. This procedure resets it back to empty whenever another computer rsyncs to it.

---

### Post by parminides on 2015-02-25
Just for fun I installed Chrome as per [http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/](http://www.howopensource.com/2011/10/install-google-chrome-in-ubuntu-11-10-11-04-10-10-10-04/). This yielded version 40.0.2214.115-1.

There's no problem with Chrome at all: no Sync Data Backup folder, deleted bookmarks don't reappear. Everything seems fine.

At some point Ubuntu quit maintaining/updating chromium for Ubuntu 12.04 (which is what my desktop runs). So it's stuck with this old version with the sqlite feature. I don't have this issue with my laptop running chromium (Version 40.0.2214.111 Ubuntu 14.04).

I've decided to run Chrome on my desktop and chromium on my laptop. I find that preferable to repeatedly copying the null sqlite database to my desktop.

So far the bookmarks are rsync'ing back and forth between Chrome and chromium without any glitches. Thanks again for your attention and help.

---

### Post by parminides on 2015-02-26
Cloudbacko Pro isn't the answer for me because I don't want my bookmarks stored on a cloud server. (Otherwise I'd just use the Chrome/Chromium feature.) That's why I sync bookmarks over my local network at home.

---

