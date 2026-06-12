---
title: "OpenOffice is very slow"
date: 2008-06-08
forum: General Help
---

### Post by Jiawen on 2008-06-08
I'm trying to edit a book I'm working on in OpenOffice Writer, but it's getting very difficult. Just sitting minimized, not on the active desktop, OO is using about 40-60% of CPU time. When I try to actually work in Writer,  typing is slow, scrolling is slow, it registers mouse location incorrectly (click on a location and it'll only finally jump to the correct spot a half-second later, which is infuriating for doing any real work) and it's generally driving me up a wall. 

Is there anything to be done? How do people work with even bigger books in OO? I suppose they only use top-spec computers for that. :(

---

### Post by mac9416 on 2008-06-08
I would ditch xubuntu. It has always been slower for me than ubuntu, even on an EXTREMELY slow box.

---

### Post by Sef on 2008-06-08
1)What *buntu and version are you running? 

2) What are your system specs?

---

### Post by Jiawen on 2008-06-09
> **mac9416 said:**
> I would ditch xubuntu. It has always been slower for me than ubuntu, even on an EXTREMELY slow box.That is not a helpful suggestion. There are many other problems with Gnome-Ubuntu for me; Xubuntu is quite superior for my purposes.
> **Sef said:**
> 1)What *buntu and version are you running? 

2) What are your system specs?I'm running Xubuntu 7.10. My system is a 1.8 GHz with 2 GB RAM. Is that what you needed to know?

---

### Post by Sef on 2008-06-09
If you have broadband, then follow this tutorial from [Zolved]("http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu") to get OOo to run faster.

It does make OOo run much faster for me.

> I'm running Xubuntu 7.10. My system is a 1.8 GHz with 2 GB RAM. Is that what you needed to know?

Yes, thank you.  Xubuntu should work without any problems on your system.

> mac9416: I would ditch xubuntu. It has always been slower for me than ubuntu, even on an EXTREMELY slow box.

Please get the facts before posting comments that turn out to be irrelevant at best.

---

### Post by Jiawen on 2008-06-11
> **Sef said:**
> If you have broadband, then follow this tutorial from [Zolved]("http://www.zolved.com/synapse/view_content/28209/How_to_make_OpenOffice_run_faster_in_Ubuntu") to get OOo to run faster.

It does make OOo run much faster for me.I've tried turning off the JRE before and had some kind of problems. (Perhaps related to the [GTK theme crashing bug]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/131526"), though I don't remember specifically what it was, now.) I hadn't tried those other options; I'll see how it runs. From a first impression, it certainly seems faster with those settings, but it's still dragging my system as a whole, and still taking 40-50% of CPU time even when idle. So, an improvement, but still not great.
> Yes, thank you.  Xubuntu should work without any problems on your system.You'd think so, wouldn't you? :)

---

### Post by rkh on 2008-06-16
Is Track Changes turned on? A known bug (too lazy to look it up for you at the moment) can cause OO.o to eat up large amounts of CPU resources when this feature is turned on. The OO.o bug people have said that it should be fixed in the next version, which should be out by August-ish.

If this is the issue, you could either try the beta version or do without the feature until the new version comes out.

---

### Post by yaknowwat on 2008-06-16
[http://download.openoffice.org/3.0beta/](http://download.openoffice.org/3.0beta/)

there is a deb for openoffice 3.0 beta which works pretty nicely sadly no quickstart tray available for openoffice 3 that is the only reason i haven't set it up natively.

---

### Post by snowpine on 2008-06-16
> **Jiawen said:**
> I'm trying to edit a book I'm working on in OpenOffice Writer, but it's getting very difficult. Just sitting minimized, not on the active desktop, OO is using about 40-60% of CPU time. When I try to actually work in Writer,  typing is slow, scrolling is slow, it registers mouse location incorrectly (click on a location and it'll only finally jump to the correct spot a half-second later, which is infuriating for doing any real work) and it's generally driving me up a wall. 

Is there anything to be done? How do people work with even bigger books in OO? I suppose they only use top-spec computers for that. :(

Hi Jiawen,

You did not mention whether your book is text-only at this stage, or if you have a lot of graphics embedded. 

I work in publishing, and we split all of our books into 10-page files once we graduate from text file to layout stage. The few times I've had to work with a larger document, it is painfully slow! This is not using OpenOffice (we use Adobe Indesign on Windows) but it is a good general tip based on my experience. Our books have lots and lots of graphics, so it is essential to split them into "chunks".

Another tip (assuming you don't have fancy graphics or formatting) is to try a lighter-resource editor such as Abiword. 

The other posters made some good suggestions, too. Good luck! ps I might have some more tips for you if you let us know how many pages your book is (so far) and whether or not it has illustrations.

---

