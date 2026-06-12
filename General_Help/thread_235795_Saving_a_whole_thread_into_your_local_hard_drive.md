---
title: "Saving a whole thread into your local hard drive"
date: 2006-08-13
forum: General Help
---

### Post by jordilin on 2006-08-13
Is there a way to capture a whole thread in ubuntuforums and save it into your local hard drive for future reference? I've been thinking of wget, but I'm afraid that's not possible.

---

### Post by Tomosaur on 2006-08-13
Yes it is, at least for single paged thread anyway. Say I want to save this thread:

```

wget -p http://www.ubuntuforums.org/showthread.php?t=235795

```

You would then open the file called "showthread.php?t=235795" in your browser.

---

### Post by jordilin on 2006-08-13
> **Tomosaur said:**
> Yes it is, at least for single paged thread anyway. Say I want to save this thread:

```

wget -p http://www.ubuntuforums.org/showthread.php?t=235795

```

You would then open the file called "showthread.php?t=235795" in your browser.

Not only for a single paged thread. The pages that follow only append the "&page=n" to the original url. So, with a little imagination we can come up with a script that passes the n pages to wget.

---

### Post by Tomosaur on 2006-08-13
Unfortunately I can't just this minute, kinda busy (only on here because I'm taking a break :P) If nobody comes back and helps you out I'll see what I can do, but you may have to wait a while unless you know what you're doing.

---

### Post by 23meg on 2006-08-13
Check out the Scrapbook extension if you use Firefox.

---

### Post by jordilin on 2006-08-13
> **23meg said:**
> Check out the Scrapbook extension if you use Firefox.

Yes, I thought about Scrapbook (which is great) but when you have multiple pages, you have to download them all manually. I was thinking of sth more automatic.

---

### Post by Tomosaur on 2006-08-13
I started working on a script which will hopefully work. It's very hackish atm but it's looking fairly promising. I'll get back to you.

---

### Post by Tomosaur on 2006-08-13
I can't believe I actually got this to work.

A few things you need to know:
1) Put this script into a directory. You'll need to open it and save it as a .sh file
2) CD to the directory you saved it in and run it like this:
```

sh threadDL.sh <url>

```
So say I wanted to download this thread, I'd use:
```

sh threadDL http://www.ubuntuforums.org/showthread.php?t=235795

```
Pay careful attention to the URL. It must be the FIRST PAGE of the thread you wish to download, or it won't work at all.

2) A folder will be created called [www.ubuntuforums.org](www.ubuntuforums.org), with all the relevant files inside.

3) If you want to download a new thread, you must move the ENTIRE [www.ubuntuforums.org](www.ubuntuforums.org) folder to somewhere COMPLETELY DIFFERENT. You cannot have any other directory in the same place as the script file, or it won't work.

4) For some reason, you can't open the files properly from the terminal. You must open firefox, select File > Open File, go to the [www.ubuntuforums.org](www.ubuntuforums.org) folder, and select the first page. If you downloaded this thread, the first page would be 'showthread.php?t=235795'.

5) The links will not work, if you want to go to the next page, you'll have to do File > Open File again.

Script is attached below.

---

### Post by jordilin on 2006-08-14
> **Tomosaur said:**
> I can't believe I actually got this to work.

A few things you need to know:
1) Put this script into a directory. You'll need to open it and save it as a .sh file
2) CD to the directory you saved it in and run it like this:
```

sh threadDL.sh <url>

```
So say I wanted to download this thread, I'd use:
```

sh threadDL http://www.ubuntuforums.org/showthread.php?t=235795

```
Pay careful attention to the URL. It must be the FIRST PAGE of the thread you wish to download, or it won't work at all.

2) A folder will be created called [www.ubuntuforums.org](www.ubuntuforums.org), with all the relevant files inside.

3) If you want to download a new thread, you must move the ENTIRE [www.ubuntuforums.org](www.ubuntuforums.org) folder to somewhere COMPLETELY DIFFERENT. You cannot have any other directory in the same place as the script file, or it won't work.

4) For some reason, you can't open the files properly from the terminal. You must open firefox, select File > Open File, go to the [www.ubuntuforums.org](www.ubuntuforums.org) folder, and select the first page. If you downloaded this thread, the first page would be 'showthread.php?t=235795'.

5) The links will not work, if you want to go to the next page, you'll have to do File > Open File again.

Script is attached below.

You are very good!! When I try to download a 2 page thread it downloads three pages. Tomosaur, try to download a 2 page thread like this one and see if you get three pages:
[http://www.ubuntuforums.org/showthread.php?t=235739](http://www.ubuntuforums.org/showthread.php?t=235739)
it needs a little tweak and finished. :D

---

### Post by jordilin on 2006-08-14
Solved, in the 22th line of the script must be:
```
while [ "$currPg" -lt "$pages" ]

```
instead of "le"

Fantastic. Tomosaur, Thanks!!

---

### Post by Tomosaur on 2006-08-14
Here's a new version, which opens all your downloaded pages into firefox (each page gets its own tab. A little irritating, but it's better than clicking 'File > Open File' all the time.

Dunno how useful it is to you, I just felt like playing around :P

---

### Post by hoowe on 2006-08-14
You can also use ```
wget "http://www.ubuntuforums.org/showthread.php?t=235795&pp=1000"
``` to catch the 1000 first post i one thread.

---

### Post by Tomosaur on 2006-08-14
:O nice, cheers.

---

### Post by jordilin on 2006-08-14
> **Tomosaur said:**
> Here's a new version, which opens all your downloaded pages into firefox (each page gets its own tab. A little irritating, but it's better than clicking 'File > Open File' all the time.

Dunno how useful it is to you, I just felt like playing around :P

Really nice!!! thanks indeed.

---

### Post by jordilin on 2006-08-14
> **hoowe said:**
> You can also use ```
wget "http://www.ubuntuforums.org/showthread.php?t=235795&pp=1000"
``` to catch the 1000 first post i one thread.

Pasting [http://www.ubuntuforums.org/showthread.php?t=235795&pp=1000](http://www.ubuntuforums.org/showthread.php?t=235795&pp=1000) in the firefox url bar it shows you the 1000 posts in one page, but wget does not catch the whole page with these 1000 posts. But, the pp=1000 trick is terribly effective when using the ScrapBook Firefox extension to catch the whole page with these 1000 posts.

---

