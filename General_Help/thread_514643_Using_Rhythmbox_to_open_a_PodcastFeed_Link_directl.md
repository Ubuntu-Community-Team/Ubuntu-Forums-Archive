---
title: "Using Rhythmbox to open a Podcast/Feed Link directly in Firefox"
date: 2007-08-01
forum: General Help
---

### Post by keyboardashtray on 2007-08-01
I know how to copy a podcast link and paste it into the "New Podcast Feed" in Rhythmbox.

What I'm trying to do is get the generic Podcast button (feed button) on a website to add that Podcast to Rythmbox automatically. An example of the [style of button]("http://www.npr.org/rss/podcast/podcast_detail.php?siteId=9911203") I'm looking at (left of the field under "Or, copy and paste this URL into a podcasting tool:"

The Rhythmbox documentation says "To add a new podcast feed, you can also right-click over the Podcasts source, and select New Podcast Feed." I have tried this and don't see the option.

I have also tried adding Rhythmbox from "choose application" (for feeds) in Firefox. It doesn't work, and now I can't get Rythmbox out of the list. 

Is there a way to subscribe to a Podcast automatically with Rhythmbox and Firefox? And if copy + pasting is the only way, does anyone know how I can get Rhthmbox out of the list of applications for subscribing to feeds in Firefox? (I like my menus tidy.)

---

### Post by keyboardashtray on 2007-08-01
Alternatively, where do you look in Ubuntu whenever a file, etc., gives you the option to "Open with..." and choose your application. Where is the Ubuntu equivalent to Window's Programs list?

---

### Post by r0dzilla on 2007-10-22
Post #1:
1.  Make sure rhythmbox is already running,

2.  Click on the subscription link on the web page hosting the pod cast

3.  The RSS feed for the podcast will be displayed in firefox

4.  Directly above the feed, on a yellow background, you will see firefox's subscription wizard.

5.  On the drop-down list choose "Choose Application" and click the "Subscribe Now" button

6.  The gnome file chooser will come up, navigate to /usr/bin/rhythmbox, click open.

7.  rhythmbox should immediately begin to download the latest podcast from that feed as well as headers for previous podcasts.


Post #2:
As for opening files in gnome, right-click on the file in question, select properties and click on the "Open With" tab.  You can now add applications that can open that type of file.

---

### Post by keyboardashtray on 2007-10-22
> **r0dzilla said:**
> Post #1:
1.  Make sure rhythmbox is already running,

2.  Click on the subscription link on the web page hosting the pod cast

3.  The RSS feed for the podcast will be displayed in firefox

4.  Directly above the feed, on a yellow background, you will see firefox's subscription wizard.

5.  On the drop-down list choose "Choose Application" and click the "Subscribe Now" button

6.  The gnome file chooser will come up, navigate to /usr/bin/rhythmbox, click open.

7.  rhythmbox should immediately begin to download the latest podcast from that feed as well as headers for previous podcasts.

.

Thank you r0dzilla! I'm definitely closer - I had rhythmbox-client selected before - this is actually doing something now. 
However, it is associating the podcasts with radio links.
 
> **r0dzilla said:**
> Post #2:
As for opening files in gnome, right-click on the file in question, select properties and click on the "Open With" tab.  You can now add applications that can open that type of file.

Thank you - I'm a little embarrassed by this one, it was a while ago though, so I'm sure you understand  :) I was under the impression there might be some master list GUI under some option I was missing.

---

### Post by osweetbeans on 2008-05-21
i have the same problem... when i subscribe it opens it associates it with web-radio rather than picking it up as a podcast subscription.

---

