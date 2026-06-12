---
title: "Is there an intelligent indexing solution that is the equivalent of Grsync for backup"
date: 2014-12-20
forum: General Help
---

### Post by YQ002lc2 on 2014-12-20
I've tried different indexing solutions in synaptic, mainly tracker, but none have really worked well.

I use Grsync a lot for backups. I like the way it functions, on command, and will backup incremental data without having to transfer the whole image each time.

My question is, is there a similar equivalent in file indexing. Something that will index, on command, and index incrementally when files are moved around or changes are saved? I don't want something that eats RAM all the time. I want to be able to run it when I choose and have it make changes to it's index based on what's changed since the last time I used it.

Any ideas?


See also: [http://askubuntu.com/questions/563824/is-there-an-intelligent-indexing-solution-that-is-the-equivalent-of-grsync-for-b](http://askubuntu.com/questions/563824/is-there-an-intelligent-indexing-solution-that-is-the-equivalent-of-grsync-for-b)

---

### Post by Irihapeti on 2014-12-20
Unison might do what you're looking for. It uses a modified version of rsync, which is designed to backup only changes. It can be run on a local network or machine, or over ssh. There's a GUI available.

There are more details at [http://www.cis.upenn.edu/~bcpierce/unison/index.html](http://www.cis.upenn.edu/~bcpierce/unison/index.html)  Like many of these things, they can take a bit of setting up.

I've been using it for a few years on my home network and I'm happy with it.

---

### Post by YQ002lc2 on 2014-12-20
I'm sorry, I typed backup when I meant to type index!
I've edited my post. 
Nonetheless, thank you for sharing the information you did about Unison. Very interesting!

---

### Post by oldos2er on 2014-12-21
You can set up [recoll]("http://www.lesbonscomptes.com/recoll/") to use real time indexing, which will re-index files when they are changed.

---

### Post by sgage on 2014-12-21
> **oldos2er said:**
> You can set up [recoll]("http://www.lesbonscomptes.com/recoll/") to use real time indexing, which will re-index files when they are changed.

I second the motion for recoll - I've been using it for years. I've tried a lot of different indexer/search tools, and it seems to me to be the most reliable, the fastest, and least heavy on resource use.

---

### Post by YQ002lc2 on 2014-12-22
Thank you oldos2er and sgage for your suggestion or recoll. 
From [http://www.lesbonscomptes.com/recoll/download.html](http://www.lesbonscomptes.com/recoll/download.html), I added the ppa and installed recoll:


          sudo add-apt-repository ppa:recoll-backports/recoll-1.15-on
          sudo apt-get update
          sudo apt-get install recoll

I'm still playing with it and trying to find some Traditional Chinese, Thai, Korean, Japanese, Devanagari, Russian,....language support.  I'll try to update after I'm more familiar with it.

Other suggestions are still welcome, as well. Especially if they contain broad multilingual support. 

Thanks again! Ubuntu forums is the best!

---

### Post by oldos2er on 2014-12-22
Afraid I can't help with the language support; hopefully someone else can.

---

