---
title: "Cloud Software"
date: 2014-02-08
forum: General Help
---

### Post by ron177 on 2014-02-08
I wonder if there's a good cloud software other than Dropbox and Ubuntu One that can be used for Ubuntu users. Has there been any attempt to make Google Drive and Amazon Cloud accessible to Linux users for example? Thanks much.

R

---

### Post by TheFu on 2014-02-09
You can run your own cloud with a few of them.
* owncloud (meh)
* rsync over ssh - what I use.
* tonido, pogoplug, etc. (and a few similar tiny disk+NAS devices), but these require you to **trust a 3rd party.**

[http://www.reddit.com/r/linux/comments/1fzod1/linux_compatiable_cloud_storage_vendors_lets/](http://www.reddit.com/r/linux/comments/1fzod1/linux_compatiable_cloud_storage_vendors_lets/) ists services, if you want to put **your data** on** someone else's computer.**  **SpiderOak** has a good reputation at my LUG. I've never used any of these ... well, I had to use sugarsync for a year because my boss did, but they didn't have a Linux client and didn't plan to.

I've played with ownCloud, but not since last July. [http://blog.jdpfu.com/2013/07/01/owncloud-anyone](http://blog.jdpfu.com/2013/07/01/owncloud-anyone)  Looks like a personal issue based on many other people finding it to work fine.  Both myself and a buddy tried and found too many issues to continue.

I've been using **rsync over ssh** for 15+ yrs. It works and can be automated.  I use this for my password manager data files, but not much else.

RMS is famous for many statements over the years.  This is one I like the most - > Cloud Computing is Careless Computing. [http://www.theguardian.com/technology/2008/sep/29/cloud.computing.richard.stallman](http://www.theguardian.com/technology/2008/sep/29/cloud.computing.richard.stallman)

---

### Post by buzzingrobot on 2014-02-09
Google Drive is accessible via Google's site but I believe they have not released a Linux app.

Don't know about Amazon.

Build-it-yourself toolsets like OwnCloud are not especially user-friendly and require access to a server.

Upload speed is often a limiting factor using cloud services as full-scale backup resources. Doing an initial backup of a typical system can takes days, if not weeks.  It might be less tedious and, in the long run, no more expensive, to buy a portable external drive. Or two, and arrange to keep the second one in a different location. (Lest your only backup drive melt when your house burns down.)

---

### Post by Gordonbp531 on 2014-02-09
I use Wuala. It's encrypted, which none of the third-party suggestions are. (The password never leaves your computer, so Wuala staff don't know it, and can't find it)
Anf if you're from Europe, it's a European company!

[https://www.wuala.com/](https://www.wuala.com/)

---

### Post by Habitual on 2014-02-09
> **ron177 said:**
> Has there been any attempt to make Google Drive and Amazon Cloud accessible to Linux users for example? Thanks much.

RThere's a plethora of Amazon clients available to Linux users:

[http://www.dragondisk.com/download-amazon-s3-client-google-cloud-storage-client.html](http://www.dragondisk.com/download-amazon-s3-client-google-cloud-storage-client.html) and [http://www.s3fox.net/](http://www.s3fox.net/) for starters.
Both manage S3 "buckets" and their contents pretty well.

Security (encrypt contents+password) should be done *on your end* before uploading.

---

