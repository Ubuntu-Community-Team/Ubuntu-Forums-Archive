---
title: "aptitude / apt-get"
date: 2007-02-28
forum: General Help
---

### Post by Dave / Mosaic on 2007-02-28
I'm trying to figure out:

Are there reasons for using, or not using, aptitude or apt-get, or synaptic for that matter, or others??

I've been browsing through the archives, but have not figured out the differences.  Supposedly they are not exactly compatible and you shouldn't use both??  aptitude looks like it is more capable with removing orphaned dependencies, but apt get is newer?

All opinions welcome...

---

### Post by Maestro23 on 2007-02-28
Apt-get vs. Aptitude: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by masteryurez on 2007-02-28
aptitude and apt-get is exactly the same thing. You can use whatever you want.
Synaptec is a graphical interface that you easily can install packages with. If you start synaptec you can see a lot of packages. You can install what packages you want. aptitude and apt-get is exactly the same thing as synaptec but you use aptitude/apt-get in your terminal. for example:
```
sudo apt-get install vlc
```
if you want to install vlc of cource. and if you want to remove vlc again you can simply write this:
```
sudo apt-get remove vlc
```

That's it. Try it yourselves!

Have a nice day :)

---

### Post by ~LoKe on 2007-02-28
Uh, no, apt-get and aptitude _aren't_ exactly the same.

---

### Post by musings on 2007-02-28
> **masteryurez said:**
> aptitude and apt-get is exactly the same thing. You can use whatever you want.
Synaptec is a graphical interface that you easily can install packages with. If you start synaptec you can see a lot of packages. You can install what packages you want. aptitude and apt-get is exactly the same thing as synaptec but you use aptitude/apt-get in your terminal. for example:


Hi,

aptitude and apt-get **aren't** the same thing. aptitude handles the removal of dependencies whereas apt-get doesn't. I'd suggest having a read of this link [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) mentioned in an earlier reply.

Regards, Gary

---

### Post by Dave / Mosaic on 2007-03-01
Hey, wow - thanks all...  that's exactly the sort of info I was hoping for.  That site is a good resource too.

Following up, just to clarify:

If you install a bunch of packages via apt-get (or, for example, by running the Ubuntu install CDs), and then do:

aptitude update
aptitude remove some-pakage

will all the orphaned dependencies be removed?  Or will aptitude still only remove stuff that it installed, based on some database?  (Maybe the 'update' builds that database?)

---

### Post by igknighted on 2007-03-01
Actually, apt-get will eventually get the orphaned dependencies.  After you complete the removal, you will be asked to run apt-get autoremove and it will clean it up.  This might only be an edgy thing, as I don't remember seeing it in Dapper.  I also don't know if this is as good as aptitude, but it seems to perform the same function.

update just updates the list of programs available in the repo's.  Aptitude can only take care of dependencies if installed with aptitude.  You cannot install wth apt-get and remove via aptitude and expect the orphaned deps to get cleaned up.

---

### Post by aysiu on 2007-03-01
> **igknighted said:**
> This might only be an edgy thing, as I don't remember seeing it in Dapper. You're correct. The *autoremove* option is new as of Edgy and is not available in Dapper or Breezy.

---

### Post by Nemix77 on 2007-03-01
aptitude is better than apt-get.  


so if I install a program using synaptic can I remove it with aptitude or apt-get autoremove.  

I know I can instal using apt-get or aptitude and remove from synaptic.

---

### Post by Dave / Mosaic on 2007-03-01
Okay - thanks everybody...

BTW, so far these forums have been a GREAT resource for somebody like me, coming back up to speed with Unix after over ten years of alienation in Windows world.  Before Seeing the Light of Ubuntu, I recently tried a couple of other Linux distributions (Fedora, YellowDog), and it was much harder to ever find anything out.

--dave

---

