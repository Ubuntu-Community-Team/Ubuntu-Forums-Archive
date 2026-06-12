---
title: "Dropbox changing case and visibility"
date: 2017-12-15
forum: General Help
---

### Post by xadder on 2017-12-15
I had a disturbing problem with Dropbox the last 2 days. Yesterday I did a lot of work in a Dropbox folder on my home notebook (that I have been using since 2015, many times). When I logged onto my office PC this morning, that work was not there!

In both cases I have Dropbox mounted in my filesystems using standard Xubuntu-installs. And it has worked flawlessly for years.

If I used the web-service, I can actually see yesterday's work and files, so I downloaded as a .zip. Unpacking that I found the directory PAPER2017_work as expected, but also paper2017_work. This second folder had my files! 

So, somehow Dropbox has started a 2nd folder where these new files were placed, but this is not visible to me as a file-system. The web-system which has the new files also just shows one folder, so it is a mixture of the original upper-case folder and the new lower-case.

Argh! Anything I can do to fix this and/or stop it happening?

(My system is Xubuntu 17.10)

---

### Post by Kirk Schnable on 2017-12-17
That is very odd, are you seeing the lowercase folder on the original filesystem of the computer where you last edited the files?  If it's disappeared there as well, I would think it's most likely some kind of bug in the sync client.

What I'm getting at here is, when syncing to another computer, I could understand Dropbox ignoring two folders with different casing when pushing it to another computer, in some cases.  I believe Windows systems have some issues with case insensitivity in this case, and some Windows programs might regard those two folders as the same folder.

If you've somehow created this situation on your Linux system, and then it didn't sync properly over to other computers, I would just use the web client to fix situation.  Create a third folder on the web with a totally different name, and move the stuff there, then delete the two original folders.

If you do not know how this situation occurred, it could be a bug in the Dropbox sync client, and in that case Dropbox support might be of more assistance than us here on the forum.  [https://www.dropbox.com/support](https://www.dropbox.com/support)

---

### Post by xadder on 2017-12-18
Hi!
I only see the lowercase version when I download a zip file from a web interface. Briefly, what happened is (with dummy names):

* Year 2015, set up folder Dropbox/AAAA - worked fine until this week from all machines
* Home notebook (Xubuntu 17.10): Dec 13 - created files in AAAA
* Office PC (also Xubuntu 17.10): Dec 14 - tried to find files in AAAA. Not there.
* A collaborator in this directory who uses the web interface could see the files though, so I used the web interface, downloaded, and found AAAA and aaaa, with my Dec 13 files in aaaa. This collaborator uses Windows to upload and download, so maybe there is a clue there, but the basic AAAA directory was created by me from linux.
* Today (Dec 18), using my home notebook, I can see the same files in AAAA just as I created then. Again, no sign of aaaa until unzipping from the web.

I can try fixing as you suggest, and will ask the dropbox support, but this behaviour was disturbing (I thought I had lost files!).

---

### Post by Kirk Schnable on 2017-12-18
I feel like I've seen this behavior before back when I frequently used Dropbox, but I fixed it on the web UI and never had the time to look into it beyond that.  It's probably a bug in their sync client, since I've encountered similar behavior before.

These days I self-host with NextCloud so I haven't used Dropbox too much.

---

