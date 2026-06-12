---
title: "nzb download questionsa"
date: 2007-02-28
forum: General Help
---

### Post by fearevilleet on 2007-02-28
Hello,

I have been downloading nzb with grabit running under wine. I just upgraded to giganews ssl encrypted access but grabit dose not support ssl connections. Dose any have have a good nzb downloader that support ssl encryption that will run natively under edgy?

---

### Post by pirothezero on 2007-03-03
You may want to try sabnzbd...I just switched to it last night from hellanzb, it may or may not do SSL though. I haven't seen an option for it. I too use giganews just not the diamond account.

---

### Post by lionel47 on 2007-06-07
Where can I find instructions on how to use SABnzbd?  I don't get it.

---

### Post by Martje_001 on 2007-07-14
Search for 'SABnzbd for Linux' on google

---

### Post by fearevilleet on 2007-07-14
[Here is a good how to]("http://ubuntuforums.org/showthread.php?t=169749&highlight=hellanzb") for hellana nzb which is much better in my option.

---

### Post by Martje_001 on 2007-07-14
Do not install it on that way! Use 'sudo aptitude install hellanzb par2 rar' instead.

---

### Post by fearevilleet on 2007-07-14
lol sorry, i installed it awhile ago and used that walk through. But it is hands down the best program for nzb. I seriously watch more tv now that I download nzbs from newsbin, it really puts torrents to shame

---

### Post by Martje_001 on 2007-07-15
Me too :P

---

### Post by leguman on 2007-08-01
you should try Pan, the new version can deal with nzb files
check out this tutorial about [usenet binaries]("http://linux-is-sexy.blogspot.com/2005/12/usenet-binaries-with-linux-tutorial.html") with linux

---

### Post by dasbooter on 2007-08-02
pan can also do a few things via the command line:

NZB Batch Options
  --nzb file1 file2 ...    Process nzb files without launching all of Pan.
  -o path, --output=path   Path to save attachments listed in the nzb files.
  --no-gui                 Only show console output, not the download queue.

I suppose that you could set up some cron jobs to automate everything but it still looks as though hellanzb might be a bit more elegant although allot more difficult to set up. I suppose one could use an rss feed somehow with hellanzb and have everything downloaded automatically fixed and unrared so you could just bring it up on whatever media server device you are using.

I would like to see a rewrite of the how to that would show how all this could be done. 

install (pretty easy now that it is in the repos)

configure the config file ( a little break down of the stuff in there)

how to actually configure it to start automatically (probably different ways ,maybe session config in gnome, advantages or disadvantages of each way)

different ways to interface with hellanzb ( so many options, maybe one of each web, command line, screen(not familiar with this command at all), tty

maybe something on secure remote use would be nice

maybe something on how to set up an rss feed to work with hellanzb

Big order I know more of a wish list I guess but  I bet there are some pretty slick set ups out there and I would be interested in hearing about them.

---

