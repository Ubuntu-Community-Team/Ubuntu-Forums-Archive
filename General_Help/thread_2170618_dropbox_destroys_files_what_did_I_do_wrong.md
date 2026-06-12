---
title: "dropbox destroys files: what did I do wrong?"
date: 2013-08-26
forum: General Help
---

### Post by dgermann on 2013-08-26
Friends--

A saga in which our protagonist (me) loses thousands of files and has no clue what he did wrong, and hopes someone in this realm can point out to him the quicksand so he does not step in it again....

Have used dropbox for 2 years or more in a production environment, with ne'er a lost file.

Recently I got the bright idea to use it to back up much of my data files. Desktop (D) box is connected via cifs to Ever at the Ready server (E) for data files. D is connected to Web and to dropbox. Not wanting to duplicate all E's files on D, I did ln -s /path/to/server's/data/files in my ~Dropbox directory. 

A week or so later someone sharing files via a private dropbox folder said they did not see the newest files in our shared dropbox folder. Then another person did not see some other new files in a different shared dropbox folder. I checked it out: the files were in my local dropbox folder, but not in the ones on dropbox.com.

Suspecting the dragon in the woods to be the huge numbers of files from my server (clogging the pipeline to Dropbox.com), I rm the directory from my ~Dropbox folder. Now the missing files appeared on Dropbox.com and in my correspondents' respective folders.

All was well, I thought.

Alas, it was not to be: whole bunches of my data files had disappeared from my server! Not every file in every directory; not every file dated before or after a certain date. Sometimes whole directories, sometimes just a few files here and there. Not any particular file type.

Luckily our protagonist had lots of backups, and was able to restore everything (he thinks). Not so luckily, he used a whole weekend of very pleasant outdoor weather inside carefully restoring files!

Where did our hero go astray? Where be the dragons and quicksands of this realm which might be avoided?

---

### Post by dragonfly41 on 2013-08-27
I haven't yet come across that dragon in the woods .. I'll bear that in mind when using dropbox and probably consider using dual dropbox accounts for redundancy of important data .. but meanwhile have you read the obvious advice from dropbox site?

[https://www.dropbox.com/help/296/en](https://www.dropbox.com/help/296/en)

---

### Post by dgermann on 2013-08-27
dragonfly41--

Thanks for helping me. No I had not read that help screen, but had checked the dropbox deleted files. Was not aware of the cache, but alas and alack, that directory is empty (it is past the 3 days it says it saves things).

But recovering them from dropbox is not the question for me. The question is why were these files deleted from my server?

I would have thought that removing a soft linked directory simply removed the link, and not the whole directory. Or if it removed the directory, it should remove the whole directory, not just bits and shreds. So it seems like there might have been some interplay between the dragons in the dropbox realm and the quicksand in the linux realm....

---

### Post by Crusty Old Fart on 2013-08-27
Could it have been that instead of actually making copies of the files to Dropbox, you ended up creating links of them back to your sources? And then when you deleted the links, they were followed back to your server?
Something similar  happened on **[thread=2170392]this thread[/thread]**.

---

### Post by tgalati4 on 2013-08-27
Sounds like a problem with de-duplication.  Do you have any de-duplication scripts or services running?  Otherwise, it's possible that dropbox had a hardware drop.  After all, they are named cloud services because clouds have a way of drifting away--like dragons.

---

### Post by crazymonkey05 on 2013-08-27
i always use ubuntu one for cloud storage or google drive as they have never failed me....and plus my school uses google to store all our assignments on and they never have problems.....although i wish they did :-P

---

### Post by dragonfly41 on 2013-08-27
Just being curious (in case I am hit by the same dragon) I searched around and found this ...

[http://konklone.com/post/dropbox-bug-can-permanently-lose-your-files](http://konklone.com/post/dropbox-bug-can-permanently-lose-your-files)

However I don't know if this is relevant.

---

### Post by Crusty Old Fart on 2013-08-27
<<< WARNING >>> Any individual who suggests that the cloud is primarily a conduit that passes data directly to NSA storage facilities will be prosecuted to the full extent of the law.

---

### Post by dgermann on 2013-08-27
Crusty--

Love your handle! Thanks for your help.

Well, that is plausible, except that it is not like your friend's experience: his was all txt files were gone and mine were files at random: some odt, some ods, some xlsx, some pdf....


tgalati4--

Have not heard of de-duplication before, so I doubt I was running anything like that. Just googled it and looked at a wikipedia article about it, and found something called opendedup which I had not heard of before. When I put dedupl and de-dupl into synaptic it comes up with two programs, neither of which I have installed. So I doubt that is the issue, although it was a good clue to check out! Thanks, tgalati4!


crazymonkey05--

I tried Ubuntu One a couple of years ago and could not get it to work well. I think that my correspondents could not easily make it work for them on Win machines. And I do not trust Google for data storage, since their user agreement says they can publish anything they find on their computers! Won't work for me! Thanks, crazymonkey05!


dragonfly41--

That's an interesting bug report. Thanks. I have gone into my dropbox deleted files and cannot see the size of the files, at least without re-downloading them to my computer, which I am skittish to do. I just clicked on a couple of files as if to open them and it does give me file sizes on the non-pdf files, and all I checked have a non-zero size.

Thanks for your help, folks!

---

### Post by tgalati4 on 2013-08-27
Modern, big-data storage systems do some scary (dragon-like) things to files.  Dedup is just one of those scary things.  If two exact copies of a file are found, one is deleted and replaced with a symbolic link--presumably saving space.  I don't know if dropbox runs dedup on their servers, but having a bunch of 0-byte files from the link above does sound like a dedup problem.  Also, the indexing of files on large storage systems give you the impression that you have your files, when you really don't.  The headers and metadata are stored separately (and on faster rate storage) than the actual data, so you really never know if there is a dragon in the cave or just its saddle.  Then there is the whole issue with RAID and its many forms that can attack data instantly.  Not unlike a pissed dragon.

---

### Post by dgermann on 2013-08-28
tgalati4--

Yes, that is scary stuff. Wow! Thanks!

---

