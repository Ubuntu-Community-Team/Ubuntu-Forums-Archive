---
title: "where's this download going?"
date: 2017-02-05
forum: General Help
---

### Post by sks24 on 2017-02-05
I'm downloading the content from a site for the site's editor of the site using 

```
wget --wait=20 --limit-rate=20K -r -p -U Chrome http://www.[sample].com/
```

The terminal says that the file is saving to "'[sample].com/index.html?feed=rss2"

I think this is going to take awhile - there are over 500 pages on the site. In any case, three questions:

1) where will I find this file after it's downloaded?
2) will the file contain a bunch of discrete files in the original format - .docs, .jpegs, - or will it just be one big plain text file?  
3) will the original URL for the pages be somewhere in the download

And I guess a fourth question: the site is currently archived in at archive.org. Will it stay there even if his web hosting company - it's zoobits - takes down his page? The problem is that they're saying he's past a 1gb limit and they are going to delete some of his content, but the customer can't get anybody to answer emails or the phone to find what what they - the customer - is supposed to do. On top of that, the site editor tried to change his Wordpress password, and now they can't get into their site to back it up. It's a total mess, basically.

I would give you the site URL but I don't want to do that until this download is finished.  

Thanks,
Scott

---

### Post by Habitual on 2017-02-05
the directory you are in.

---

### Post by Perfect Storm on 2017-02-05
Properly your home directory if you havn't change directory.

---

### Post by howefield on 2017-02-05
> **sks24 said:**
> where will I find this file after it's downloaded?

As said above, you'll find the files in the directory from which you run the wget command, by default /home. If you want to specify a download location use the -P option, eg..

```
wget --wait=20 --limit-rate=20K -r -p -U Chrome http://www.[sample].com/ -P ~/Downloads
```

> will the file contain a bunch of discrete files in the original format - .docs, .jpegs, - or will it just be one big plain text file?

You should get all the constituent parts of the website in original format, if I understand you correctly. In any event you should be able to open the downloads folder as it is coming in and see what is being written.
  
> will the original URL for the pages be somewhere in the download

I think the folder containing the files will be named similarly to the website, so it will be obvious.

> And I guess a fourth question: the site is currently archived in at archive.org. Will it stay there even if his web hosting company - it's zoobits - takes down his page?

Yes, although sometimes you don't get all the website archived, you'll can visit archive.org and see how it looks on various dates.. it'll stay that way even if the hosting company removes the hosting from their servers. 

> I would give you the site URL but I don't want to do that until this download is finished.

Can't see how that would be useful, or even wanted.

---

### Post by sks24 on 2017-02-06
Thanks so much to all of you for taking the time to respond to my questions. Everything seems to be in order.

---

